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
tr -d '\r' < infile.txt > new.txt && mv new.txt infile.txt
```

## Grep a pattern and look up certain lines in a file
```
grep -n "CM000681.2_Homo_sapiens_chromosome_19,_GRCh38_re" file.txt 
```
Looking up lines 100-200
```
awk 'FNR>=100 && FNR<=200' file.txt
```

## Set permission (read, write, and excecute) for a username
```
setfacl -m u:username:rwx Files
```

## Data storage to see file size in a directory
This will return file size for all files in the directory
```
du -h aFolder
```
If you like to see the total size of a directory,
```
du -s /home/myFolder
```
To see the usage in pharmsci project directory. The "blocks" column in the current usage.
```
mmlsquota --block-size auto -j pharmsciARD_ngs gpfs
```
