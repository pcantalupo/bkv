$ makeblastdb -version
makeblastdb: 2.6.0+
 Package: blast 2.6.0, build Dec  7 2016 15:12:09

# parse_seqids param needed for 'blastdbcmd -entry' (see issue#1)
makeblastdb -dbtype nucl -parse_seqids -in ../NC_001538.1.fa -out NC_001538.1

