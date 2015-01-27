#Work Flow/Plan for RAD Seq Pipeline#

----------
## STACKS ##
The program STACKS is used to filter, demultiplex, and synthesize genotype patterns from RAD Seq data. Each step below will talk about a different function of the STACKS package and what it produces in both analysis and file types. 
 
## Raw Data to Single Sample FASTQ ##

Raw data delivered from Illumina comes stripped of primer sequences but leaves the remaining barcodes intact. 

This data needs filtering/demultiplexing using a function called *process_radtags*. 

This function searches the raw data for the unique barcodes provided in a TSV file by the user. After finding each barcode it also checks for the associated restriction enzyme rad tag (unique restriction site based on the enzyme used, for my purposes Sbf1). If it identifies both sequences the "read" of total sequence information for that line is compiled in a sequence fastq file associated with the barcode in a samples directory. I will in future runs of this process associate the barcode with the sample info as the function can rename fastq files with names provided in the TSV file. 

**function:** *process_radtags*

**process:** demultiplex reads, filter for quality

**output:** .fastq, sample folders, logfile

----------

## Denovo Mapping and Genotyping ##
STACKS has been developed with reproducibility and ease of functionality in mind. The authors have created several pipeline scripts that call together multiple functions in proper order to produce a database of all information synthesized from sequence data. The basic two pipelines are *denovo_map.pl* and *ref_map.pl*. The latter of the two requires a reference map to align sequence reads to. Since I don't have a fully realized reference map, I will instead use *denovo_map.pl* to independently align my sequence information into a functional map for each individual. 

*denovo_map.pl* utilizes three functions within STACKS to build information for genotyping. 

The first is *ustacks* which builds loci and calls SNPs from each fastq file entered based on related rad tags (cut sites that appear similar in multiple individuals).

The second is *cstacks* which catalogs all loci from the sequence information for individuals (most commonly from parents but since we are doing crosses here this will just be from the population).

The third is  