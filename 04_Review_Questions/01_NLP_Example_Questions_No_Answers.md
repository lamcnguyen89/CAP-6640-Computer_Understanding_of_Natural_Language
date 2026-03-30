# NLP Example Questions

## Table of Contents

1. [Open-Ended Questions](#open-ended-questions)
2. [True/False Review](#truefalse-review)
3. [Multiple Choice Questions](#multiple-choice-questions)

---

## Open-Ended Questions

### Introduction to NLP

#### Question 1: Paradigm Shifts in NLP

- **(A)** Describe the major paradigm shifts in the historical evolution of NLP, from rule-based systems to statistical models and finally to neural and transformer-based approaches.
- **(B)** Analyze why each transition occurred, focusing on the limitations of the previous paradigm and the roles of computational power and data availability.

#### Question 2: Ambiguity and the Hardness of NLP

- **(A)** Explain why ambiguity is a fundamental challenge in natural language processing and how syntactic ambiguity can grow exponentially with sentence complexity.
- **(B)** Compare natural languages with formal computer languages in terms of ambiguity, determinism, and interpretability, and discuss the implications for computational modeling.

#### Question 3: Task Taxonomy in NLP

- **(A)** Define and distinguish between syntactic, semantic, and pragmatic NLP tasks.
- **(B)** Analyze how these task categories interact in a complete language understanding pipeline, and explain why syntactic processing alone is insufficient for full interpretation.

---

### Word Embeddings and Distributional Semantics

#### Question 1: Limitations of Discrete Representations and the Distributional Hypothesis

- **(A)** Formally explain why one-hot word representations are orthogonal and why this property prevents the encoding of semantic similarity.
- **(B)** Describe how the distributional hypothesis addresses these limitations and analyze how dense word embeddings induce a geometric notion of graded similarity.

#### Question 2: Word2Vec Objective and Optimization

- **(A)** Derive the predictive objective of the Word2Vec model, including the softmax formulation of $P(o \mid c)$ and its relationship to cross-entropy loss.
- **(B)** Explain why stochastic gradient descent is necessary for scalability and analyze how gradient-based optimization leads to emergent semantic structure in the embedding space.

#### Question 3: Skip-Gram vs CBOW and Training Dynamics

- **(A)** Compare the Skip-Gram and CBOW architectures in terms of prediction direction, training behavior, and sensitivity to rare versus frequent words.
- **(B)** Analyze how the end-to-end training pipeline, including vocabulary construction, context window extraction, embedding lookup, and parameter updates, enables word vectors to capture distributional meaning.

---

### Neural Training and Optimization

#### Question 1: Optimization and Negative Sampling

- **(A)** Explain why the full softmax objective in Skip-Gram is computationally expensive and how stochastic gradient descent enables scalable training.
- **(B)** Derive the intuition behind skip-gram with negative sampling and analyze how replacing multiclass prediction with binary classification preserves semantic learning while improving efficiency.

#### Question 2: Count-Based vs Predictive Embeddings

- **(A)** Compare count-based representations using co-occurrence matrices and dimensionality reduction (e.g., SVD) with direct prediction methods such as Word2Vec.
- **(B)** Analyze the trade-offs between these approaches in terms of computational efficiency, representational expressiveness, and downstream task performance.

#### Question 3: Evaluation and Word Sense Ambiguity

- **(A)** Distinguish between intrinsic and extrinsic evaluation of word embeddings and discuss their respective strengths and limitations.
- **(B)** Explain why static embeddings struggle with word sense ambiguity and analyze how contextual or multi-representation approaches address this limitation.

---

### Window-Based Models and Neural Classification

#### Question 1: Window-Based Modeling and Margin Objectives

- **(A)** Explain how a window-based formulation reduces NLP tasks such as Named Entity Recognition to local classification problems and describe the modeling assumptions involved.
- **(B)** Derive the max-margin hinge loss used to separate correct and corrupted windows, and analyze how margin-based learning differs from probabilistic objectives.

#### Question 2: Neural Scoring and Backpropagation

- **(A)** Describe how a neural scoring function maps concatenated word embeddings from a context window to a scalar compatibility score.
- **(B)** Explain how backpropagation computes parameter updates in this multi-layer network and analyze how gradients flow through the computational graph during training.

#### Question 3: Optimization Dynamics and Embedding Fine-Tuning

- **(A)** Explain how stochastic gradient descent enables scalable optimization in neural NLP models trained over large corpora.
- **(B)** Analyze the trade-offs involved in fine-tuning pretrained word embeddings during task-specific training, particularly with respect to overfitting and semantic drift.

---

### Named Entity Recognition

#### Question 1: Window-Based NER and Margin Optimization

- **(A)** Explain how Named Entity Recognition for location entities can be formulated as a binary classification problem using fixed-size context windows.
- **(B)** Derive the max-margin loss function $J = \max(0, 1 - S + S_c)$ and analyze how pairing true and corrupted windows drives discriminative learning.

#### Question 2: Neural Scoring and Gradient Flow

- **(A)** Describe how a feed-forward neural network computes an unnormalized compatibility score for a context window.
- **(B)** Explain how backpropagation operates over the computational graph to update parameters, including the role of upstream and local gradients.

#### Question 3: Embedding Fine-Tuning and Optimization Trade-offs

- **(A)** Explain the risks associated with retraining pre-trained word embeddings during task-specific training.
- **(B)** Analyze how dataset size influences the decision to fine-tune embeddings and discuss the trade-off between task specialization and global semantic consistency.

---

### Syntactic Parsing

#### Question 1: Phrase Structure and Context-Free Grammars

- **(A)** Explain how phrase structure encodes hierarchical organization in sentences and describe how context-free grammars (CFGs) formalize this structure using production rules.
- **(B)** Analyze how recursion in CFGs enables nested constructions and discuss limitations of CFG-based representations in handling structural ambiguity.

#### Question 2: Structural Ambiguity and Parsing Decisions

- **(A)** Describe at least two sources of structural ambiguity (e.g., prepositional phrase attachment, coordination scope) and explain why syntactic parsing must resolve them for accurate interpretation.
- **(B)** Compare how phrase structure grammar and dependency grammar represent ambiguous constructions and discuss implications for computational parsing.

#### Question 3: Dependency Parsing and Neural Models

- **(A)** Explain how dependency grammar represents syntactic structure as a tree of word-to-word relations and contrast it with constituency-based representations.
- **(B)** Describe how modern deep learning–based parsers use annotated treebanks and neural architectures to predict syntactic structure, and analyze the advantages of data-driven parsing over rule-based grammar systems.

---

### Language Modeling Foundations

#### Question 1: Probabilistic Foundations of Language Modeling

- **(A)** Formally define a language model as a conditional probability distribution and explain how it assigns probabilities to entire word sequences.
- **(B)** Analyze why language modeling is foundational for NLP applications and how probabilistic modeling supports ambiguity resolution and sequence comparison.

#### Question 2: n-Gram Models and Their Limitations

- **(A)** Explain the Markov assumption underlying n-gram language models and describe how n-gram probabilities are estimated from corpus counts.
- **(B)** Analyze the sparsity and storage problems in high-order n-gram models, and discuss how smoothing, backoff, and interpolation partially address these issues.

#### Question 3: From Count-Based to Neural Language Models

- **(A)** Explain why n-gram models struggle to generalize beyond observed word sequences and how this limitation affects text generation quality.
- **(B)** Describe how fixed-window neural language models address sparsity and storage constraints, and analyze how continuous representations enable generalization beyond exact counts.

---

### Recurrent Neural Networks

#### Question 1: Fixed-Window vs Recurrent Language Models

- **(A)** Explain the limitations of fixed-window language models in capturing long-range dependencies.
- **(B)** Describe how recurrent neural networks address these limitations through hidden-state recurrence and analyze how this changes the conditional probability formulation of language modeling.

#### Question 2: RNN Architecture and Sequence Probability Modeling

- **(A)** Describe how an RNN updates its hidden state at each timestep and how this state summarizes prior context.
- **(B)** Explain how an RNN language model computes conditional word probabilities and how this enables autoregressive text generation.

#### Question 3: Training and Backpropagation Through Time

- **(A)** Explain why training RNN language models requires Backpropagation Through Time (BPTT) and describe how the network is conceptually unrolled.
- **(B)** Analyze why gradient propagation across many timesteps creates optimization challenges and discuss the computational implications of parameter reuse across time.

---

### Sequence-to-Sequence Models

#### Question 1: Conditional Language Modeling and Encoder–Decoder Architecture

- **(A)** Formally define sequence-to-sequence learning as conditional language modeling and explain how the output sequence probability is factorized.
- **(B)** Describe the encoder–decoder architecture and analyze why compressing the entire input sequence into a single fixed-length context vector creates an information bottleneck.

#### Question 2: Architectural Extensions in Seq2Seq Models

- **(A)** Explain the motivation for bidirectional RNNs and stacked (multi-layer) RNNs in encoder–decoder models.
- **(B)** Analyze how attention mechanisms address limitations of fixed-length representations and improve decoding for long input sequences.

#### Question 3: Neural Machine Translation and Evaluation

- **(A)** Explain how neural machine translation is formulated as a sequence-to-sequence task and describe the role of attention in improving translation quality.
- **(B)** Compare automatic evaluation metrics such as perplexity and BLEU with human evaluation, and analyze challenges in assessing Seq2Seq model performance.

---

### Convolutional Neural Networks for NLP

#### Question 1: Structural Limitations of RNNs and Motivation for CNNs

- **(A)** Explain the structural limitations of RNNs in modeling phrase-level meaning, including prefix dependency, recency bias, and final-step prediction bottlenecks.
- **(B)** Analyze why these limitations motivate the use of convolutional architectures for certain NLP tasks.

#### Question 2: Convolution and Pooling in Text CNNs

- **(A)** Formally describe how 1D convolution operates over word embeddings to produce feature maps, including the roles of window size, stride, padding, and channels.
- **(B)** Compare max pooling, average pooling, and k-max pooling, and analyze how each affects sentence-level representation.

#### Question 3: CNNs for Sentence Classification and Architectural Trade-offs

- **(A)** Describe the standard CNN architecture for sentence classification, including convolutional filters of varying widths, pooling, fully connected layers, and output activation functions.
- **(B)** Compare CNNs with RNNs and Transformers in terms of phrase modeling, computational efficiency, and ability to capture long-range dependencies.

---

### Advanced CNN Architectures

#### Question 1: Model Comparisons and Multi-Channel CNNs

- **(A)** Compare Bag-of-Vectors models, Window Models, CNNs, and RNNs in terms of structural assumptions, computational properties, and ability to model order and context.
- **(B)** Explain how multi-channel CNNs enhance feature representation and analyze how parallel embedding channels contribute complementary information.

#### Question 2: Vertical Gating and Optimization in Deep Architectures

- **(A)** Explain the concept of vertical gating and describe how residual connections and highway networks stabilize deep neural architectures.
- **(B)** Analyze the role of Batch Normalization in mitigating internal covariate shift and enabling efficient training of very deep networks.

#### Question 3: Very Deep CNNs, QRNNs, and Architectural Evolution

- **(A)** Describe the design of Very Deep CNNs (VD-CNN) for text processing and explain how depth substitutes for recurrence in hierarchical feature construction.
- **(B)** Explain the motivation behind Quasi-Recurrent Neural Networks (QRNNs) and analyze their trade-offs compared to traditional RNNs and attention-based models.

---

### Subword and Character-Level Modeling

#### Question 1: Motivation and Linguistic Foundations of Subword Modeling

- **(A)** Explain why treating words as atomic units creates limitations in open-vocabulary and morphologically rich languages.
- **(B)** Analyze how character-level and subword-level modeling address out-of-vocabulary issues, morphological variation, and multilingual generalization.

#### Question 2: Subword Tokenization Algorithms and Their Trade-Offs

- **(A)** Compare Byte Pair Encoding (BPE), WordPiece, and the Unigram Language Model in terms of their optimization objectives and segmentation strategies.
- **(B)** Analyze the computational trade-offs between vocabulary size and sequence length in Transformer models, including implications for attention complexity and memory usage.

#### Question 3: Character-Level Modeling, Tokenizer Drift, and Scaling

- **(A)** Describe how pure character-level architectures construct representations and discuss their advantages and computational costs.
- **(B)** Explain the concept of tokenizer drift and evaluate how tokenization choices influence robustness, domain transfer, and scaling in modern large language models.

---

## True/False Review

### Language Modeling (1-10)

1. Language modeling assigns probabilities to entire word sequences.
2. In an n-gram model, the probability of a word depends on all previous words in the sequence.
3. Sparsity in n-gram models increases exponentially as n grows.
4. Backoff methods address unseen n-grams by reverting to lower-order models.
5. Fixed-window language models can condition on arbitrarily long context.
6. RNNs maintain a hidden state that summarizes prior context.
7. In RNN language models, parameters are reused at each timestep.
8. Backpropagation Through Time conceptually unrolls the RNN across time.
9. RNNs are fully parallelizable across timesteps during training.
10. Sequential processing in RNNs can cause recency bias.

### Seq2Seq and Attention (11-20)

11. Seq2Seq models factorize conditional probabilities autoregressively.
12. Early encoder–decoder models compress input into a single fixed-length vector.
13. Bidirectional RNNs process sequences in only one direction.
14. Attention allows the decoder to access all encoder states dynamically.
15. BLEU measures recall of semantic similarity using embeddings.
16. Perplexity measures predictive likelihood of a sequence.
17. Neural Machine Translation is formulated as conditional language modeling.
18. Seq2Seq models always produce fixed-length outputs.
19. Stacked RNNs increase representational depth.
20. Attention reduces effective dependency path length.

### CNNs for NLP (21-42)

21. CNNs process tokens sequentially like RNNs.
22. CNN filters detect local n-gram patterns.
23. Max pooling selects the strongest activation across positions.
24. CNNs inherently model long-range dependencies without stacking.
25. CNNs are highly parallelizable across positions.
26. Recency bias is a known limitation of RNNs.
27. Prefix dependency refers to reliance on earlier tokens.
28. Pooling produces fixed-length representations regardless of input size.
29. 1D convolution slides filters across embedding matrices.
30. Stride controls how far the filter moves per step.
31. Padding ensures equal treatment of boundary tokens.
32. k-max pooling preserves multiple top activations.
33. CNNs require recurrence to detect phrase-level patterns.
34. Multi-channel CNNs combine multiple embedding representations.
35. Residual connections help mitigate vanishing gradients.
36. Highway networks introduce gating across depth.
37. Batch Normalization normalizes activations across batches.
38. BatchNorm introduces learnable scaling and shifting parameters.
39. Very Deep CNNs operate at the character level.
40. QRNNs precompute gates using convolution.
41. QRNNs are fully sequential like LSTMs.
42. Attention-based models eliminate recurrence entirely.

### Word Embeddings (43-60)

43. Word embeddings are learned by optimizing predictive objectives.
44. One-hot vectors encode graded semantic similarity.
45. Orthogonality in one-hot vectors prevents similarity modeling.
46. Distributional semantics defines meaning by context usage.
47. Word2Vec maximizes likelihood of word-context pairs.
48. Skip-Gram predicts context words from center words.
49. CBOW predicts center words from context words.
50. Negative sampling replaces full softmax with binary classification.
51. SGD computes exact gradients over entire corpora.
52. Margin-based loss enforces relative separation of scores.
53. Corrupted windows serve as negative examples in margin learning.
54. Backpropagation computes gradients via the chain rule.
55. Fine-tuning embeddings always improves performance.
56. Static embeddings assign a single vector per word.
57. Contextual embeddings generate context-dependent vectors.
58. Intrinsic evaluation measures downstream task performance.
59. Extrinsic evaluation measures performance on real NLP tasks.
60. Analogy tasks test linear relationships in embedding space.

### Subword and Character Modeling (61-100)

61. Subword modeling reduces vocabulary size.
62. Character-level models eliminate OOV problems.
63. BPE merges frequent adjacent pairs greedily.
64. WordPiece maximizes corpus likelihood during merges.
65. The Unigram LM supports probabilistic segmentation.
66. Subword units always correspond to true linguistic morphemes.
67. Tokenizer drift occurs when domain changes affect segmentation.
68. Self-attention complexity scales quadratically with sequence length.
69. Larger vocabularies reduce embedding matrix size.
70. Byte-level tokenization eliminates OOV issues entirely.
71. Character-level models increase sequence length.
72. Morphologically rich languages benefit from subword modeling.
73. Word embeddings are dense low-dimensional vectors.
74. Count-based methods rely on co-occurrence matrices.
75. SVD reduces dimensionality in count-based models.
76. Direct prediction models optimize predictive objectives.
77. Bag-of-Vectors models capture word order explicitly.
78. Window models capture only local context.
79. CNNs can serve as feature extractors for classifiers.
80. RNN training is slower due to sequential dependency.
81. Residual connections shorten effective gradient path length.
82. Very Deep CNNs rely on character embeddings.
83. QRNNs replace recurrence entirely with self-attention.
84. Fixed-window models discard information outside the window.
85. Neural LMs generalize via distributed representations.
86. n-gram models generalize based on similarity between contexts.
87. Smoothing prevents zero probabilities for unseen n-grams.
88. Transformer models rely heavily on residual connections.
89. Subword tokenization affects compute and memory trade-offs.
90. Convolutional filters share weights across positions.
91. Pooling preserves exact token positions.
92. RNN hidden states compress prior context repeatedly.
93. Bidirectional RNNs access future context during encoding.
94. Neural parsers learn structure from annotated treebanks.
95. Dependency grammar models syntax as word-to-word relations.
96. CFG rules apply independently of surrounding context.
97. Structural ambiguity arises from attachment decisions.
98. Language models support speech recognition applications.
99. Attention mechanisms dynamically weight encoder states.
100.  Below-word modeling improves robustness to spelling variation.

---

## Multiple Choice Questions

### Language Modeling (1-10)

1. A language model assigns probabilities to:
   - **A)** Individual characters only
   - **B)** Entire word sequences
   - **C)** Only bigrams
   - **D)** Only unseen words

2. In an n-gram model, the Markov assumption states that:
   - **A)** Words are independent
   - **B)** The next word depends only on the previous n−1 words
   - **C)** The entire sentence is needed
   - **D)** Syntax is ignored

3. Sparsity in n-gram models increases because:
   - **A)** Vocabulary shrinks
   - **B)** Data becomes cleaner
   - **C)** Possible combinations grow exponentially
   - **D)** Softmax is expensive

4. Backoff methods address unseen n-grams by:
   - **A)** Ignoring them
   - **B)** Using higher-order models
   - **C)** Falling back to lower-order models
   - **D)** Random sampling

5. Fixed-window language models discard:
   - **A)** Future tokens
   - **B)** Tokens outside the window
   - **C)** Embeddings
   - **D)** Vocabulary

6. Neural language models generalize using:
   - **A)** Exact counts
   - **B)** Hard-coded rules
   - **C)** Distributed representations
   - **D)** Treebanks

7. Perplexity measures:
   - **A)** Syntactic correctness
   - **B)** Prediction uncertainty
   - **C)** BLEU similarity
   - **D)** Parsing accuracy

8. Smoothing prevents:
   - **A)** Large vocabularies
   - **B)** Zero probabilities
   - **C)** Long sequences
   - **D)** Recurrence

9. Increasing vocabulary size increases:
   - **A)** Sequence length
   - **B)** Embedding matrix size
   - **C)** Attention speed
   - **D)** Sparsity reduction

10. n-gram models struggle with:
    - **A)** Local grammar
    - **B)** Exact repetition
    - **C)** Long-range dependencies
    - **D)** Counting frequencies

---

### RNNs (11-20)

11. The RNN hidden state represents:
    - **A)** Only current input
    - **B)** Entire vocabulary
    - **C)** Compressed prior context
    - **D)** Word embeddings

12. RNNs differ from feedforward networks because they:
    - **A)** Use convolution
    - **B)** Share parameters across time
    - **C)** Remove recurrence
    - **D)** Ignore sequence order

13. Backpropagation Through Time requires:
    - **A)** Removing recurrence
    - **B)** Unrolling the network across time
    - **C)** Attention mechanisms
    - **D)** Pooling layers

14. RNN training is slower because:
    - **A)** No embeddings
    - **B)** Sequential computation
    - **C)** Too few parameters
    - **D)** Overfitting

15. Recency bias arises because:
    - **A)** First tokens dominate
    - **B)** Final hidden state emphasizes recent tokens
    - **C)** Attention is used
    - **D)** CNN pooling

16. RNN generation is:
    - **A)** Parallel
    - **B)** Autoregressive
    - **C)** Bidirectional
    - **D)** Non-sequential

17. Parameters in RNNs are:
    - **A)** Unique per timestep
    - **B)** Shared across timesteps
    - **C)** Randomly sampled
    - **D)** Not trainable

18. The prefix dependency issue refers to:
    - **A)** Right-to-left modeling
    - **B)** Dependence only on suffix
    - **C)** Sequential left-to-right compression
    - **D)** Global attention

19. RNNs struggle with:
    - **A)** Short sequences
    - **B)** Convolution
    - **C)** Very long dependencies
    - **D)** Word embeddings

20. Hidden state compression can cause:
    - **A)** Increased parallelization
    - **B)** Representational dilution
    - **C)** Better pooling
    - **D)** Deterministic outputs

---

### Seq2Seq & Attention (21-30)

21. Seq2Seq models learn:
    - **A)** Fixed outputs
    - **B)** Conditional generation
    - **C)** Static classification
    - **D)** Only POS tagging

22. The encoder outputs:
    - **A)** Softmax probabilities
    - **B)** A context representation
    - **C)** BLEU score
    - **D)** Random vector

23. Early Seq2Seq models suffered from:
    - **A)** Too many filters
    - **B)** Fixed-length bottleneck
    - **C)** No vocabulary
    - **D)** Overfitting embeddings

24. Attention allows the decoder to:
    - **A)** Ignore input
    - **B)** Access all encoder states
    - **C)** Remove recurrence
    - **D)** Shrink vocabulary

25. Bidirectional RNNs process:
    - **A)** Only forward
    - **B)** Only backward
    - **C)** Both directions
    - **D)** Random order

26. BLEU primarily measures:
    - **A)** Recall only
    - **B)** n-gram precision
    - **C)** Syntax trees
    - **D)** Perplexity

27. Perplexity measures:
    - **A)** Translation overlap
    - **B)** Likelihood
    - **C)** Character error
    - **D)** Recall

28. Stacked RNNs:
    - **A)** Remove depth
    - **B)** Increase abstraction
    - **C)** Ignore syntax
    - **D)** Remove recurrence

29. Attention reduces:
    - **A)** Vocabulary size
    - **B)** Effective path length
    - **C)** Embedding dimension
    - **D)** Training data

30. Neural Machine Translation is an example of:
    - **A)** Classification
    - **B)** Clustering
    - **C)** Seq2Seq modeling
    - **D)** Parsing

---

### CNNs for Text (31-45)

31. CNNs detect:
    - **A)** Global syntax
    - **B)** Local n-gram patterns
    - **C)** Only suffixes
    - **D)** Tree structures

32. Convolution is:
    - **A)** Sequential
    - **B)** Parallel across positions
    - **C)** Recursive
    - **D)** Symbolic

33. Max pooling selects:
    - **A)** Average activation
    - **B)** Minimum value
    - **C)** Strongest activation
    - **D)** Random activation

34. Stride controls:
    - **A)** Filter width
    - **B)** Filter movement step
    - **C)** Vocabulary size
    - **D)** Embedding size

35. Padding ensures:
    - **A)** Zero vocabulary
    - **B)** Boundary coverage
    - **C)** No pooling
    - **D)** Sequential order

36. CNNs are highly:
    - **A)** Sequential
    - **B)** Parallelizable
    - **C)** Deterministic
    - **D)** Symbolic

37. CNN filters share weights:
    - **A)** Across positions
    - **B)** Across vocabularies
    - **C)** Across tasks
    - **D)** Across models

38. Pooling produces:
    - **A)** Variable-length outputs
    - **B)** Fixed-length representations
    - **C)** Recurrence
    - **D)** Attention

39. CNNs primarily model:
    - **A)** Long-distance recursion
    - **B)** Phrase-level features
    - **C)** Entire sequence memory
    - **D)** Dependency trees

40. CNNs struggle with:
    - **A)** Local patterns
    - **B)** Long-range dependencies
    - **C)** Short sentences
    - **D)** Parallelism

41. Multi-channel CNNs use:
    - **A)** Single embedding type
    - **B)** Multiple embedding types
    - **C)** Only characters
    - **D)** Only bytes

42. 1×1 convolution performs:
    - **A)** Sequence pooling
    - **B)** Channel transformation
    - **C)** Recurrence
    - **D)** Attention

43. Residual connections:
    - **A)** Increase vanishing gradients
    - **B)** Shorten gradient paths
    - **C)** Remove depth
    - **D)** Remove pooling

44. Batch Normalization normalizes:
    - **A)** Vocabulary
    - **B)** Activations
    - **C)** Tokens
    - **D)** Labels

45. QRNNs combine:
    - **A)** Attention and parsing
    - **B)** Convolution and gating
    - **C)** CNN and Transformer only
    - **D)** Pure recurrence

---

### Word Embeddings & Word2Vec (46-60)

46. One-hot vectors are:
    - **A)** Dense
    - **B)** Orthogonal
    - **C)** Contextual
    - **D)** Probabilistic

47. Distributional semantics defines meaning by:
    - **A)** Dictionaries
    - **B)** Context usage
    - **C)** Rules
    - **D)** Syntax

48. Word2Vec optimizes:
    - **A)** Parsing trees
    - **B)** Predictive likelihood
    - **C)** BLEU score
    - **D)** SVD directly

49. Skip-Gram predicts:
    - **A)** Center from context
    - **B)** Context from center
    - **C)** Entire sentence
    - **D)** POS tags

50. CBOW predicts:
    - **A)** Context words
    - **B)** Center word
    - **C)** Syntactic structure
    - **D)** Dependencies

51. Negative sampling replaces:
    - **A)** SGD
    - **B)** Softmax over full vocabulary
    - **C)** Convolution
    - **D)** Parsing

52. SVD reduces:
    - **A)** Vocabulary
    - **B)** Dimensionality
    - **C)** Token count
    - **D)** Attention cost

53. Count-based models rely on:
    - **A)** Context windows
    - **B)** Co-occurrence matrices
    - **C)** Attention
    - **D)** Recurrence

54. Intrinsic evaluation tests:
    - **A)** Downstream performance
    - **B)** Similarity/analogy tasks
    - **C)** Parsing accuracy
    - **D)** Speech recognition

55. Extrinsic evaluation measures:
    - **A)** Embedding similarity
    - **B)** Real task performance
    - **C)** Window size
    - **D)** Softmax efficiency

56. Static embeddings assign:
    - **A)** Multiple vectors per word
    - **B)** One vector per word
    - **C)** Character vectors
    - **D)** Byte vectors

57. Contextual embeddings produce:
    - **A)** Fixed vectors
    - **B)** Context-dependent vectors
    - **C)** One-hot vectors
    - **D)** Count tables

58. Margin loss enforces:
    - **A)** Absolute probability
    - **B)** Relative separation
    - **C)** Softmax normalization
    - **D)** Perplexity reduction

59. Corrupted windows serve as:
    - **A)** Positive examples
    - **B)** Negative examples
    - **C)** Parsing rules
    - **D)** Embeddings

60. Fine-tuning embeddings risks:
    - **A)** Increased sparsity
    - **B)** Semantic drift
    - **C)** Fewer parameters
    - **D)** Tokenization errors

---

### Subword & Character Modeling (61-100)

61. Subword modeling reduces:
    - **A)** Expressiveness
    - **B)** Vocabulary size
    - **C)** Context
    - **D)** Parallelism

62. Character-level models eliminate:
    - **A)** Recurrence
    - **B)** OOV words
    - **C)** Attention
    - **D)** Softmax

63. BPE merges:
    - **A)** Rare pairs
    - **B)** Frequent pairs
    - **C)** Entire sentences
    - **D)** Random tokens

64. WordPiece maximizes:
    - **A)** Frequency only
    - **B)** Likelihood
    - **C)** BLEU
    - **D)** SVD

65. Unigram LM uses:
    - **A)** Greedy merges
    - **B)** EM-style probabilistic pruning
    - **C)** Deterministic splits
    - **D)** One-hot encoding

66. Subwords are:
    - **A)** Always morphemes
    - **B)** Statistical units
    - **C)** Syntactic trees
    - **D)** Tokens with fixed meaning

67. Self-attention complexity is:
    - **A)** Linear
    - **B)** Logarithmic
    - **C)** Quadratic in sequence length
    - **D)** Constant

68. Byte-level tokenization ensures:
    - **A)** Smaller sequences
    - **B)** OOV elimination
    - **C)** Fewer tokens
    - **D)** Fixed vocabulary

69. Tokenizer drift occurs when:
    - **A)** Training and deployment domains differ
    - **B)** Embeddings change
    - **C)** RNN fails
    - **D)** CNN pooling shifts

70. Morphologically rich languages benefit from:
    - **A)** Larger vocabularies
    - **B)** Subword modeling
    - **C)** Bag-of-words
    - **D)** Removing embeddings

71. Character-level CNNs operate:
    - **A)** On words only
    - **B)** On characters
    - **C)** On trees
    - **D)** On POS tags

72. Increasing vocabulary decreases:
    - **A)** Memory
    - **B)** Embedding matrix size
    - **C)** Sequence length
    - **D)** Compute

73. Smaller vocabulary increases:
    - **A)** Attention cost
    - **B)** Embedding memory
    - **C)** Softmax speed
    - **D)** BatchNorm

74. Subword modeling helps with:
    - **A)** Syntax trees
    - **B)** Transliteration
    - **C)** Removing tokens
    - **D)** Shrinking corpora

75. Transformer scaling depends on:
    - **A)** Token count
    - **B)** Grammar rules
    - **C)** POS tagging
    - **D)** SVD

76. Writing systems influence:
    - **A)** Attention heads
    - **B)** Segmentation strategies
    - **C)** Batch size
    - **D)** Loss functions

77. Agglutinative languages produce:
    - **A)** Few word forms
    - **B)** Many affixed forms
    - **C)** No morphemes
    - **D)** Only prefixes

78. Abugida scripts encode:
    - **A)** Full words
    - **B)** Consonant-vowel units
    - **C)** Only vowels
    - **D)** Logograms

79. Logographic systems represent:
    - **A)** Phonemes
    - **B)** Morphemes or words
    - **C)** Letters
    - **D)** Bigrams

80. Byte-level models increase:
    - **A)** Parallelism
    - **B)** Sequence length
    - **C)** Vocabulary
    - **D)** Recurrence

81. Subword modeling improves:
    - **A)** Memory only
    - **B)** Robustness to spelling variation
    - **C)** Grammar rules
    - **D)** Recursion

82. Unigram LM supports:
    - **A)** Multiple segmentations
    - **B)** One deterministic segmentation
    - **C)** Only character splits
    - **D)** No pruning

83. BPE is:
    - **A)** Probabilistic
    - **B)** Greedy frequency-based
    - **C)** EM-based
    - **D)** Contextual

84. Character models are useful for:
    - **A)** Clean formal text only
    - **B)** Noisy user text
    - **C)** Removing embeddings
    - **D)** Reducing depth

85. Tokenization affects:
    - **A)** Scaling cost
    - **B)** Syntax trees only
    - **C)** BatchNorm
    - **D)** Recurrence only

86. Transformers benefit from:
    - **A)** Long sequences
    - **B)** Efficient compression
    - **C)** Larger stride
    - **D)** More recurrence

87. Subword units balance:
    - **A)** Vocabulary size and generalization
    - **B)** Grammar and syntax
    - **C)** Parsing and tagging
    - **D)** Convolution and pooling

88. Byte-level models operate on:
    - **A)** Unicode bytes
    - **B)** Morphemes
    - **C)** Words
    - **D)** Syllables

89. OOV stands for:
    - **A)** Out of Vocabulary
    - **B)** Order of Value
    - **C)** Overlapping Vector
    - **D)** Output Variance

90. Character-level modeling increases:
    - **A)** Softmax speed
    - **B)** Token count
    - **C)** Vocabulary size
    - **D)** Parallelism

91. Tokenization impacts:
    - **A)** Memory and compute
    - **B)** Only embeddings
    - **C)** Only parsing
    - **D)** Only CNNs

92. Subword tokenization supports:
    - **A)** Multilingual modeling
    - **B)** Only English
    - **C)** Only character scripts
    - **D)** Only small corpora

93. Large vocabularies reduce:
    - **A)** Embedding memory
    - **B)** Sequence length
    - **C)** Parameter count
    - **D)** Storage

94. Attention cost scales with:
    - **A)** Vocabulary size
    - **B)** Sequence length squared
    - **C)** Embedding dimension
    - **D)** Batch size

95. Statistical segmentation may not align with:
    - **A)** Morphemes
    - **B)** Tokens
    - **C)** Embeddings
    - **D)** Softmax

96. SentencePiece implements:
    - **A)** WordPiece only
    - **B)** Unigram LM
    - **C)** BPE only
    - **D)** Softmax

97. Subword modeling improves:
    - **A)** Exact counting
    - **B)** Generalization across word forms
    - **C)** Recurrence depth
    - **D)** Treebanks

98. Open vocabulary means:
    - **A)** Fixed lexicon
    - **B)** New words continually appear
    - **C)** Only nouns
    - **D)** Only English

99. Character models are robust to:
    - **A)** Parsing errors
    - **B)** Typos
    - **C)** Attention collapse
    - **D)** Overfitting only

100.  The evolution of NLP architectures trends from:
      - **A)** Attention → CNN → RNN
      - **B)** Recurrence → Convolution → Attention
      - **C)** CNN → RNN → Parsing
      - **D)** Bag-of-words → Parsing → RNN
