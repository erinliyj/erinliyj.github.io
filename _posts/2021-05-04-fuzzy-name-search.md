---
title: "Fuzzy Name Search"
excerpt: "With Application Explained"
last_modified_at: 2021-05-05 11:26:53
excerpt_separator: "<!--more-->"
categories:
  - Tips
tags:
  - Strings
  - Distance
  - Similarity
toc: true
---

## What this does
Given a string, return a list of similar strings from a defined library


## The use case

![Google Finance Search](/assets/images/google-finance-search.png)

When using Google Finance, I never have to type out the full name of a company before auto-complete fill the name for me. This can be done through fuzzy name matching in three easy steps.

#### Step 1: Define a library of legit names

First of all we need a list of company names that's legit. Normally this list can be obtained from website of the stock exchange. Take Nasdaq as an example, we can download a csv file of all traded companies here https://www.nasdaq.com/market-activity/stocks/screener. 


#### Step 2: Vectorize names
Both the library and the target company name are text strings. We can calculate **edit distance** as a mean of comparison. However, for more scalable solution, we will convert the strings to a vector of numbers using TFIDF. We will train a TFIDF vectorizers with company names.

```python
import pandas as pd
import pickle 

# First import the csv file with company names and transform to a list
company_names=pd.read_csv(input_file_path)['Name'].tolist()

# Then train a TFIDF vectorizer with it
from sklearn.feature_extraction.text import TfidfVectorizer

vectorizer_names = TfidfVectorizer(min_df=1, analyzer='char_wb', ngram_range=(3,3))
vectorizer_names.fit(company_names)
tf_idf_matrix_names = vectorizer_names.transform(company_names)

# Save the trained vectorizer for future use
import pickle
with open('vectorizer_names.pickle', 'wb') as handle:
    pickle.dump(vectorizer_names, handle, protocol=pickle.HIGHEST_PROTOCOL)
```

#### Step 3: Fuzzy name matching using Cosine Similarity

Now we can match the target name with names in the library. First we will transform the target name into a vector with the trained vectorizer.

```python
# Asssume I'm searching for google, and I typed GOOGL
tf_idf_input_names = vectorizer_names.transform(['GOOGL'])

```

Now we can compare this vector to the list of vectors in our name library by calculating cosine similarity. One popular python package is [pairwise] from sklearn.


[pairwise]:https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html

[sparse-dot-topn]:https://pypi.org/project/sparse-dot-topn/
