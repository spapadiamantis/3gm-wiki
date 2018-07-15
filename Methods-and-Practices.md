## Methods & Practices

### Heuristic methods for detecting ammendments

This project uses heuristics for detecting ammendments. You can have a look at `3gm/syntax.py` module for more information.  

### Storing data

This project has to do with a lot of documents so selecting a NoSQL database like MongoDB would be a perfect fit for the project. The articles are organized in collections by paragraphs. It uses the `pymongo` module to communicate with the MongoDB database server. The scripts used for communication with the database as well as query building from syntactic analysis is found in the `3gm/database.py` module.

### Unit testing & Continuous Integration

This project uses the `pytest` module for running unit tests. You can install `pytest` and run the tests via:

```bash
sudo pip3 install pytest
cd ./src/
pytest tests.py
```

The tests are also run on Travis CI which is used for continuous integration in this project. The configuration file for Travis CI is `.travis.yml`.