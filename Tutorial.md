This page illustrates a step-by-step procedure to set up this project 

## Step 0: Preparation and Installation 

The installation instructions include installing the project requirements as well as the project itself via `distutils`. 

The procedure of installation is outlined in the [Installation Page](https://github.com/eellak/gsoc2018-3gm/wiki/Installation)

## Step 1: Gather Documents

1. In order to setup the project you need to gather Government Gazette Documents from [ET](https://et.gr) either by hand or using the [Fetching Tool](https://github.com/eellak/gsoc2018-3gm/wiki/Fetching-Documents) to either fetch using your own parameters or schedule the task. There is also pre-processed data on the repository under `data/dataset.zip` for tests. 
2. Put the data in directory. For example:

```
data/
  |-   file1.{pdf,txt}
  |-   file2.{pdf,txt}
     ...
  |-   filen.{pdf,txt}
```   

3. If the data is already in `.txt` format then you can head over [Step 3](#step-3-codification-procedure)

## Step 2: Converting the documents 

If the documents are in PDF format (either contain text or not) you should convert them to plain text format. For this purpose you will need to follow the steps outlined [here](https://github.com/eellak/gsoc2018-3gm/wiki/Document-Processing) to setup the conversion process. Then you can [batch-convert](https://github.com/eellak/gsoc2018-3gm/wiki/Document-Processing#using-the-converterpy-tool-for-batch-conversion) the documents with one command: 

```
python3 scripts/converter.py -input_dir ../data/1998/ -output_dir ../data/1998/ -pdf2txt pdf2txt.py
```   

## Step 3: Codification Procedure



