# Useful-Scripts-Oneliners
Set of useful Scripts and Oneliners

# Convert Large fasta to bits of 100 bp fasta without overlaps

grep -v '^>' input.fa | tr -d '\n' | fold -w 100 | nl -n rz -s '_' | sed "s|^|>|" | sed "s|_|\n|"  > output.fa
