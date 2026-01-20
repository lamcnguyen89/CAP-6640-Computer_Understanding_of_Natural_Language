

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

(B) Explain why increasing sentence length and structural complexity exacerbates ambiguity, and why this makes deterministic language processing insufficient.

**Question 2: NLP Task Structure (Lecture 2)**
(A) Define syntactic, semantic, and pragmatic NLP tasks, and explain the type of information each operates on.

(B) Explain why higher-level NLP tasks depend on lower-level ones, and why errors at lower levels propagate upward.

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

