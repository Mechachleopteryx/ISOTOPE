# ISOTOPE
ISOform-guided prediction of epiTOPEs in cancer

![ISOTOPE_pipeline.jpg](https://user-images.githubusercontent.com/23315833/103201760-f84bcc00-48f0-11eb-9c3e-613cfc7f4b1a.png)

The following pipeline have been developed for the identification of cancer-specific splicing-derived epitopes from RNA-seq. 

The pipeline is divided in 4 parts, depending the event type the user wants to obtain:

   * Pseudoexons (**Exonizations**)
   * New exons skipping events (**Neoskipping**)
   * Alternative splice site (**A5_A3**)
   * Intron retention (**IR**)
   
For the obtention of exonizations, neoskipping and A5_A3 events, the first input are the read counts mapped to all posible junctions in the genome. This file (readCounts.tab) is created through Junckey (https://github.com/comprna/Junckey#1-format-star-output). From these junctions, ISOTOPE will obtain all splicing events expressed significantly.

For the identification of IR events, a normalized expression like TPMs for all possible intronic regionic is needed. To this end, we first created a transcriptome with all possible intronic regions using kma (https://github.com/pachterlab/kma). By using a pseudoalligner like Salmon (https://combine-lab.github.io/salmon/) or Kallisto (https://pachterlab.github.io/kallisto/about) the quantification to these regions could be applied. With these values, ISOTOPE will filtered out intron retention events lowly expressed.


The workflow is quite similar between all event types, but there are some specificities important to take into account 
   
The user must run each of the 3 parts sequentially. The scripts are ready to be run in a slurm cluster. Until all jobs generated by a part are finished do not run the following part. In the wiki (https://github.com/comprna/ISOTOPE/wiki) section we have detailled how to run each of these steps. If you have a query related with the tool or any problem regarding the execution, please create an issue in the repository. 
