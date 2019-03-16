
# Generating Word Embeddings - Lab

## Introduction

In this lab, we'll learn how to generate our own word embeddings by training our own Word2Vec model, and also by building embedding layers right into our Deep Neural Networks!

## Objectives

You will be able to:

* Demonstrate a basic understanding of the architecture of the Word2Vec model
* Demonstrate an understanding of the various tunable parameters of word2vec such as vector size and window size

## Getting Started

In this lab, we'll start by creating our own word embeddings by making use of the Word2Vec Model. Then, we'll move onto building Neural Networks that make use of **_Embedding Layers_** to accomplish the same end-goal, but directly in our model. 

The easiest way to make use of Word2Vec is to import it from the [Gensim Library](https://radimrehurek.com/gensim/). This model contains a full implementation of Word2Vec, which we can use to begin training immediately. For this lab, we'll be working with the [News Category Dataset from Kaggle](https://www.kaggle.com/rmisra/news-category-dataset/version/2#_=_).  This dataset contains headlines and article descriptions from the news, as well as categories for which type of article they belong to.  In this lab, we'll learn how to train a Word2Vec model on the text data to generate word embeddings for them. In the next lab, we'll then use the vectors created by our Word2Vec model to effectively train a classifier to predict the category of news given the headline and description of each article. In this lab, we won't do any classification, although we will learn how to train a Word2Vec model and explore the relationships between different word vectors in our embedding!

Run the cell below to import everything we'll need for this lab. 


```python
import pandas as pd
import numpy as np
np.random.seed(0)
from gensim.models import Word2Vec
from nltk import word_tokenize
```

Now, we'll import the data. You'll find the data stored in the file `'News_Category_Dataset_v2.json'`.  This file is compressed, so that it can be more easily stored in a github repo. **_Make sure to unzip the file before continuing!_**

In the cell below, use the `read_json` function from pandas to read the dataset into a DataFrame. Be sure to also include the parameter `lines=True` when reading in the dataset!

Once you've loaded in the data, inspect the head of the DataFrame to see what our data looks like. 


```python
raw_df = None
```

## Preparing the Data

Since we're working with text data, we'll still need to do some basic preprocessing and tokenize our data. You'll notice from the sample of the data above that two different columns contain text data--`headline` and `short_description`. The more text data our Word2Vec model has, the better it will perform. Therefore, we'll want to combine the two columns before tokenizing each comment and training our Word2Vec model. 

In the cell below:

* Create a column called `combined_text` that consists of the data from `df.headline` plus a space character (`' '`) plus the data from `df.short_description`.
* Use the `combined_text` column's `map()` function and pass in `word_tokenize`. Store the result returned in `data`.


```python
df['combined_text'] = None
data = None
```

Let's inspect the first 5 items in `data` to see how everything looks. 


```python
data[:5]
```

You'll notice that although the words are tokenized, they are still in the same order they were in as headlines. This is important, because the words need to be in their original order for Word2Vec to establish the meaning of them. Recall from our previous lesson on how Word2Vec works that we can specify a  **_Window Size_** that tells the model how many words to take into consideration at one time. 

If our window size was 5, then the model would start by looking at the words "Will Smith joins Diplo and", and then slide the window by one, so that it's looking at "Smith joins Diplo and Nicky", and so on, until it had completely processed the text example at index 1 above. By doing this for every piece of text in the entire dataset, the Word2Vec model learns excellent vector representations for each word in an **_Embedding Space_**, where the relationships between vectors capture semantic meaning (recall the vector that captures gender in the previous "king - man + woman = queen" example we saw).

Now that we've prepared our data, let's train our model and explore a bit!

## Training the Model

We'll start by instantiating a Word2Vec Model from gensim below. 

In the cell below:

* Create a `Word2Vec` model and pass in the following arguments:
    * The dataset we'll be training on, `data`
    * The size of the word vectors to create, `size=100`
    * The window size, `window=5`
    * The minimum number of times a word needs to appear in order to be counted in  the model, `min_count=1`.
    * The number of threads to use during training, `workers=4`


```python
model = None
```

Now, that we've created our Word2Vec model, we still need to train it on our model. 

In the cell below:

* Call `model.train()` and pass in the following parameters:
    * The dataset we'll be training on, `data`
    * The `total_examples`  of sentences in the dataset, which we can find in `model.corpus_count`. 
    * The number of `epochs` we want to train for, which we'll set to `10`

Great! We now have a fully trained model! The word vectors themselves are stored inside of a `Word2VecKeyedVectors` instance, which we'll find stored inside of `model.wv`. For simplicity's sake, let's go ahead and store this inside of the variable `wv` in order to save ourselves some keystrokes down the line. 


```python
wv = model.wv
```

## Examining Our Word Vectors

Now that we have a trained Word2Vec model, let's go ahead and explore the relationships between some of the words in our corpus! 

One cool thing we can use Word2Vec for is to get the most similar words to a given word. We can do this passing in the word to `wv.most_similar()`. 

In the cell below, let's try getting the most similar word to `'Texas'`.

Interesting! All of the most similar words are also states. 

We can also get the least similar vectors to a given word by passing in the word to the `most_similar()` function's `negative` parameter. 

In the cell below, get the least similar words to `'Texas'`.

These seem like just noise. This is because of the way Word2Vec is computing the similarity between word vectors in the embedding space. Although the word vectors closest to a given word vector are almost certainly going to have similar meaning or connotation with our given word, the word vectors that the model considers 'least similar' are just the word vectors that are farthest away, or have the lowest cosine similarity. It's important to understand that while the closest vectors in the embedding space will almost certainly share some level of semantic meaning with a given word, there is no guarantee that this relationship will hold at large distances. 

We can also get the vector for a given word by passing in the word as if we were passing in a key to a dictionary. 

In the cell below, get the word vector for `'Texas'`.

Let's get all of the word vectors from the object at once. We can find these inside of `wv.vectors`.  Do this now in the cell below.  

As a final exercise, let's try recreating the _'king' - 'man' + 'woman' = 'queen'_ example we've seen before. We can do this by using the `most_similar` function and putting the things we want added together inside of an array passed to the `positive` parameter, and the things we want subtracted as an array passed to the the `negative` parameter. 

Do this now in the cell below. 

As we can see from the output above, our model isn't perfect, but 'Queen' is still in the top 3, and with 'Princess' not too far behind. As we can see from the word in first place, 'reminiscent', our model is far from perfect. This is likely because we didn't give it too much training, or training data. However, for the small amount of training data it was given, the model still performs remarkably well! 

We'll see in the next lab that from a practical standpoint, one of the best things we can do for performance is to start by loading in the weights from an open-sourced model that has been trained for a very long time on a massive amount of data, such as the GloVe model from the Stanford NLP Group. There's not really any benefit from training the model ourselves, unless our text uses different, specialized vocabulary that isn't likely to be well represented inside an open-source model.

## Summary

In this lab, we learned how to train and use a Word2Vec model to created vectorized word embeddings!
