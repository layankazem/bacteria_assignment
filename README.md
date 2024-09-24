# Log into ibex

 ```bash
ssh kazemlz@ilogin . ibex . kaust .edu. sa
```


# Create a Directory
## Create a new directory where you will store the data files and perform the analysis. Then exit.
 ```bash
mkdir data-bacteria-assignment
cd data-bacteria-assignment
exit
```


# Copy the File to IBEX
## Navigate to the File Location. Then use the scp command to copy the file to IBEX.
 ```bash
cd "C:\Users\layan\Downloads\bacteria\bacteria_assignment"
scp ncbi_datasetzip.zip kazemlz@ilogin.ibex.kaust.edu.sa:~/data-bacteria-assignment/
```


# Navigate to the Directory and Unzip the File
## Log into IBEX. Navigate to the directory where the file was transferred. Verify.
 ```bash
ssh kazemlz@ilogin.ibex.kaust.edu.sa
cd ~/data-bacteria-assignment
unzip ncbi_datasetzip.zip
ls
```


# Navigate to the Data directory
## Make sure you have the right files. 
 ```bash
cd ncbi_dataset
ls
cd data
ls
```


# What is the smallest and what is the largest genome in the ones you just downloaded? How large are these genomes?
```bash
cut -f 1,11 data_summary.tsv > size.tsv
tail -n +2 size.tsv | sort -t$'\t' -k2 -n | head -n 1
tail -n +2 size.tsv | sort -t$'\t' -k2 -n | tail -n 1
```
## answer: Smallest: Chlamydia trachomatis D/UW-3/CX 1042519   Largest: Vibrio cholerae O1 biovar El Tor str. N16961    4033464 
###### Received help from Ashhad for this code


# Find the number of genomes that contain at least two "c" in the species name.
```bash
tail -n +2 data_summary_new.tsv | cut -f 1 | grep -i "c.*c" | sort | uniq | wc -l
```
## answer: 7
###### Received help from Manal for this code


# Find the number of genomes that contain at least two "c" but do not contain the word "coccus."
```bash
tail -n +2 data_summary_new.tsv | cut -f 1 | grep -i "c.*c" | grep -vi "coccus" | sort | uniq | wc -l
```
## answer: 5
###### Received help from Manal for this code


# Find the number of genomes that contain at least two "c" but do not contain the word "coccus."
```bash
find ncbi_dataset/data/ -name "*.fna" -size +3M | wc -l
```
## answer: 6



