# Named Entity Recognition

During GSOC-2019 our main goal was to enhance the NLP capabilities of the program. To this end we decided it is vital to train a Named Entity Recognition (NER) model using solely Greek Government Gazette texts.It is trained using the [Greek spaCy](https://spacy.io/models/el/) pre-trained model and a dataset created with [Prodigy](https://prodi.gy/).

## NER labels 

We decided not to train extra named entities labels since it could require immense amounts of data and used the original annotation scheme of Greek spaCy. This scheme contains 6 labels:

ORG for organization, PERSON for person , GPE for geopolitical entities, LOC for locations, PRODUCT for products and EVENT for events.

Since we couldn’t redetermine entity labels we tried to apply this scheme to the scope of our problem. More specifically we used:

* ORG for organizations, government authorities, courts, churches and anything that falls into this category in the sense that it is an organized structure and people are part of it.
* GPE for countries and federations. To distinguish from the above “Ελλάδα” (meaning Greece) is a GPE but “Ελληνικό Δημόσιο” (meaning Greek state or the conglomerate of Greek state  mechanisms)  is tagged as ORG.
* LOC for locations and geographic indications but not  for countries.
* PERSON for either a specific individual or the office that an individual may hold, his administrational role(“ο Υπουργός Υγείας”)
* PRODUCTS for actual products but also for any product of the praxis of an organization or a GPE, meaning also pacts, agreements, programs, guidelines or systems.
* EVENT for events such as "Αργία"


## Building Named Entities from the `codifier`

The `entity_recognizer.py` module populates everything from the database. Invoking it using
```
python3 entity_recognizer.py
```
would build named entities for your codifier corpus. Then it builds the topics collection to the MongoDB database. Named entities are built in the same way as topic models.

## Using the NER model

As mentioned, our model is a spaCy model and can be accessed through the entity recognizer [class](https://spacy.io/api/entityrecognizer#_title) of spaCy's API. The model can be found in the 'models' directory of the project. You can also use visualizers like [displaCy](https://spacy.io/usage/visualizers)

For example you can import the module using:
```

import spacy
nlp  = spacy.load('3gm_ner_model')

```
You can then use the model to detect named entities on chunks of Greek legal text.

```
text = '''«Διάσπαση του Υπουργείου Εσωτερικών, Αποκέντρωσης και Ηλεκτρονικής Διακυβέρνησης στα Υπουργεία: α) Εσωτερικών και β) Διοικητικής Μεταρρύθμισης και Ηλεκτρονικής Διακυβέρνησης, συγχώνευση των Υπουργείων Οικονομίας, Ανταγωνιστικότητας και Ναυτιλίας και Θαλάσσιων Υποθέσεων, Νήσων και Αλιείας στο Υπουργείο Ανάπτυξης, Ανταγωνιστικότητας και Ναυτιλίας και μεταφορά στον Πρωθυπουργό των Γενικών Γραμματειών Ενημέρωσης και Επικοινωνίας και στο Υπουργείο Παιδείας, Δια Βίου Μάθησης και Θρησκευμάτων της Γενικής Γραμματείας Νέας Γενιάς» (ΦΕΚ Α΄ 147)'''
doc = nlp(text)
displacy.serve(doc, style="ent")

```
<p align="center">

<img src="ner_example.png">

</p>

