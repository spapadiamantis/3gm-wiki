# Use as command line tool

After following the Installation Instructions Wiki Page you will be able to use the codifier tool provided for this project.  The command line tool is located at `3gm/codifier.py`. You can use the tool by providing documents in plaintext format as command line arguments. For example:

## As a UNIX tool

According to [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) applying multiple amendments to a legal text must also be chained as a _pipelined process_. As for that you can use `codifier.py` in the following way:

1. Simple Case: 
```bash
python3 law_codifier.py ../../examples/20180100102.txt initial-out.txt  <../../examples/initial-version.txt > final-version.txt
```
2. Pipelined example:
```bash
<initial-version.txt codifier.py ammendment-1.txt initial-1-out.txt |
codifier.py ammendment-2.txt initial-2-out.txt |
codifier.py ammendment-3.txt initial-3-out.txt > final-version.txt
```
3. Exporting to a different format 
```bash
<initial-version.txt python3 codifier.py ammendment-1.txt | python3 exporter.py --markdown > final-version.md
```
4. You can use `diff` to see the differences in the new legal text compared to the old one

   ```bash
   diff final-version.txt initial-out-txt
   ```

### Exporting Arguments 

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









