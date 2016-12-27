# Unbalanced-Huffman-Tree (UHT-compression)

UHT package includes the following tools:
Analysis tools:
	- SHT_compress 
		This tool applies the compression based on the standard Huffman tree.
	- UHT_compress
		This tool applies the compression based on an unbalanced Huffman tree.

Main compression tool:
	- UHTL_compress
		This tool applies the compression based on an unbalanced Huffman tree where the kmers that are selected for encoding must contain at least one occurrence of the base with the least frequency. Also, 
		multiple compression method, MUHTL, is applicable in this script.

Decompression tool:
	- UHT_decompress
		This tool is the tool that decompress any of the above compression methods.


--Software version--
This is version 1.0.0, supporting compressing of genome fasta files.

--Prerequisite--
heap package 


--Installation--
The tool is built using python and it is already in binaries; there is no need for installation.

--Running the Tools--

- SHT_compress 
	- Run command:
		./dist/SHT_compress/SHT_compress genome_file.fasta n
		where n is the number of kmers with maximum frequencies. The lengths of kmers to be encoded is 1-10. 
	- Output/s:
		genome_file_1.uht 

- UHT_compress
 
	- Run command:
		./dist/UHT_compress/UHT_compress genome_file.fasta 
		The maximum length of kmers to be encoded is 1, 3-10; 2-mers is not included as this kmer length will be encoded using 5 bits, in case this kmer contain the the least frequent base (which will be encoded using 3 bits) 
		then encoding this kmer length is not feasible in the first place and effect the (k+1 or more)-mers encoding.  
	- Output/s:
		genome_file_1.uht 

- UHTL_compress
	- Run command:
		./dist/UHTL_compress/UHTL_compress genome_file.fasta p
		where p is the number of partitions to be used. The lengths of kmers to be encoded is 1-10. 
		Note that empirical results show that the best compression ratio achieved by multiple partitions encoding is when the length of each partition is around 1Mbp.

	- Output/s:
		genome_file_1.uht if the number of selected partitions is 1, or 
		genome_file_1.uht, genome_file_2.uht, ..,genome_file_{p}.uht where p is the number of selected partitions. 
		
- UHT_decompress 

	- Run command:
		./dist/UHT_decompress/UHT_decompress genome_file_1.uht
	- Output/s:
		genome_file_1.fasta 

--Contacts--
For more queries or questions, please contact
Anas Al-okaily, anas.al-okaily@uconn.edu


Last update: 12/2016



