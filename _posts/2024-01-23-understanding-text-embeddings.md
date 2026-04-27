---
layout: post
title:  "Understanding Text Embeddings: From Words to Documents"
author: soma
categories: [Deep Learning]
image: assets/images/12.jpg
tags: [Deep Learning, Natural language Processing , Text embeddings]
image: assets/images/2022-11-10-hyperparameter-optimization-deep-neural-networks/Hyperparameter-optimization-cover1.jpg
description: "Evolution of Text Embeddings: From Words to Documents."
# featured: false
# hidden: true
# rating: 4.5
comments: true
---
# Evolution of Text Embeddings: From Words to Documents

Text embeddings convert language into numerical vectors that machines can understand. Over time, embeddings evolved from representing individual words to sentences and full documents, significantly improving contextual understanding and downstream NLP performance.

Below is a brief overview of how text embedding techniques have evolved over time.

## 1. Word Embeddings (First Generation)

### GloVe (Global Vectors for Word Representation)

**Created by:** Stanford University Research  

GloVe is one of the earliest widely adopted word embedding methods. It learns word representations by leveraging global word co-occurrence statistics from large corpora such as Wikipedia and Gigaword.

GloVe is effective for capturing semantic similarity but does not understand context dynamically (static embeddings).

The following Python code sample loads pre-trained **GloVe embeddings** and retrieves the vector representation of the word **"king"**.

```python
from gensim.downloader import load

glove = load("glove-wiki-gigaword-300")
vector = glove["king"]
```

**Key characteristics:**

- Static word embeddings (same vector for each word)  
- Strong at semantic similarity tasks  
- Trained on large corpora (e.g., Wikipedia and Gigaword)  
- Typical embedding dimension: **50–300**


### Word2Vec

**Created by:** Google Research  

Word2Vec introduced neural network–based embeddings using **CBOW (Continuous Bag of Words)** and **Skip-Gram** architectures. It became one of the foundational techniques in modern NLP for learning distributed word representations.  

The following Python code sample loads pre-trained **Word2Vec embeddings** and retrieves the vector representation of the word **"computer"**.

```python
from gensim.downloader import load

w2v = load("word2vec-google-news-300")
vector = w2v["computer"]
```

**Key characteristics:**

- Learns word relationships via prediction tasks  
- Captures analogies *(king - man + woman ≈ queen)*  
- Static embeddings (no context awareness)  
- Trained on the Google News corpus  
- Typical embedding dimension: **300**


### FastText

**Created by:** Facebook AI Research (FAIR)

FastText extends Word2Vec by representing words as **character n-grams**. This allows the model to better handle **rare words, misspellings, and morphologically complex languages**.

The following Python code sample trains a simple **FastText model** and retrieves the **vector representation of the word "processing"**.

```python
from gensim.models import FastText

model = FastText(sentences=[["natural", "language", "processing"]], vector_size=100)
vector = model.wv["processing"]
```

**Key characteristics**

- Uses subword (character n-gram) information  
- Better handling of out-of-vocabulary words  
- Still static embeddings  
- Useful for morphologically rich languages


