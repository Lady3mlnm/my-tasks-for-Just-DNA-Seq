# opencravat-longevity

Repository for longevity annotators for opencravat.

The repository contains:
* notebooks to preprocess the data. In the data:
  **longevity_genes_original.csv** - original data from [https://genomics.senescence.info](https://genomics.senescence.info/longevity/)

  **longevity_genes_splitted_rs.csv** - filtered and splitted data with only rs in the column 'Variant(s)'. One rs per record.
  
  **longevity_genes_splitted_not_rs.csv** - filtered data without rs in the column 'Variant(s)'. Here cells of the column 'Variant(s)' can contain several variants or value NaN.
  
  **longevity_genes_splitted_all.csv** - all processed data in one file (just in case). That is combination of content of files **longevity genes_splitted_rs.csv** and **longevity_genes_splitted_not_rs.csv**.
* annotators/longevitymap - annotator code
* environment.yaml - file for conda environment

## setting up

Install conda environment
-------------------------
Annotation modules and dvc are included in the conda environment that goes with the project.
The environment can be setup either with Anaconda or micromamba (superior version of conda).
Here is installation instruction for micromamba:
```
wget -qO- https://micromamba.snakepit.net/api/micromamba/linux-64/latest | tar -xvj bin/micromamba
```
We can use ./micromamba shell init ... to initialize a shell (.bashrc) and a new root environment in ~/micromamba:
```
./bin/micromamba shell init -s bash -p ~/micromamba
source ~/.bashrc
```
To create a micromamba environment use:
```
micromamba create -f environment.yaml
micromamba activate opencravat-longevity
```

The instructions above are provided for Linux and MacOS (note: in MacOS you have to install wget).
For Windows you can either install Linux Subsystem or use Windows version of anaconda.

Runing notebooks
--------------

To run notebooks just activate the environment and type:
```
jupyter lab notebooks
```

Note: after folder renaming notebooks need fixing

Writing an annotator
--------------------

First, read the [tutorial](https://open-cravat.readthedocs.io/en/latest/Annotator-Tutorial.html) about opencravat annotations and locate the path to the modules directory:

```base
oc config md
```

Change to the module folder, for example:
```bash
oc config md .
```

