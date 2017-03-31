# Discussion of pool seq papers to help us evaluate our own protocol

## March 31st 2017
[Kofler et al. 2016](http://www.g3journal.org/content/6/11/3507#sec-1). Suitability of different mapping algorithms
- no single one removed all artefacts.
- novalign and bwa mem did pretty well for Fst.
- Best to use two and use intersection of SNPs in VCF. The suggest bowtie2(g) and novalign(l) seemed to be the best combination.
- There way of intersection is looking at the p-values for Fisher exact test at each site for each mapped. Use the p-value which is less significant. We (SM PK, ID) all think this may be too conservative as it could throw out real sites. Perhaps averaging values? 
- Is a better possibility to compare VCFs (VCFtools) for all alleles and average frequencies or something?

