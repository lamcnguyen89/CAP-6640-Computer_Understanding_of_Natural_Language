# Final Review Questions

## Multiple Choice Questions

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

4. Which limitation of MLE (Maximum Likelihood Estimation) training is explicitly mentioned?
   A. High computational efficiency
   B. Alignment with ROUGE metrics
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

## True/False Questions

1. Natural Language Generation (NG) systems synthesize new text rather than
   selecting predefined outputs. **True**
2. Abstractive summarization generates new paraphrased summaries using neural such as BART, PEGASUS, and T5. **True**
3. Extractive summarization selects key sentences or phrases directly from the source text. **True**
4. Bottom-up summarization first selects salient content and then rewrites it into a coherent summary. **True**
5. Reinforcement Learning (RL) for summarization optimizes models by maximizing long-term rewards rather than token-level likelihood. **True**
6. Maximum Likelihood Estimation (MLE) training aligns directly with evaluation metrics such as ROUGE. **False**
7. Exposure bias occurs because during training the model observes gold-standard summaries but at inference time generates tokens autoregressively. **True**
8. Self-Critical Sequence Training (SCST) uses the model's greedy-decoded summary as a baseline to reduce gradient variance. **True**
9. Actor-Critic methods include an actor that generates summaries and a critic that estimates expected reward. **True**
10. Higher ROUGE scores always correspond to improved human readability. **False**
11. Maximum Mutual Information (MMI) modifies the objective by incorporating P(S | T) and penalizing high-frequency responses. **True**
12. Conversational Question Answering (CQA) treats each question independently
    without maintaining conversational context. **False**
13. CA requires understanding previous questions, prior answers, and evolving
    discourse state. **True**
14. Retrieval-based systems dynamically generate responses using language models
    such as GPT or BART. **False**
15. Hybrid CA approaches combine retrieval and generation, as in Retrieval-
    Augmented Generation (RAG). **True**
16. Memory networks are used to store and retrieve conversation history in CQA
    systems. **True**
17. Conversational Q A datasets such as CoQ and QuAC involve multi-turn question
    answering over context. **True**
18. Storytelling in NLP requires modeling plot progression, character development,
    and stylistic consistency. **True**
19. Prompt design has n o significant effect on storytelling quality. **False**
20. Multi-turn interactive prompting allows users to introduce plot twists that the
    model continues dynamically. **True**
21. Skip-Thought vectors learn sentence representations by predicting neighboring
    sentences in a corpus. **True**
22. Event-based story generation represents narratives as sequences of structured
    events rather than raw token **True**
23. Language modeling reduces sequence probability estimation to autoregressive
    next-token prediction. **True**
24. Conditional language modeling generates a target sequence independent of input
    n-gram models approximate conditional probabilities using a fixed context
    window. **False**
25. Transformer-based models rely on recurrence rather than self-attention. **False**
26. Teacher forcing supplies the ground-truth token during training when predicting
    the next token. **True**
27. Exposure bias arises because training and inference use the same distribution. **False**
28. Decoding is a search problem over an exponentially large hypothesis space. **True**
29. Greedy decoding guarantees globally optimal sequences. **False**
30. Beam search retains multiple high-scoring hypotheses during decoding. **True**
31. Top-k sampling eliminates all stochasticity in decoding. **False**
32. Perplexity measures token-level prediction accuracy but does not guarantee high-
    quality generation. **True**
33. Coreference resolution is the task of clustering mentions that refer to the same
    real-world entity. **True**
34. Anaphora includes all forms of coreference without restriction. **False**
35. Coreference resolution is fundamentally a clustering problem over textual
    mentions. **True**
36. MUC evaluates clustering using mention-level overlap. **False**
37. B^3 computes precision and recall at the mention level. **True**
38. CEAF aligns predicted and gold clusters using optimal one-to-one matching. **True**
39. Mention-pair models guarantee global consistency across clusters. **False**
40. Mention-ranking models select the best antecedent for each mention. **True**
41. Coreference defines a n equivalence relation that must satisfy reflexivity,
    symmetry, and transitivity. **True**
42. Self-attention enables modeling of long-distance dependencies across documents. **True**
43. Coreference resolution depends only on lexical similarity and not o n world
    knowledge. **False**
44. Deep learning enables automatic feature learning from raw data. **True**
45. Single-task learning promotes knowledge sharing across tasks. **False**
46. Pre-training learns general-purpose representations o n large datasets. **True**
47. Multi-task learning integrates multiple objectives into a shared parameter
    space. **True**
48. Hard parameter sharing eliminates negative transfer between tasks. **False**
49. Soft parameter sharing maintains separate models while regularizing their
    similarity. **True**
50. Negative transfer occurs when gradients from tasks conflict. **True**
51. Fine-tuning always preserves previously learned knowledge. **False**
52. LoRA reduces trainable parameters b y factorizing weight updates into low-rank
    matrices. **True**
53. Instruction tuning requires separate output heads for each task. **False**
54. Multitask kearning cab be formulated as a multi-objective optimization problem **True**
55. Semantic composition derives sentence meaning from the structured combination of its parts. **True**
56. Meaning arises solely from individual words without considering structure or
    context. **False**
57. Recursion allows infinite embedding of phrases within phrases. **True**
58. Center embedding is cognitively easy for humans to process. **False**
59. Parsing ambiguity directly affects semantic interpretation. **True**
60. Distributional models handle logical operators such a s quantifiers and negation
    effectively. **False**
61. neural models explicitly encode hierarchical structure. **False**
62. Transformers enforce explicit tree structures during semantic composition. **False**
63. Formal semantics models meaning as function application aligned with syntax. **True**
64. Hybrid neuro-symbolic models combine structured logic with neural
    representations. **True**
65. Compositional generalization requires systematic recombination beyond memorized
    patterns. **True**
66. Autoregressive models predict the next token given prior context. **True**
67. Autoencoding models use masked language modeling with bidirectional context. **True**
68. Sequence-to-sequence models encode input and decode output sequences. **True**
69. Retrieval-augmented models rely only on parametric knowledge stored in model
    weights. **False**
70. Multimodal models integrate text with image, audio, or video representations. **True**
71. Instruction-aligned models use supervised fine-tuning and preference
    optimization. **True**
72. Causal language modeling uses bidirectional context during training. **False**
73. Scaling laws show predictable performance improvements with increased model size
    and data. **True**
74. Retrieval-augmented generation reduces hallucination by conditioning on external
    documents. **True**
75. Self-attention scales linearly with sequence length. **False**
76. Mixture-of-Experts activates all parameters for every token. **False**
77. Human intelligence exhibits strong few-shot learning and adaptability to novel
    tasks. **True**
78. Machine learning systems by design possess structured reasoning mechanisms. **False**
79. Few-shot generalization in machines remains an open research challenge. **True**
80. Language models are robust to distribution shifts and minor input perturbations. **False**
81. Generated explanations from LLMs always reflect the true internal reasoning
    process. **False**
82. Formal reasoning guarantees validity through strict inference rules. **True**
83. LLMs primarily operate within informal reasoning regimes. **True**
84. Chain-of-Thought prompting modifies model parameters during inference. **False**
85. Chain-of-Thought prompting can improve performance on multi-step reasoning
    tasks. **True**
86. Perplexity directly measures reasoning ability in language models. **False**
87. Emergent abilities refer to nonlinear improvements in performance with scale. **True**
88. Ethical risks in NLP arise from data, model architecture, deployment context,
    and societal factors. **True**
89. Algorithmic bias can originate from representation, historical, and measurement **True**
90. Publicly available data always implies ethical permissibility for model
    training. **False**
91. Generative models can be used to produce misinformation and automated
    propaganda. **True**
92. NLP systems are inherently transparent and easy to audit. **False**
93. The CIA triad consists of confidentiality, integrity, and availability. **True**
94. Bias in NLP systems is limited to dataset imbalance only. **False**
95. Cognitive biases in human language can be inherited by NLP models. **True**
96. Bias can arise during data collection, annotation, model training, and
    deployment. **True**
97. Fairness definitions such as demographic parity and equalized odds are always
    compatible. **False**
98. Bias mitigation is a continuous process across the NLP lifecycle. **True**
