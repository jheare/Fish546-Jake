# Data Record #
----
### Raw Sequence Data ###
**directory** OWL

**Raw Files**

lane1_ NoIndex_ L001_ R1_ 001.fastq.gz

lane1_ NoIndex_ L001_ R1_ 002.fastq.gz

lane1_ NoIndex_ L001_ R1_ 003.fastq.gz

lane1_ NoIndex_ L001_ R1_ 004.fastq.gz

lane1_ NoIndex_ L001_ R1_ 005.fastq.gz

lane1_ NoIndex_ L001_ R1_ 006.fastq.gz

lane1_ NoIndex_ L001_ R1_ 007.fastq.gz

lane1_ NoIndex_ L001_ R1_ 008.fastq.gz

lane1_ NoIndex_ L001_ R1_ 009.fastq.gz

lane1_ NoIndex_ L001_ R1_ 010.fastq.gz

lane1_ NoIndex_ L001_ R1_ 011.fastq.gz

lane1_ NoIndex_ L001_ R1_ 012.fastq.gz

lane1_ NoIndex_ L001_ R1_ 013.fastq.gz

lane1_ NoIndex_ L001_ R1_ 014.fastq.gz

*fastq files for lane reads are stored on OWL as gzipped files.*

**directory** Hummingbird ./srlab/samples

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

*Working fastq files work are stored on Hummingbird and are gunzipped*

**directory** repository ./Fish546-Jake/data

**Barcode File**

decradbarcodes1.txt

*barcode file containing unique barcode and sample names. Created in Excel from a google sheets file provided by Sam*
##
### process_radtags output ###
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

*96 fastq files created from the barcode index in *process_radtags**

**directory** repository ./Fish546-Jake/data

**process radtags log file**
process_ radtags.log

*10 Samples used for *ustacks* selected via highest number of retained reads.* 

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
### ustacks output ###
*all files produces are in the standard tab delimited format .tsv, substitute ID for appropriate sample name*

**directory** Hummingbird ./srlab/ustacks

**Assembled Loci file**
ID.tags.tsv (10 files)

**SNP calls file**
ID.snps.tsv (10 files)

**Haplotypes/Alleles file**
ID.alleles.tsv (10 files)
##
### cstacks output ###
**directory** Hummingbird ./srlab/ustacks

**Loci catalog file**
batch_ 1.catalog.tags.tsv

**SNP catalog file**
batch_ 1.catalog.snps.tsv

**Allele catalog file**
batch_ 1.catalog.alleles.tsv

##
### sstacks output ###
**directory** Hummingbird ./srlab/ustacks

**Matches file**
ID.matches.tsv (10 files)

##
### populations output ###
*Each sample file in ustacks was designated with a different SQL batch number (1-10), substitute these numbers for the appropriate file*
**directory** Hummingbir ./srlab/ustacks

**Summary Population Statistics**
batch_ X.sumstats.tsv (10 files)

**Summary of Summary Statistics**
batch_ X.sumstats_ summary.tsv (10 files)

**FST Calculations**
batch_ X.fst_ Y-Z.tsv (10 files)

**Haplotype statistics**
batch_ X.hapstats.tsv (10 files)

**Haplotype FST calculations**
batch_ X.phistats.tsv (10 files)

**Haplotype FST calculations for pairwise comparisons**
batch_ X.phistats_ Y-Z.tsv (10 files)

**Full sequence haplotypes for population members**
batch_ X.fa (10 files)

**Raw genotypes foe each nucleotide**
batch_ X.genomics.tsv (10 files)

**Variant Call Format file**
ID.VCF (10 files)