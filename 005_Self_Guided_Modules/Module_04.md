Introduction to Module 4
Module Introduction
Main Focus: This module advances beyond basic neural sequence models to examine modern architectural choices for representation learning in NLP. It focuses on convolutional and gated neural architectures for text, highlighting how design decisions such as depth, channel structure, normalization, and gating affect feature extraction, optimization stability, and computational efficiency. The module explores convolutional neural networks (CNNs) as powerful, parallelizable alternatives to recurrent models, emphasizing their role as learned feature extractors for classification and sequence modeling. Students will analyze how architectural components such as multi- channel inputs, vertical gating, residual connections, and very deep convolutional stacks enable scalable and expressive neural models for language.

Secondary Focus: Building on architectural foundations, the module introduces modeling below the word level through subword and character-based representations. It examines why word-level modeling is insufficient for open-vocabulary and morphologically rich languages, and how subword tokenization and character-level neural models address out-of-vocabulary issues and improve generalization. Students will study major subword approaches including Byte Pair Encoding (BPE), WordPiece, and Unigram Language Models, as well as purely character-level CNN and hybrid architectures. The module connects these representation choices to modern NLP systems, including neural machine translation and large pretrained language models.

Module Objectives
By the end of this module, students will be able to:

Explain why deep convolutional architectures are effective for NLP tasks
Describe multi-channel CNNs and their role in feature representation
Compare CNNs, RNNs, and gated architectures for text modeling
Explain vertical gating, residual connections, and their impact on training deep networks
Describe the purpose and effects of batch normalization in deep models
Explain the role of 1×1 convolutions in dimensionality reduction and model efficiency
Analyze very deep CNN architectures for text classification
Explain the limitations of word-level representations in NLP
Describe character-level and subword-based modeling approaches
Compare BPE, WordPiece, and Unigram subword tokenization methods
Explain how subword modeling supports multilingual and low-resource NLP
Table of Contents of the Module
Component

Supporting Material

Assessment

Lecture 11: Advanced CNN Architectures and Gated Models

Lecture slides Download Lecture slides; in-class discussion

Homework 4

Lecture 12: Subword and Character-Level Modeling

Lecture slides Download Lecture slides; examples and case studies

Homework 4

Lecture 13: Deep Sequence Alternatives and Efficiency

Lecture slides Download Lecture slides; architectural comparisons

Homework 4; Self-guided Lab

Course Materials
Review the lecture slides and Canvas pages for each topic
Watch the recorded lectures for architectural intuition and design trade-offs
Activities and Assessments
Practice Activities
Review architectural diagrams and compare modeling choices across CNNs, RNNs, and subword-based systems. Experiment with character- and subword-level representations using provided examples or the self-guided lab.

Graded Assessments
Complete Homework 4, covering all lectures in this module
Apply module concepts in subsequent project milestones
