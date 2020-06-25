# Analysis pipeline for SARs-CoV-2 RGTM Sequencing Data

## Input raw data 
The input data are not yet publicly available. Please email me (nolson@nist.gov) if you are interested in the input sequencing data.

## Running pipeline
We used the python package [`snakemake`](https://snakemake.readthedocs.io/en/stable/) for pipeline construction and orchestrate execution. [`conda`](https://docs.conda.io/en/latest/miniconda.html) was used for dependency mangement. The ONT basecaller `guppy`, is not available as a conda package and was installed from the [ONT website](https://nanoporetech.com/).
To run the pipeline;
- first install conda and create a conda environment for running snakemake following the conda installation instructions in the Snakemake documentation.
- next download `guppy` from the ONT website and copy unzipped guppy directory to the `workflow/src` directory.
- finally to run the pipeline use `snakemake -p --use-conda --snakefile workflow/Snakefile -j #`.

Notes for running pipeline: The pipeline run time on a 2020 13inch macbook pro is 28 hours. Nanopore basecalling took ~24 hours and was the bulk of the pipeline run time. The gpu `guppy` basecaller is significantly faster and recommended when available (e.g. when running the pipeline on a windows or linux machine with a NVIDIA GPU).

