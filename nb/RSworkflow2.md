# Stacks Workflow #
### Work Platform ###
All analysis performed using Stacks 1.24 on OSX 10.9.5 remote server. Connected to server using PuTTY 0.63 ssh manager for windows and a local host tunnel to access ipython notebooks. I used Python version 2.7.6 (Anaconda 1.9.2 (x86_64)) with IPython version 2.1.0.

You can download Stacks at its [host website](http://creskolab.uoregon.edu/stacks/) for use with data. Though the current version is 1.27 and requires the use of SQLlite. 

### Processing radtags ###
Raw sequence data was returned in 14 gzipped fastq files. Copies of these files were placed on OWL for long term storage. Working versions were unzipped using gzip and then copied into a **Hummingbird/Users/srlab/lane1rad**. A tab delimited barcode file was also created to combine barcodes with the appropriate sample name in the  **Hummingbird/Users/srlab/Fish546-Jake/data** directory as a file called decradbarcodes1.txt. This barcode file and fastq files were then processed with STACKS using a sub function called *process_radtags* which demultiplexed the data while removing reads with ambiguous barcodes and radtags. This program then output fastq files containing all the reads for each sample based on the barcode into **Hummingbird/Users/srlab/samples**. A log file produced by the program was then moved from the samples directory to the data directory for backup. While no errors are produced from this run, it only produces fastq files with barcodes instead of sample names.

**You can see a notebook of the *process_radtags* workflow [here](http://nbviewer.ipython.org/urls/raw.github.com/jheare/Fish546-Jake/master/nb/RAD-Seq%20Process.ipynb).**

### Denovo mapping ###
Fastq files produced from *process_radtags* were checked for quality. The top 10 samples containing more than 180k reads were then selected to run through each step of the *denovo_map.pl* pipeline. Sample fastq files can be found in **Hummingbird/Users/srlab/samples**. 
#### *ustacks* ####
First the samples were run through the *ustacks* function which assembled the loci for each sample producing a sample.tags.tsv file, then called for SNPs producing a sample.snps.tsv file, and finally determined haplotypes and alleles creating a sample.alleles.tsv. No errors were produced for *ustacks* as it needs no input file to discern populations. Files were placed into the directory **Hummingbird/Users/srlab/ustacks**. This creates approximately 30 files. 
#### *cstacks* ####
A population map tab delimited file produced outside of STACKS created with sample name and population designation. This file was then applied with the files produced from *ustacks* to *cstacks* to produce catalogs of all loci, snps, and haplotypes for each designated population in files Population.catalog.tags.tsv, Population.catalog.snps.tsv, Population.catalog.alleles.tsv. *cstacks* produced no error in this run but due to the lack of a population file it grouped all the selected samples into a single population catalog. Due to this, analysis during *sstacks* assumes no differences between samples and does not create catalogs around each population. Moving forward this only allows for *sstacks* and *populations* to treat all samples as sourced from a single population. The catalogs were output to the directory **Hummingbird/Users/srlab/ustacks.**
#### *sstacks* ####
Finally these catalogs were then used to compare individual samples to the population catalogs using the *sstacks* function which produced a matches file sample.matches.tsv. *sstacks* produces matches.tsv files for each sample only compared to the single population file. These files were output to **Hummingbird/Users/srlab/ustacks**

**You can see a notebook of the Denovo Mapping work [here](http://nbviewer.ipython.org/github/jheare/Fish546-Jake/blob/master/nb/Denovo%20Map%20Piecemeal.ipynb).**