

# Assignment: Distributional Meaning and Word Embeddings
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


(B) Using vector orthogonality and dot products, explain why one-hot representations cannot encode semantic similarity.

**Question 4: Failure of Discrete Representations (Lecture 3)**
(A) Using the information retrieval example discussed in Lecture 3, explain why discrete representations fail to retrieve semantically related content.

(B) Explain why synonym-based fixes using lexical resources are insufficient, focusing on context sensitivity and graded similarity.

**Question 5: Distributional Semantics (Lecture 3)**
(A) Define distributional semantics using the concept of context windows and co-occurrence, and explain how meaning becomes data-driven.

(B) Explain how distributional semantics induces a geometric structure over words that enables similarity computation.

Question 6: Word2Vec as an Optimization Problem (Lecture 3)
(A) Describe the Word2Vec framework as a predictive learning problem, including the role of center and context words.

(B) Explain how maximizing prediction likelihood leads to semantically meaningful word embeddings.

**Question 7: Optimization and Efficiency (Lecture 4)**
(A) Explain why full gradient descent is infeasible for training word embeddings on large corpora.

(B) Explain how stochastic gradient descent and negative sampling address computational efficiency while preserving learning quality.

Question 8: Evaluation and Word Sense (Lecture 4)
(A) Compare intrinsic and extrinsic evaluation of word embeddings, including their strengths and limitations.

(B) Explain why static word embeddings struggle with word sense ambiguity and why global or contextual information is required.

