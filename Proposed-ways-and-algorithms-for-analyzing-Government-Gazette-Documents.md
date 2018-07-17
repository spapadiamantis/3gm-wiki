# Proposed ways and algorithms for analyzing Government Gazette Documents

To start with the typical structure a GG (e.g. FEK 1881) document contains articles each of which contains directions such as alterations, additions or deletions of sections such as paragraphs in other legal documents or the creation of new ones referred as “commands”. The whole GG document is signed by the competent ministers listed at the end of the documents. Then the main body of the article that has to be merged in another law or create a new law by its own.
The dataset should be split and commands should be extracted from the main bodies using named entity recognition for identifying Law IDs (defined as regular expressions) and separating commands from main bodies which are going to be altered. For example (taken from GG):

**Command**

Μετά το άρθρο 9Α του ν. 4170/2013, που προστέθηκε με το άρθρο 3 του ν. 4474/2017, προστίθεται άρθρο 9ΑΑ, ως εξής:

**Main Body**
Άρθρο 9ΑΑ 
Πεδίο εφαρμογής και προϋποθέσεις της υποχρεωτικής αυτόματης ανταλλαγής πληροφοριών όσον αφορά στην Έκθεση ανά Χώρα
1. Η Τελική Μητρική Οντότητα ενός Ομίλου Πολυεθνικής Επιχείρησης (Ομίλου ΠΕ) που έχει τη φορολογική της κατοικία στην Ελλάδα ή οποιαδήποτε άλλη Αναφέρουσα Οντότητα, σύμφωνα με το Παράρτημα ΙΙΙ Τμήμα ΙΙ, υποβάλλει την Έκθεση ανά Χώρα όσον αφορά το οικείο Φορολογικό Έτος Υποβολής Εκθέσεων εντός δώδεκα (12) μηνών από την τελευταία ημέρα του Φορολογικού 
Έτους Υποβολής Εκθέσεων του Ομίλου ΠΕ, σύμφωνα με το Παράρτημα ΙΙΙ Τμήμα ΙΙ.

Finally, a sequence of commands is generated, checked and then executed. For instance the above Command would add an article after another article in already merged law. 

## Method

An example method would be the following _heuristic_ method:

```
For each command

1. The words with high probabilities of being keywords are extracted via an LSTM model
2. For each (likely to be) keyword use a correlation method (e.g. weighted hamming distance) to extract the command (verb)
3. Detect Named Entities using regular expressions (e.g. laws and articles)
4. Construct the command sequence to be executed
5. Execute the command and store it to the database   
```