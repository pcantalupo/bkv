The 'new' gtf file is my ongoing attempt to add the second exon of the Small T transcript.

NC_001538.noOverlapRegions.noVP3.gtf - derivate of NC_001538.gtf where I
1. changed sT annotation to only the sT unique region in the intron
2. changed VP2 annotation to only the VP2 unique region upstream of VP1 (VP2
overlaps ~115bp of VP1 at VP1 5' end).
3. removed VP3



# Created a Gencode format GTF file by adding gene_type "protein_coding" to
# the 9th column (2/1/2021). Did this for running nf-core/rnaseq v3.0
~/bin/addcol.pl -p -1 -v 'gene_type "protein_coding"' NC_001538.gtf | perl -pe 's/;\t/; /' > NC_001538_Gencode.gtf
~/bin/addcol.pl -p -1 -v 'gene_type "protein_coding"' NC_001538.noOverlapRegions.noVP3.gtf | perl -pe 's/;\t/; /' > NC_001538.noOverlapRegions.noVP3_Gencode.gtf



