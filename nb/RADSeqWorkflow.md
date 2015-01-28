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

**output:** ID.fastq, sample folders, logfile

----------

## Denovo Mapping ##
STACKS has been developed with reproducibility and ease of functionality in mind. The authors have created several pipeline scripts that call together multiple functions in proper order to produce a database of all information synthesized from sequence data. The basic two pipelines are *denovo_map.pl* and *ref_map.pl*. The latter of the two requires a reference map to align sequence reads to. Since I don't have a fully realized reference map, I will instead use *denovo_map.pl* to independently align my sequence information into a functional map for each individual. 

*denovo_map.pl* utilizes three functions within STACKS to build information for genotyping and population genetics analysis. 

The first is *ustacks* which builds loci and calls SNPs from each fastq file entered based on related rad tags (cut sites that appear similar in multiple individuals).

**function:** *ustacks*

**process:** build loci and call SNPs

**output:** ID.tags.tsv (assembled loci), ID.snps.tsv (SNP calls), ID.alleles.tsv (Haplotypes,alleles from loci)

***

The second is *cstacks* which catalogs all loci from the sequence information for sampled individuals.

**function:** *cstacks*

**process:** creates catalog of loci, SNPs, alleles

**output:** BatchID.catalog.tags.tsv (loci catalog), BatchID.catalog.snps.tsv (SNP catalog), BatchID.catalog.alleles.tsv (allele catalog)

***

The third is  *sstacks* which will match all samples against the general population catalogue.

**function:** *sstacks*

**process:** compares general samples with population catalogue

**output**: ID.matches.tsv (matches to the catalog)

***
## Population Genetics ##
Part of the *denovo_map.pl* pipeline is the *populations* function which takes information created in the first three functions and generates summary statistics for unique populations as identified by a population map (population maps are a TSV file with sample names in the first column and population identifier in the second). 

*populations* calculates heterozygosity, FST, and FIS based on loci, SNP, and allele information. Output information can also be converted into VCF or other popular file types for use with programs such as STRUCTURE. 

**function:** *populations*

**process:** calculates summary statistics for population genetics

**output:** batch_ ID.sumstats.tsv (summary statistics for each population), batch_ ID.sumstats _summary.tsv (summary of summary statistics for each population), batch_ ID.fst_ Y-Z.tsv (FST calculations for pairwise comparisons of populations), batch_ ID.hapstats.tsv (Haplotype based summary statistics for each locus in each population), batch_ ID.phistats.tsv (Haplotype based FST calculations for all populations), batch_ ID.phistats_ Y-Z.tsv (Haplotype based FST calculations for pairwise population comparisons), batch_ ID.fa (full sequence haplotypes for population members), batch_ X.genomics.tsv (Raw genotypes for each nucleotide in the dataset), ID.VCF

***
## Summary ##

After receiving Raw data from Illumina the following is performed:

1. *process_radtags* demultiplexes and filters reads
2. *denovo_map.pl* pipeline includes
3. *ustacks* builds loci, SNPs, alleles
4. *cstacks* creates population catalogs for loci, SNPs, alleles
5. *sstacks* compares individuals to catalogs
6. *populations* generates summary statistics for population genetics as well as create files for use with other programs such as STRUCTURE.

The end result of this is to produce relevant statistics about the differences between populations as well as create files which will make visualize of these differences easier. 

***
## STRUCTURE and GenePop ##
Once VCF files have been created the program STRUCTURE will be used to visualize relatedness of populations. GenePop will use GenePop files to vizualize genotypes within the populations. 