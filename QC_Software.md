# Just some random links to software to help with aspects of QC

## QC with raw reads etc...
[FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)

[FASTQCR](http://www.sthda.com/english/rpkgs/fastqcr/) Quality Control of Sequencing Data (aggregating info for many FastQC files).

[NGSCheckMate](https://github.com/parklab/NGSCheckMate) or identifying next generation sequencing (NGS) data files from the same individual.  (i.e. are the samples the ones you think they are).

[GenomeScope](https://github.com/schatzlab/genomescope) can infer the global properties of a genome from unassembled sequenced data


## QC SAM and BAM files
[samtools](http://www.htslib.org/). In particular samtools flagstat as a quick check.

[samstat](http://samstat.sourceforge.net/). Very simple, and sometimes only works on bam files. However, the reports are really quite helpful, in particular with examining what might be going on if you have low mapping quality (MAPQ).

[see here](https://omictools.com/quality-control6-category) for a list of other QC tools for reads.
