# Just some random links to software to help with aspects of QC

## QC with raw reads etc...
[FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)

[FASTQCR](http://www.sthda.com/english/rpkgs/fastqcr/) Quality Control of Sequencing Data (aggregating info for many FastQC files).

[NGSCheckMate](https://github.com/parklab/NGSCheckMate) or identifying next generation sequencing (NGS) data files from the same individual.  (i.e. are the samples the ones you think they are).

[GenomeScope](https://github.com/schatzlab/genomescope) can infer the global properties of a genome from unassembled sequenced data


## QC SAM and BAM files
[samtools](http://www.htslib.org/). In particular samtools flagstat as a quick check.

[deeptools](https://deeptools.readthedocs.io/en/latest/) A python library with all sorts of nice functions for visualizing SAM and BAM files and pile ups for QCing

[samstat](http://samstat.sourceforge.net/). Very simple, and sometimes only works on bam files. However, the reports are really quite helpful, in particular with examining what might be going on if you have low mapping quality (MAPQ).

[qualimap](http://qualimap.bioinfo.cipf.es/). Qualimap examines sequencing alignment data in SAM/BAM files according to the features of the mapped reads and provides an overall view of the data that helps to the detect biases in the sequencing and/or mapping of the data and eases decision-making for further analysis. 

[MultiQC](https://github.com/ewels/MultiQC). Seems like a way of integrating and generating summary reports across many samples from raw reads to sam/bam to vcf. A bit like FASTQCR perhaps (?). 

[bedtools](https://github.com/arq5x/bedtools2). From description: bedtools utilities are a swiss-army knife of tools for a wide-range of genomics analysis tasks. The most widely-used tools enable genome arithmetic: that is, set theory on the genome. For example, bedtools allows one to intersect, merge, count, complement, and shuffle genomic intervals from multiple files in widely-used genomic file formats such as BAM, BED, GFF/GTF, VCF

[see here](https://omictools.com/quality-control6-category) for a list of other QC tools for reads.

