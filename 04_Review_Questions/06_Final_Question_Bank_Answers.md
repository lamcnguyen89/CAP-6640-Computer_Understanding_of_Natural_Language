1. What distinguishes Natural Language Generation (NG) from classification tasks?
   A. Selecting predefined outputs
   **B. Constructing novel sequences that preserve meaning and fluency**
   C. Assigning labels to tokens
   D. Extracting key phrases

2. Which models are explicitly listed as examples for abstractive summarization?
   A . BERT, RoBERTa, DeBERTa
   **B. BART, PEGASUS, T5**
   C. GPT, LLaMA, Falcon
   D. CLIP, BLIP, Flamingo

3. What is the primary advantage of bottom-up summarization?
   A. Eliminates need for neural models
   **B. Improves content control and reduces hallucination**
   C . Maximizes token-level likelihood
   D. Removes extractive components

4. Which limitation of MLE training is explicitly mentioned?
   A. High computational efficiency
   B. Alignment with ROUGE metrics (Is this this answer?)
   **C. Exposure bias and mismatch with evaluation metrics**
   D. Improved long-term coherence

5. What does REINFORCE optimize in RL-based summarization?
   A. Token-level likelihood
   **B. Expected reward using Monte Carlo sampling**
   C. Cross-entropy loss only
   D. Beam search objective

6. What is the role of the critic in Actor-Critic methods?
   A. Generates summaries
   B. Encodes input text
   **C. Estimates expected reward**
   D. Performs decoding

7. Why do Seq2Seq dialogue systems produce generic responses?
   A. Due to reinforcement learning
   **B. Because likelihood maximization favors high-frequency responses**
   C. Because they lack attention mechanisms
   D. Because they use beam search

8. What does Maximum Mutual Information (MMI) introduce?
   A. Only P(T|S)
   **B. P(S|T) and penalization of high-frequency responses**
   C. Only token-Level like lihood
   D. Beam size optimization

9. What is the purpose of n-gram blocking in dialogue systems?
   A. Improve training speed
   **B. Prevent repeated phrases during decoding**
   C. Increase model size
   D. Enhance attention weights

10. What is the role of the latent variable z_t in strategic-NG separation?
    A. Predicts surface text directly
    B. Encodes token embeddings
    **C. Predicts future dialogue impact**
    D. Performs decoding

11. What happens during rollout-based decision making at test time?
    A. Model selects first generated response
    **B. Model simulates future dialogue trajectories and selects highest expected reward**
    C. Model maximizes token probability only
    D. Model disables reinforcement learning

12. What is the defining characteristic of Conversational Question Answering (CQA)?
    A. Each question is processed independently
    **B. It maintains conversational context across multiple turns**
    C. It only uses retrieval-based methods
    D. It ignores prior answers

13. Which challenge is explicitly associated with CQA?
    A. Tokenization efficiency
    **B. Context tracking and resolving coreference**
    C. Beam search optimization
    D. Vocabulary compression

14. What are the three primary modeling approaches used in CQA systems?
    A. Classification, clustering, regression
    **B. Retrieval-based, generative, hybrid**
    C. CNN-based, RNN-based, Transformer-based
    D. Supervised, unsupervised, reinforcement

15. Which architecture is used to store and retrieve conversation history in CQA?
    A. Recurrent networks
    **B. Memory networks**
    C. Autoencoders
    D. Graph neural networks

16. Which datasets are explicitly mentioned for conversational QA?
    A. SQUAD, GLUE, SuperGLUE
    B. ImageNet, coco, VIST
    **C. COQA, QUAC, DOQA**
    D. Wikitext, BookCorpus, Common Crawl

17. What distinguishes conversational QA datasets from extractive QA benchmarks?
    A. They only use retrieval
    **B. Answers are generated abstractively rather than copied verbatim**
    C. They do not use context
    D. They only contain single-turn questions

18. What is a key requirement of storytelling in NLP?
    A. Token-level probability maximization
    **B. Long-range coherence and causal structure**
    C. Only short sentence generation
    D. Fixed vocabulary constraints

19. What is the effect of prompt structure in storytelling?
    A. No impact on generation quality
    B. Only affects tokenization
    **C. Significantly shapes narrative coherence and creativity**
    D. Reduces model size

20. What capability does multi-turn interactive prompting provide?
    A. Removes context dependence
    **B. Enables collaborative storytelling with user-driven plot changes**
    C. Limits narrative diversity
    D. Prevents long-range coherence

21. What is the purpose of Skip-Thought vectors?
    A. Predict next token probability
    **B. Learn sentence representations by predicting surrounding sentences**
    C. Encode images into vectors
    D. Perform syntactic parsing

22. What is the main advantage of event-based story generation?
    A. Maximizes lexical overlap
    **B. Encourages causal progression and reduces repetitive surface-level generation**
    C. Eliminates need for neural models
    D. Uses only word-level modeling

23. What does autoregressive decomposition reduce sequence modeling to?
    A. Sequence classification
    **B. Next-token prediction**
    C. Token clustering
    D. Sequence alignment

24. What is minimized during training of language models?
    A. Perplexity directly
    B. Entropy
    **C. Cross-entropy loss**
    D. Beam width

25. What limitation do RNNs face in modeling long-range dependencies?
    A. Overfitting
    **B. Vanishing gradients**
    C. Lack of parameters
    D. Limited vocabulary

26. What mechanism enables Transformers to model long-range dependencies?
    A. Recurrence
    B. Convolution
    **C. Self-attention**
    D. Pooling

27. What causes exposure bias?
    **A. Training uses ground-truth tokens but inference uses model predictions**
    B. Model overfits to data
    C. Beam search errors
    D. Tokenization mismatch

28. Why is exact decoding intractable?
    A. Lack of training data
    B. Memory limitations only
    C. Numerical instability
    **D. Exponential growth of the search space**

29. What is the key limitation of greedy decoding?
    **A. Locally optimal but globally suboptimal sequences**
    B. High computational cost
    C. Requires large memory
    D. Produces diverse outputs

30. What does beam search improve?
    A. Training efficiency
    **B. Exploration by keeping multiple hypotheses**
    C. Tokenization quality
    D. Vocabulary size

31. Why is length normalization applied?
    A. Improve speed
    B. Increase vocabulary
    **C. Mitigate bias toward shorter sequences**
    D. Reduce memory usage

32. What is the effect of temperature scaling?
    A. Changes token order
    **B. Reshapes probability distribution sharpness**
    C. Eliminates randomness
    D. Increases sequence length

33. What does perplexity measure?
    **A. Next-token prediction uncertainty**
    B. Sequence length
    C. Beam size
    D. Model depth

34. What is the goal of coreference resolution?
    A. Token classification
    **B. Clustering mentions referring to the same entity**
    C. Sentence parsing
    D. Language modeling

35. What is a mention in coreference resolution?
    A. A token
    B. A sentence
    **C. A noun phrase, pronoun, or proper noun**
    D. A document

36. What does MUC measure?
    **A. Links between mentions**
    B. Token accuracy
    C. Sentence similarity
    D. Embedding distance

37. What does CEAF optimize?
    A. Token overlap
    B. Sentence alignment
    C. Feature similarity
    **D. Cluster alignment**

38. What is the main limitation of mention-pair models?
    A. Low accuracy
    **B. Lack of global consistency**
    C. High computation
    D. Limited vocabulary

39. What do mention-ranking models improve?
    A. Token prediction
    B. Parsing
    **C. Antecedent selection consistency**
    D. Embedding size

40. What is the role of null antecedents?
    **A. Represent singleton mentions**
    B. Improve speed
    C. Reduce parameters
    D. Increase vocabulary

41. What is a key benefit of neural coreference models?
    A. Rule-based reasoning
    **B. Learned contextual representations**
    C. Fixed features
    D. No training required

42. What does discourse salience influence?
    A. Tokenization
    B. Embedding size
    **C. Pronoun resolution**
    D. Beam search

43. What challenge arises in cross-lingual coreference?
    A. Tokenization only
    B. Vocabulary size
    C. Decoding
    **D. Morphological and syntactic variation**

44. What is the main structural formulation of coreference?
    **A. Partitioning mentions into clusters**
    B. Sequence labeling
    C. Classification
    D. Regression

45. What shift did deep learning introduce?
    A. Manual feature engineering
    **B. Automatic representation learning**
    C. Rule-based systems
    D. Static embeddings

46. What is a limitation of single-task learning?
    A. High accuracy
    B. Fast training
    **C. Lack of knowledge sharing**
    D. Low computation

47. What is the purpose of pre-training?
    **A. Learn transferable representations**
    B. Reduce model size
    C. Eliminate training
    D. Improve tokenization

48. What is hard parameter sharing?
    A. Separate models per task
    **B. Shared encoder with task-specific outputs**
    C. No sharing
    D. Random sharing

49. What is negative transfer?
    A. Improved performance
    B. Faster training
    **C. Task interference due to conflicting gradients**
    D. Reduced parameters

50. What is the role of LoRA?
    A. Increase parameters
    B. Remove training
    C. Improve tokenization
    **D. Reduce trainable parameters via low-rank updates**

51. What does instruction tuning enable?
    **A. Single model handling multiple tasks via instructions**
    B. Separate models per task
    C. Fixed outputs
    D. No adaptation

52. What is catastrophic forgetting?
    A. Improved performance
    **B. Loss of previous task knowledge**
    C. Faster inference
    D. Reduced memory

53. What does zero-shot learning rely on?
    A. Retraining
    B. Labels
    **C. Pre-trained representations**
    D. Feature engineering

54. What is scalarization?
    A. Removing objectives
    B. Increasing parameters
    C. Separate training
    **D. Combining multiple losses into a weighted sum**

55. What defines Pareto optimality?
    **A. No task improves without harming another**
    B. Maximum accuracy
    C. Minimum loss
    D. Single objective optimization

56. What does semantic composition study?
    A. Token prediction
    **B. How sentence meaning is built from parts**
    C. Parsing only
    D. Classification

57. What property allows infinite embedding?
    A. Attention
    B. Tokenization
    **C. Recursion**
    D. Optimization

58. What does PP attachment ambiguity illustrate?
    A. Tokenization issues
    B. Training difficulty
    C. Vocabulary mismatch
    **D. Structural ambiguity affecting meaning**

59. What is a limitation of bag-of-words models?
    **A. Lack of role and structure encoding**
    B. High computation
    C. Overfitting
    D. Large memory

60. What does lambda calculus represent?
    A. Word embeddings
    B. Tokenization
    **C. Function-based semantic composition**
    D. Parsing trees

61. What is the goal of hybrid models?
    A. Reduce parameters
    **B. Combine neural and symbolic approaches**
    C. Eliminate structure
    D. Improve speed

62. What does SCAN evaluate?
    A. Parsing accuracy
    B. Embedding quality
    C. Token prediction
    **D. Compositional generalization**

63. How do Transformers compose meaning?
    A. Tree recursion
    B. Rule-based parsing
    **C. Self-attention**
    D. Bag-of-words

64. What does inductive bias influence?
    **A. Generalization behavior**
    B. Tokenization
    C. Vocabulary
    D. Speed

65. What distinguishes compositionality from memorization?
    A. Dataset size
    **B. Ability to generalize to unseen combinations**
    C. Training time
    D. Model size

66. What does scope ambiguity involve?
    A. Token overlap
    B. Sentence length
    C. Parsing speed
    **D. Multiple interpretations due to quantifier scope**

67. What defines autoregressive models?
    **A. Predict next token from prior context**
    B. Mask tokens
    C. Encode full sequence
    D. Retrieve documents

68. What is the objective of masked language modeling?
    A. Predict next token
    **B. Reconstruct masked tokens**
    C. Retrieve text
    D. Translate sequences

69. What characterizes Seq2Seq models?
    A. Classification
    B. Retrieval
    **C. Encode input and decode output**
    D. Masking

70. What is the purpose of retrieval augmentation?
    A. Reduce parameters
    B. Increase training speed
    C. Improve tokenization
    **D. Incorporate external knowledge**

71. What does scaling primarily improve?
    A. Tokenization
    **B. Model performance**
    C. Vocabulary
    D. Parsing

72. What is RLHF used for?
    A. Token prediction
    B. Retrieval
    **C. Aligning outputs with human preferences**
    D. Parsing

73. What is the role of dense retrievers in RAG?
    **A. Retrieve relevant documents**
    B. Generate text
    C. Train model
    D. Encode tokens

74. What challenge do multimodal models face?
    A. Tokenization
    B. Scaling
    C. Decoding
    **D. Cross-modal alignment**

75. What is quantization used for?
    A. Increase parameters
    **B. Reduce memory and speed up inference**
    C. Improve accuracy
    D. Train models

76. What is Flash Attention designed to address?
    A. Tokenization
    B. Vocabulary
    **C. Attention memory and compute efficiency**
    D. Training data

77. What is the advantage of MoE models?
    A. Simplicity
    B. Small size
    C. Deterministic outputs
    **D. Large capacity with sparse computation**

78. What distinguishes human cognition from machine learning?
    A. Speed
    **B. Adaptability and abstraction**
    C. Data size
    D. Tokenization

79. What is few-shot learning?
    A. Large dataset training
    B. Reinforcement learning
    **C. Learning from very few examples**
    D. Supervised training

80. What is OOD robustness?
    **A. Performance under distribution shifts**
    B. Training accuracy
    C. Token prediction
    D. Model size

81. What is a limitation of LLM explanations?
    A. Too short
    B. Too fast
    C. Too large
    **D. May not reflect internal reasoning**

82. What characterizes formal reasoning?
    A. Heuristics
    **B. Strict logical rules**
    C. Probabilities
    D. Tokens

83. What does Chain-of-Thought prompting do?
    **A. Generates intermediate reasoning steps**
    B. Changes model weights
    C. Reduces parameters
    D. Removes context

84. What is the main debate about LLM reasoning?
    A. Speed vs size
    B. Data vs compute
    **C. Reasoning vs statistical pattern completion**
    D. Tokens vs embeddings

85. What do reasoning benchmarks evaluate?
    A. Tokenization
    B. Speed
    C. Vocabulary
    **D. Multi-step inference and consistency**

86. What is a key limitation of LLM reasoning?
    A. Low speed
    **B. Hallucination and inconsistency**
    C. Small models
    D. Lack of tokens

87. What does generalization require?
    **A. Robustness beyond training distribution**
    B. More parameters
    C. Faster training
    D. Larger vocabulary

88. What does perplexity measure?
    A. Reasoning ability
    B. Model size
    **C. Prediction uncertainty**
    D. Data size

89. What is algorithmic bias?
    A. Model speed
    **B. Bias learned from data patterns**
    C. Tokenization error
    D. Hardware issue

90. What is a key privacy concern in NLP?
    A. Speed
    B. Memory size
    **C. Memorization of sensitive data**
    D. Tokenization

91. What is dual-use technology?
    **A. Beneficial and malicious applications**
    B. Only safe systems
    C. Only harmful systems
    D. Only academic systems

92. What does confidentiality refer to in the CIA triad?
    A. Speed
    B. Accuracy
    C. Availability
    **D. Protection of sensitive data**

93. What is representation bias?
    A. Model architecture issue
    B. Training error
    **C. Underrepresentation of groups in data**
    D. Tokenization

94. What is annotation bias?
    A. Hardware Limitation
    **B. Subjective labeling decisions**
    C. Model size
    D. Vocabulary

95. What is counterfactual evaluation used for?
    A. Training
    B. Optimization
    C. Tokenization
    **D. Bias detection via input variation**

96. What is demographic parity?
    **A. Equal prediction rates across groups**
    B. Equal data size
    C. Equal training
    D. Equal tokens

97. What does equalized odds enforce?
    A. Equal predictions
    B. Equal data
    **C. Equal error rates across groups**
    D. Equal speed

98. What is a key limitation of fairness definitions?
    A. Too simple
    **B. They may conflict with each other**
    C. Too fast
    D. Too accurate

99. What supports accountability in NLP systems?
    A. Larger models
    B. Faster training
    C. More data
    **D. Model cards and documentation**
