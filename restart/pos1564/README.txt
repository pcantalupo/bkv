# Restart the BKV genome at position 1564. So, move the first 1563bp from the beginning to the end
#  this restarts genome at the ATG of VP1 (position 1564 is the "A" in "ATG")
samtools faidx ../../NC_001538.fa NC_001538:1564-5153 > 1.fa
samtools faidx ../../NC_001538.fa NC_001538:1-1563 > 2.fa
cat <(echo ">NC_001538") <(cat 1.fa 2.fa | grep -v '^>') | ~/bin/seq2fasta.pl > NC_001538_pos1564.fa
gzip -c NC_001538_pos1564.fa > NC_001538_pos1564.fa.gz


# Manually construct the GTF file.
#   subtract 1563 from the coordinates in the ../../NC_001538_Gencode.gtf file (commit 3f1bceef790c)
#     - then add 5153 if the value is negative
#     - for VP2 and VP3, set the end value to 5153
#     - create new entries for VP2b and VP3b that start at pos1 and end at 116
diff ../../NC_001538_Gencode.gtf NC_001538_pos1564_Gencode.gtf

