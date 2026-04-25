Introduction to Module 3
Module Introduction
Main Focus: This module develops the formal foundations of language modeling as a core problem in Natural Language Processing. It begins by defining language modeling as the task of assigning probabilities to word sequences and predicting the next word given prior context. The module first introduces probabilistic language models, focusing on n-gram models, their underlying independence assumptions, and their practical construction from large corpora. It examines why n-gram models work, where they fail, and how sparsity, storage, and generalization fundamentally limit count-based approaches. These limitations motivate the transition from purely statistical models to neural language models that learn continuous representations and generalize beyond observed word sequences.

Secondary Focus: Building on probabilistic modeling, the module introduces neural approaches to sequence modeling. It begins with fixed-window neural language models and then develops recurrent language models (RNNs) that explicitly model sequential dependencies over time. The module examines the architectural differences between feed-forward networks and RNNs, details training via backpropagation through time, and analyzes the vanishing and exploding gradient problems that limit long-range dependency learning. It then introduces gated architectures, including LSTMs and GRUs, as principled solutions for preserving long-term information. Finally, the module presents sequence-to-sequence models and encoder–decoder architectures with attention, framing neural machine translation as conditional language modeling and highlighting challenges in scalability, interpretability, and evaluation.

Module Objectives
By the end of this module, students will be able to:

Formally define language modeling as probabilistic next-word prediction
Explain the n-gram independence assumption and how n-gram probabilities are estimated
Analyze sparsity and storage problems in n-gram language models
Explain smoothing, backoff, and interpolation as partial solutions to sparsity
Describe fixed-window neural language models and their limitations
Explain how recurrent neural networks model sequential dependencies
Describe backpropagation through time and its computational implications
Explain vanishing and exploding gradients in recurrent models
Explain how LSTMs and GRUs mitigate long-range dependency problems
Describe bidirectional and multi-layer RNN architectures
Explain encoder–decoder and sequence-to-sequence models
Explain attention mechanisms and why they overcome fixed-length bottlenecks
Describe neural machine translation as conditional language modeling
Compare automatic and human-based evaluation metrics for language models
Table of Contents of the Module
Component

Supporting Material

Assessment

Lecture 8: Probabilistic Language Modeling

Lecture slides Download Lecture slides; in-class discussion

Homework 3 (covers Lectures 8–10)

Lecture 9: Recurrent Language Models

Lecture slides Download Lecture slides; in-class discussion

Homework 3

Lecture 10: Sequence-to-Sequence Models

Lecture slides Download Lecture slides; in-class discussion

Homework 3; Module 3 Self-Guided Lab

Course Materials
Reading Review lecture slides and Canvas pages for each topic.
Video Watch recorded lectures for detailed derivations and examples.
Activities / Assessments
Practice Activities
Review lecture materials carefully and work through probability examples, language model generation examples, and architecture diagrams. Students are encouraged to complete the Module 3 Self-Guided Lab to experiment with n-gram models, RNNs, and sequence generation.

Graded Assessments
Quiz Complete Homework 3, covering Lectures 8–10.
