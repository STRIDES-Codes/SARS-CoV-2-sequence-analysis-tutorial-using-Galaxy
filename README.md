# SARS-CoV-2-sequence-analysis-tutorial-using-Galaxy

The aim of this project is to create a tutorial on SARS-CoV-2 sequence analysis using
Galaxy and ARTIC protocol Illumina sequencing data.

For some background, the [US CDC COVID-19 Genomic Epidemiology Toolkit](https://www.cdc.gov/amd/training/covid-19-gen-epi-toolkit.html) provides videos on "What is genomic epidemiology?" and "The SARS-CoV-2 genome". SARS-CoV-2 is the virus that causes the
disease COVID-19. The ARTIC sequencing protocol is described in this [video](https://www.youtube.com/watch?v=7733_Hs-VQo&feature=youtu.be) by Dr Josh Quick, taken from the [CLIMB-BIG-DATA / ARTICnetwork workshop](https://www.climb.ac.uk/artic-and-climb-big-data-joint-workshop/) in January 2021.

## Galaxy, Galaxy Training Network and the Galaxy Training materials

[Galaxy](https://galaxyproject.org/) is a web based environment for bioinformatics. The Galaxy Training Network (GTN) is an informal
collaboration of trainers who use Galaxy and contribute to the [Galaxy Training materials](https://training.galaxyproject.org/).

For an introduction to Galaxy, consult the [intro material](https://training.galaxyproject.org/training-material/topics/introduction/).

## Contributing to the Galaxy Training tutorials

The Galaxy Training website is built from a GitHub [repository](https://github.com/galaxyproject/training-material) using the Jekyll site builder. There are some guides on [to how to write tutorials and contribute](https://training.galaxyproject.org/training-material/topics/contributing/). Contributions can either be added via the command line (with a local copy of the training materials) or via the Github web interface.

You will need:

1. A [GitHub](https://github.com/) account

2. A [fork](https://www.earthdatascience.org/workshops/intro-version-control-git/about-forks/) of the Galaxy training material repository [https://github.com/galaxyproject/training-material](https://github.com/galaxyproject/training-material). This will be provided as part of the hackathon, *don't make your own fork for now*.

3. Either a local copy of the fork or a copy opened with [gitpod.io](https://gitpod.io).
  a. To make a local copy use `git clone`. *Warning:* This is a 2 GB download. You can reduce that size to about 1 GB by doing a shallow clone, i.e. `git clone --depth=1`.
  b. Using `gitpod` will be explained.

There is an existing tutorial, [From NCBI's Sequence Read Archive (SRA) to Galaxy: SARS-CoV-2 variant analysis](https://training.galaxyproject.org/training-material/topics/variant-analysis/tutorials/sars-cov-2/tutorial.html) that we can use for inspiration. The source for that material is [here](https://github.com/galaxyproject/training-material/tree/main/topics/variant-analysis/tutorials/sars-cov-2).


# Hands-on experience with Galaxy
1. First you need to register with [galaxy.sanbi.za](https://galaxy.sanbi.ac.za/) if you dont't have an account or login if you already have an account.
2. To get data click on the **Shared Data** icon --> **Data Libraries** then select SARS-CoV-2 Amplicon Sequencing
    i.  Export the **SARS-CoV-2 Amplicon Sequencing** to the History as collection.
    ii. Make FASTQ datasets into **list of pairs** and enter the name of your new collection (your prefered name)
3. Trimming the FASTQ reads with **fastq** tool. Search for this tool in the search tools icon of Galaxy.
    - input is Paired collection of the given name above (step 2 ii)
4. Mapping of your reads with **BWA MEM**. Select this tool in the search tools icon. 
    - Input is the the output of fastp above (step 3)
    - Reference genome select *Use a genome from history and build index* from the drop down arrow
    - Select *paired collection* from the Single or Paired-end reads drop down arrow
    - Select the first and second set of reads appropriately
5. Compute mapping statistics using **samtools stats**. Search for this tool in the search tools icon of Galaxy.
6. Trimming the aligned BAM reads with **ivar trim**. Search for this tool in the search tools icon of Galaxy.
    - Input is bam dataset
    - Select *Built-in* from the Source of primer information
    - Select *SARS-CoV-2-ARTICv3* from the Primer scheme name
    - Select *Yes* for Include reads not ending in any primer binding sites?
    - Enter Quality score (FASTQ qaulity) of 20
    - Enter Frequency threshold of 0.7, good for targeting common variants.
7.  Convert the iVar tabular varaiants output to a .vcf file format with **iVar Variants to VCF** tool.
8.  Rename the reference sequence with **Text transformation with sed**
    - Paste this **/^[^#]/s/^[^\t]+\t/NC_045512.2\t/** sed code in the SED Program window.
9.  Annonate the SARS-CoV-2 variants with the **SnpEff eff** tool. Make sure you use the SARS-CoV-2 version
    - Make sure you select your reference sequence as named above (step 8)
10. Call consensus from the aligned BAM file with **ivar consensus**.
    - input is the trimmed BAM reads.
    - Enter 20 for Minimum quality score threshold 
    - Enter 0.7 for Minimum frequency threshold
    - Enter 20 for Minimum depth 
    - Select *No* for Exclude regions with smaller depth than the minimum threshold
    - Select *Yes* for Use N instead of - for regions with less than minimum coverage
11. Rename the FASTA header with **Text transformation with sed** to be the name of the sample.
    - Paste this **/^>/s/Consensus_(.*)_threshold_.*/\1/** sed code in the SED Program window.
12. Phylogenetic lineage assignment with **Pangolin**.
    - Leave the *Download the latest Pangolin from web* option as default for the pangoLEARN source section
    - Rerun the **Pangolin** with UShER model selected as *Yes*. UShER model is a new model for lineage identification
13. Phylogenetic lineage designation with **Nextclade**. 

Find the link to the tutorial [here](https://4000-fuchsia-damselfly-0ht5y5jf.ws-eu08.gitpod.io/training-material/topics/variant-analysis/tutorials/sars-cov-2-amplicon/tutorial.html)

Note: When you excute your run take note of the following colors:
color | Description
----- | ----------- 
Grey | waiting job
Yellow | running 
Red | error
Green | completed 

See the schematic illustration of the above steps.
![workflow diagram](https://github.com/mudiboevans/SARS-CoV-2-sequence-analysis-tutorial-using-Galaxy/blob/main/image.png) 

# Members
- Peter van Heusden
- Evans Mudibo
- Jesse A Asimeng
- Bright Asante
- Brian Bwanya

