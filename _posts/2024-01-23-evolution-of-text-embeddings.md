---
layout: post
title:  "Evolution of Text Embeddings: From Words to Documents"
author: soma
categories: [Deep Learning]
image: assets/images/12.jpg
tags: [Deep Learning, Natural language Processing, Text embeddings]
image: assets/images/2024-01-23-evolution-of-text-embeddings/embeddings-cover.jpg
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

## 2. Sentence Embeddings (Second Generation)

### BERT (Bidirectional Encoder Representations from Transformers)

**Created by:** Google AI  

BERT introduced deep contextual embeddings using the Transformer architecture.  
Unlike earlier models, the meaning of a word changes depending on the context in which it appears.

The following Python code sample loads a **pre-trained BERT-based sentence embedding model** and generates a **vector representation for the sentence "Machine learning is fascinating"**.

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer("bert-base-nli-mean-tokens")
embedding = model.encode("Machine learning is fascinating")
```

**Key characteristics**

- Context-aware (bidirectional understanding)  
- Transformer-based architecture  
- Strong performance in NLP benchmarks  
- Embedding dimension: 768

### DistilBERT

**Created by:** Hugging Face  

DistilBERT is a compressed version of BERT created using **knowledge distillation**, a technique where a large model teaches a smaller model to perform similarly. It retains most of BERT’s performance while being faster and lighter.

The following Python code sample loads a **pre-trained DistilBERT-based sentence embedding model** and generates a **vector representation for the sentence "AI is transforming industries"**.

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer("distilbert-base-nli-stsb-mean-tokens")
embedding = model.encode("AI is transforming industries")
```
**Key characteristics**

- Faster and smaller than BERT  
- Retains contextual understanding  
- Suitable for production-scale applications  
- Embedding dimension: 768  

### SISTER (Simple SenTence EmbeddeR)

**Created by:** Community-driven Python ecosystem (built on fastText-style embeddings; commonly used in lightweight NLP pipelines)

SISTER generates sentence embeddings by averaging word vectors (typically fastText-based), making it efficient but less context-aware than transformer models.

The following Python code sample loads a **SISTER sentence embedding model** and generates a **vector representation for the sentence "Natural language processing is evolving"**.

```python
import sister

model = sister.MeanEmbedding(lang="en")
embedding = model("Natural language processing is evolving")
```

**Key characteristics**

- Lightweight and fast  
- Limited contextual understanding  
- Built on word-vector aggregation  
- Typical dimension: 300  



## 3. Text / Document Embeddings (Modern Generation)

Modern embedding models generate vector representations for **words, sentences, paragraphs, or entire documents** while capturing deeper semantic meaning and context.

These models are typically built using **Transformer architectures** and trained on very large datasets.

They power many modern AI applications including:

- Semantic search  
- Recommendation systems  
- Document clustering  
- Question answering  
- Retrieval-Augmented Generation (RAG)  
- Vector database retrieval  

Unlike early word embeddings, modern embeddings capture **context across longer text**, making them well suited for enterprise AI systems.

### Common Characteristics

- Context-aware semantic representations  
- Support for multiple text lengths (word → document)  
- High-dimensional vectors optimized for similarity search  
- Easy integration with APIs and vector databases  


### OpenAI Text Embeddings (`text-embedding-ada-002`)

**Created by:** OpenAI  

One widely used implementation of modern text embeddings is **`text-embedding-ada-002`**, available through the OpenAI API. It generates dense vector representations used in **semantic search, document retrieval, clustering, and recommendation systems**.

The following Python code sample uses the **OpenAI API** to generate a **text embedding** for the sentence *"Artificial intelligence is transforming businesses"*. The model converts the input text into a high-dimensional numerical vector that can be used for tasks such as **semantic search, similarity comparison, clustering, and retrieval systems**.

```python
from openai import OpenAI

client = OpenAI()

emb = client.embeddings.create(
    model="text-embedding-ada-002",
    input="Artificial intelligence is transforming businesses"
)

vector = emb.data[0].embedding
```

Newer embedding models have been introduced with improvements in **accuracy, efficiency, and multilingual capability**.


### OpenAI (`text-embedding-3-small`)

**Created by:** OpenAI  

A newer OpenAI embedding model optimized for **cost-efficient semantic search and large-scale retrieval systems**.

**Key characteristics**

- Embedding dimension: 1536  
- Optimized for high-volume semantic search  
- Lower cost than earlier models  
- Compatible with most vector databases  



### OpenAI (`text-embedding-3-large`)

**Created by:** OpenAI  

Designed for **higher semantic accuracy**, especially in enterprise search and knowledge retrieval systems.

**Key characteristics**

- Embedding dimension: 3072  
- Higher semantic precision than smaller models  
- Suitable for complex retrieval tasks  

---

### Cohere Embeddings (`embed-v3`)

**Created by:** Cohere  

Cohere provides **multilingual embeddings** designed for search, clustering, and classification across many languages.

**Key characteristics**

- Strong multilingual support  
- Optimized for retrieval and ranking  
- Commonly used in enterprise NLP pipelines

The following Python code sample uses the **Cohere API** to generate a **text embedding** for the sentence *"AI is transforming industries"*. 

```python
import cohere

co = cohere.Client("YOUR_API_KEY")

response = co.embed(
    texts=["AI is transforming industries"],
    model="embed-english-v3.0"
)

vector = response.embeddings[0]
```

### Google Embeddings (textembedding-gecko)

**Created by:** Google  

Available through **Google Vertex AI**, these embeddings support applications such as **semantic search, document similarity, recommendation systems, and retrieval pipelines** within the Google Cloud ecosystem.

**Key characteristics**

- Integrated with the **Google Cloud AI ecosystem**
- Supports **semantic search and recommendation tasks**
- Designed for **enterprise AI pipelines**

The following Python code sample uses **Google Vertex AI's embedding model (`textembedding-gecko`)** to generate a **vector representation of a sentence**.  


```python
from vertexai.language_models import TextEmbeddingModel

model = TextEmbeddingModel.from_pretrained("textembedding-gecko")

embeddings = model.get_embeddings(
    ["Artificial intelligence is transforming businesses"]
)

vector = embeddings[0].values
```

## Summary

The evolution of text embeddings reflects the rapid advancement of **Natural Language Processing (NLP)**, progressing from simple word representations to sophisticated semantic models capable of understanding entire documents and powering modern AI applications.

### 1. Word-Level Embeddings (Static Representations)

**Examples:** GloVe, Word2Vec, FastText  

**Focus:** Representing the meaning of individual words based on co-occurrence patterns in large text corpora. These embeddings assign a **single vector to each word** and do **not capture context**.

---

### 2. Sentence-Level Embeddings (Contextual Representations)

**Examples:** BERT, DistilBERT, SISTER  

**Focus:** Capturing **contextual meaning within sentences**, allowing models to better understand relationships between words depending on their usage.

---

### 3. Modern Text / Document Embeddings (API and Cloud-Based)

**Examples:**  
text-embedding-ada-002, text-embedding-3-small, text-embedding-3-large, Cohere embed-v3, Google textembedding-gecko  

**Focus:** Generating **semantic representations for text at multiple levels** — from words to full documents. These models are typically delivered through **APIs or cloud AI platforms** and are widely used in:

- Semantic search  
- Vector databases  
- Recommendation systems  
- Document retrieval  
- Retrieval-Augmented Generation (RAG)

---

Overall, embeddings have evolved from **static word vectors → contextual sentence representations → scalable semantic embeddings for entire documents**, forming a foundational component of many modern AI systems.