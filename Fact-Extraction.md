# Fact Extraction

As part of GSOC-2019 we tried to enhance the the NLP capabilities of the project. To address this we trained a new NER model, using spaCy information on which, can be found in [this segment](https://github.com/ellak/gsoc2018-3gm/wiki/Named-Entity-Recognision) of the wiki and added new fact extraction algorithms using regular expressions.

Concerning regular expressions we expanded the entities.py file and added several expressions that aim to extract useful information for a wide range of users. The new module can detect monetary and non-monetary amounts, scales conditions, constraints, dates, exact times, duration and various other specific codes and numbers such as:

* URLs, e-mails, phone numbers, IBAN numbers, zip codes
* CPC and CPV codes
* IDs and Military IDs
* Natura regions, Wildlife sanctuaries, NUTS regions
* EU directives, regulations and decisions
* Ship tonnage, hull numbers and ship flags
* ISO and ELOT protocols
* [OPS](http://www.ops.gr/Ergorama/), [ADA](https://diavgeia.gov.gr/search)s, [AFM](https://ec.europa.eu/taxation_customs/tin/pdf/el/TIN_-_country_sheet_ES_el.pdf), [KAEK](https://www.lex.gr/index.php/el/ti-einai-o-kaek) numbers

Entity extraction is currently performed int the parser module. Each LawCodifier object contains an entities dictionary in the form of:

```
{'Urls': [], 'CPC Codes': [], 'CPV Codes': [], 'IBANs': [], 'E-mails': [], 'Id Numbers': [], 'Military Personel': [], 'Natura 2000 Regions': [], 'Scales': [], 'EU Directives': [], 'EU Regulations': [], 'EU Decisions': [], 'Phone Numbers': [], 'Protocols': [], 'AFM numbers': [], 'NUTS Region Codes': [], 'Exact times': [], 'Ship Tonnage': [], 'KAEK Codes': [], 'Hull': [], 'Flags': [], 'Monetary Amounts': [], 'Metrics': [], 'Conditions': [], 'Contraints': [], 'Durations': []}
```
Each entity extracted is the accompanied with a the number of the line it is found in the LawCodifier object.

You can access these dictionaries through the singleton variable for the codifier:

```
>>> codifier.codifier.laws[identifier].entities
```

Where identifier is the string corresponding to the law. For example 'π.δ. 84/2019' which can be found [here](https://www.kodiko.gr/nomologia/document_navigation/539871/p.d.-84-2019) returns the following entities:

```
π.δ. 84/2019 {'Urls': [], 'CPC Codes': [], 'CPV Codes': [], 'IBANs': [], 'E-mails': [(934, ['webmaster.et@et.gr']), (967, ['helpdesk.et@et.gr']), (970, ['webmaster.et@et.gr']), (972, ['grammateia@et.gr'])], 'Id Numbers': [], 'Military Personel': [], 'Natura 2000 Regions': [], 'Scales': [], 'EU Directives': [], 'EU Regulations': [], 'EU Decisions': [], 'Phone Numbers': [(957, [' 210 5279000', ' 210 5279054']), (960, [' 210 5279178']), (961, [' 210 5279000']), (962, [' 210 5279167', ' 210 5279139'])], 'Protocols': [], 'AFM numbers': [], 'NUTS Region Codes': [], 'Exact times': [(963, ['13:30'])], 'Ship Tonnage': [], 'KAEK Codes': [], 'Hull': [], 'Flags': [], 'Monetary Amounts': [(928, ['1,00 €']), (929, ['0,20 €']), (930, ['1,50 €']), (931, ['0,30 €'])], 'Metrics': [], 'Conditions': [(919, ['εάν']), (921, ['εάν']), (931, ['εάν']), (946, ['τις προϋποθέσεις'])], 'Contraints': [(184, ['πλην']), (609, ['πλην']), (614, ['πλην']), (784, ['μέχρι']), (922, ['αρκεί'])], 'Durations': [(919, ['επί']), (921, ['επί'])]}

```
