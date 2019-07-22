# Welcome to MAIRA!

In first place, MAIRA has been developed to support the portable ONT (Oxford Nanopore Technology) MinION long-read sequencer having great potential for studying microbial communities directly in the field. Such an analysis in the field requires software that performs well when there is limited access to the internet and computational power is restricted to that offered by a laptop. MAIRA is a software package meeting all these requirements. It is designed to run on a (high-end) laptop (without internet access) and aims at identifying present bacterial species, and their genes, with high accuracy and speed.

# Getting started

As MAIRA is written in Java, installing the program can be done quite easily through one of its installer programs (see next section). If your operating system is LINUX you should double check if you are running the Java runtime environment version 12 (or later). Otherwise you do not have to care on that.

Upon startup, MAIRA will first load its own version of the NCBI taxonomy tree (which takes a couple of seconds). Once being initialized, MAIRA is ready to kick off an analysis of long-read data. To produce good results, keep in mind that your reads should have an average read length of at least 3000bp. 

There are three different ways the read data can be provided to MAIRA. 
- Choose "File -> Run on -> FASTA File" to analyse the set of reads in a specifc FASTA/FASTQ file. 
- Choose "File -> Run on -> FASTA Folder" to analyse all FASTA/FASTQ files of a specific folder.
- Choose "File -> Run on -> monitored Folder" to automatically analyse all FASTA/FASTQ files being submitted to a specific folder. This is of particular interest for running a real-time analysis of reads produced by an ONT sequencing device (such as an ONT MinION for example).

To kick off the analysis you first have to download MAIRAs specific SQL database (11GB) as well as a set of index files for the aligner you plan to use (about 200GB).  Here, you can either use our Java-based built-in aligner ELLA or the external aligner LAST (see http://last.cbrc.jp/). ELLA has the advantage that it is ready to run out of the box (which means you do not have to install anything else) whereas LAST has to be configured by your own but in return provides the better runtime. It's up to you!

In the "Advanced" Tab of the setting window you can further specify the sensitivity of the marker database directly affecting the accuracy of the genus classifaction step. Keep in mind that the higher the sensitivity the larger the total runtime gets. To our expericience, the "low" sensitivity version of the marker databse still produces good reliable results. Further, you can specify the size of the read batches being analysed in each cycle. By default this is set to 10,000.

While running, MAIRA continously updates the probabilities of certain genera being present in the underlying read data. To control the runtime, you can choose which genera should be further analysed down to species level. This can be done by setting the traffic lights in the genus table (the table at the top on the left-hand side) to either red, yellow, or green:

- **red:** The red light prevents MAIRA from analysing a genus further down to species level. This should be used to avoid spending runtime on genera that are not of deeper interest.
-  **yellow:** The yellow light means that MAIRA automatically sets the genus to green if its probability is larger than 0.8. In the beginning, all genera are automatically set to yellow.
- **green:** The green light kicks off an analysis of a genus down to species level. 

MAIRA displays all detected genera and species directly within the NCBI taxonomic tree. You can manipualte the appearance of that tree by setting specific thresholds to genus and species nodes by opening the "Taxonomy Bar" at the bottom of the tree pane.

To save your result, you can either just store the tree data ("File -> Save -> Save Tree") or all alignment information ("File -> Save -> Save Project"). Note that so far we have not implemented any export functions. In near future, however, you will be able to extract specific sets of reads and alignments to further analyse your data. 

# Installing MAIRA and obtaining databases

MAIRA is written in Java and requires a Java runtime environment version 12 or later, freely available from www.java.org. Note that the Windows and MacOS X installers both contain a bundled JRE and so separate installation of Java should not be necessary for these two operating systems.

To install MAIRA locally on your computer simply choose an installer program following the weblink below. During the installing process you will have to decide how much working memory you want to provide to MAIRA. Notice that this strongly depends on the aligner you plan to use. If you decide to use our built-in aligner ELLA you should provide at least 14GB, otherwise if you decide to use LAST 4GB should be enough (as LAST we run outside of the VM). If you want to stay flexible and your working device has enough memory (>24GB), we recommend to choose 16GB.

**[Download MAIRA Installers](http://ab.inf.uni-tuebingen.de/data/software/maira/download/welcome.html)** 

To analyze a set of reads you further have to download the MAIRA database (11GB).

**[Download MAIRA database](http://maira.informatik.uni-tuebingen.de/maira/web_archive/maira.db)**

Moreover, depending on the aligner you plan tu use, you have to further download either our pre-computed ELLA databases or our pre-computed LAST databases (each around 200GB).

**[Download ELLA databases](http://maira.informatik.uni-tuebingen.de/maira/web_archive/ella_aligner_db.zip)**, **[Download LAST databases](http://maira.informatik.uni-tuebingen.de/maira/web_archive/last_aligner_db.zip)**

# Publication

MAIRA hasn't been published yet. Currently, however, we are working hard on several manuscripts, which we hope to get published until the end of 2019. As soon as we have any news we will notify you right here on MAIRAs GitHub repository.

