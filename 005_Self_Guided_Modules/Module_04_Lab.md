# Module 4 Self-Guided Lab: Neural Architectures and Subword Modeling

This lab is a self-directed, ungraded activity designed to help you operationalize the core concepts from Lectures 11–13. The goal is to move from architectural theory to hands-on understanding by experimenting with convolutional neural networks for text and subword-based representations that address vocabulary and morphology challenges.

You are encouraged to experiment freely. There is no submission or grading associated with this lab. The value comes from implementing components, inspecting intermediate representations, and connecting observed behavior back to the design motivations discussed in lecture.

Recommended Programming Environment
The recommended environment for this lab is Python using Google Colab. Colab provides a ready-to-use environment with GPU support (optional), no local installation, and easy access to modern deep learning libraries.

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 as the runtime
Core Libraries
numpy – numerical operations
torch – neural network implementation
torchtext – text preprocessing (optional)
sentencepiece – subword tokenization
matplotlib – visualization

```python
!pip install torch torchtext sentencepiece matplotlib
```

Standard Datasets
You may use any small text dataset. Recommended options:

AG News (topic classification)
IMDb (sentiment classification)
Any custom toy corpus for inspection
For simplicity, small hand-written datasets are sufficient for this lab.

## Activity 1: Text as a Sequence of Embeddings

This activity revisits the embedding layer as the interface between discrete text and neural computation.

Tokenize sentences into word indices
Map indices to dense vectors using an embedding layer
Inspect the shape of the resulting tensor

```python
import torch
import torch.nn as nn

vocab_size = 1000
embed_dim = 50
embedding = nn.Embedding(vocab_size, embed_dim)

sentence = torch.tensor([12, 45, 332, 78])
embedded = embedding(sentence)
embedded.shape
```

Think about:

Why does the output have shape (sequence_length, embedding_dim)?
Why does this representation preserve word order?

## Activity 2: Convolution Over Text

This activity demonstrates how CNNs extract local n-gram features.

```python
conv = nn.Conv1d(in_channels=embed_dim, out_channels=100, kernel_size=3)
x = embedded.transpose(0,1).unsqueeze(0)
features = conv(x)
features.shape
```

Think about:

What linguistic pattern does a width-3 filter capture?
Why are multiple filters needed?

## Activity 3: Max-Pooling and Salient Features

This activity explores why pooling is used in CNN-based text models.

```python
pooled = torch.max(features, dim=2).values
pooled.shape
```

Interpret max-pooling as feature selection
Compare pooled vs unpooled representations

## Activity 4: CNN-Based Text Classification

Combine embeddings, convolutions, pooling, and a classifier.

Build a simple CNN text classifier
Observe how local patterns influence predictions
Think about:

Why CNNs are efficient for long sequences
What information is lost compared to RNNs

## Activity 5: Subword Tokenization with SentencePiece

This activity introduces subword modeling to address vocabulary limitations.

```python
import sentencepiece as spm

spm.SentencePieceTrainer.train(
    input='toy_corpus.txt',
    model_prefix='spm',
    vocab_size=200,
    model_type='bpe'
)

sp = spm.SentencePieceProcessor()
sp.load('spm.model')
sp.encode("unbelievable", out_type=str)
```

Think about:

How subwords capture morphology
Why rare words benefit most

## Activity 6: Comparing Word-Level and Subword-Level Inputs

Compare CNN inputs using word tokens vs subword tokens.

Tokenize the same sentence both ways
Compare sequence lengths and coverage

Think about:

Trade-offs between sequence length and vocabulary size
Why subwords are standard in modern NLP models
Reflection
Why CNNs are effective feature extractors for text
How architectural bias shapes learned representations
Why subword modeling is essential for scalability and robustness
This lab prepares you for later modules on Transformers and pretrained language models, where subword tokenization and architectural efficiency are foundational.
