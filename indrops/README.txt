# added gene_biotype annotation to each row to make it work with Indrops
# (specifically RSEM since RSEM ignores genes that ARE NOT protein_coding)
perl -ne 'chomp; $_ .= q/ gene_biotype "protein_coding";/; print $_,$/' NC_001538.gtf > NC_001538.gene_biotype.gtf


# removed all genes except LTAg and VP1 in "EarlyLate" files since Indrops
# can only detect Early or Late gene expression in BKV
