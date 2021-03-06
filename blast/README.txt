$ makeblastdb -version
makeblastdb: 2.7.1+
 Package: blast 2.7.1, build Oct 18 2017 19:57:24

# parse_seqids param needed for 'blastdbcmd -entry' (see issue#1)
makeblastdb -dbtype nucl -parse_seqids -in ../NC_001538.1.fa -out NC_001538.1

