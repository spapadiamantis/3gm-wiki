# Project Architecture

## Technologies Used

### Core

The technologies being used in the project are Python 3.x with an NLP toolkit and MongoDB as database infrastructure providing a document-based schema in which information is kept in JSON format. The communication between MongoDB and Python is done via the `pymongo` package. Finally, the `pytest` package is used for testing.

 ### Web Application

The web application that is hosted at [3gm.papachristoumarios.me](http://3gm.papachristoumarios.me) is developed using the Flask Web Micro-framework. The web application also comes with a RESTful API via which the information is accessible to via requests. 

![](architecture/1.png)

### Building and Deployment

The building and deployment procedure is done via GNU Make in a provided Makefile under the root directory.

---

## Procedure Outline  

### General

 ![](architecture/2.png)



The documents are being parsed by the parser and the parser objects / issue object are generated. After that, the issues are scanned using regular expressions for new statutes. The new statutes are placed on different objects (statute objects). Then the main object (the codifier) is responsible for cross-linking the existing issues together. Then the links and the statutes are passed to the amendment detection algorithm and the new versions are generated. The statutes and links are kept in a document-based database schema  (MongoDB) via serialization. The versioning system which consists of large documents is kept in GridFS. Finally there are options for checkout and rollback on existing statutes and links. 

### Pipeline

The pipelined process of codification consists of the following parts: 



![](architecture/3.png)





1. Gather Statutes: The statutes are gathered and the objects are generated
2. Cross-link Statutes: The statutes are cross-linked
3. Statistical Analysis (optional stage): Statistical Analysis tasks such as Topic Models with LDA or PageRank are applied in order to extract useful information from the statutes and provide with more functionality such as rank-based search, similarity analysis etc. 
4.  Codification Procedure: As outlined above, the codification procedure combines the statutes with their **modifying** links to create the versioning history of the statutes. 



## References

1. Spinellis, Diomidis, and Georgios Gousios. *Beautiful Architecture: Leading Thinkers Reveal the Hidden Beauty in Software Design*. " O'Reilly Media, Inc.", 2009.

 