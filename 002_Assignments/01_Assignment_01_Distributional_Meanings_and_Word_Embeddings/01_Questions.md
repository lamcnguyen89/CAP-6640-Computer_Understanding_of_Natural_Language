

# Assignment 1: Distributional Meaning and Word Embeddings
This assignment examines how meaning is represented, learned, optimized, and evaluated in Natural Language Processing. All questions are based strictly on the material covered in Lectures 2, 3, and 4. Each question consists of two parts and requires precise, technically grounded answers.

This is an individual assignment. Clarity, correctness, and depth of reasoning are expected.

## Requirements

Unlimited Attempts Allowed
Available: Jan 13, 2026 12:00am until Jan 28, 2026 11:59pmAvailable: Jan 13, 2026 12:00am until Jan 28, 2026 11:59pm

**Submission Guidelines**
Submit a single PDF document
Clearly label each question and part (A, B)
Answers should be concise, technical, and well-structured
Do not include material beyond Lectures 2–4
Each question is worth 5 pts

## Questions

**Question 1: Why Natural Language Is Hard (Lecture 2)**
(A) Explain why ambiguity is a fundamental challenge in natural language understanding. Your answer must address how ambiguity arises from structure, context, and interpretation.

Ambiguity as a fundamental challenge in NLP can be explained through these 3 concepts: Structure, Context and Interpretation. 

- Structure: Is the grammatical organization of language. Ambiguity can arise for example in a sentence where there are multiple subjects and objects, and it is not so clear cut which is which. Or you might have a grammatical structure in formal written prose, but those rules will change in informal texts such as text messaging, or say twitter texts.

- Context: A word can have different meanings depending on the surrounding words. For example the word "Camping" can mean going out and living in outdoor environments, or it can mean staying in a spot and not moving inside a video game

- Interpretation: An example would be how a phrase can be neutral or aggressive depending on many subjective factors.

(B) Explain why increasing sentence length and structural complexity exacerbates ambiguity, and why this makes deterministic language processing insufficient.

Ambiguity is increased with length and complexity because that is more data and relationships that the computer has to parse and understand. The more data that has to be dealt with the more computing power is required. And currently, we do not have enough data or computing power to make nlp deterministic.

**Question 2: NLP Task Structure (Lecture 2)**
(A) Define syntactic, semantic, and pragmatic NLP tasks, and explain the type of information each operates on.

- Syntactic Tasks: Understands language structure such as grammar. It operates on characters and individual symbols.

- Semantic Tasks: Aims to capture the meaning of words. It operates on the units of words, sentences, and entire texts

- Pragmatic Tasks: Interprets language in contexts. The units of understanding pragmatic tasks are situational factors, tone and implied meanings

(B) Explain why higher-level NLP tasks depend on lower-level ones, and why errors at lower levels propagate upward.

The lowest level tasks are syntactic tasks. They are the foundation of the higher level tasks such as pragmatic tasks and you have to get the foundations first. For example, how are you able to understand the meaning behind a text if you are unable to read the words (syntax).

**Question 3: One-Hot Encoding and Geometry (Lecture 3)**
(A) Formally describe one-hot encoding for a vocabulary of size |V|, including its dimensionality and geometric interpretation.

One-Hot Encoding is turning a group of words into a matrix/vector that the computer can read and understand. For a vocabulary of size |V|, the vector of a single word will have a dimension of size V x V. And the numbers will be diagonal along this square vector.

(B) Using vector orthogonality and dot products, explain why one-hot representations cannot encode semantic similarity.

When you take the dot product of words that have too similar of a vector, the result is orthogonal. This creates issues when trying to to encode similar words.

**Question 4: Failure of Discrete Representations (Lecture 3)**
(A) Using the information retrieval example discussed in Lecture 3, explain why discrete representations fail to retrieve semantically related content.

Because the dot product of semantically similar words is orthogonal

(B) Explain why synonym-based fixes using lexical resources are insufficient, focusing on context sensitivity and graded similarity.

These fixes miss nuance. A heuristic of how words are used doesn't apply to all situations. Next, these resources can be out of date since language changes quickly. Next, it takes human labor and finally, there is no accurate calculation of word similarity tht is required for accurate NLP processing.

**Question 5: Distributional Semantics (Lecture 3)**
(A) Define distributional semantics using the concept of context windows and co-occurrence, and explain how meaning becomes data-driven.

Distributional semantics are when a words meaning is given by other words that it often appears closely by. Context window is the size of number of words around the object word that the algorithm is looking at in order to determine the meaning of the word. The larger the context window, the more words the algorithm looks at surrounding the word. So the meaning of the word becomes data-driven because the more instances that you find words together, the more likely that this meaning involves close by words. This can be measured statistically and therefore it becomes data-driven.

(B) Explain how distributional semantics induces a geometric structure over words that enables similarity computation.

The geometric structure can be considered where similar words will be closer together and clumped in groups within the vector space of all the words. The closer they are together in clumps, the more similar they are. 

**Question 6: Word2Vec as an Optimization Problem (Lecture 3)**
(A) Describe the Word2Vec framework as a predictive learning problem, including the role of center and context words.

Word2Vec is where we have a large body of text, where there is a fixed vocabulary. Each word is represented by a vector. It is predictive because the algorithm is trying to determine the context of words with the context window. The center of the context window is the word you are trying to predict.

(B) Explain how maximizing prediction likelihood leads to semantically meaningful word embeddings.

The more likely and often that words are close together, means that they are more likely to be embedded together and therefore meaningful definitions can be created by words close together

**Question 7: Optimization and Efficiency (Lecture 4)**
(A) Explain why full gradient descent is infeasible for training word embeddings on large corpora.

It is infeasible because using full gradient descent will take too long and require too much compute power.

(B) Explain how stochastic gradient descent and negative sampling address computational efficiency while preserving learning quality.

SGD addresses computational efficiency by repeatedly sampe windows and update after each one. Negative sampling address efficiency by  training binary logistic regression for a true pair versus several noise pairs.

**Question 8: Evaluation and Word Sense (Lecture 4)**
(A) Compare intrinsic and extrinsic evaluation of word embeddings, including their strengths and limitations.

Intrinsic evaluation is fast to compute and helps to understand the system. However it is not clear whether the evaluation has any real basis in reality.

Extrinsic evaluation takes a long time to compute and is unclear if the iterations or subsystem is the problem. However it is based in reality.

(B) Explain why static word embeddings struggle with word sense ambiguity and why global or contextual information is required.

Static word embeddings struggle because words can have multiple meanings and the meaning is determined by the context of the surrounding words.