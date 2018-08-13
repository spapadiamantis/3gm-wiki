# Contributing to the project

## Future Work

### Training statistical models with custom tag maps

In order to further improve the accuracy of the amendment detection algorithm, we propose [training a statistical model](https://spacy.io/usage/training) with a [custom tag map with custom parts of speech (POS)](https://spacy.io/api/tagger). This training can be done with tools such as [prodigy.ai](https://spacy.io/api/tagger) in order to construct [a custom treebank](https://github.com/papachristoumarios/UD_Greek-GDT) with the needed dependencies. Then we can detect the amendment with a simple [tree traversal](https://en.wikipedia.org/wiki/Tree_traversal). 

### Differential versioning with MongoDB

In this stage the various versions of the statutes are kept in records in GridFS. In order to minify the chunks created by GridFS we propose the development of differential versioning for keeping track of the history. This can be done via invoking the [`diff`](https://en.wikipedia.org/wiki/Diff) UNIX tool. The goal is to build a tool like `git` (or even migrate completely to git).

### Digitize Older documents (pre-1999)

The pre-1999 (1976-1999) documents of the Greek Government Gazette need OCR in order to be read. There has been an attempt to digitize them using Google Tesseract v4.0 OCR Engine with neat results in the years 1990-1999. For better results, however, either a custom LSTM model (as Google Tesseract utilizes) needs to be trained in order to detect the Greek typographic elements from the Government Gazette Issues or the gathering of documents from another sources needs to be done.  



**Any further feedback on future improvements and work is always appreciated. **

---

## For lawyers

If you are a lawyer, you are very helpful to us. We would like you to tell us:

1. If the laws are applied in the right order

2. If there are legal texts that are absent

3. If the topic is satisfactory   

## For computer scientists

If you are a computer scientist, you are very helpful to us. You can contribute to:

1. Rebuilding older texts. To do this, you can visit the [Internet Archive Project](https://archive.org/details/GreekGovernmentGazette). 
2. Help us with ideas about Natural Language Processing algorithms (NLP) or other Machine Learning Algorithms to improve the detection of modifications or add features to the project in general.
3. If you find a problem, or want to suggest some improvement, [open an issue](https://github.com/eellak/gsoc2018-3gm/issues).
4. If you want to study the structure of the project, you can see [the code](https://github.com/eellak/gsoc2018-3gm) and [the wiki](https://github.com/eellak/gsoc2018-3gm/wiki)

## For citizens

Your contribution is more than helpful! We would like [to hear your opinion](#Contact)

## Contact

Send us an email to [info AT ellak DOT gr](mailto:info@ellak.gr)