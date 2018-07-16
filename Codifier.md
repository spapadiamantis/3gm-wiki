# Use as command line tool

After following the Installation Instructions Wiki Page you will be able to use the codifier tool provided for this project.  The command line tool is located at `3gm/codifier.py`. You can use the tool by providing documents in plaintext format as command line arguments. For example:

## With `--source`, `--target` and `--output` options:
```bash
$ codifier.py -h
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

## As a UNIX tool

According to [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) applying multiple amendments to a legal text must also be chained as a _pipelined process_. As for that you can use `codifier.py` in the following way:

1. Simple Case: 
```bash
codifier.py ammendment-1.txt <initial-version.txt >ammended-version.txt
```
2. Pipelined example:
```bash
<initial-version.txt codifier.py ammendment-1.txt |
codifier.py ammendment-2.txt |
codifier.py ammendment-3.txt > final-version.txt
```
3. Exporting to a different format 
```bash
<initial-version.txt codifier.py ammendment-1.txt |
codifier.py ammendment-2.txt |
codifier.py ammendment-3.txt | exporter.py --markdown > final-version.md
```
As arguments for the exporting tool `exporter.py` you can also use:
 * `--latex` for (Xe)LaTeX
 * `--issue` for Issue-Like format
 * `--str` for one-line string
 * `--plaintext` for plaintext.

# Use as a module

1. Import by 

```python
import codifier
```
After importing codifier there is already a global `LawCodifier` object provided under the name `codifier`:
```python3
>>> codifier.codifier
<codifier.LawCodifier object at 0x7fd7e4032208>
```

2. You can also create a `LawCodifier` object as 

```python
cod = codifier.LawCodifier('<directory-of-gg-issues>')
```
In this case the data provided by the issues directory is populated to the database.

3. Build the codifier database from existing documents
Place the documents under a directory `/data` with the following arrangement:

```
data/YYYY/YYYY*.txt
```

Then build the database via:

```python
import codifier
codifier.codifier = codifier.build(start=1998, end=2018, data_dir='data/') 
```

# Use via the flask application

1. Setup the database 
2. Deploy the flask application (inside `3gm` directory) via:
```bash
./run.sh
```

## API Documentation

The API Docs are located at `docs/` under the root of this repository. 









