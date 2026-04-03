## The GTF format

Here, you will work with a GTF file: gencode.v44.basic.annotation.gene_only.gtf

This specific GTF file contains all known human genes according to the GENCODE consortium. 

The GTF format is as follows: 

```
Column 1: chromosome
Column 2: source
Column 3: feature
Column 4: start
Column 5: end
Column 6: score
Column 7: strand
Column 8: frame
Column 9: info
```

For example:

```
chr1	HAVANA	gene	11869	14409	.	+	.	gene_id "ENSG00000290825.1"; gene_type "lncRNA"; gene_name "DDX11L2"; level 2; tag "overlaps_pseudogene";
chr1	HAVANA	gene	12010	13670	.	+	.	gene_id "ENSG00000223972.6"; gene_type "transcribed_unprocessed_pseudogene"; gene_name "DDX11L1"; level 2; hgnc_id "HGNC:37102"; havana_gene "OTTHUMG00000000961.2";
chr1	HAVANA	gene	14404	29570	.	-	.	gene_id "ENSG00000227232.5"; gene_type "unprocessed_pseudogene"; gene_name "WASH7P"; level 2; hgnc_id "HGNC:38034"; havana_gene "OTTHUMG00000000958.1";
chr1	ENSEMBL	gene	17369	17436	.	-	.	gene_id "ENSG00000278267.1"; gene_type "miRNA"; gene_name "MIR6859-1"; level 3; hgnc_id "HGNC:50039";
```

Similar to a bed file, the GTF file contains genomic coordinates (chromosome, start and end) of different genomic features. 

In this file, the only feature you have are genes. Each row is a different gene.

For example, the first row corresponds to gene DDX11L2, located on chromosome 1, starts at position 11869 and is 14409-11869=2540 bases long

Please note that all the columns are tab-separated, however, the INFO field consists of semicolon-separated key-value pairs; values are space-separated within each key-value pair.

The info field contains a lot of information about the genes such as gene type, the gene name and id, and other less commonly-used id's for this gene. 

**IMPORTANT**

This file is large, so you should not perform calculations on the login node. Use a computing or interactive node (qrsh). 

## Instructions 

First, download or transfer the GTF file to Hoffman2.

Hint: You can download individual files from Github, but you can also download the entire repository if that's easier. 

You will write a shell script with the name format "W1_assignment_FIRSTNAME_LASTNAME.sh" and write code for each task. for example: 

```
# Task 1: how many genes are there in the GTF file? 
ng=$(less gencode.v44.basic.annotation.gene_only.gtf | wc -l)
echo "T1: There are ${ng} genes"
```

The main difference with the quiz is that now, you are writting a shell script instead of a plain text file. 
Make sure the answers are provided with code and that the tasks promtps are commented i.e. # as shown in the example above.

## Tasks 

1. Create a new GTF file with the coordinates (start and end) shifted 10 bases to the right e.g. 50 --> 60
2. Substitute the ";" separator with tab ("\t") in the new GTF file. 
3. After the substitution above, not all rows may have the same number of columns. How can we check if the number of tab-separated columns *per line* is consistent throughout the whole file?
4. Some genes don't have a proper gene name and are simply assigned a gene_id (which starts with ENSG000) in the gene_name field (e.g. gene_name "ENSG00000239906"). Which chromosome has the most unnamed genes? 
5. Chromosome 6 contains the HLA gene family. The names of the genes from this family start with the prefix "HLA-". List all the HLA gene (only the names) in the GTF file. 
6. Add arguments to make your shell script a [submission script](https://www.hoffman2.idre.ucla.edu/Using-H2/Computing/Computing.html#how-to-build-a-submission-script) runable with qsub. Use command-line argument `#$ -o log_answers.FIRSTNAME_LASTNAME.txt` to direct your output to this file.

## Submission

You only need to copy your shell file  "W1_assignment_FIRSTNAME_LASTNAME.sh" to `/u/scratch/g/giovas`. Same way you submitted the Quiz. 

I will submit each of your scripts to the cluster and check your answers in your log file: log_answers.FIRSTNAME_LASTNAME.txt

```
qsub W1_assignment_FIRSTNAME_LASTNAME.sh
```
You can run this command from your end to check your output and make sure all the commands run well.

**Make sure your shell script has the right permision (chmod 745)**. Otherwise I cannot read it nor qsub it.

## Questions?

Feel free to reach out: giovas@ucla.edu

