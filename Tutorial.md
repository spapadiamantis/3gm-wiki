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

1. Populate the database with detected laws

```python
>>> from codifier import LawCodifier
>> cod = LawCodifier('../data/new')
```

2. Get the new laws published at the GG Issues (ΦΕΚ Α') 
```python
>> cod.codify_new_laws()
```

3. Codify the a law using the `codify_law(law)` command (under development)
```python
>>> cod.codify_law(ν. 4448/2018')
```

4. Get a law as a string or export it to PDF via the Texification Tool using `xelatex`
```python
# as a string
>> result = cod.get_law('ν. 4448/2018')
# or a pdf using xelatex
>> cod.texify_law('ν. 4448/2018', 'Κωδικοποιημένος_Νόμος.pdf') 
```

5. The data is organized in the MongoDB database in versions for easier lookup.
The contents of each version are organized in periods. 

```
_id: "ν. 4448/2018"
versions: Array
   0: Object
      articles: Object
             1: Object
                0: Array
                   0: "Τα Μέρη, στο πλαίσιο του παρόντος Μνημονίου Κατανόησης και σύμφωνα με ..."
             2: Object
      lemmas: Object
      titles: Object
      _version: 0
      amendee: "ν. 4448/2018"
```

## Step 4: Optional Functionality 

1. [Apply Topic Models on Government Gazette Issues](https://github.com/eellak/gsoc2018-3gm/wiki/Topic-Modelling)
2. [Document Embeddings with Doc2Vec]([Apply Topic Models on Government Gazette Issues](https://github.com/eellak/gsoc2018-3gm/wiki/Doc2Vec)

