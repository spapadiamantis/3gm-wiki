# Evaluation and Metrics

## Evaluating the Accuracy of the Algorithm

### Detection Accuracy

Consider a statute and the links that point to it (in paragraph level). We consider applying the links in chronological order. We define the _Detection Accuracy_ as:

<p align='center'>

<img src="ac1.png">

</p>

Note that one paragraph might contain more than one amendment. We consider a detection successful iff there is at least one detection (since we do not know the number of amendments a priori). 

### Querying Accuracy

Then the number of successful queries divided by the number of amendments defines _Query Accuracy_

<p align='center'>

<img src="ac2.png">

</p>

### Overall Accuracy

For the overall Detection / Querying Accuracy we take the mean of the individual accuracies. 



