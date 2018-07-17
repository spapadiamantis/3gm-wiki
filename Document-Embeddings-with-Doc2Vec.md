This page is intended on building a similarity analyzer (like Topic Modelling with LDA) based on Doc2Vec algorithm contained in the `gensim` package. This page will guide you through the training of a Doc2Vec model. 

## Step 0: Export corpus and labels

1. Build the codifier using the provided data.
```python
>>> import codifier
>>> cod = codifier.build(start=1999, end=2018, data_dir='<data-dir>')
```

Export the whole corpus via
```python3 
>>> cod.export_codifier_corpus('corpus.txt', 'labels.txt')
```

This will export each statute in a separate line and will generate `corpus.txt` and `labels.txt` containing the corpus and the labels respectively.

## Step 1: Train using `gensim.models.Doc2Vec`

1. Import gensim
```python3
import gensim.models as g
import logging
import sys
import tokenizer
from gensim.models.doc2vec import TaggedDocument
from multiprocessing import cpu_count

#enable logging
logging.basicConfig(format='%(asctime)s : %(levelname)s : %(message)s', level=logging.INFO)

```
2. Define parameters (you can adjust them to obtain different results

```python3
#doc2vec parameters
vector_size = 150
window_size = 8
min_count = 4
sampling_threshold = 1e-5
negative_size = 5
train_epoch = 50
dm = 0 #0 = dbow; 1 = dmpv
worker_count = cpu_count() - 1

3. Get the labels 

```python
with open(labels_file, 'r') as f:
	labels = f.read().splitlines()
```

4. Create `TaggedDocument` objects using the labels as single tags: 

```python
taggeddocs = []

with open('corpus', 'r') as f:
	docs = f.read().splitlines()

for label, doc in zip(labels, docs):
	td = TaggedDocument(words=tokenizer.tokenizer.split(doc.lower(), delimiter=' '), tags=[label])
	#print(td)
	taggeddocs.append(td)

```

5. Train the model with:

```python3 
model = g.Doc2Vec(taggeddocs, size=vector_size, window=window_size, min_count=min_count, sample=sampling_threshold, workers=worker_count, hs=0, dm=dm, negative=negative_size, dbow_words=1, dm_concat=1, pretrained_emb=None, iter=train_epoch)

#save model
model.save('laws_model.bin')
```

6. The full script is located at  `train_doc2vec.py`

## Step 2: Getting similar words or documents

1. Most similar words via `model.most_similar`

```python
>>> model.most_similar('υπουργός', topn=10)
[('υφυπουργός', 0.5026417374610901), ('αναθέτει', 0.48663175106048584), ('συμβούλιο', 0.4686082601547241), ('ραδιοτηλεόρασης.', 0.4630734920501709), ('υπουργό', 0.4535461366176605), ('αποφαινόμενο', 0.4525904059410095), ('προσφύγει', 0.4489518404006958), ('έγγραφες', 0.4454580545425415), ('αποφασίζει', 0.44335660338401794), ('αρμόδιος', 0.4433564841747284)]
>>> 
```

2. Or documents via `model.docvecs.most_similar`:  
```python
>>> model.docvecs.most_similar('ν. 4009/2011')
[('π.δ. 127/2010', 0.29893651604652405), ('π.δ. 58/2015', 0.24261419475078583), ('π.δ. 13/2013', 0.23538821935653687), ('ν. 4001/2011', 0.22230146825313568), ('ν. 4321/2015', 0.19321933388710022), ('ν. 4420/2016', 0.19074279069900513), ('π.δ. 48/1999', 0.18942637741565704), ('π.δ. 148/2010', 0.18506628274917603), ('π.δ. 172/2014', 0.17951558530330658), ('π.δ. 134/2017', 0.17921951413154602)]
```


