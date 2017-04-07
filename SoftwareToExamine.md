# Just some links to software, tools etc. to help analyse pooled sequence data.


## Drosophila Genome Nexus
[Drosophila Genome Nexus](https://academic.oup.com/mbe/article/33/12/3308/2450097/A-Thousand-Fly-Genomes-An-Expanded-Drosophila). Links to over 1000 Drosophila melanogaster genomes, and importantly the variants detected among these! [here](http://www.johnpool.net/genomes.html) is the link to the file.


## Generally useful tools for sequence QC
[NGSCheckMate: software for validating sample identity in next-generation sequencing studies within and across data types](https://academic.oup.com/nar/article-lookup/doi/10.1093/nar/gkx193). github repo is [here](https://github.com/parklab/NGSCheckMate)

## Viewing mapped reads, polymorphisms etc (for SAM, BAM, VCF etc).
[blog post reviewing different alignment viewers ones](http://jermdemo.blogspot.ca/2010/08/ngs-viewers-reviewed.html)

[tview] see samtools

[IGV](http://software.broadinstitute.org/software/igv/)

[tablet](https://ics.hutton.ac.uk/tablet/)

[IGB](http://bioviz.org/igb/)

[highlander](http://sites.uclouvain.be/highlander/) Also variant calling..

[pybamview](http://melissagymrek.com/pybamview/)

[readXplorer](https://www.uni-giessen.de/fbz/fb08/Inst/bioinformatik/software/ReadXplorer/access)

[ving](http://vm-gb.curie.fr/ving/) In R/bioconductor

[alview](https://github.com/NCIP/alview)

[seqmonk](http://www.bioinformatics.babraham.ac.uk/projects/seqmonk/)


## Identifying polymorphisms (that work well for pools).
[Evaluation of variant detection software for pooled next-generation sequence data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4518579/). A couple of important points from this paper. First GATK works well, but takes a long time even with small pools, and fails with large pools like we have used. While VarScan has low FP rates, its sensitivity and detecting true SNPs was VERY LOW. CRISP and LoFreq do pretty well, but CRISP seems to edge out LoFreq for pools with larger number of samples. Everything is based on default parameters though.

[Best Practices for data preparation for calling SNPs](https://software.broadinstitute.org/gatk/best-practices/). Some parts are relevant (i.e. map to reference, mark duplicates, realign around small indels etc.). See [this](https://software.broadinstitute.org/gatk/img/BP_workflow_3.6.png)

[FreeBayes](https://github.com/ekg/freebayes). Seems to have a good option for pooled data.

[VarScan](http://dkoboldt.github.io/varscan/). Seems like it has an active community.

[CRISP](https://github.com/vibansal/crisp/).Comprehensive Read Analysis for Identification of SNVs (and short indels) from Pooled sequencing data. While the original method is from 2010, it seems (based on github repo) to still be in active use? Not clear. It sounds like compiling it with the new version of SAMtools may not work.

[LoFreq](http://csb5.github.io/lofreq/citation/)

[snape](https://www.ncbi.nlm.nih.gov/pubmed/22992255). Not such an active community?

[SNPeff](http://snpeff.sourceforge.net/). Genetic variant annotation and effect prediction toolbox. Not for identifying SNPs, but for annotating them.

## Using two different mapping tools and comparing VCFs
[Suitability of Different Mapping Algorithms for Genome-wide Polymorphism Scans with Pool-Seq Data](https://www.ncbi.nlm.nih.gov/pubmed/27613752)

## allele frequencies and basic evolutionary parameters.
[SNPGenie](https://www.ncbi.nlm.nih.gov/pubmed/26227143): estimating evolutionary parameters to detect natural selection using pooled next-generation sequencing data. Link to code on github [here](https://github.com/hugheslab/snpgenie)

[Genotype-Frequency Estimation from High-Throughput Sequencing Data](http://www.genetics.org/content/201/2/473.short). Link to software is [here](https://github.com/Takahiro-Maruki/Package-GFE). 

[estimating N_E from pooled sequencing data](https://github.com/ThomasTaus/Nest). Paper is [here](Estimating the Effective Population Size from Temporal Allele Frequency Changes in Experimental Evolution)

[correcting biases in allele frequency estimation with some machine learning approaches](https://www.ncbi.nlm.nih.gov/pubmed/26156142)

[LDx](http://petrov.stanford.edu/pdfs/86.pdf) Estimation of Linkage Disequilibrium from HighThroughput
Pooled Resequencing Data

## Some reasons to be optimistic (or not) about pooled sequencing.
[Validation of SNP allele frequencies determined by pooled next-generation sequencing in natural populations of a non-model plant species](https://www.ncbi.nlm.nih.gov/pubmed/24244686)

(https://www.ncbi.nlm.nih.gov/pubmed/23730833)

[another paper demonstrating pretty good concordance between pool seq and individual sequencing for allele frequencies](https://www.ncbi.nlm.nih.gov/pubmed/26461136)

[Next Generation Sequencing of Pooled Samples: Guideline for Variants' Filtering](https://www.ncbi.nlm.nih.gov/pubmed/27670852)

[Estimation of population allele frequencies from next-generation sequencing data: pool-versus individual-based genotyping](https://www.ncbi.nlm.nih.gov/pubmed/23730833)

[several library prep strategies give similar allele frequencies](https://www.ncbi.nlm.nih.gov/pubmed/26014582)


### and some or nots

[Population-genetic inference from pooled-sequencing data](https://www.ncbi.nlm.nih.gov/pubmed/24787620). The paper "Genotype-Frequency Estimation from High-Throughput Sequencing Data" uses the method discussed here I think.

[The Power to Detect Quantitative Trait Loci Using Resequenced, Experimentally Evolved Populations of Diploid, Sexual Organisms ](https://academic.oup.com/mbe/article/31/4/1040/1108505/The-Power-to-Detect-Quantitative-Trait-Loci-Using). Power analyses for E&R experiments with pooled data.

## Assorted other things

[The Marth Lab](http://marthlab.org/software.html) seems to have lots of new tools in development for variant detection etc..
