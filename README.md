# salk-lab

# (1). CpG island, distribution plot and LDSC
Read paper: https://genomebiology.biomedcentral.com/articles/10.1186/s13059-021-02335-w#Sec10
Title: Human brain region-specific variably methylated regions are enriched for heritability of distinct neuropsychiatric traits

## Task 1: Downloading of CpG islands and CpG shores
Following method part "Annotation and external data", download and prepare the CpG islands and CpG shores files.
Expected format (separated by tab):
chrom   start   end ID

Download & Format CpG islands:
1. Head to http://genome.ucsc.edu/cgi-bin/hgTables
2. Select the following options:
    * **Genome:** Human
    * **Assembly:** GRCh38/hg38
    * **Group:** Regulation
    * **Track:** CpG Islands
    * **Table:** cpgIslandExt
    * **Region:** Genome
    * **Output format:** Selected fields from primary and related tables
    * **Output filename:** CpG_Island
    * **Output field separator:** tsv (tab-separated)
    * **File type returned:** Plain text
3. Click "Get Output"
4. Select the following fields:
    * chrom
    * chromStart
    * chromEnd
    * cpgNum
6. Click "Get Output"
7. Run following Python script to format file
``` python
import pandas as pd

df = pd.read_csv("CpG_Island", sep="\t")

df = df.rename(columns={"#chrom" : "chrom", "chromStart" : "start", "chromEnd" : "end"})

df["ID"] = df["chrom"] + ":" + df["start"].astype(str) + "-" + df["end"].astype(str)

df["strand"] = "+"

df = df[["chrom", "start", "end", "ID", "cpgNum", "strand"]]

df.to_csv("CpG_Island", sep="\t", index=False)
```

## Task 2: Fig 1E
We may need to plot the same figure (Fig 1E) on our own dataset. So, please read the method and figure out how to plot this kind of figure and prepare the code. The input file will be given as bigwig format.
In the "Availability of data and materials" part, the uploaded all the code onto github, you may need to look into their code.
Not sure which software/tools did they use to plot this figure, but I know that deeptools can be used to plot similar figure.

## Task 3: LDSC
Following the method "Stratified linkage disequilibrium score regression" of this paper, prepare the input and code to run LDSC.
The input should be DMR, GWAS summary statistics and model file, output should be the enriched traits (phenotype).
You can download the DMR from the supplementary files of this paper as input.


# Setup anvil
link: https://www.rcac.purdue.edu/knowledge/anvil/access/login/sshkeys


# example code
```python
import os,sys
import matplotlib.pylab as plt


print("..")
```
