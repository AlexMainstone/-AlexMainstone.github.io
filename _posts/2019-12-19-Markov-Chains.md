---
layout: post
title: 'Markov Chains'
date: 2019-12-19 18:26:22
description: Generating Fantasy city names with Markov chains
tags: AI gamedev maths
categories:
---

I have been working on generating random world maps and decided to give name generation a shot. I now have a header file that can be fed words to generate new words using the input as a dataset.

## Forming a dataset
It should be noted first that I will be using `n` to represent the number of letters we are storing as our key in the map.

First things first, we need to generate a dataset, to store this dataset I used the following variable:

`map<string, vector<pair<int char>>> markov_data`

Which means we access it as follows:

`following_letter_frequency = markov_data[N-LETTER PAIR]`

So for each n-letters we store every possible character that comes after, we store this in a pair with an integer that we can incrememt to represent the frequency in which this character appears after the n-letters.

So, I loop through the input data, take every n-sets of letters and store the following letter in the corresponding pair vector.

## Creating new data
Now, all we have to do is get a random key for our map as our start, then pick the next letters to come after our current last `n` letters, we do this an appropriate amount of times to create reasonably sized names (4-9ish). I decided to ensure that the random start decided by the key always has at least vowel, as I didn't think names like that looked right.

## Output
```
eyci
adee
rallech
vamelc
ecari
uend
tunnid
ubinesig
verina
eital
xinah
iphilda
uzylysph
ierta
``` 
