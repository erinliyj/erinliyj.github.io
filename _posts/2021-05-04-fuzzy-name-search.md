---
title: "String Matching With Distance Measures"
excerpt: "With Three Applications Explained."
last_modified_at: 2021-05-05 11:26:53
excerpt_separator: "<!--more-->"
categories:
  - Tips
tags:
  - NLP
  - Strings
  - Distance
  - Similarity
toc: true
---

## What this does
Given a string, return a list of similar strings from a defined library


## The use case
![Google Finance Search]({{ site.url }}{{ site.baseurl }}/assets/images/google-finance-search.png)

When using Google Finance, I never have to type out the full name of a company before auto-complete fill the name for me. This can be done through fuzzy name matching in three easy steps.

#### Step 1: Define a library of legit names

First of all we need a list of company names that's legit. Normally this list can be obtained from website of the stock exchange. Take Nasdaq as an example, we can download a csv file of all traded companies here https://www.nasdaq.com/market-activity/stocks/screener. 

You can automate this process through web scraping. 


#### Step 2: Vectorize names

#### Step 3: Fuzzy name matching




