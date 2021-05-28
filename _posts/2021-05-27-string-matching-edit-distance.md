---
title: "String Matching With Edit Distance"
excerpt: "With Three Applications Explained."
last_modified_at: 2021-05-28 15:18:05
excerpt_separator: "<!--more-->"
categories:
  - Tips
tags:
  - Strings
  - Distance
  - Similarity
toc: true
---

## It's application

String matching is a useful technique in text analysis. Here we will focus on **edit distance** methods.

## Levenshtein Distance

A common method is to use Levenshtein distance. It calculates edit distance of two strings, and edit can be substitution, insertion, or deletion.

<script src="https://gist.github.com/erinliyj/b812c40a6298fadb3ab7843be160e1e5.js"></script>

Levenshtein distance works well for matching one-word strings. There are a lot more interesting ways of approximate and phonetic matching of strings. **Jellyfish** and **fuzzy** are two popular python packages to be used. Make sure to check them out!


## Hamming Distance
   
> Hamming distance measures the minimum number of *substitutions* required to change one string into the other.

It requires two strings to be the **same length**, which is rarely the case in real world problems. 

<script src="https://gist.github.com/erinliyj/531fca9050e7a62527017afe1dea37d4.js"></script>

