## Multiple Choice Questions

### Language Modeling (1-10)

1. A language model assigns probabilities to:
   - **A)** Individual characters only
   - **B)** **Entire word sequences**
   - **C)** Only bigrams
   - **D)** Only unseen words

2. In an n-gram model, the Markov assumption states that:
   - **A)** Words are independent
   - **B)** **The next word depends only on the previous n−1 words**
   - **C)** The entire sentence is needed
   - **D)** Syntax is ignored

3. Sparsity in n-gram models increases because:
   - **A)** Vocabulary shrinks
   - **B)** Data becomes cleaner
   - **C)** **Possible combinations grow exponentially**
   - **D)** Softmax is expensive

4. Backoff methods address unseen n-grams by:
   - **A)** Ignoring them
   - **B)** Using higher-order models
   - **C)** **Falling back to lower-order models**
   - **D)** Random sampling

5. Fixed-window language models discard:
   - **A)** Future tokens
   - **B)** **Tokens outside the window**
   - **C)** Embeddings
   - **D)** Vocabulary

6. Neural language models generalize using:
   - **A)** Exact counts
   - **B)** Hard-coded rules
   - **C)** **Distributed representations**
   - **D)** Treebanks

7. Perplexity measures:
   - **A)** Syntactic correctness
   - **B)** **Prediction uncertainty**
   - **C)** BLEU similarity
   - **D)** Parsing accuracy

8. Smoothing prevents:
   - **A)** Large vocabularies
   - **B)** **Zero probabilities**
   - **C)** Long sequences
   - **D)** Recurrence

9. Increasing vocabulary size increases:
   - **A)** Sequence length
   - **B) Embedding matrix size**
   - **C)** Attention speed
   - **D)** Sparsity reduction

10. n-gram models struggle with:
    - **A)** Local grammar
    - **B)** Exact repetition
    - **C) Long-range dependencies**
    - **D)** Counting frequencies

---

### RNNs (11-20)

11. The RNN hidden state represents:
    - **A)** Only current input
    - **B)** Entire vocabulary
    - **C) Compressed prior context**
    - **D)** Word embeddings

12. RNNs differ from feedforward networks because they:
    - **A)** Use convolution
    - **B) Share parameters across time**
    - **C)** Remove recurrence
    - **D)** Ignore sequence order

13. Backpropagation Through Time requires:
    - **A)** Removing recurrence
    - **B) Unrolling the network across time**
    - **C)** Attention mechanisms
    - **D)** Pooling layers

14. RNN training is slower because:
    - **A)** No embeddings
    - **B) Sequential computation**
    - **C)** Too few parameters
    - **D)** Overfitting

15. Recency bias arises because:
    - **A)** First tokens dominate
    - **B) Final hidden state emphasizes recent tokens**
    - **C)** Attention is used
    - **D)** CNN pooling

16. RNN generation is:
    - **A)** Parallel
    - **B) Autoregressive**
    - **C)** Bidirectional
    - **D)** Non-sequential

17. Parameters in RNNs are:
    - **A)** Unique per timestep
    - **B) Shared across timesteps**
    - **C)** Randomly sampled
    - **D)** Not trainable

18. The prefix dependency issue refers to:
    - **A)** Right-to-left modeling
    - **B)** Dependence only on suffix
    - **C) Sequential left-to-right compression**
    - **D)** Global attention

19. RNNs struggle with:
    - **A)** Short sequences
    - **B)** Convolution
    - **C) Very long dependencies**
    - **D)** Word embeddings

20. Hidden state compression can cause:
    - **A)** Increased parallelization
    - **B) Representational dilution**
    - **C)** Better pooling
    - **D)** Deterministic outputs

---

### Seq2Seq & Attention (21-30)

21. Seq2Seq models learn:
    - **A)** Fixed outputs
    - **B) Conditional generation**
    - **C)** Static classification
    - **D)** Only POS tagging

22. The encoder outputs:
    - **A)** Softmax probabilities
    - **B) A context representation**
    - **C)** BLEU score
    - **D)** Random vector

23. Early Seq2Seq models suffered from:
    - **A)** Too many filters
    - **B) Fixed-length bottleneck**
    - **C)** No vocabulary
    - **D)** Overfitting embeddings

24. Attention allows the decoder to:
    - **A)** Ignore input
    - **B) Access all encoder states**
    - **C)** Remove recurrence
    - **D)** Shrink vocabulary

25. Bidirectional RNNs process:
    - **A)** Only forward
    - **B)** Only backward
    - **C) Both directions**
    - **D)** Random order

26. BLEU primarily measures:
    - **A)** Recall only
    - **B) n-gram precision**
    - **C)** Syntax trees
    - **D)** Perplexity

27. Perplexity measures:
    - **A)** Translation overlap
    - **B) Likelihood**
    - **C)** Character error
    - **D)** Recall

28. Stacked RNNs:
    - **A)** Remove depth
    - **B) Increase abstraction**
    - **C)** Ignore syntax
    - **D)** Remove recurrence

29. Attention reduces:
    - **A)** Vocabulary size
    - **B) Effective path length**
    - **C)** Embedding dimension
    - **D)** Training data

30. Neural Machine Translation is an example of:
    - **A)** Classification
    - **B)** Clustering
    - **C) Seq2Seq modeling**
    - **D)** Parsing

---

### CNNs for Text (31-45)

31. CNNs detect:
    - **A)** Global syntax
    - **B) Local n-gram patterns**
    - **C)** Only suffixes
    - **D)** Tree structures

32. Convolution is:
    - **A)** Sequential
    - **B) Parallel across positions**
    - **C)** Recursive
    - **D)** Symbolic

33. Max pooling selects:
    - **A)** Average activation
    - **B)** Minimum value
    - **C) Strongest activation**
    - **D)** Random activation

34. Stride controls:
    - **A)** Filter width
    - **B) Filter movement step**
    - **C)** Vocabulary size
    - **D)** Embedding size

35. Padding ensures:
    - **A)** Zero vocabulary
    - **B) Boundary coverage**
    - **C)** No pooling
    - **D)** Sequential order

36. CNNs are highly:
    - **A)** Sequential
    - **B) Parallelizable**
    - **C)** Deterministic
    - **D)** Symbolic

37. CNN filters share weights:
    - **A) Across positions**
    - **B)** Across vocabularies
    - **C)** Across tasks
    - **D)** Across models

38. Pooling produces:
    - **A)** Variable-length outputs
    - **B) Fixed-length representations**
    - **C)** Recurrence
    - **D)** Attention

39. CNNs primarily model:
    - **A)** Long-distance recursion
    - **B) Phrase-level features**
    - **C)** Entire sequence memory
    - **D)** Dependency trees

40. CNNs struggle with:
    - **A)** Local patterns
    - **B) Long-range dependencies**
    - **C)** Short sentences
    - **D)** Parallelism

41. Multi-channel CNNs use:
    - **A)** Single embedding type
    - **B) Multiple embedding types**
    - **C)** Only characters
    - **D)** Only bytes

42. 1×1 convolution performs:
    - **A)** Sequence pooling
    - **B) Channel transformation**
    - **C)** Recurrence
    - **D)** Attention

43. Residual connections:
    - **A)** Increase vanishing gradients
    - **B) Shorten gradient paths**
    - **C)** Remove depth
    - **D)** Remove pooling

44. Batch Normalization normalizes:
    - **A)** Vocabulary
    - **B) Activations**
    - **C)** Tokens
    - **D)** Labels

45. QRNNs combine:
    - **A)** Attention and parsing
    - **B) Convolution and gating**
    - **C)** CNN and Transformer only
    - **D)** Pure recurrence

---

### Word Embeddings & Word2Vec (46-60)

46. One-hot vectors are:
    - A) Dense
    - **B) Orthogonal**
    - C) Contextual
    - D) Probabilistic

47. Distributional semantics defines meaning by:
    - A) Dictionaries
    - **B) Context usage**
    - C) Rules
    - D) Syntax

48. Word2Vec optimizes:
    - A) Parsing trees
    - **B) Predictive likelihood**
    - C) BLEU score
    - D) SVD directly

49. Skip-Gram predicts:
    - A) Center from context
    - **B) Context from center**
    - C) Entire sentence
    - D) POS tags

50. CBOW predicts:
    - A) Context words
    - **B) Center word**
    - C) Syntactic structure
    - D) Dependencies

51. Negative sampling replaces:
    - A) SGD
    - **B) Softmax over full vocabulary**
    - C) Convolution
    - D) Parsing

52. SVD reduces:
    - A) Vocabulary
    - **B) Dimensionality**
    - C) Token count
    - D) Attention cost

53. Count-based models rely on:
    - A) Context windows
    - **B) Co-occurrence matrices**
    - C) Attention
    - D) Recurrence

54. Intrinsic evaluation tests:
    - A) Downstream performance
    - **B) Similarity/analogy tasks**
    - C) Parsing accuracy
    - D) Speech recognition

55. Extrinsic evaluation measures:
    - A) Embedding similarity
    - **B) Real task performance**
    - C) Window size
    - D) Softmax efficiency

56. Static embeddings assign:
    - A) Multiple vectors per word
    - **B) One vector per word**
    - C) Character vectors
    - D) Byte vectors

57. Contextual embeddings produce:
    - A) Fixed vectors
    - **B) Context-dependent vectors**
    - C) One-hot vectors
    - D) Count tables

58. Margin loss enforces:
    - A) Absolute probability
    - **B) Relative separation**
    - C) Softmax normalization
    - D) Perplexity reduction

59. Corrupted windows serve as:
    - A) Positive examples
    - **B) Negative examples**
    - C) Parsing rules
    - D) Embeddings

60. Fine-tuning embeddings risks:
    - A) Increased sparsity
    - **B) Semantic drift**
    - C) Fewer parameters
    - D) Tokenization errors

---

### Subword & Character Modeling (61-100)

61. Subword modeling reduces:
    - A) Expressiveness
    - **B) Vocabulary size**
    - C) Context
    - D) Parallelism

62. Character-level models eliminate:
    - A) Recurrence
    - **B) OOV words**
    - C) Attention
    - D) Softmax

63. BPE merges:
    - A) Rare pairs
    - **B) Frequent pairs**
    - C) Entire sentences
    - D) Random tokens

64. WordPiece maximizes:
    - A) Frequency only
    - **B) Likelihood**
    - C) BLEU
    - D) SVD

65. Unigram LM uses:
    - A) Greedy merges
    - **B) EM-style probabilistic pruning**
    - C) Deterministic splits
    - D) One-hot encoding

66. Subwords are:
    - A) Always morphemes
    - **B) Statistical units**
    - C) Syntactic trees
    - D) Tokens with fixed meaning

67. Self-attention complexity is:
    - A) Linear
    - B) Logarithmic
    - **C) Quadratic in sequence length**
    - D) Constant

68. Byte-level tokenization ensures:
    - A) Smaller sequences
    - **B) OOV elimination**
    - C) Fewer tokens
    - D) Fixed vocabulary

69. Tokenizer drift occurs when:
    - **A) Training and deployment domains differ**
    - B) Embeddings change
    - C) RNN fails
    - D) CNN pooling shifts

70. Morphologically rich languages benefit from:
    - A) Larger vocabularies
    - **B) Subword modeling**
    - C) Bag-of-words
    - D) Removing embeddings

71. Character-level CNNs operate:
    - A) On words only
    - **B) On characters**
    - C) On trees
    - D) On POS tags

72. Increasing vocabulary decreases:
    - A) Memory
    - B) Embedding matrix size
    - **C) Sequence length**
    - D) Compute

73. Smaller vocabulary increases:
    - **A) Attention cost**
    - B) Embedding memory
    - C) Softmax speed
    - D) BatchNorm

74. Subword modeling helps with:
    - A) Syntax trees
    - **B) Transliteration**
    - C) Removing tokens
    - D) Shrinking corpora

75. Transformer scaling depends on:
    - **A) Token count**
    - B) Grammar rules
    - C) POS tagging
    - D) SVD

76. Writing systems influence:
    - A) Attention heads
    - **B) Segmentation strategies**
    - C) Batch size
    - D) Loss functions

77. Agglutinative languages produce:
    - A) Few word forms
    - **B) Many affixed forms**
    - C) No morphemes
    - D) Only prefixes

78. Abugida scripts encode:
    - A) Full words
    - **B) Consonant-vowel units**
    - C) Only vowels
    - D) Logograms

79. Logographic systems represent:
    - A) Phonemes
    - **B) Morphemes or words**
    - C) Letters
    - D) Bigrams

80. Byte-level models increase:
    - A) Parallelism
    - **B) Sequence length**
    - C) Vocabulary
    - D) Recurrence

81. Subword modeling improves:
    - A) Memory only
    - **B) Robustness to spelling variation**
    - C) Grammar rules
    - D) Recursion

82. Unigram LM supports:
    - **A) Multiple segmentations**
    - B) One deterministic segmentation
    - C) Only character splits
    - D) No pruning

83. BPE is:
    - A) Probabilistic
    - **B) Greedy frequency-based**
    - C) EM-based
    - D) Contextual

84. Character models are useful for:
    - A) Clean formal text only
    - **B) Noisy user text**
    - C) Removing embeddings
    - D) Reducing depth

85. Tokenization affects:
    - **A) Scaling cost**
    - B) Syntax trees only
    - C) BatchNorm
    - D) Recurrence only

86. Transformers benefit from:
    - A) Long sequences
    - **B) Efficient compression**
    - C) Larger stride
    - D) More recurrence

87. Subword units balance:
    - **A) Vocabulary size and generalization**
    - B) Grammar and syntax
    - C) Parsing and tagging
    - D) Convolution and pooling

88. Byte-level models operate on:
    - **A) Unicode bytes**
    - B) Morphemes
    - C) Words
    - D) Syllables

89. OOV stands for:
    - **A) Out of Vocabulary**
    - B) Order of Value
    - C) Overlapping Vector
    - D) Output Variance

90. Character-level modeling increases:
    - A) Softmax speed
    - **B) Token count**
    - C) Vocabulary size
    - D) Parallelism

91. Tokenization impacts:
    - **A) Memory and compute**
    - B) Only embeddings
    - C) Only parsing
    - D) Only CNNs

92. Subword tokenization supports:
    - **A) Multilingual modeling**
    - B) Only English
    - C) Only character scripts
    - D) Only small corpora

93. Large vocabularies reduce:
    - A) Embedding memory
    - **B) Sequence length**
    - C) Parameter count
    - D) Storage

94. Attention cost scales with:
    - A) Vocabulary size
    - **B) Sequence length squared**
    - C) Embedding dimension
    - D) Batch size

95. Statistical segmentation may not align with:
    - **A) Morphemes**
    - B) Tokens
    - C) Embeddings
    - D) Softmax

96. SentencePiece implements:
    - A) WordPiece only
    - **B) Unigram LM**
    - C) BPE only
    - D) Softmax

97. Subword modeling improves:
    - A) Exact counting
    - **B) Generalization across word forms**
    - C) Recurrence depth
    - D) Treebanks

98. Open vocabulary means:
    - A) Fixed lexicon
    - **B) New words continually appear**
    - C) Only nouns
    - D) Only English

99. Character models are robust to:
    - A) Parsing errors
    - **B) Typos**
    - C) Attention collapse
    - D) Overfitting only

100.  The evolution of NLP architectures trends from:
      - A) Attention → CNN → RNN
      - **B) Recurrence → Convolution → Attention**
      - C) CNN → RNN → Parsing
      - D) Bag-of-words → Parsing → RNN
