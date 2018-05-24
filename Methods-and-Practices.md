## Methods & Practices

### Heuristic methods for detecting ammendments

This project uses heuristics for detecting ammendments. You can have a look at `src/syntax.py` module for more information.  

### Word2Vec Models

For research purposes and further usage in the codification process a word2vec model with gensim is trained on various GG issues. That is to detect similarities between words in order to be used with syntactic analysis heuristic methods. For example the most similar words to the word "Υπουργός" (Minister) are

```python
[('Υπουργό', 0.6968967914581299), ('Υπουργού', 0.6823141574859619), ('Εσωτερικών', 0.6715962886810303), ('Αλληλεγγύης', 0.6563194990158081), ('Γραμματέας', 0.6339884996414185), ('Οικονομίας', 0.6258766651153564), ('Γενικό', 0.6158846616744995), ('Μεταφορών', 0.6002545952796936), ('Φορέας', 0.5990256071090698)]
```

which is pretty satisfying. The word vectors are also reduced in dimension using t-Stochastic Neighbour Embedding.

### Storing data

This project has to do with a lot of documents so selecting a NoSQL database like MongoDB would be a perfect fit for the project. The articles are organized in collections by paragraphs. It uses the `pymongo` module to communicate with the MongoDB database server. The scripts used for communication with the database as well as query building from syntactic analysis is found in the `src/database.py` module.

### Unit testing & Continuous Integration

This project uses the `pytest` module for running unit tests. You can install `pytest` and run the tests via:

```bash
sudo pip3 install pytest
cd ./src/
pytest tests.py
```

The tests are also run on Travis CI which is used for continuous integration in this project. The configuration file for Travis CI is `.travis.yml`.