# Module 1 Self-Guided Lab: Distributional Semantics and Word Embeddings

This lab is a self-directed, ungraded activity designed to help you operationalize the core concepts from Lectures 2–4. The goal is to move from theory to practice by exploring how word meaning emerges from data, how embeddings are learned through optimization, and how their quality can be analyzed empirically.

You are encouraged to experiment freely. There is no submission or grading associated with this lab. The value comes from running the code, observing the behavior of representations, and connecting those observations back to the lecture concepts.

Recommended Programming Environment
The recommended environment for this lab is Python using Google Colab. Colab provides a ready-to-use environment with GPU support (optional), no local installation, and easy access to common NLP libraries.

To get started:

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 as the runtime
All code snippets below are compatible with Colab.

Core Libraries
The following libraries will be used throughout the lab:

numpy – numerical computation and vector operations
scikit-learn – similarity computation, dimensionality reduction
gensim – Word2Vec implementation and pretrained embeddings
matplotlib – visualization
Install (or confirm) these libraries in Colab:

```python
!pip install numpy scikit-learn gensim matplotlib
```

Standard Datasets
You may use any text corpus, but the following are standard, well-supported options:

Text8: A cleaned Wikipedia subset (commonly used for Word2Vec)
Wikipedia dumps: For larger-scale experiments
NLTK sample corpora: Small and convenient for quick testing
Example: loading the Text8 dataset using Gensim:

```python
from gensim.models import Word2Vec
from gensim.models.word2vec import Text8Corpus

corpus = Text8Corpus('text8')
```

(Colab users may need to download the dataset first.)

## Activity 1: One-Hot Encoding and Its Limitations

This activity demonstrates why discrete representations fail to capture semantic similarity.

Steps:

Build a small vocabulary from a corpus
Represent words using one-hot vectors
Compute similarity between words

```python
import numpy as np

vocab = ["hotel", "motel", "cat", "quantum"]
word_to_index = {w:i for i,w in enumerate(vocab)}

def one_hot(word):
    vec = np.zeros(len(vocab))
    vec[word_to_index[word]] = 1
    return vec

hotel = one_hot("hotel")
motel = one_hot("motel")

np.dot(hotel, motel)
```

Think about:

Why is the similarity always zero for distinct words?
What geometric property causes this behavior?

## Activity 2: Distributional Semantics with Context Windows

This activity operationalizes the idea that meaning comes from context.

Steps:

Define a symmetric context window
Collect word–context co-occurrence counts
Inspect which words appear in similar contexts

```python
from collections import defaultdict

corpus = "i like deep learning i like nlp i enjoy flying".split()
window_size = 2
cooccurrence = defaultdict(lambda: defaultdict(int))

for i, word in enumerate(corpus):
    for j in range(max(0, i-window_size), min(len(corpus), i+window_size+1)):
        if i != j:
            cooccurrence[word][corpus[j]] += 1
```

Think about:

How does window size affect the type of similarity captured?
Why are these matrices sparse?

## Activity 3: Training Word Embeddings (Word2Vec)

This activity treats Word2Vec as an optimization problem.

Steps:

Train a Word2Vec model
Inspect learned embeddings
Compute similarity between words

```python
from gensim.models import Word2Vec

sentences = [
    ["i","like","deep","learning"],
    ["i","like","nlp"],
    ["i","enjoy","flying"]
]

model = Word2Vec(
    sentences,
    vector_size=50,
    window=2,
    min_count=1,
    sg=1  # Skip-gram
)

model.wv.similarity("deep", "nlp")
```

Think about:

Why does similarity emerge without explicit synonym rules?
What role does optimization play?

## Activity 4: Count-Based vs. Predictive Representations

Compare co-occurrence-based vectors with learned embeddings.

Steps:

Apply dimensionality reduction (e.g., SVD or PCA) to co-occurrence matrices
Compare neighborhood structure with Word2Vec embeddings

```python
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt

words = ["like", "deep", "nlp", "enjoy"]
vectors = [model.wv[w] for w in words]

pca = PCA(n_components=2)
proj = pca.fit_transform(vectors)

plt.scatter(proj[:,0], proj[:,1])
for i, w in enumerate(words):
    plt.text(proj[i,0], proj[i,1], w)
plt.show()
```

## Activity 5: Evaluating Word Embeddings

Explore both intrinsic and extrinsic evaluation.

Intrinsic:

Word similarity using cosine similarity
Analogy-style vector arithmetic

```python
model.wv.most_similar(positive=["king","woman"], negative=["man"])
```

Extrinsic (optional):

Use embeddings as features in a small classification task
Observe performance impact

## Word Sense Exploration

Inspect how static embeddings conflate multiple meanings.

```python
model.wv.most_similar("bank")
```

Think about:

Which senses are mixed together?
Why does this happen in static embeddings?
Reflection
As you complete this lab, reflect on the following:

How optimization shapes semantic geometry
Why embeddings generalize better than symbolic representations
What limitations remain in static word vectors
This lab prepares you conceptually and practically for later topics involving contextual and transformer-based representations.
