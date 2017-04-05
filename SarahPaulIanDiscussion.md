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
  - allowing for a maximum insert size of 800bp and no more than 10 mismatches/100bp.
2. PCR duplicates were removed using samtools (v0.1.18)
3. local re-alignment around indels using GATK (v1.4-25)
4. Mapped SNPs and short indels using CRISP, excluding reads with base or mapping qualities below 10. The justification for using 10 (as opposed to 20 which is more common) is because they only used common SNPs that had previously been identified in DGRP.
5. SNPs mapping to repetitive regions such as microsatellites and transposable elements, identified in the standard RepeatMasker library for *D. melanogaster* (obtained from http://genome.ucsc.edu) were excluded from analysis as were SNPs within 5 bp of polymorphic indels.
6. SNPs with average minor allele frequency across all populations less than 15%, with minimum per-population coverage less than 10× or maximum per-population coverage greater than 400× were removed from analysis.
7. Finally, to ensure that the examined SNPs were not artifacts of our pooled resequencing, we removed any SNP not present in the SNP tables provided by freeze 2 of the DGRP. Of the 1,500,000 SNPs initially identified, ∼500,000 SNPs remained after applying these filters.
8. SNPs were annotated using SNPeff version 2.0.
9. F_ST estimates were done as shown in the paper, but corrected for both the number of sampled chromosomes and number of reads at any site.



### Schlotterer lab (PK)

### Pool lab (SM)

