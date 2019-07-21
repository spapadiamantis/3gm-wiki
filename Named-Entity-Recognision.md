# Named Entity Recognision

During GSOC-2019 our main goal was to enhance the NLP capabilities of the program. To this end we decided it is vital to train a Named Entity Recognision (NER) model using solely Greek Government Gazette texts.It is trained using the [Greek spaCy](https://spacy.io/models/el/) pre-trained model and a dataset created with [Prodigy](https://prodi.gy/).

## NER labels 

We decided not to train extra named entities labels since it could require immense amounts of data and used the original annotation scheme of greek spaCy. This scheme contains 6 labels:

ORG for organisation, PERSON for person , GPE for geopolitical entities, LOC for locations, PRODUCT for products and EVENT for events.

Since we couldn’t redetermine entity labels we tried to apply this scheme to the scope of our problem. More specifically we used:

* ORG for organisations, government authorities, courts, churches and anything that falls into this category in the sense that it is an organised structure and people are part of it.
* GPE for countries and federations. To distinguish from the above “Ελλάδα” (meaning Greece) is a GPE but “Ελληνικό Δημόσιο” (meaning Greek state or the conglomerate of Greek state  mechanisms)  is tagged as ORG.
* LOC for locations and geographic indications but not  for countries.
* PERSON for either a specific individual or the office that an individual may hold, his administrational role(“ο Υπουργός Υγείας”)
* PRODUCTS for actual products but also for any product of the praxis of an organisation or a GPE, meaning also pacts, agreements, programs, guidelines or systems.
* EVENT for events such as "Αργία"


## Building Named Entities from the `codifier`

The `entity_recogniser.py` module populates everything from the database. Invoking it using
```
python3 entity_recogniser.py
```
