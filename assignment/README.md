## The GTF format

Here, you will work with a GTF file: gencode.v44.basic.annotation.gene_only.gtf

This specific GTF file contains all known human genes according to the GENCODE consortium. 

The GTF format is as follows: 

```
CHROM	SOURCE	FEAT	START	END	SCORE	STRAND	FRAME	INFO

chr1	HAVANA	gene	11869	14409	.	+	.	gene_id "ENSG00000290825.1"; gene_type "lncRNA"; gene_name "DDX11L2"; level 2; tag "overlaps_pseudogene";
chr1	HAVANA	gene	12010	13670	.	+	.	gene_id "ENSG00000223972.6"; gene_type "transcribed_unprocessed_pseudogene"; gene_name "DDX11L1"; level 2; hgnc_id "HGNC:37102"; havana_gene "OTTHUMG00000000961.2";
chr1	HAVANA	gene	14404	29570	.	-	.	gene_id "ENSG00000227232.5"; gene_type "unprocessed_pseudogene"; gene_name "WASH7P"; level 2; hgnc_id "HGNC:38034"; havana_gene "OTTHUMG00000000958.1";
chr1	ENSEMBL	gene	17369	17436	.	-	.	gene_id "ENSG00000278267.1"; gene_type "miRNA"; gene_name "MIR6859-1"; level 3; hgnc_id "HGNC:50039";
```

Similar to a bed file, the GTF file contains genomic coordinates (chromosome, start and end) of different genomic features. 

In this file, the only feature you have are genes. Each row is a different gene.

For example, the first row corresponds to gene DDX11L2, located on chromosome 1, starts at position 11869 and is 14409-11869=2540 bases long

Please note that all the columns are tab-separated, however, the INFO field consists of semicolon-separated key-value pairs; values are space-separated within each key-value pair.

** IMPORTANT **

This file is large, so you should not perform calculations on the login node. Use a computing or interactive node (qrsh). 

## Instructions 

First, download or trasnfer the GTF file to Hoffman2.

You will write a shell script with the format "W1_assignment_FIRSTNAME_LASTNAME.sh" and write code for each task. for example: 

```
# Task 1: how many genes are there in the GTF file? 
ng=$(less gencode.v44.basic.annotation.gene_only.gtf | wc -l)
echo "T1: There are $ng genes"
```

## Tasks 

1. Which chromosome contains the most genes? 
2. Which chromosome contains the least? 
3. In total, are there more genes on the positive (+) or negative (-) strand? 
4. Given that the human genome contains 3.1 billion (3.1 * 10^9) bases. What percentage of the genome is covered by genes? (assume no overlapping coordinates)
5. In total, are there more "protein_coding" genes or "lncRNA" genes? 
6. Which gene is the longest?  
7. Split the current GTF into two files based on the 'SOURCE' column. Create one GTF that only contains `HAVANA` source and one GTF that contains `ENSEMBL` source. Use an if-statement to check which of these files has more genes. Print a message such as "HAVANA contains more genes" or "ENSEMBL contains more genes". 
8. Add arguments to make your shell script a submission script runable with qsub. Use -o joblog.$USER

## Submission

You only need to submit your shell file  "W1_assignment_FIRSTNAME_LASTNAME.sh" to **/u/scratch/g/giovas**. Same way you submitted the Quiz. 
I will submit each of your scripts to the cluster and check yout answers in your log file: joblog.$USER 


