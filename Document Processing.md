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

# Document Parser

In order to be codified and processed, each document is parsed through the `IssueParser` class located under `parser.py` in the main module. The parser API is described as follows: 







The standalone module can be used via creating `IssueParser` 

```python
import parser
issue = parser.IssueParser('issue.txt')

# use one of the API functions described above 
# e.g. 
issue.detect_new_laws()
```



 

