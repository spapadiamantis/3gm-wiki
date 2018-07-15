# Usage 

After following the Installation Instructions Wiki Page you will be able to use the codifier tool provided for this project.  The command line tool is located at `src/codifier.py`. You can use the tool by providing documents in plaintext format as command line arguments. For example:

### With `--source`, `--target` and `--output` options:
```bash
$ python3 codifier.py -h
usage: codifier.py [-h] [--source SOURCE] [--target TARGET] [--output OUTPUT]

This is the command line tool for codifying documents

optional arguments:
  -h, --help       show this help message and exit

optional arguments:
  --source SOURCE  Source Statute
  --target TARGET  Target Statute
  --output OUTPUT  Output file
```

For example
```bash
codifier.py --source source.txt --target target.txt --output output.txt
```
If the `--output` flag is omitted, the output is sent to `stdout`. 
You can pipeline it using the exporter script to get the output in Markdown:

```bash
codifier.py --source source.txt --target target.txt | exporter.py markdown > output.md
```

### As a UNIX tool

According to [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) 


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









