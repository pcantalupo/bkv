Genome assembly ViralProj14074: https://www.ncbi.nlm.nih.gov/data-hub/genome/GCF_000837865.1/
RefSeq FTP site: https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/837/865/GCF_000837865.1_ViralProj14074/
RefSeq GTF file direct link: https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/837/865/GCF_000837865.1_ViralProj14074/GCF_000837865.1_ViralProj14074_genomic.gtf.gz

# create a RefSeq GTF without the VERSION number
sed 's/NC_001538.1/NC_001538/g' GCF_000837865.1_ViralProj14074_genomic.gtf > GCF_000837865_ViralProj14074_genomic.gtf

Since the RefSeq GTF file (GCF_000837865.1_ViralProj14074_genomic.gtf)
doesn't contain transcript and exon features, I replaced the CDS,
start_codon and stop_codon features with transcript and exon features.  I
changed the cryptic gene_ids like BKVPyVgp1 to common gene names like LTAg,
VP1, etc...  I removed several unnecessary attribute fields (i.e.  gbkey,
etc...).  The output file from all this is: NC_001538.gtf


The 'new' gtf file is my ongoing attempt to add the second exon of the Small T transcript.

NC_001538.noOverlapRegions.noVP3.gtf - derivate of NC_001538.gtf where I
1. changed sT annotation to only the sT unique region in the intron
2. changed VP2 annotation to only the VP2 unique region upstream of VP1 (VP2
overlaps ~115bp of VP1 at VP1 5' end).
3. removed VP3



# Created a Gencode format GTF file:
# 1. added gene_type "protein_coding" to the 9th column (2/1/2021). Did this for running nf-core/rnaseq v3.0
~/bin/addcol.pl -p -1 -v 'gene_type "protein_coding"' NC_001538.gtf | perl -pe 's/;\t/; /' > NC_001538_Gencode.gtf
~/bin/addcol.pl -p -1 -v 'gene_type "protein_coding"' NC_001538.noOverlapRegions.noVP3.gtf | perl -pe 's/;\t/; /' > NC_001538.noOverlapRegions.noVP3_Gencode.gtf
# 5. manually change transcript_ids to match common gene names (8/18/2021)



# Test that resulting Gencode compatible version of GTF works with RSEM:
module load rsem/1.3.1
mkdir rsem
rsem-prepare-reference --gtf NC_001538_Gencode.gtf NC_001538.1.fa rsem/bkv


