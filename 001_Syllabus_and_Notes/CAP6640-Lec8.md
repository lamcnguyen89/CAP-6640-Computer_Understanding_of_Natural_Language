Lecture 8: Language Modeling: N-Grams, Sparsity, and Neural Language Models
This lecture introduces language modeling as a core computational task in Natural Language Processing. A language model is defined as a system that assigns probabilities to word sequences and predicts the next word based on preceding context. The lecture develops this idea formally, beginning with probabilistic definitions and progressing through classical n-gram language models, their limitations, and their partial solutions.

The lecture emphasizes why language modeling is foundational to NLP applications, how probabilistic assumptions simplify computation, and why sparsity and storage constraints fundamentally limit count-based models. These limitations motivate the introduction of neural and fixed-window language models as alternatives that generalize beyond exact word counts.

Key Point: A language model assigns probabilities to word sequences and predicts the next word based on prior context.
Lecture Objectives
Introduce the basic notion of language models
Define language modeling as next-word prediction
Explain n-grams as probabilistic language models
Identify sparsity and storage problems in n-gram models
Explain smoothing, backoff, and interpolation
Introduce fixed-window and neural language models
What Is Language Modeling?
Language modeling is the task of predicting the next word in a sequence given previous words. Formally, given a sequence of words:

x(1), x(2), x(3), …, x(t)

a language model computes a probability distribution over the next word:

P(x(t+1) | x(1), x(2), …, x(t))

where x(t+1) can be any word in the vocabulary V = {w1, …, w|V|}. Any system that computes this distribution is called a language model (LM).

Language Models as Probability Assigners
A language model can also be viewed as a system that assigns a probability to an entire piece of text. Given a sequence:

x(1), x(2), x(3), …, x(T)

the model assigns a probability to the sequence based on how likely the word order is under natural language usage.

This perspective explains why language models can be used to compare alternative sentences or completions based on probability.

Motivation: Why Language Models?
Language models are central to NLP because they support:

Understanding context: capturing semantic and syntactic structure
Reducing ambiguity: preferring likely word sequences
Human–computer interaction: enabling fluent responses
Search and retrieval: improving relevance of results
Applications of Language Models
Speech recognition
Machine translation
Text auto-completion and prediction
Chatbots and virtual assistants
Summarization and text generation
Optical character recognition (OCR)
The n-Gram Language Model
Before deep learning, language modeling was primarily approached using n-gram models. An n-gram is a sequence of n consecutive words.

Unigram: “the”, “students”, “opened”
Bigram: “the students”, “students opened”
Trigram: “the students opened”
4-gram: “the students opened their”
The key assumption is that the next word depends only on the previous n−1 words.

Estimating n-Gram Probabilities
n-gram probabilities are estimated by counting occurrences in a large corpus. For example, in a 4-gram model:

“students opened their” occurred 1000 times
“students opened their books” occurred 400 times
“students opened their exams” occurred 100 times
This yields:

P(books | students opened their) = 0.4
P(exams | students opened their) = 0.1

Problem 1: Sparsity in n-Grams
As n increases, many valid word sequences never appear in training data. This leads to zero probabilities for unseen n-grams.

Causes of sparsity include:

Finite training data
Rare or novel phrases
Exponential growth of possible n-grams
For a vocabulary of 10,000 words:

Bigram space: 108
Trigram space: 1012
Key Point: Many valid word sequences receive zero probability due to data sparsity.
General Solutions to Sparsity
Smoothing: add small counts (e.g., Laplace smoothing)
Kneser–Ney smoothing: context-sensitive adjustment
Backoff: use lower-order n-grams
Interpolation: combine multiple n-gram orders
Problem 2: Storage in n-Gram Models
n-gram models must store counts for all observed n-grams. Increasing n or corpus size increases model size substantially.

Although small models (e.g., trigram models over Reuters) can be built quickly, probability distributions often lack granularity and generalization.

Generating Text with n-Grams
n-gram models can generate text by repeatedly sampling the next word from the predicted probability distribution. While generated text often has reasonable local grammar, it is frequently globally incoherent.

This demonstrates that grammaticality alone does not guarantee semantic coherence.

Neural Language Models (Motivation)
To overcome sparsity and storage issues, neural language models replace discrete counts with continuous representations. Rather than memorizing n-grams, neural models learn to generalize based on similarity between word contexts.

The lecture introduces fixed-window neural language models as a bridge from count-based models to fully sequential neural models covered in later lectures.

Fixed-Window Language Models
Fixed-window language models predict the next word using a neural network that consumes a fixed number of preceding words, similar to window-based classification used earlier for NER.

Example:

as the proctor started the clock the students opened their _______

The model scores candidate words based on the window and selects the most likely completion.

Lecture Takeaway
This lecture establishes probabilistic language modeling as the foundation of sequence prediction in NLP. n-gram models provide a simple and interpretable baseline, but suffer from sparsity and storage limitations. These limitations motivate neural language models that generalize beyond exact word counts and prepare the ground for recurrent and sequence-based models introduced next.

