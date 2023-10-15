# Restart the BKV genome at position 201. So, move the first 200bp from the beginning to the end
joe NC_001538.fa  ->  NC_001538_pos201.fa
gzip -c NC_001538_pos201.fa > NC_001538_pos201.fa.gz

# reduce coordinates by 200bp since I'm moving the first 200bp of the genome to the end
awk -F"\t" -v OFS="\t" '{$4-=200; $5-=200; print $0}' ../../NC_001538_Gencode.gtf > NC_001538_pos201_Gencode.gtf


