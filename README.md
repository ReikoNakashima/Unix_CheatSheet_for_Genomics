# Unix_CheatSheet_for_Genomics
Useful unix codes for genomics data

Read length distribution in fastq.gz file
```
zcat $input_file | awk '{if(NR%4==2) print length($1)}' | sort -n | uniq -c > read_length.txt

```
