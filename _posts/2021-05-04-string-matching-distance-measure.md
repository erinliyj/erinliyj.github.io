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
1. Fuzzy name matching. When you need to match entreid based on, well, their names. However there can be typos or different spelling which makes exact string matching difficult.
2. String data cleaning. If you have a dataset with character field such as **city**, you can correct mispelling with string matching technique
3. Duplicate entry detection. The idea is simple, when the body of two sentences are 90% similar, they are probably duplicates

Next we will talk about how to achieve each of the above.

## Use Case One: Fuzzy Name Matching

## Use Case Two: Address Cleaning

## Use Case Three: Duplicate Question Detection


---


## Other Methods And Why We Don't Use Them
1. Hamming Distance (Complexity= $O$(n))
   
   > Hamming Distance measures the minimum number of *substitutions* required to change one string into the other.

   Hamming Distance requires two strings to be the **same length**. Which is always not the case in real world problems. 

   <script src="https://gist.github.com/erinliyj/531fca9050e7a62527017afe1dea37d4.js"></script>

2. Euclidean Distance
