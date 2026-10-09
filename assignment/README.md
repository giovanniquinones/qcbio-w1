# Repeat Masker BED file
The file `RepeatMasker.hg38.bed` contains the coordinates of repeat elements on the human genome.

The columns are:

```
Chromosome  Start       End       Repeat_Class   Repeat_Family Strand
chr1        8388315     8388618   SINE           Alu           -
chr1        25165803    25166380  LINE           L1            +
chr1        33554185    33554483  SINE           Alu           -
chr1        41942894    41943205  SINE           Alu           -
```

Each repeat class, for example SINE, is divided into repeat families, for example Alu, MIR, tRNA, etc... 
