# Table of Contents

- **Getting started**
  - [Home](https://github.com/eellak/gsoc2018-3gm/wiki)
  - [Installation](https://github.com/eellak/gsoc2018-3gm/wiki/Installation)
  - [Operation](https://github.com/eellak/gsoc2018-3gm/wiki/Operation)
  - [Codifier](https://github.com/eellak/gsoc2018-3gm/wiki/Codifier)
  - [Architecture](https://github.com/eellak/gsoc2018-3gm/wiki/Architecture)
  - [Final Progress Report](https://github.com/eellak/gsoc2018-3gm/wiki/Final-Report-for-Google-Summer-of-Code-2018)
  - [Reading List](https://github.com/eellak/gsoc2018-3gm/wiki/Reading-List)
- **Algorithms**
  - [Amendment Detection](https://github.com/eellak/gsoc2018-3gm/wiki/Algorithms-for-analyzing-Government-Gazette-Documents)
  - [Topic Modeling](https://github.com/eellak/gsoc2018-3gm/wiki/Topic-Modelling)
  - [Ranking](https://github.com/eellak/gsoc2018-3gm/wiki/Ranking-Laws-using-PageRank)
  - [Evaluation and Metrics](https://github.com/eellak/gsoc2018-3gm/wiki/Evaluation-and-Metrics)
- **Datasets and Continuous Integration**
  - [Fetching Documents](https://github.com/eellak/gsoc2018-3gm/wiki/Fetching-Documents)
  - [Processing Documents](https://github.com/eellak/gsoc2018-3gm/wiki/Document-Processing)
- **Documentation**
  - [API Documentation](https://github.com/eellak/gsoc2018-3gm/wiki/API-Documentation)
  - [RESTful API](https://github.com/eellak/gsoc2018-3gm/wiki/RESTful-API)
  - Help (for web application)
    - [English](https://github.com/eellak/gsoc2018-3gm/wiki/Help-(in-English))
    - [Greek](https://github.com/eellak/gsoc2018-3gm/wiki/Help-(in-Greek))
- **Development**
  - [Testing](https://github.com/eellak/gsoc2018-3gm/wiki/Testing)
  - [Licensing](https://github.com/eellak/gsoc2018-3gm/wiki/Licensing)
  - [Future Work & Contributing](https://github.com/eellak/gsoc2018-3gm/wiki/Contributing-To-The-Project)
  - [Document Embeddings](https://github.com/eellak/gsoc2018-3gm/wiki/Document-Embeddings-with-Doc2Vec)

---

# About the project

We live in a complex regulatory environment. As citizens, we obey government regulations from many authorities. As members of organized societies and groups, we must obey organizational policies and rules. As social beings, we are bound by conventions we make with others. As individuals, they are bound by personal rules of conduct. The full number and size of regulations can be really scary. We can agree on some general principles but, at the same time, we can disagree on how these principles apply to specific situations. In order to minimize such disagreements, regulators are often obliged to create numerous regulations or very large regulations to deal with special cases.

In the recent years plenty of attention has been gathering around analyzing public sector texts via text mining methods enabled by modern libraries, algorithms and practices and bought to to the forefront by open source projects such as textblob, spaCy, SciPy, Tensorflow and NLTK. These collaborative productive efforts seem to be a shift towards more efficient understanding of natural language by machines which can be used in conjunction with public documents in order to provide useful tools for legislators. This emerging sector is usually referred as "Computational Law".

This project, developed under the auspices the Google Summer of Code 2018 Program, carries out the extraction of Government Gazette (ΦΕΚ) texts from the National Printing House (ET), cross-links them with each other and, finally, identifies and applies the amendments to the legal text by providing automatic codification of the Greek legislation using methods and techniques of Natural Language Processing. This will allow the elimination of bureaucratic procedures and great time savings for lawyers looking for the most recent versions of statutes in legal databases. The detection of amendments is automated in order to amend the amendments to the laws merged into a common law, a procedure known as codification of the law. The new "merged" / modified / codified laws can show the current text of a law at every moment. This is something that is being traditionally done by hand and our aim was to automate it.

Finally, the laws are clustered into topics according to their content using a non-supervised machine learning model (Latent Dirichlet Allocation) to provide a more holistic representation of Greek legislation. Also, for easier indexing, PageRank was used and therefore the interconnections of the laws were positively taken into account, because the more references there is a legislative text than the other the more important it is characterized.

Through the analysis, categorization and codification of the GG documents, this project facilitates key elements of everyday life such as the elimination of bureaucracy and the efficient management of public documents to implement tangible solutions, which allows huge savings for lawyers and citizens.

# Project Proposal for Google Summer of Code 2018

## Initial Problem Statement

In the recent years plenty of attention has been gathering around analyzing public sector texts via text mining methods enabled by modern libraries, algorithms and practices and bought to to the forefront by open source projects such as textblob, spaCy, SciPy, Tensorflow and NLTK. These collaborative productive efforts seem to be a shift towards more efficient understanding of natural language by machines which can be used in conjunction with public documents in order to provide a more robust organization and codification in the legal sector.  

This project extends the existing Government Gazette (GG) text mining code by implementing features in order to organize and (cross)-link GG texts with legal text and analyzing them, thus providing an automated legal codex.  This will enable elimination of bureaucratic processes and huge time savings for jurists who for example seek legal documents in legal databases.

## Initial Project Proposal

For this purpose, the GG documents have to be downloaded as PDFs and parse them to raw text files. Heuristic rules and Named Entity Recognition methodologies have to be applied in order to detect competent ministers and references to other legal texts which will be converted into hypertext format.

This process is either targeted in detecting amendments proposed and signed in the GG documents so that they can be incorporated within other laws or detecting similar categories of amendments and merging them under a common law, also referred as law codification. The newly “merged” / edited / codified laws could be then legislated. The project will be coded preferably in the Python programming language.   

A first metric of the evaluation of the project could be the successful categorization of laws referring to a certain category of laws (e.g. regarding mediation or new laws) and are contained in different GG articles. A second key metric would be the extension of this to a large number of law categories. Last but not least, the project can be tested with the NLP library spaCy.io which is also a proposed project through this year’s Google Summer of Code proposals by GFOSS, which can also be tested beyond the scope of this GSoC.

Through the case of analyzing, categorizing and codifying Government Gazette issues this proposal sets out to illustrate key points such as elimination of bureaucracy and efficient management of public documents for the implementation of tangible solutions enabling huge savings of time for jurists. The synergy of machine learning algorithms combined with in vitro processing of legal texts signifies the potential for broader usage of machine learning in the public sector; an area with ample amounts of unorganized data.

**Keywords:** _text mining, government gazette, machine learning, law codification_