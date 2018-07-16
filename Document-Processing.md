# Converting Documents to text format

## Conversion Tools

The process of processing and codifying features the conversion stage first. For this purpose a conversion tool is developed. This tool uses the `pdfminer.six` module for extracting text out of PDF files with the `pdf2txt.py` command line tool. In case the document has no text, i.e. it is a scanned document and every page is an image, there is an OCR tool under `scripts/ocr.py` for processing these documents.

### Installing `pdfminer.six`

You can install the `pdfminer.six` package via 

```bash
pip3 install pdfminer.six
```

The `pdf2txt.py` module should be available. Otherwise you can clone the [Github Repository](https://github.com/pdfminer/pdfminer.six) and the tool is located at `tools/pdf2txt.py`. 



### Installing OCR Support with Tesseract 

Older Government Gazette Issues (from years before 2000) are usually stored in image format (i.e. scanned pages with text). These documents are processed using OCR in order for the text to be extracted for the [parser class](#Document Parser). We are using the open-source tool [Tesseract](https://github.com/tesseract-ocr/tesseract) which is being developed by Google. Its newest version (Tesseract 4.0) features new models for OCR a new OCR engine based on LSTM neural networks. It initially works (well) on x86/Linux. Model data for 101 languages is available in the [tessdata repository](https://github.com/tesseract-ocr/tessdata). For more information about how OCR is being done using Neural Networks is available [here](https://github.com/tesseract-ocr/tesseract/wiki/NeuralNetsInTesseract4.00). Tesseract is bridged with our project using the `pyocr` module. 

#### Installing Tesseract

Getting the new version (4.0 alpha) with LSTM support, which works very good on our documents you must compile `tesseract` from source. For a legacy installation you can use Tesseract 3.x which is available from your package manager. 

Tesseract also needs language data to work. The language data have the form `xyz.traineddata` where `xyz` is the language code, namely `eng` for English characters, `ell` for Modern Greek characters and `grc` for Greek Polytonic characters (used before 1976 when "Katharevousa" was the official language for documents in Greece). You must download the `eng and ` `ell` trained data in order for tesseract to work. You can do so by:

```bash
sudo wget https://github.com/tesseract-ocr/tessdata/raw/master/ell.traineddata -P /usr/share/tesseract-ocr/tessdata/ && 
sudo wget https://github.com/tesseract-ocr/tessdata/raw/master/ell.traineddata -P /usr/share/tesseract-ocr/tessdata/
```

This will store the required models under the global tessdata directory. If you want to store them in another directory, you must set the `TESSDATA_PREFIX` environment variable on your `.bashrc` configuration by adding the following line at the end of it:

```bash
export TESSDATA_PREFIX="/path/to/tessdata/"
```

Then running  the `source` command to reload  `.bashrc` 

```bash
source .bashrc
```



## Using the `converter.py` tool for batch conversion 

The documents can be converted to raw text combining both techniques (direct conversion to text or conversion to text via OCR) using the `converter.py` script under `scripts/converter.py`.  For faster results, the tool uses a `multiprocessing.Pool` to run jobs simultaneously. 

Usage:

```
usage: converter.py [-h] [-pdf2txt PDF2TXT] [-input_dir INPUT_DIR]
                    [-output_dir OUTPUT_DIR] [--njobs NJOBS]

Tool for batch conversion. For more details and documentation visit
https://github.com/eellak/gsoc2018-3gm/wiki/Document-Processing#using-the-
converterpy-tool-for-batch-conversion

optional arguments:
  -h, --help            show this help message and exit

required arguments:
  -pdf2txt PDF2TXT      pdf2txt.py Executable
  -input_dir INPUT_DIR  Input Directory
  -output_dir OUTPUT_DIR
                        Output Directory

optional arguments:
  --njobs NJOBS         Number of parallel jobs (default = 1)
```

Example (with `nohup`):

```bash
nohup python3 converter.py -input_dir ../data/1998/ -output_dir ../data/1998/ -pdf2txt pdf2txt.py &
```

# Datasets 

There are two datasets on this repository containing Government Gazette Issues in plain text format.
Due to continuous integration issues, these datasets are kept in a separate branch with Git LFS. 

1. Dataset from years 2000 - 2018 under `data/dataset.zip`

2. Dataset from years 1976 - 1999 (legacy) under `data/dataset_legacy.zip`

To get them simply checkout and pull the `datasets` branch via 

```
git checkout -b datasets
git pull origin datasets 
```

You can also download *scraped PDFs in txt format* from [here](https://pithos.okeanos.grnet.gr/public/7Z2GQvF0boDbCjYWFnmyc)

# Document Parsing Modules

The parsing modules provides is `IssueParser` for parsing Government Gazette Issues and `LawParser` for parsing laws referred in Government Gazette Issues. You can read the docs [here](https://github.com/eellak/gsoc2018-3gm/tree/master/docs).
 

