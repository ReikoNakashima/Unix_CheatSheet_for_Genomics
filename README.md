# Unix_CheatSheet_for_Genomics
Useful unix codes for genomics data. It uses samtools and other computational tools to extract information.

## Read length
Read length distribution in a fastq.gz file.
```
zcat input.fastq.gz | awk '{if(NR%4==2) print length($1)}' | sort -n | uniq -c > read_length.txt

```

Read length distribution (mapped reads only) in a bam file. 
```
samtools view -F 4 input.bam | awk '{print length($10)}' > read_length.txt
```

## Remove carriage return in a file
```
tr -d '\r' < a_file.txt > new.txt && mv new.txt a_file.txt
```

## Grep a pattern and look up a certain line in a file
```
grep -n "CM000681.2_Homo_sapiens_chromosome_19,_GRCh38_re" file.txt 
```

```
awk 'FNR>=100 && FNR<=200' file.txt
```
