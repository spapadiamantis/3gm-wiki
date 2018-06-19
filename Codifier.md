# Usage 



After following the Installation Instructions Wiki Page you will be able to use the codifier tool provided for this project.  The command line tool is located at `src/codifier.py`. You can use the tool by providing documents (in PDF or raw text format) as command line arguments. For example:

```bash
./codifier.py file1.pdf file2.txt file3.pdf
```

Be sure you have setup the MongoDB server in order to make changes to the database. 


## Using as a module

1. Import by 

```python
import codifier
```

2. Create a `LawCodifier` object as 

```python
cod = codifier.LawCodifier('<directory-of-gg-issues>')
```

3. Codify a statute with `codify_law()` method. For example

```python
cod.codify_law('ν. 1920/1991')
```

**DISCLAIMER** This is work in progress so it is expected to be unstable. 









