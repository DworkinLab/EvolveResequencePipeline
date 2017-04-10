# Discussion of pool seq papers to help us evaluate our own protocol

## March 31st 2017
[Kofler et al. 2016](http://www.g3journal.org/content/6/11/3507#sec-1). Suitability of different mapping algorithms
- no single one removed all artefacts.
- novalign and bwa mem did pretty well for Fst.
- Best to use two and use intersection of SNPs in VCF. The suggest bowtie2(g) and novalign(l) seemed to be the best combination.
- There way of intersection is looking at the p-values for Fisher exact test at each site for each mapped. Use the p-value which is less significant. We (SM PK, ID) all think this may be too conservative as it could throw out real sites. Perhaps averaging values? 
- Is a better possibility to compare VCFs (VCFtools) for all alleles and average frequencies or something?
- Worth noting that the free version of novalign is limited in how many cores can be used (grrr.).


## April 5th 2017: Contrasting the differential computational pipelines from different research groups for pooled resequencing.

### Petrov lab (ID)
I examined the protocols in two studies.

[Bergland et al.](http://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1004775). 2014. Genomic Evidence of Rapid and Stable Adaptive Oscillations over Seasonal Time Scales in Drosophila. PLoS Genetics.

The motivation was to examine how seasonal variation may result in "balanced polymorphism" (as there is no constant optimum), and may 
maintain SGV in populations.

They resequenced samples of *D. melanogaster* from populations sampled between 2003-2010. Each population sampled was between 50-200 individuals. Isofemales lines were made and progeny from this (around gen 5) were pooled to generate template DNA. 

1. Mapping to D.mel reference (v 5.39) using bwa (v 0.5.9-r16)
  - allowing for a maximum insert size of 800bp and no more than 10 mismatches/100bp. See below as they only used SNPs previously identified in the DGRP (so they were ok with higher overall error rates). i.e.
  ```{bash}
  bwa aln -t10 -f r1.sai sample1.fastq
  bwa aln -t10 -f r2.sai sample2.fasta
  bwa sampe dmel_ref.fasta r1.fastq.trimmed.sai r2.fastq.trimmed.sai r1.fastq.trimmed r2.fastq.trimmed \
    | samtools view -Sb - > /yourdir/samples.bam
  ```
 Files wre then indexed as normal `samtools index ...` and sorted as normal `samtools sort ...`.
 
2. PCR duplicates were removed using samtools (v0.1.18) with the bam files.
```{bash}
samtools rmdup ...
```

3. local re-alignment around indels using GATK (v1.4-25). The new versions may not support this anymore (check manual).

```{bash}
java -Xmx8g -jar ~/GenomeAnalysisTK-1.4-25-g23e7f1b/GenomeAnalysisTK.jar -I \ 
  samples.sorted.dedup.bam -R dmel_ref.fasta -T RealignerTargetCreator -o \
  ./new_alignments/indelTargets/samples.intervals &
wait

java -Xmx8g -jar ~/GenomeAnalysisTK-1.4-25-g23e7f1b/GenomeAnalysisTK.jar -I \ 
  samples.sorted.dedup.bam -R dmel_ref.fasta -T IndelRealigner -targetIntervals \ 
  ./new_alignments/indelTargets/samples.intervals -o /dirs/m/samples.realign.bam & \
  wait

```
4. Mapped SNPs and short indels using CRISP, excluding reads with base or mapping qualities below 10. The justification for using 10 (as opposed to 20 which is more common) is because they only used common SNPs that had previously been identified in DGRP.
5. SNPs mapping to repetitive regions such as microsatellites and transposable elements, identified in the standard RepeatMasker library for *D. melanogaster* (obtained from http://genome.ucsc.edu) were excluded from analysis as were SNPs within 5 bp of polymorphic indels.
6. SNPs with average minor allele frequency across all populations less than 15%, with minimum per-population coverage less than 10× or maximum per-population coverage greater than 400× were removed from analysis.
7. Finally, to ensure that the examined SNPs were not artifacts of our pooled resequencing, we removed any SNP not present in the SNP tables provided by freeze 2 of the DGRP. Of the 1,500,000 SNPs initially identified, ∼500,000 SNPs remained after applying these filters.
8. SNPs were annotated using SNPeff version 2.0.
9. F_ST estimates were done as shown in the paper, but corrected for both the number of sampled chromosomes and number of reads at any site.

The second paper from the Petrov lab was:
[Machado et al.](http://onlinelibrary.wiley.com/doi/10.1111/mec.13446/abstract). Comparative population genomics of latitudinal variation in Drosophila simulans and Drosophila melanogaster. Mol. Ecol.

Motivation: Examine the influence of latitudinal variation and its impact with respect to selection and demography (using population genomics).

Some of the work was individual flies. For the pools, these used two samples. These were a few of the samples from the above study.
They also used a correction for effective number of chromosomes (N_C) in the sample (see the paper).
1. mapped raw reads (no trimming I guess) to D.mel genome v5.5 using bwa aln (v 0.7.9) and sampe with default parameters.
2. Reads mapping to autosomes were down-sampled to match the N_C of the X chromosomes.
3. Applied a Pool-seq error model.

I emailed the lead author (Heather Machado) and she confirmed that the SNP calls in this were those from the study above. She also mentioned that she is now using VarScan for SNP calling for pooled data.
### Schlotterer lab (PK)

### Pool lab (SM)
[Bastide et al.](http://genetics.org/content/early/2016/09/15/genetics.116.192492). 2016. A Variable Genetic Architecture of Melanic Evolution in Drosophila melanogaster.

Point of study was to find the genetic basis of melanism.

Three dark pigemented populations were crossed with light color Zambian populations. Eight reciprocal crosses were set up for each of the combinations of crossed populations and the progeny were interbred until F20. F20 flies were scored for pigmentation and the most extreme 30 females were pooled together for sequencing for either dark or light color.

  - Library prep -> 100bp read lengths with 300bp inserts 
  - Mapped to D.mel reference (v 5.57) using BWA (v 0.6.2-r126) 
  - BAM files remapped using Stampy (v1.0.21)
  - Reads filtered for mapping quality of 20 and proper pairs with samtools (v0.1.18)
  - Picard (v1.109) use to remove PCR duplicates
  - Alignment around indels improved with GATK (v3.2)
  - Generated mpileups with PoPoolation2 (v1.201)
  - Calculated ancestry differentiation with their own [perl scripts](https://github.com/JohnEPool/SIBSAM1)

