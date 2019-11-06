# bagel-TextBlob

## Building a Text Classification System

### Adding Data

**First we’ll create some training and test data:**
Using/editing the dummmy data from `train.json` & `test.json`.

### Loading Data from Files

***Example:*** Passing the opened file into the constructor

```py
with open('train.json', 'r') as fp:
    cl = NaiveBayesClassifier(fp, format="json")
```

### Creating a Classifier & Training it

```py
from textblob import TextBlob
from textblob.classifiers import NaiveBayesClassifier
with open('train.json', 'r') as fp:
    cl = NaiveBayesClassifier(fp, format="json")
```

### Classifying Text

Call the **classify(text)** method to use the classifier.

***Example:***

```py
cl.classify("This is an amazing library!")
```

Or if you have more than 1 line of text:

```py
blob = TextBlob("The beer is good. But the hangover is horrible.", classifier=cl)
for s in blob.sentences:
    print(s)
    print(s.classify())
```

### For Sentiment Analysis

***Example of positive:***

```py
from textblob import TextBlob
from textblob.sentiments import NaiveBayesAnalyzer
blob = TextBlob("I love this library", analyzer=NaiveBayesAnalyzer())
blob.sentiment
```

***Example of negative:***

```py
from textblob import TextBlob
from textblob.sentiments import NaiveBayesAnalyzer
blob = TextBlob("My boss is horrible.", analyzer=NaiveBayesAnalyzer())
blob.sentiment
```
