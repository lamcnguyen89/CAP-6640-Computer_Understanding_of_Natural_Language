## **TRUE**/**FALSE** Review

### Language Modeling (1-10)

1. Language modeling assigns probabilities to entire word sequences. **TRUE** Language models (LMs) assign probabilities to entire word sequences, typically factorized as P(w₁, w₂, ..., wₙ) = ∏ P(wᵢ | w₁, ..., wᵢ₋₁). This allows them to evaluate the likelihood of any sequence and support applications like generation, ranking, and disambiguation.
2. In an n-gram model, the probability of a word depends on all previous words in the sequence. **FALSE** - In an n-gram model, the probability of a word depends only on the previous n-1 words (Markov assumption), not all previous words.
3. Sparsity in n-gram models increases exponentially as n grows. **TRUE** - Sparsity in n-gram models increases exponentially as n grows because the number of possible n-gram combinations grows exponentially with n.
4. Backoff methods address unseen n-grams by reverting to lower-order models. **TRUE** - Backoff methods address unseen n-grams by reverting to lower-order models (e.g., if a trigram is unseen, back off to bigram or unigram).

5. Fixed-window language models can condition on arbitrarily long context. **FALSE** - Fixed-window language models can only condition on a fixed-size context window, not arbitrarily long context.
6. RNNs maintain a hidden state that summarizes prior context. **TRUE** - RNNs maintain a hidden state that summarizes prior context at each timestep.
7. In RNN language models, parameters are reused at each timestep. **TRUE** - In RNN language models, parameters are reused at each timestep (weight sharing across time).
8. Backpropagation Through Time conceptually unrolls the RNN across time. **TRUE** - Backpropagation Through Time conceptually unrolls the RNN across time to compute gradients.
9. RNNs are fully parallelizable across timesteps during training. **FALSE** - RNNs are not fully parallelizable across timesteps during training due to sequential dependencies between hidden states.
10. Sequential processing in RNNs can cause recency bias. **TRUE** - Sequential processing in RNNs can cause recency bias, where recent tokens have more influence on the final hidden state than earlier tokens.

### Seq2Seq and Attention (11-20)

11. Seq2Seq models factorize conditional probabilities autoregressively. **TRUE** - Seq2Seq models factorize conditional probabilities autoregressively, computing P(y|x) = ∏ P(y*t | y*<t, x) where each output token is predicted conditioned on all previous outputs.
12. Early encoder–decoder models compress input into a single fixed-length vector. **TRUE** - Early encoder–decoder models compress the entire input sequence into a single fixed-length context vector (the final encoder hidden state), creating an information bottleneck.
13. Bidirectional RNNs process sequences in only one direction. **FALSE** - Bidirectional RNNs process sequences in both directions (forward and backward), not just one direction, allowing access to both past and future context.
14. Attention allows the decoder to access all encoder states dynamically. **TRUE** - Attention allows the decoder to dynamically access all encoder states at each decoding step, computing weighted combinations based on relevance rather than relying solely on a fixed context vector.
15. BLEU measures recall of semantic similarity using embeddings. **FALSE** - BLEU measures precision of n-gram overlap between generated and reference translations, not recall of semantic similarity using embeddings. It's a surface-form matching metric.
16. Perplexity measures predictive likelihood of a sequence. **TRUE** - Perplexity measures predictive likelihood of a sequence, defined as the exponentiated average negative log-likelihood: exp(-1/N ∑ log P(w_i)), indicating model uncertainty.
17. Neural Machine Translation is formulated as conditional language modeling.**TRUE** - Neural Machine Translation is formulated as conditional language modeling P(target | source), where the model learns to generate target sequences conditioned on source sequences.
18. Seq2Seq models always produce fixed-length outputs. **FALSE** - Seq2Seq models produce variable-length outputs through autoregressive generation that continues until an end-of-sequence token is produced, not fixed-length outputs.

19. Stacked RNNs increase representational depth. **TRUE** - Stacked (multi-layer) RNNs increase representational depth by allowing hierarchical feature learning, where each layer processes increasingly abstract representations.
20. Attention reduces effective dependency path length. **TRUE** - Attention reduces effective dependency path length by allowing direct connections between decoder states and relevant encoder positions, bypassing the sequential propagation required in vanilla RNNs.

### CNNs for NLP (21-42)

21. CNNs process tokens sequentially like RNNs. **FALSE** - CNNs process tokens in parallel across positions, not sequentially like RNNs. This parallelizability is one of the key advantages of CNNs over RNNs.

22. CNN filters detect local n-gram patterns. **TRUE** - CNN filters detect local n-gram patterns by sliding over adjacent word embeddings and learning to recognize specific phrase-level features.
23. Max pooling selects the strongest activation across positions. **TRUE** - Max pooling selects the strongest (maximum) activation across all positions, capturing the most important feature regardless of where it appears in the sequence.
24. CNNs inherently model long-range dependencies without stacking. **FALSE** - CNNs do not inherently model long-range dependencies without stacking. They capture local patterns within their receptive field; stacking multiple convolutional layers is necessary to expand the receptive field and capture longer-range dependencies.
25. CNNs are highly parallelizable across positions. **TRUE** - CNNs are highly parallelizable across positions because convolution operations at different positions are independent and can be computed simultaneously.
26. Recency bias is a known limitation of RNNs. **TRUE** - Recency bias is a known limitation of RNNs, where recent tokens have disproportionate influence on the final hidden state compared to earlier tokens due to sequential compression.
27. Prefix dependency refers to reliance on earlier tokens. **TRUE** - Prefix dependency refers to the reliance on earlier tokens in sequential models like RNNs, where the representation at each step depends on all previous tokens processed left-to-right.
28. Pooling produces fixed-length representations regardless of input size. **TRUE** - Pooling (max, average, or k-max) produces fixed-length representations regardless of input sequence length by aggregating variable-length feature maps into fixed-size vectors.
29. 1D convolution slides filters across embedding matrices. **TRUE** - 1D convolution slides filters across the temporal dimension of embedding matrices, applying the same filter weights at each position to detect local patterns.
30. Stride controls how far the filter moves per step. **TRUE** - Stride controls how far the filter moves per step during convolution—stride of 1 means moving one position at a time, larger strides skip positions.
31. Padding ensures equal treatment of boundary tokens. **TRUE** - Padding (typically zero-padding) ensures equal treatment of boundary tokens by allowing filters to be centered on edge positions, preventing information loss at sequence boundaries.
32. k-max pooling preserves multiple top activations. **TRUE** - k-max pooling preserves the top k activations (instead of just the maximum), maintaining information about multiple important features and their relative order.
33. CNNs require recurrence to detect phrase-level patterns. **FALSE** - CNNs do not require recurrence to detect phrase-level patterns. Convolutional filters directly capture local n-gram patterns without any recurrent connections.
34. Multi-channel CNNs combine multiple embedding representations. **TRUE** - Multi-channel CNNs combine multiple embedding representations (e.g., static pretrained embeddings and task-specific fine-tuned embeddings) processed through separate channels, similar to RGB channels in image CNNs.
35. Residual connections help mitigate vanishing gradients. **TRUE** - Residual connections (skip connections) help mitigate vanishing gradients by providing direct gradient paths that bypass intermediate layers, enabling training of very deep networks.
36. Highway networks introduce gating across depth. **TRUE** - Highway networks introduce gating mechanisms across depth, allowing the network to learn which information to pass through unchanged versus transformed, improving gradient flow in deep architectures.
37. Batch Normalization normalizes activations across batches. **TRUE** - Batch Normalization normalizes activations across the batch dimension, reducing internal covariate shift and stabilizing training.

38. BatchNorm introduces learnable scaling and shifting parameters. **TRUE** - Batch Normalization introduces learnable scaling (γ) and shifting (β) parameters that allow the network to recover representational capacity after normalization.
39. Very Deep CNNs operate at the character level. **TRUE** - Very Deep CNNs (VD-CNNs) operate at the character level, applying deep convolutional architectures directly to character embeddings to learn hierarchical representations.
40. QRNNs precompute gates using convolution. **TRUE** - QRNNs (Quasi-Recurrent Neural Networks) precompute gates using convolution operations in parallel, then apply element-wise gating sequentially, combining CNN parallelism with RNN-like sequential processing.
41. QRNNs are fully sequential like LSTMs. **FALSE** - QRNNs are not fully sequential like LSTMs. They use parallel convolution to compute gates, with only the final pooling step being sequential, making them much more parallelizable than traditional LSTMs.
42. Attention-based models eliminate recurrence entirely. **TRUE** - Attention-based models (particularly Transformers) eliminate recurrence entirely, relying instead on self-attention mechanisms to capture dependencies across all positions in parallel.

### Word Embeddings (43-60)

43. Word embeddings are learned by optimizing predictive objectives. **TRUE** - Word embeddings are learned by optimizing predictive objectives (e.g., predicting context words in Word2Vec, or maximizing co-occurrence likelihood in GloVe).

44. One-hot vectors encode graded semantic similarity. **FALSE** - One-hot vectors do NOT encode graded semantic similarity. All one-hot vectors are orthogonal to each other, making all words equidistant regardless of their semantic relationships.

45. Orthogonality in one-hot vectors prevents similarity modeling. **TRUE** - Orthogonality in one-hot vectors prevents similarity modeling because the dot product (and cosine similarity) between any two different one-hot vectors is always zero, making it impossible to distinguish semantically similar from dissimilar words.

46. Distributional semantics defines meaning by context usage. **TRUE** - Distributional semantics defines meaning by context usage, based on the distributional hypothesis: "words that occur in similar contexts tend to have similar meanings."

47. Word2Vec maximizes likelihood of word-context pairs. **TRUE** - Word2Vec maximizes the likelihood of observing actual word-context pairs in the training corpus while distinguishing them from random (negative) pairs.

48. Skip-Gram predicts context words from center words. **TRUE** - Skip-Gram predicts context words given a center word (one-to-many prediction).

49. CBOW predicts center words from context words. **TRUE** - CBOW (Continuous Bag of Words) predicts the center word from surrounding context words (many-to-one prediction).
50. Negative sampling replaces full softmax with binary classification. **TRUE** - Negative sampling replaces the expensive full softmax computation over the entire vocabulary with multiple binary classification problems (distinguishing **TRUE** context pairs from randomly sampled negative pairs).
51. SGD computes exact gradients over entire corpora. **FALSE** - SGD (Stochastic Gradient Descent) computes noisy, unbiased gradient estimates on small batches or individual examples, NOT exact gradients over entire corpora. This is what makes it scalable.
52. Margin-based loss enforces relative separation of scores. **TRUE** - Margin-based loss (e.g., hinge loss) enforces that correct examples score higher than incorrect examples by at least a specified margin.
53. Corrupted windows serve as negative examples in margin learning. **TRUE** - Corrupted windows (where the center word or context is randomly replaced) serve as negative examples in margin-based learning objectives.
54. Backpropagation computes gradients via the chain rule. **TRUE** - Backpropagation computes gradients via the chain rule, propagating error signals backward through the computational graph.
55. Fine-tuning embeddings always improves performance. **FALSE** - Fine-tuning embeddings does NOT always improve performance. It can cause overfitting on small datasets and semantic drift, potentially degrading performance. The decision depends on dataset size and task characteristics.
56. Static embeddings assign a single vector per word. **TRUE** - Static embeddings (like Word2Vec, GloVe) assign a single fixed vector per word type, regardless of context.
57. Contextual embeddings generate context-dependent vectors. **TRUE** - Contextual embeddings (like ELMo, BERT, GPT) generate different vectors for the same word depending on its surrounding context.
58. Intrinsic evaluation measures downstream task performance. **FALSE** - Intrinsic evaluation measures embedding quality directly through tasks like word similarity and analogies, NOT downstream task performance. That's extrinsic evaluation.
59. Extrinsic evaluation measures performance on real NLP tasks. **TRUE** - Extrinsic evaluation measures embeddings' performance on real NLP tasks (sentiment analysis, NER, machine translation, etc.).
60. Analogy tasks test linear relationships in embedding space. **TRUE** - Analogy tasks (e.g., "king - man + woman ≈ queen") test whether linear relationships in the embedding space capture semantic and syntactic patterns.

### Subword and Character Modeling (61-100)

61. Subword modeling reduces vocabulary size. **TRUE** - Subword modeling reduces vocabulary size by representing words as combinations of subword units rather than treating each unique word form as a separate vocabulary entry.
62. Character-level models eliminate OOV problems. **TRUE** - Character-level models eliminate OOV problems because any word can be represented as a sequence of characters, which are from a fixed, small alphabet.
63. BPE merges frequent adjacent pairs greedily. **TRUE** - BPE (Byte Pair Encoding) merges the most frequent adjacent pairs greedily in an iterative process.
64. WordPiece maximizes corpus likelihood during merges. **TRUE** - WordPiece maximizes corpus likelihood during merges, choosing merges that increase the likelihood of the training data.
65. The Unigram LM supports probabilistic segmentation. **TRUE** - The Unigram LM supports probabilistic segmentation by maintaining multiple possible segmentations with associated probabilities.
66. Subword units always correspond to **TRUE** linguistic morphemes. **FALSE** - Subword units do NOT always correspond to **TRUE** linguistic morphemes. They are statistical units optimized for corpus frequency, not linguistic validity.
67. Tokenizer drift occurs when domain changes affect segmentation. **TRUE** - Tokenizer drift occurs when domain changes affect segmentation patterns, causing mismatches between training and deployment tokenization.
68. Self-attention complexity scales quadratically with sequence length. **TRUE** - Self-attention complexity scales quadratically with sequence length (O(n²)) because each token attends to all other tokens.
69. Larger vocabularies reduce embedding matrix size. **FALSE** - Larger vocabularies INCREASE embedding matrix size (vocab_size × embedding_dim), not reduce it.
70. Byte-level tokenization eliminates OOV issues entirely. **TRUE** - Byte-level tokenization eliminates OOV issues entirely by operating on a fixed set of 256 byte values that can represent any text.
71. Character-level models increase sequence length. **TRUE** - Character-level models increase sequence length because words are broken into individual characters, creating longer sequences than word-level tokenization.
72. Morphologically rich languages benefit from subword modeling. **TRUE** - Morphologically rich languages benefit from subword modeling because it can capture productive morphological processes without exploding the vocabulary.
73. Word embeddings are dense low-dimensional vectors. **TRUE** - Word embeddings are dense low-dimensional vectors (typically 100-300 dimensions) with real-valued entries.
74. Count-based methods rely on co-occurrence matrices. **TRUE** - Count-based methods (like PMI, PPMI) rely on co-occurrence matrices that capture how often words appear together.
75. SVD reduces dimensionality in count-based models. **TRUE** - SVD (Singular Value Decomposition) reduces dimensionality in count-based models by factorizing the co-occurrence matrix.
76. Direct prediction models optimize predictive objectives. **TRUE** - Direct prediction models (like Word2Vec) optimize predictive objectives to learn embeddings.
77. Bag-of-Vectors models capture word order explicitly. **FALSE** - Bag-of-Vectors models do NOT capture word order explicitly; they treat sentences as unordered collections of word vectors.
78. Window models capture only local context. **TRUE** - Window models capture only local context within a fixed-size window around the target word.
79. CNNs can serve as feature extractors for classifiers. **TRUE** - CNNs can serve as feature extractors for classifiers by learning hierarchical representations from raw input.
80. RNN training is slower due to sequential dependency. **TRUE** - RNN training is slower due to sequential dependency, which prevents parallelization across timesteps.
81. Residual connections shorten effective gradient path length. **TRUE** - Residual connections shorten effective gradient path length by providing direct gradient paths that bypass intermediate layers.
82. Very Deep CNNs rely on character embeddings. **TRUE** - Very Deep CNNs (VD-CNNs) rely on character embeddings as input rather than word-level representations.
83. QRNNs replace recurrence entirely with self-attention. **FALSE** - QRNNs do NOT replace recurrence entirely with self-attention. They use convolution for gate computation but retain sequential pooling.
84. Fixed-window models discard information outside the window. **TRUE** - Fixed-window models discard information outside the window, limiting their receptive field.
85. Neural LMs generalize via distributed representations. **TRUE** - Neural LMs generalize via distributed representations that capture semantic similarities between words.
86. n-gram models generalize based on similarity between contexts. **FALSE** - n-gram models do NOT generalize based on similarity between contexts; they rely on exact matches and cannot generalize to unseen n-grams without smoothing.
87. Smoothing prevents zero probabilities for unseen n-grams. **TRUE** - Smoothing prevents zero probabilities for unseen n-grams by redistributing probability mass.
88. Transformer models rely heavily on residual connections. **TRUE** - Transformer models rely heavily on residual connections to enable training of deep architectures with many layers.
89. Subword tokenization affects compute and memory trade-offs. **TRUE** - Subword tokenization affects compute and memory trade-offs by balancing vocabulary size (embedding memory) against sequence length (attention cost).
90. Convolutional filters share weights across positions. **TRUE** - Convolutional filters share weights across positions, applying the same learned filter at each location in the sequence.
91. Pooling preserves exact token positions. **FALSE** - Pooling does NOT preserve exact token positions; max pooling selects the strongest activation regardless of position, losing positional information.
92. RNN hidden states compress prior context repeatedly. **TRUE** - RNN hidden states compress prior context repeatedly at each timestep, progressively summarizing longer histories into fixed-size vectors.
93. Bidirectional RNNs access future context during encoding. **TRUE** - Bidirectional RNNs access future context during encoding by processing sequences in both forward and backward directions.
94. Neural parsers learn structure from annotated treebanks. **TRUE** - Neural parsers learn structure from annotated treebanks through supervised learning on syntactic annotations.
95. Dependency grammar models syntax as word-to-word relations. **TRUE** - Dependency grammar models syntax as word-to-word relations (head-dependent pairs) rather than hierarchical phrase structures.
96. CFG rules apply independently of surrounding context. **TRUE** - CFG (Context-Free Grammar) rules apply independently of surrounding context; the applicability of a rule depends only on the non-terminal being expanded.
97. Structural ambiguity arises from attachment decisions. **TRUE** - Structural ambiguity arises from attachment decisions, such as where prepositional phrases or relative clauses attach in the parse tree.
98. Language models support speech recognition applications. **TRUE** - Language models support speech recognition applications by providing probability estimates for word sequences, helping disambiguate acoustic signals.
99. Attention mechanisms dynamically weight encoder states. **TRUE** - Attention mechanisms dynamically weight encoder states at each decoding step based on relevance to the current output position.
100.  Below-word modeling improves robustness to spelling variation. **TRUE** - Below-word (subword/character) modeling improves robustness to spelling variation, typos, and morphological
