---
title: "String Matching With Distance Measures"
excerpt: "With Three Applications Explained."
last_modified_at: 2021-05-05 11:26:53
excerpt_separator: "<!--more-->"
categories:
  - Tips
tags:
  - Machine Learning
  - Data Science
  - NLP
  - Strings
  - Distance
  - Similarity
toc: true
---

## It's application

String matching is a useful technique in text analysis. It can be used for the following purposes:
1. Fuzzy name matching. When you need to match entries based on, well, their names. However, there can be typos or different spelling which makes exact string matching difficult.
2. String data cleaning. If you have a dataset with character field such as **city name**, you can correct misspelling with string matching technique
3. Detect duplicate questions 
4. Recommand similar posts

Next we will talk about how to achieve each of the above.

## Use Case One: Fuzzy Name Matching

A common method is to use Levenshtein distance. It calculates edit distance of two strings, and edit can be substitution, insertion, or deletion.

<script src="https://gist.github.com/erinliyj/b812c40a6298fadb3ab7843be160e1e5.js"></script>

Levenshtein distance works well for matching one-word strings. There are a lot more interesting ways of approximate and phonetic matching of strings. **Jellyfish** and **fuzzy** are two popular python packages to be used. Make sure to check them out!


## Use Case Two: Address Cleaning

:construction_worker: Work in progress...


## Use Case Three: Duplicate Question Detection

In this use case we are dealing with longer strings, for example, the header of a question asked on Stack Overflow. How do we detect if similar questions have been asked before? We can achieve this in two steps
  - Step A: encode text into numbers
  - Step b: calculate similarity.

For demonstration, I will use this [Stack Overflow data on Kaggle](https://www.kaggle.com/stackoverflow/stackoverflow?select=posts_questions). And I will use three different methods for **step A** and **step B**. You can mix-n-match these different methods


#### TFIDF + Cosine Similarity

#### Word2Vec + ???

#### :robot:Transformers + ???



<!-- Include some speed test here -->

---


## Other Methods And Why We Don't Use Them
1. Hamming distance: complexity= $O(n)$
   
   > Hamming distance measures the minimum number of *substitutions* required to change one string into the other.

   It requires two strings to be the **same length**, which is rarely the case in real world problems. 

   <script src="https://gist.github.com/erinliyj/531fca9050e7a62527017afe1dea37d4.js"></script>
   <!-- 
  ```python

  def hamming_distance(x, y):
    return sum()
  
  ``` -->

2. Euclidean Distance
