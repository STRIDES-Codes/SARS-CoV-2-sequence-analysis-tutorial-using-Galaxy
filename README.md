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

