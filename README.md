# Week-3

# Dtata Wrangling

#copy the file

scp ~/Desktop/ncbi.zip fallatah@ilogin.ibex.kaust.edu.sa:/home/fallatah

# unzip
[fallatah@login509-02-l ~]$ unzip ncbi.zip 
Archive:  ncbi.zip
  inflating: README.md               
  inflating: ncbi_dataset/data/data_summary.tsv  
  inflating: ncbi_dataset/data/assembly_data_report.jsonl  
  inflating: ncbi_dataset/data/GCA_000006745.1/GCA_000006745.1_ASM674v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000006825.1/GCA_000006825.1_ASM682v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000006865.1/GCA_000006865.1_ASM686v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000007125.1/GCA_000007125.1_ASM712v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008545.1/GCA_000008545.1_ASM854v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008565.1/GCA_000008565.1_ASM856v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008605.1/GCA_000008605.1_ASM860v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008625.1/GCA_000008625.1_ASM862v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008725.1/GCA_000008725.1_ASM872v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008785.1/GCA_000008785.1_ASM878v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008525.1/GCA_000008525.1_ASM852v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000008745.1/GCA_000008745.1_ASM874v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000027305.1/GCA_000027305.1_ASM2730v1_genomic.fna  
  inflating: ncbi_dataset/data/GCA_000091085.2/GCA_000091085.2_ASM9108v2_genomic.fna  
  inflating: ncbi_dataset/data/dataset_catalog.json  
  inflating: md5sum.txt    
# smllest and largesr
[fallatah@login509-02-l ~]$ cd ~/ncbi_dataset/data/
#input:
[fallatah@login509-02-l data]$ tail -n +2 data_summary.tsv | sort -t$'\t' -k11 -n | head -n 1

# output:
Chlamydia trachomatis D/UW-3/CX		strain: D/UW-3/CX	272561	ASM872v1	GCA_000008725.1	GenBank	Annotation submitted by ChGP	Complete Genome	1042519	1042519	2001-01-09	939	PRJNA45	SAMN02603114
[fallatah@login509-02-l data]$ 

# largest:
[fallatah@login509-02-l data]$ sort -t$'\t' -k11 -n data_summary.tsv | tail -n 1
Vibrio cholerae O1 biovar El Tor str. N16961		strain: N16961	243277	ASM674v1	GCA_000006745.1	GenBank	Annotation submitted by TIGComplete Genome	2961149	4033464	2001-01-09	4007	PRJNA36	SAMN02603969
# smallest and  lrgest size
[fallatah@login509-02-l data]$ tail -n +2 data_summary.tsv | sort -t$'\t' -k11 -n | head -n 1 | cut -f 11

1042519

[fallatah@login509-02-l data]$ sort -t$'\t' -k11 -n data_summary.tsv | tail -n 1 | cut -f 11

4033464

# coccus
[fallatah@login509-02-l week3]$  grep -E "\b\w*c\w*c\w*\b" *.fna | wc -l

7

[fallatah@login509-02-l week3]$ grep -E "\b\w*c\w*c\w*\b" *.fna | grep -Ev "coccus" | wc -l

2

# size
[fallatah@login509-02-l week3]$ find . -name "*.fna" -size +3M | wc -l

3
