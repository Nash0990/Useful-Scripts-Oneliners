# Useful-Scripts-Oneliners
Set of useful Scripts and Oneliners

# Convert Large fasta to bits of 100 bp fasta with/out overlaps

# Using sh 
grep -v '^>' input.fa | tr -d '\n' | fold -w 100 | nl -n rz -s '_' | sed "s|^|>|" | sed "s|_|\n|"  > output.fa

# Using pyfasta

pyfasta split -n 1 -k 100 -o 0 chr1.fa

-n Number of output files
-k length
-o Overlap

# Genbank to Fasta
|awk '/^ACCESSION   / {printf(">%s\n",$2);next;} /^ORIGIN/ {inseq=1;next;} /^\/\// {inseq=0;} {if(inseq==0) next; gsub(/[0-9 ]/,"",$0); printf("%s\n",$0);}' | head -n 30
