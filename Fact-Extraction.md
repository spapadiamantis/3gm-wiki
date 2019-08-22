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

Where identifier is the string corresponding to the law. For example 'ν. 4513/2018'.


