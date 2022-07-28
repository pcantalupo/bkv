# Version 5 blast database

makeblastdb -dbtype nucl -parse_seqids -in ../NC_001538.1.fa -out NC_001538.1
blastdbcmd -info -db NC_001538.1
 Database: ../NC_001538.1.fa	1 sequences; 5,153 total bases
 Date: Jul 28, 2022  9:00 AM	Longest sequence: 5,153 bases
 BLASTDB Version: 5


# Version 4 (deprecated)

$ makeblastdb -version
makeblastdb: 2.7.1+
 Package: blast 2.7.1, build Oct 18 2017 19:57:24

# parse_seqids param needed for 'blastdbcmd -entry' (see issue#1)
makeblastdb -dbtype nucl -parse_seqids -in ../NC_001538.1.fa -out NC_001538.1

