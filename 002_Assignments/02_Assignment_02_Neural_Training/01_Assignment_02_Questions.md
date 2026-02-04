# Assignment 2: Neural Training, Optimization, and Parsing
This assignment examines how neural models are trained for NLP tasks and how syntactic structure is formally represented and computed. All questions are based strictly on the material covered in Lectures 5, 6, and 7. Each question consists of two parts and requires precise, technically grounded answers.

This is an individual assignment. Clarity, correctness, and depth of reasoning are expected.

## Requirements

Unlimited Attempts Allowed
Available: Jan 13, 2026 12:00am until Feb 11, 2026 11:59pm1/13/2026 to 2/11/2026

**Submission Guidelines**
Submit a single PDF document
Clearly label each question and part (A, B)
Answers should be concise, technical, and well-structured
Do not include material beyond Lectures 5–7
Each question is worth 5 pts (total: 40 pts)
Choose a submission type

## Questions

**Question 1: Window-Based NER Classification (Lecture 5)**
(A) Explain how Named Entity Recognition (NER) for location entities is formulated as a binary classification problem using fixed-size context windows.

(B) Using the sentence examples discussed in Lecture 5, explain how changing the content of a context window alters the semantic interpretation of the center word.

**Question 2: Neural Scoring Functions (Lecture 5)**
(A) Describe how a feed-forward neural network is used to compute an unnormalized score for a context window.

(B) Explain why these scores are not probabilities and how they are used comparatively during training.

**Question 3: Max-Margin Loss and Corrupted Windows (Lecture 5)**
(A) Formally describe the max-margin loss function used in Lecture 5, including the roles of the true window score and the corrupted window score.

(B) Explain why model parameters are updated only when the margin constraint is violated and how this focuses learning.

**Question 4: Retraining Word Vectors Pitfall (Lecture 5)**
(A) Using the “TV / telly / television” example, explain what happens to word representations when embeddings are updated during training.

(B) Explain why this behavior creates a mismatch between training and testing, and why small datasets exacerbate the problem.

**Question 5: Backpropagation and Computational Graphs (Lecture 6)**
(A) Explain how a neural network can be represented as a computational graph, identifying the roles of source nodes, intermediate nodes, and edges.

(B) Explain how gradients are propagated through this graph during backpropagation, distinguishing between local gradients and upstream gradients.

**Question 6: Gradient Computation and Learning Dynamics (Lecture 6)**
(A) Explain how the chain rule is applied at a single node during backpropagation to compute gradients with respect to model parameters.

(B) Explain why backpropagation proceeds in the reverse direction of the forward pass and how this enables error minimization.

**Question 7: Phrase Structure and Structural Ambiguity (Lecture 7)**
(A) Define phrase structure and explain how hierarchical organization gives rise to multiple valid syntactic interpretations.

(B) Using prepositional phrase attachment as an example, explain what structural ambiguity is and why it poses challenges for parsing.

**Question 8: Dependency Grammar and Neural Parsing (Lecture 7)**
(A) Describe dependency grammar and explain how syntactic structure is represented as a dependency tree.

(B) Explain how deep learning–based parsing differs from rule-based grammar parsing, focusing on the role of annotated treebanks.

