# Data Record #
##Change to narrative. Describe columns in TSV files as they pertain to the data.##
----
### Raw Sequence Data ###
Raw sequence data was returned in 14 gzipped fastq files. Copies of these files were placed on OWL for long term storage. Working versions were unzipped using gzip and then copied into a **Volumes/Data/Jake/lane1rad**.

**directory** Data ./Jake/lane1rad

**Work Files**

lane1_ NoIndex_ L001_ R1_ 001.fastq

lane1_ NoIndex_ L001_ R1_ 002.fastq

lane1_ NoIndex_ L001_ R1_ 003.fastq

lane1_ NoIndex_ L001_ R1_ 004.fastq

lane1_ NoIndex_ L001_ R1_ 005.fastq

lane1_ NoIndex_ L001_ R1_ 006.fastq

lane1_ NoIndex_ L001_ R1_ 007.fastq

lane1_ NoIndex_ L001_ R1_ 008.fastq

lane1_ NoIndex_ L001_ R1_ 009.fastq

lane1_ NoIndex_ L001_ R1_ 010.fastq

lane1_ NoIndex_ L001_ R1_ 011.fastq

lane1_ NoIndex_ L001_ R1_ 012.fastq

lane1_ NoIndex_ L001_ R1_ 013.fastq

lane1_ NoIndex_ L001_ R1_ 014.fastq

A tab delimited barcode file was also created to combine barcodes with the appropriate sample name in the  **Hummingbird/Users/srlab/Fish546-Jake/data** directory as a file called decradbarcodes1.txt. This barcode file and fastq files were then processed with STACKS using a sub function called *process_radtags* which demultiplexed the data while removing reads with ambiguous barcodes and radtags.

**directory** repository ./Fish546-Jake/data

**Barcode File**

decradbarcodes1.txt

##
### process_radtags output ###

This program then output fastq files containing all the reads for each sample based on the barcode into **Hummingbird/Users/srlab/samples**. 

**directory** Hummingbird ./srlab/samples

**processed fastq files**

sample_ CCCTAA.fq     sample_ GGTTTG.fq
sample_ AAACGG.fq     sample_ CCGAGG.fq     sample_ GTAAGT.fq
sample_ AACGTT.fq     sample_ CCGCAT.fq     sample_ GTATCC.fq
sample_ AACTGA.fq     sample_ CCTAAC.fq     sample_ GTCATC.fq
sample_ AAGACG.fq     sample_ CGAGGC.fq     sample_ GTGCCT.fq
sample_ AAGCTA.fq     sample_ CGCAGA.fq     sample_ GTGTAA.fq
sample_ AATATC.fq     sample_ CGCGTG.fq     sample_ GTTGGA.fq
sample_ AATGAG.fq     sample_ CGGTCC.fq     sample_ TAAGCT.fq
sample_ ACAAGA.fq     sample_ CGTCTA.fq     sample_ TAATTC.fq
sample_ ACAGCG.fq     sample_ CGTGAT.fq     sample_ TACACA.fq
sample_ ACATAC.fq     sample_ CTACAG.fq     sample_ TACGGG.fq
sample_ ACCATG.fq     sample_ CTCGCC.fq     sample_ TAGTAT.fq
sample_ ACCCCC.fq     sample_ CTGCGA.fq     sample_ TATCAC.fq
sample_ ACTCTT.fq     sample_ CTGGTT.fq     sample_ TCAAAG.fq
sample_ ACTGGC.fq     sample_ CTTATG.fq     sample_ TCCTGC.fq
sample_ AGCCAT.fq     sample_ CTTTGC.fq     sample_ TCGATT.fq
sample_ AGCGCA.fq     sample_ GAAATG.fq     sample_ TCGCCA.fq
sample_ AGGGTC.fq     sample_ GAACCA.fq     sample_ TCGGAC.fq
sample_ AGGTGT.fq     sample_ GACGAC.fq     sample_ TCTCGG.fq
sample_ AGTAGG.fq     sample_ GACTCT.fq     sample_ TCTTCT.fq
sample_ AGTTAA.fq     sample_ GAGAGA.fq     sample_ TGAACC.fq
sample_ ATAGTA.fq     sample_ GATCGT.fq     sample_ TGACAA.fq
sample_ ATCAAA.fq     sample_ GCAGAT.fq     sample_ TGCCCG.fq
sample_ ATGCAC.fq     sample_ GCATGG.fq     sample_ TGCTTA.fq
sample_ ATGTTG.fq     sample_ GCCGTA.fq     sample_ TGGGGA.fq
sample_ ATTCCG.fq     sample_ GCGACC.fq     sample_ TTATGA.fq
sample_ CAAAAA.fq     sample_ GCGCTG.fq     sample_ TTCCGT.fq
sample_ CAATCG.fq     sample_ GCTCAA.fq     sample_ TTCTAG.fq
sample_ CACCTC.fq     sample_ GGACTT.fq     sample_ TTGAGC.fq
sample_ CAGGCA.fq     sample_ GGCAAG.fq     sample_ TTTAAT.fq
sample_ CATACT.fq     sample_ GGGCGC.fq     sample_ TTTGTC.fq
sample_ CCATTT.fq     sample_ GGGGCG.fq
sample_ CCCGGT.fq     sample_ GGTACA.fq

A log file produced by the program was then moved from the samples directory to the data directory for backup. While no errors are produced from this run, it only produces fastq files with barcodes instead of sample names.

**directory** repository ./Fish546-Jake/data

**process radtags log file**
process_ radtags.log

### Samples for Stacks Process ###

Fastq files produced from *process_radtags* were checked for quality. The top 10 samples containing more than 180k reads were then selected to run through Stacks process. Sample fastq files can be found in **Hummingbird/Users/srlab/samples**.

**samples used**

sample_ CACCTC

sample_ CCCTAA

sample_ GCTCAA

sample_ GTGTAA

sample_ ACATAC

sample_ ACCATG

sample_ ACCCCC

sample_ CAAAAA

sample_ TACACA

sample_ CAGGCA

*in all subsequent references to these samples, they be referred to as ID instead of mentioning every individual file*
##
### ustacks ###
First the samples were run through the *ustacks* function which assembled the loci for each sample producing a sample.tags.tsv file, then called for SNPs producing a sample.snps.tsv file, and finally determined haplotypes and alleles creating a sample.alleles.tsv. No errors were produced for *ustacks* as it needs no input file to discern populations. Files were placed into the directory **Hummingbird/Users/srlab/ustacks**. This creates 30 files. 

| **Sample** 	|  **Reads** 	| **Mean Coverage** 	|  **St Dev** 	|
|:------:	|:------:	|:-------------:	|:-------:	|
| CACCTC 	|  79749 	|    9.77419    	|  21.343 	|
| CCCTAA 	| 162821 	|    15.5762    	| 54.4303 	|
| GCTCAA 	| 415583 	|    35.3757    	| 110.388 	|
| GTGTAA 	| 447678 	|    37.4178    	|  132.4  	|
| ACATAC 	| 615296 	|    48.1594    	| 113.335 	|
| ACCATG 	| 367241 	|    30.7252    	| 128.328 	|
| ACCCCC 	| 416392 	|    35.7519    	| 154.377 	|
| CAAAAA 	|  41575 	|    7.34319    	| 31.5243 	|
| TACACA 	|  6152  	|    5.97252    	| 18.3384 	|
| CAGGCA 	| 101739 	|    12.8119    	| 65.4695 	|

**directory** Hummingbird ./srlab/ustacks

**Assembled Loci file**
ID.tags.tsv (10 files)

**SNP calls file**
ID.snps.tsv (10 files)

**Haplotypes/Alleles file**
ID.alleles.tsv (10 files)
##
### cstacks output ###

A population map tab delimited file produced outside of STACKS created with sample name and population designation. This file was then applied with the files produced from *ustacks* to *cstacks* to produce catalogs of all loci, snps, and haplotypes for each designated population in files Population.catalog.tags.tsv, Population.catalog.snps.tsv, Population.catalog.alleles.tsv. *cstacks* produced no error in this run but due to the lack of a population file it grouped all the selected samples into a single population catalog. Due to this, analysis during *sstacks* assumes no differences between samples and does not create catalogs around each population. Moving forward this only allows for *sstacks* and *populations* to treat all samples as sourced from a single population. The catalogs were output to the directory **Hummingbird/Users/srlab/ustacks.**

| **Process** 	|   **Sample**  	| **K-mers** 	|  **Loci** 	|
|:-------:	|:---------:	|:------:	|:-----:	|
| cstacks 	| catalog 1 	|  32481 	| 28771 	|

**directory** Hummingbird ./srlab/ustacks

**Loci catalog file**
batch_ 1.catalog.tags.tsv

**SNP catalog file**
batch_ 1.catalog.snps.tsv

**Allele catalog file**
batch_ 1.catalog.alleles.tsv

##
### sstacks output ###

Finally these catalogs were then used to compare individual samples to the population catalogs using the *sstacks* function which produced a matches file sample.matches.tsv. *sstacks* produces matches.tsv files for each sample only compared to the single population file. These files were output to **Hummingbird/Users/srlab/ustacks**

| **Process** 	| **Sample** 	| **Matches** 	| **Haplotypes** 	|
|---------	|--------	|---------	|------------	|
| sstacks 	| CACCTC 	| 7498    	| 8274       	|
| sstacks 	| CCCTAA 	| 9721    	| 10873      	|
| sstacks 	| GCTCAA 	| 10983   	| 12330      	|
| sstacks 	| GTGTAA 	| 11200   	| 12608      	|
| sstacks 	| ACATAC 	| 11884   	| 13346      	|
| sstacks 	| ACCATG 	| 11123   	| 12517      	|
| sstacks 	| ACCCCC 	| 10873   	| 12278      	|
| sstacks 	| CAAAAA 	| 5135    	| 5575       	|
| sstacks 	| TACACA 	| 821     	| 905        	|
| sstacks 	| CAGGCA 	| 7367    	| 8170       	|

**directory** Hummingbird ./srlab/ustacks

**Matches file**
ID.matches.tsv (10 files)

