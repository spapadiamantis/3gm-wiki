# Converting Documents to text format

## Conversion Tools

The process of processing and codifying features the conversion stage first. For this purpose a conversion tool is developed. This tool uses the `pdfminer.six` module for extracting text out of PDF files with the `pdf2txt.py` command line tool. In case the document has no text, i.e. it is a scanned document and every page is an image, there is an OCR tool under `scripts/ocr.py` for processing these documents.



### Installing `pdfminer.six`

You can install the `pdfminer.six` package via 

```bash
pip3 install pdfminer.six
```

The `pdf2txt.py` module should be available. Otherwise you can clone the [Github Repository](https://github.com/pdfminer/pdfminer.six) and the tool is located at `tools/pdf2txt.py`. 



### Installing OCR Support 

Older Government Gazette Issues (from years before 2000) are usually stored in image format (i.e. scanned pages with text). These documents are processed using OCR in order for the text to be extracted for the [parser class](#Document Parser). We are using the open-source tool [Tesseract](https://github.com/tesseract-ocr/tesseract) which is being developed by Google. Its newest version (Tesseract 4.0) features new models for OCR a new OCR engine based on LSTM neural networks. It initially works (well) on x86/Linux. Model data for 101 languages is available in the [tessdata repository](https://github.com/tesseract-ocr/tessdata). For more information about how OCR is being done using Neural Networks is available [here](https://github.com/tesseract-ocr/tesseract/wiki/NeuralNetsInTesseract4.00). Tesseract is bridged with our project using the `pyocr` module.  



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



 

