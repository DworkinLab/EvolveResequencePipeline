# Just some links to software to help analyse pooled sequence data.


## Viewing mapped reads, polymorphisms etc (for SAM, BAM, VCF etc).
[blog post reviewing different ones](http://jermdemo.blogspot.ca/2010/08/ngs-viewers-reviewed.html)

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
[Evaluation of variant detection software for pooled next-generation sequence data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4518579/)

[FreeBayes](https://github.com/ekg/freebayes). Seems to have a good option for pooled data.

[varscan](http://dkoboldt.github.io/varscan/). Seems like it has an active community.

[CRISP](https://github.com/vibansal/crisp/).Comprehensive Read Analysis for Identification of SNVs (and short indels) from Pooled sequencing data. While the original method is from 2010, it seems (based on github repo) to still be in active use? Not clear. It sounds like compiling it with the new version of SAMtools may not work.

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



## Assorted other things

[The Marth Lab](http://marthlab.org/software.html) seems to have lots of new tools in development for variant detection etc..
