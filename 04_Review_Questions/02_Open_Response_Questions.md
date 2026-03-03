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

**Answer:** NLP evolved through three major paradigms: (1) Rule-based systems (1950s-1980s) used hand-crafted grammars and expert knowledge; (2) Statistical methods (1990s-2000s) learned patterns from data using probabilistic models like HMMs and n-grams; (3) Neural approaches (2010s+) used deep learning with word embeddings, RNNs, and Transformers to learn hierarchical representations end-to-end.

- **(B)** Analyze why each transition occurred, focusing on the limitations of the previous paradigm and the roles of computational power and data availability.

**Answer:** Rule-based systems failed to scale due to linguistic complexity and brittleness. Statistical models emerged with more data and compute but suffered from feature engineering and sparsity. Neural methods succeeded when massive datasets, GPU acceleration, and architectural innovations (attention, pretraining) enabled learning rich representations directly from data without manual feature design.

#### Question 2: Ambiguity and the Hardness of NLP

- **(A)** Explain why ambiguity is a fundamental challenge in natural language processing and how syntactic ambiguity can grow exponentially with sentence complexity.

**Answer:** Ambiguity is fundamental because natural language permits multiple valid interpretations of the same input—lexically (word senses), syntactically (parse trees), and semantically (meaning). Syntactic ambiguity grows exponentially because each prepositional phrase, modifier, or coordination structure can attach to multiple constituents, creating a combinatorial explosion: with n ambiguous attachments, the number of valid parse trees can approach Catalan numbers O(4^n/n^(3/2)), making exhaustive enumeration intractable without probabilistic models to rank interpretations.

- **(B)** Compare natural languages with formal computer languages in terms of ambiguity, determinism, and interpretability, and discuss the implications for computational modeling.

**Answer:** Natural languages are inherently ambiguous, context-dependent, and lack explicit formal specifications, requiring probabilistic models and world knowledge for disambiguation. Formal languages are unambiguous by design, deterministic in evaluation, and fully specified by explicit grammars, enabling deterministic parsers. This means NLP systems must use statistical learning and neural approximation to handle ambiguity and incompleteness, while compilers leverage precise syntax for guaranteed correctness—making NLP fundamentally harder and requiring data-driven rather than rule-based approaches.

#### Question 3: Task Taxonomy in NLP

- **(A)** Define and distinguish between syntactic, semantic, and pragmatic NLP tasks.

**Answer:** Syntactic NLP tasks focus on the grammatical structure and form of language, including parsing, part-of-speech tagging, and constituency/dependency tree construction—essentially analyzing how words are arranged according to grammatical rules. Semantic tasks address the meaning of linguistic expressions, such as word sense disambiguation, semantic role labeling, and entity linking, determining what sentences mean independent of context. Pragmatic tasks interpret language in context, including coreference resolution, sentiment analysis, and dialogue act classification, capturing how meaning depends on speaker intent, discourse context, and real-world knowledge.

- **(B)** Analyze how these task categories interact in a complete language understanding pipeline, and explain why syntactic processing alone is insufficient for full interpretation.

**Answer:** In a complete language understanding pipeline, these categories form a hierarchical dependency: syntactic analysis provides structural scaffolding that semantic interpretation builds upon, while pragmatics resolves ambiguities and interprets meaning within broader context. Syntactic processing alone is insufficient because structure doesn't determine meaning—syntactically identical sentences can have different meanings (e.g., "The duck is ready to eat" where "duck" is subject vs. object), and pragmatic factors like sarcasm, implicature, and world knowledge fundamentally alter interpretation beyond what syntax and semantics alone can capture. Full understanding requires integrating all three levels to resolve ambiguity, ground references, and infer communicative intent.

---

### Word Embeddings and Distributional Semantics

#### Question 1: Limitations of Discrete Representations and the Distributional Hypothesis

- **(A)** Formally explain why one-hot word representations are orthogonal and why this property prevents the encoding of semantic similarity.

**Answer:** One-hot word representations are orthogonal because each word is represented as a vector with exactly one dimension set to 1 (corresponding to that word's index in the vocabulary) and all other dimensions set to 0. This encoding scheme ensures that for any two distinct words w₁ and w₂, their one-hot vectors v₁ and v₂ satisfy v₁ᵀv₂ = 0, making them orthogonal. This orthogonality prevents encoding semantic similarity because the inner product (and consequently cosine similarity) between any two different words is always zero, regardless of whether they are semantically related (like "cat" and "dog") or completely unrelated (like "cat" and "astronomy"). Since geometric measures of similarity like cosine similarity rely on non-zero inner products to quantify relatedness, the uniform orthogonality of one-hot vectors means that all words are equidistant from each other in the representation space, making it impossible to distinguish between semantically similar and dissimilar word pairs.

- **(B)** Describe how the distributional hypothesis addresses these limitations and analyze how dense word embeddings induce a geometric notion of graded similarity.

**Answer:** The distributional hypothesis, which states that "words that occur in similar contexts tend to have similar meanings," addresses the limitations of one-hot representations by enabling the learning of dense, low-dimensional word embeddings where semantic relationships are encoded geometrically. Instead of assigning arbitrary, orthogonal vectors to words, distributional methods (like Word2Vec or GloVe) learn embeddings by observing word co-occurrence patterns in large corpora—words that appear in similar contexts (e.g., "cat" and "dog" both appearing near words like "pet," "feed," "walk") will have their embedding vectors pushed closer together in the learned space. These dense embeddings induce a geometric notion of graded similarity because semantically related words end up with high cosine similarity (vectors pointing in similar directions), while unrelated words have low or negative similarity. This continuous similarity measure enables the representation to capture fine-grained semantic relationships, analogical reasoning (e.g., king - man + woman ≈ queen), and generalization across semantically similar words, fundamentally solving the rigidity of discrete one-hot representations.

#### Question 2: Word2Vec Objective and Optimization

- **(A)** Derive the predictive objective of the Word2Vec model, including the softmax formulation of $P(o \mid c)$ and its relationship to cross-entropy loss.

**Answer:**

- **(B)** Explain why stochastic gradient descent is necessary for scalability and analyze how gradient-based optimization leads to emergent semantic structure in the embedding space.

**Answer:**

#### Question 3: Skip-Gram vs CBOW and Training Dynamics

- **(A)** Compare the Skip-Gram and CBOW architectures in terms of prediction direction, training behavior, and sensitivity to rare versus frequent words.

**Answer:** Skip-Gram and CBOW represent complementary prediction directions in Word2Vec: Skip-Gram predicts context words given a center word (one-to-many), while CBOW predicts the center word from surrounding context words (many-to-one). This architectural difference creates distinct training behaviors—Skip-Gram treats each context position as a separate training example, generating multiple updates per center word and thus providing more training signal, which makes it particularly effective for rare words that appear infrequently but in diverse contexts. CBOW, by contrast, averages context embeddings before prediction, smoothing over positional variations and emphasizing the aggregate distributional pattern, which makes it faster to train and more effective for frequent words where abundant data supports stable averaging, but causes it to underrepresent rare words whose limited occurrences get diluted in the averaging process. Consequently, Skip-Gram exhibits higher sensitivity to rare words and captures finer-grained semantic distinctions, while CBOW trains faster and performs better on high-frequency words where statistical averaging improves robustness.

- **(B)** Analyze how the end-to-end training pipeline, including vocabulary construction, context window extraction, embedding lookup, and parameter updates, enables word vectors to capture distributional meaning.

**Answer:** The end-to-end Word2Vec training pipeline enables embeddings to capture distributional meaning through a coordinated sequence of operations that directly optimize for contextual co-occurrence patterns. First, vocabulary construction establishes the discrete token space and assigns each word a learnable embedding vector. Then, context window extraction (e.g., sliding a window of size 5) generates training pairs that operationalize the distributional hypothesis by linking each word to its immediate lexical neighborhood. During forward propagation, embedding lookup retrieves the relevant vectors, which are then passed through a shallow neural network (either projecting center embeddings to predict context in Skip-Gram, or aggregating context embeddings to predict the center in CBOW) to compute prediction scores via dot products followed by softmax. The cross-entropy loss measures how well the model predicts observed co-occurrences, and backpropagation computes gradients that flow back through the network to update both the embedding matrix and output weights. Through iterative stochastic gradient descent over millions of such context windows, embeddings for words appearing in similar contexts (e.g., "cat" and "dog" both co-occurring with "pet," "feed") receive similar gradient updates that push their vectors closer together in the shared embedding space, while unrelated words diverge—thus geometrically encoding the distributional hypothesis where semantic similarity emerges directly from patterns of contextual usage learned end-to-end from raw text.

---

### Neural Training and Optimization

#### Question 1: Optimization and Negative Sampling

- **(A)** Explain why the full softmax objective in Skip-Gram is computationally expensive and how stochastic gradient descent enables scalable training.

**Answer:** The full softmax objective in Skip-Gram is computationally expensive because computing P(o|c) = exp(u_o^T v_c) / Σ_w exp(u_w^T v_c) requires normalizing over the entire vocabulary V at every training step, making each gradient computation O(|V|) where |V| can be hundreds of thousands of words. For a corpus with millions of training pairs, this becomes prohibitively expensive. Stochastic gradient descent (SGD) enables scalable training by processing one (or mini-batches of) context-target pairs at a time rather than computing gradients over the entire dataset, which dramatically reduces memory requirements and allows incremental updates. By randomly sampling training examples and updating parameters immediately, SGD provides noisy but unbiased gradient estimates that converge efficiently while avoiding the need to load the entire corpus into memory or perform full-vocabulary summations repeatedly, making Word2Vec training practical even on large corpora with commodity hardware.

- **(B)** Derive the intuition behind skip-gram with negative sampling and analyze how replacing multiclass prediction with binary classification preserves semantic learning while improving efficiency.

**Answer:** Skip-gram with negative sampling (SGNS) reformulates the expensive multiclass softmax prediction into multiple independent binary classification problems: instead of predicting which word appears in context from all vocabulary words, it asks "does word o actually appear near word c?" (positive example) versus "does random word w_neg appear near c?" (negative example), training the model to distinguish true context pairs from randomly sampled noise using sigmoid binary classifiers. This preserves semantic learning because words appearing in similar contexts still receive similar gradient updates—true context pairs (c, o_true) push their dot products u_o^T v_c higher, while negative samples push unrelated pairs apart, effectively implementing the distributional hypothesis by making contextually similar words cluster together while separating unrelated words. Efficiency improves dramatically because instead of computing O(|V|) softmax normalization per example, SGNS only computes k+1 sigmoid evaluations (one positive, k negatives, typically k=5-20), reducing complexity from O(|V|) to O(k), enabling training on billion-word corpora in hours while maintaining the fundamental principle that semantic similarity emerges from co-occurrence patterns encoded geometrically in the learned embedding space.

#### Question 2: Count-Based vs Predictive Embeddings

- **(A)** Compare count-based representations using co-occurrence matrices and dimensionality reduction (e.g., SVD) with direct prediction methods such as Word2Vec.

**Answer:** Count-based representations construct explicit co-occurrence matrices that capture global corpus statistics by counting how frequently words appear near each other within fixed context windows, then apply dimensionality reduction techniques like Singular Value Decomposition (SVD) or Positive Pointwise Mutual Information (PPMI) weighting to produce dense, low-dimensional embeddings that preserve the major patterns of co-occurrence while reducing sparsity and noise. In contrast, direct prediction methods like Word2Vec (Skip-Gram and CBOW) optimize neural network parameters to predict context words from center words (or vice versa) using local training objectives, learning embeddings implicitly through backpropagation as the model adjusts weights to maximize predictive accuracy on word-context pairs sampled from the corpus. The fundamental difference is that count-based methods explicitly compute and decompose global statistics in a two-stage process (count then factor), while predictive methods learn embeddings end-to-end by iteratively updating parameters based on local prediction errors, with the distributional hypothesis emerging implicitly through the optimization process rather than being explicitly encoded in a co-occurrence matrix.

- **(B)** Analyze the trade-offs between these approaches in terms of computational efficiency, representational expressiveness, and downstream task performance.

**Answer:** The trade-offs between these approaches reflect competing priorities in computational efficiency, representational expressiveness, and task performance. Count-based methods with SVD benefit from leveraging global corpus statistics and deterministic matrix factorization, making them reproducible and potentially more stable, but they require constructing and storing massive sparse matrices (O(|V|²) entries for vocabulary size V) and performing expensive SVD operations (O(min(|V|², nd²)) for n documents and d dimensions), which becomes prohibitively costly for large vocabularies. Predictive methods like Word2Vec scale more gracefully through stochastic online learning with negative sampling, requiring only O(k) computations per training example (where k is the number of negative samples, typically 5-20) and enabling incremental updates without materializing full co-occurrence matrices, though they introduce hyperparameter sensitivity (learning rate, window size, negative sample count) and non-deterministic convergence due to random initialization and sampling. In terms of representational expressiveness, recent analyses (Levy & Goldberg, 2014) show that Word2Vec with negative sampling implicitly factorizes a shifted PMI matrix, suggesting theoretical equivalence, though predictive methods often capture more nuanced semantic relationships and perform better on analogy tasks and downstream applications, possibly because the iterative optimization with sampling acts as implicit regularization that prevents overfitting to noisy co-occurrences, while count-based methods can be sensitive to hyperparameters like smoothing, weighting schemes, and the number of SVD dimensions retained—ultimately, modern practice favors predictive methods for their computational scalability and strong empirical performance, though hybrid approaches like GloVe combine global statistics (like count-based methods) with local context prediction objectives to merge the strengths of both paradigms.

#### Question 3: Evaluation and Word Sense Ambiguity

- **(A)** Distinguish between intrinsic and extrinsic evaluation of word embeddings and discuss their respective strengths and limitations.

**Answer:** Intrinsic evaluation measures word embeddings directly through tasks like word similarity (comparing cosine similarity to human judgments on pairs like "cat"/"dog"), analogy completion (solving "king - man + woman ≈ queen"), and clustering quality, offering fast, interpretable assessments of whether embeddings capture semantic relationships without requiring downstream task infrastructure—however, these evaluations may not correlate strongly with real-world performance since optimizing for similarity judgments doesn't guarantee utility in practical applications. Extrinsic evaluation assesses embeddings indirectly by measuring performance on downstream NLP tasks like sentiment analysis, named entity recognition, or machine translation, where embeddings serve as input features—this approach directly measures practical utility and end-to-end effectiveness but is expensive (requiring full task pipelines), confounds embedding quality with task-specific factors (architecture, hyperparameters, training data), and provides less interpretable feedback about what semantic properties the embeddings capture, making it harder to diagnose specific representational deficiencies.

- **(B)** Explain why static embeddings struggle with word sense ambiguity and analyze how contextual or multi-representation approaches address this limitation.

**Answer:** Static embeddings struggle with word sense ambiguity because they assign each word type a single fixed vector regardless of context, forcing polysemous words like "bank" (financial institution vs. river edge) to collapse all senses into one averaged representation that dilutes distinct meanings and fails to capture sense-specific semantic relationships—for instance, the static "bank" vector will be equidistant from both "money" and "river," preventing accurate disambiguation. Contextual embeddings (like ELMo, BERT, GPT) address this limitation by generating dynamic, context-dependent representations where the same word receives different vectors based on surrounding tokens—"bank" in "river bank" produces a vector close to "shore" while "bank" in "savings bank" aligns with "finance"—effectively performing implicit word sense disambiguation through attention mechanisms that weight context appropriately. Multi-representation approaches like multi-prototype embeddings explicitly learn multiple vectors per word type (one per sense cluster discovered through unsupervised methods), allowing direct modeling of polysemy, though these require sense disambiguation mechanisms and may not scale as gracefully as fully contextual models that handle disambiguation implicitly through infinite context-dependent representations.

---

### Window-Based Models and Neural Classification

#### Question 1: Window-Based Modeling and Margin Objectives

- **(A)** Explain how a window-based formulation reduces NLP tasks such as Named Entity Recognition to local classification problems and describe the modeling assumptions involved.

**Answer:** Window-based formulation reduces NLP tasks like Named Entity Recognition to local classification by extracting fixed-size context windows around each target token (e.g., 2 words left and right) and treating each window as an independent classification instance—for example, deciding whether the center word is a location entity based only on its immediate neighbors. The key modeling assumptions are: (1) local sufficiency: all information needed for classification is contained within the fixed window, ignoring long-range dependencies; (2) context independence: each window is classified independently without considering interactions between adjacent predictions; and (3) fixed receptive field: the window size is predetermined and uniform across all instances, potentially missing relevant context that falls outside the window boundaries. This transforms a structured sequence labeling problem into a collection of local binary or multiclass classification decisions that can be trained efficiently using standard neural architectures.

- **(B)** Derive the max-margin hinge loss used to separate correct and corrupted windows, and analyze how margin-based learning differs from probabilistic objectives.

**Answer** The max-margin hinge loss is derived by pairing each correct window (with score S for a true entity mention) against corrupted windows (with scores S_c for negative examples where the center token is not the target entity type) and defining the loss as J = max(0, 1 - S + S_c), which penalizes the model whenever the correct window's score fails to exceed the corrupted window's score by at least a margin of 1. Margin-based learning differs fundamentally from probabilistic objectives (like cross-entropy with softmax) by focusing on relative score separation rather than absolute probability calibration—it only cares that correct examples score higher than incorrect ones by a safety margin, allowing confident predictions (S >> S_c) to contribute zero loss, whereas probabilistic objectives always apply non-zero loss by measuring divergence from the true probability distribution, continuously pushing probabilities toward 0 or 1. This makes margin-based methods more robust to outliers and less sensitive to probability miscalibration, though they sacrifice probabilistic interpretability and may struggle with uncertainty quantification compared to likelihood-based approaches.

#### Question 2: Neural Scoring and Backpropagation

- **(A)** Describe how a neural scoring function maps concatenated word embeddings from a context window to a scalar compatibility score.

**Answer:** A neural scoring function maps concatenated word embeddings from a context window to a scalar compatibility score through a multi-layer feedforward architecture: given a context window of size 2k+1 centered on a target word, the embeddings for all words in the window (each of dimension d) are concatenated into a single vector of dimension (2k+1)×d, which is then passed through one or more hidden layers with non-linear activations (typically ReLU or tanh) to extract compositional features, and finally projected through a linear output layer to produce an unnormalized scalar score representing the compatibility or likelihood that the center word belongs to a particular class (e.g., being a location entity in NER). This architecture enables the model to learn non-linear combinations of the contextual embeddings, capturing patterns like "words appearing near 'in' and 'located' are likely locations," with the score used directly in margin-based objectives or normalized via softmax for probabilistic classification.

- **(B)** Explain how backpropagation computes parameter updates in this multi-layer network and analyze how gradients flow through the computational graph during training.

**Answer:** Backpropagation computes parameter updates by applying the chain rule to propagate gradients backward through the computational graph from the loss function to all parameters: starting with the loss gradient ∂J/∂s (where s is the output score), gradients flow backward through the output layer to compute ∂J/∂W_out and ∂J/∂h (where h is the hidden layer activation), then through the non-linear activation function using its local derivative (e.g., ∂tanh/∂z = 1 - tanh²(z)), continuing backward through hidden layers to compute ∂J/∂W_hidden, and finally reaching the embedding layer where ∂J/∂E updates the word vectors themselves. During training, gradients accumulate differently across the computational graph: parameters in later layers (closer to the loss) receive direct gradient signals and update quickly, while gradients flowing to embeddings pass through multiple matrix multiplications and non-linearities, potentially becoming diluted—this hierarchical gradient flow means that the network learns to compose local contextual patterns in hidden layers while simultaneously fine-tuning word embeddings to encode distributional semantics that support these compositional operations, with stochastic gradient descent enabling efficient parameter updates by processing mini-batches of context windows rather than the entire corpus.

#### Question 3: Optimization Dynamics and Embedding Fine-Tuning

- **(A)** Explain how stochastic gradient descent enables scalable optimization in neural NLP models trained over large corpora.

**Answer:** Stochastic gradient descent (SGD) enables scalable optimization in neural NLP models by processing one training example (or small mini-batches) at a time rather than computing gradients over the entire corpus, which dramatically reduces memory requirements from O(N) to O(1) where N is the corpus size and allows parameter updates to begin immediately without waiting for a full pass through billions of tokens. Unlike batch gradient descent which requires loading the entire dataset and computing exact gradients—prohibitively expensive for corpora with millions of documents—SGD samples random training instances (e.g., individual word-context pairs in Word2Vec or sentences in language modeling), computes noisy but unbiased gradient estimates using backpropagation, and updates parameters incrementally with each example, effectively turning optimization into an online learning process. This stochastic sampling introduces gradient noise that actually helps escape local minima and provides implicit regularization, while the frequent parameter updates (potentially millions per epoch) enable faster convergence than waiting for full-batch gradients, making it feasible to train neural models with hundreds of millions of parameters on web-scale corpora using standard hardware—ultimately, SGD's O(k) computational complexity per update (where k is mini-batch size, typically 32-256) versus O(N) for batch methods is what makes modern deep learning for NLP computationally tractable.

- **(B)** Analyze the trade-offs involved in fine-tuning pretrained word embeddings during task-specific training, particularly with respect to overfitting and semantic drift.

**Answer:** Fine-tuning pretrained word embeddings during task-specific training involves critical trade-offs between task specialization and semantic integrity: when training data is abundant (e.g., >100k examples), fine-tuning allows embeddings to adapt to task-specific distributional patterns, potentially improving performance by adjusting "dog" to be closer to "aggressive" in sentiment analysis of product reviews where negative dog-related mentions dominate, but this risks overfitting when datasets are small since the limited task data provides insufficient signal to reliably update high-dimensional embeddings (e.g., 300 dimensions × 50k vocabulary = 15M parameters), causing the model to memorize spurious training correlations rather than learning generalizable patterns. Additionally, fine-tuning causes semantic drift where task-specific updates corrupt the rich, general-purpose semantic relationships learned from billions of tokens during pretraining—for instance, adjusting embeddings for a medical NER task might push "doctor" away from "physician" if the training set happens to use only one term, degrading the embedding's utility for transfer to other tasks and breaking useful analogical relationships (king - man + woman ≈ queen) that rely on stable geometric structure. The optimal strategy depends on dataset size: freeze embeddings for small datasets (<10k examples) to prevent overfitting and preserve pretrained semantics, fine-tune with small learning rates (10x smaller than other parameters) for medium datasets to allow gentle adaptation while maintaining general structure, and fully fine-tune for large datasets where abundant signal justifies task-specific specialization—modern practice often uses hybrid approaches like adapter layers or low-rank adaptation (LoRA) that add task-specific parameters while keeping pretrained embeddings frozen, achieving specialization without semantic corruption.

---

### Named Entity Recognition

#### Question 1: Window-Based NER and Margin Optimization

- **(A)** Explain how Named Entity Recognition for location entities can be formulated as a binary classification problem using fixed-size context windows.

**Answer:** Named Entity Recognition for location entities can be formulated as a binary classification problem by extracting fixed-size context windows (e.g., 2 words on each side) around each candidate token and training a classifier to predict whether the center word is a location entity or not. Each window becomes an independent training example where the concatenated word embeddings from the context are fed into a neural network that outputs a scalar score—positive windows contain true location entities at the center (labeled as class 1), while negative windows contain non-location tokens (labeled as class 0). This local windowing assumption treats each token's entity classification as independent, converting the structured sequence labeling problem into a collection of binary decisions that can be trained efficiently using standard supervised learning, though it ignores dependencies between adjacent entity labels and assumes all necessary information for classification is contained within the fixed context window

- **(B)** Derive the max-margin loss function $J = \max(0, 1 - S + S_c)$ and analyze how pairing true and corrupted windows drives discriminative learning.

#### Question 2: Neural Scoring and Gradient Flow

- **(A)** Describe how a feed-forward neural network computes an unnormalized compatibility score for a context window.

**Answer:** A feed-forward neural network computes an unnormalized compatibility score for a context window by first concatenating the word embeddings of all tokens within the window (e.g., 2k+1 words for a window of size k) into a single high-dimensional input vector of size (2k+1)×d, where d is the embedding dimension. This concatenated vector is then passed through one or more hidden layers with non-linear activation functions (typically ReLU or tanh) that learn to compose and extract higher-level features from the local context, followed by a final linear projection layer that produces a scalar score representing the compatibility or likelihood that the center word belongs to a particular class (e.g., being a location entity in Named Entity Recognition). This score remains unnormalized—it's a raw logit value that can be used directly in margin-based objectives or normalized via softmax for probabilistic classification—and the network learns to assign higher scores to valid context-label combinations through gradient-based optimization.

- **(B)** Explain how backpropagation operates over the computational graph to update parameters, including the role of upstream and local gradients.

**Answer:** Backpropagation operates over the computational graph by applying the chain rule to propagate error gradients backward from the loss function through each layer to all learnable parameters. Starting with the loss gradient ∂J/∂s (where s is the output score), gradients flow backward through the output layer to compute ∂J/∂W_out and ∂J/∂h (where h is the hidden activation), then through the non-linear activation using its local derivative (e.g., ∂ReLU/∂z = 1 if z>0, else 0), continuing through hidden layers to compute ∂J/∂W_hidden, and finally reaching the embedding layer to update word vectors via ∂J/∂E. At each layer, the gradient with respect to a parameter is computed as the product of the upstream gradient (flowing from layers closer to the loss) and the local gradient (the derivative of that layer's operation with respect to its parameters), enabling the network to adjust all parameters—from output weights to word embeddings—in directions that reduce the loss. This hierarchical gradient flow allows the network to simultaneously learn compositional feature extractors in hidden layers while fine-tuning word embeddings to encode contextual patterns that support the classification objective.

#### Question 3: Embedding Fine-Tuning and Optimization Trade-offs

- **(A)** Explain the risks associated with retraining pre-trained word embeddings during task-specific training.

**Answer:** Retraining pre-trained word embeddings during task-specific training carries significant risks, primarily overfitting and semantic drift. When training data is limited (e.g., <10k examples), fine-tuning high-dimensional embeddings (typically 300 dimensions × tens of thousands of vocabulary = millions of parameters) provides insufficient signal to reliably update the weights, causing the model to memorize spurious training correlations rather than learning generalizable patterns. Additionally, task-specific updates can corrupt the rich, general-purpose semantic relationships learned from billions of tokens during pretraining—for example, adjusting embeddings for a domain-specific sentiment task might push "excellent" away from "great" if the training set happens to use them in different contexts, breaking useful analogical relationships (king - man + woman ≈ queen) and degrading the embedding's utility for transfer to other tasks or domains.

- **(B)** Analyze how dataset size influences the decision to fine-tune embeddings and discuss the trade-off between task specialization and global semantic consistency.

**Answer:** Dataset size critically influences fine-tuning decisions through a trade-off between task specialization and semantic consistency: with small datasets (<10k examples), embeddings should remain frozen to preserve pretrained semantic structure and prevent overfitting; medium datasets (10k-100k examples) benefit from fine-tuning with reduced learning rates (typically 10× smaller than other parameters) to allow gentle task-specific adaptation while maintaining general semantic relationships; large datasets (>100k examples) provide sufficient signal to justify full fine-tuning where task specialization outweighs the risk of semantic drift. The fundamental tension is that task-specific fine-tuning improves performance by adapting embeddings to domain-specific distributional patterns (e.g., making "bank" closer to "finance" in a banking corpus), but this specialization comes at the cost of corrupting global semantic consistency learned from massive pretraining corpora, potentially reducing cross-task transfer and breaking compositional reasoning—modern practice increasingly favors hybrid approaches like adapter layers or LoRA that add task-specific parameters while keeping pretrained embeddings frozen, achieving specialization without semantic corruption.

---

### Syntactic Parsing

#### Question 1: Phrase Structure and Context-Free Grammars

- **(A)** Explain how phrase structure encodes hierarchical organization in sentences and describe how context-free grammars (CFGs) formalize this structure using production rules.

**Answer:** Phrase structure encodes hierarchical organization by grouping words into nested constituents (like noun phrases, verb phrases) that function as single units within larger structures, representing the intuition that sentences aren't flat sequences but rather tree-like compositions where phrases can contain sub-phrases. Context-free grammars formalize this structure through production rules of the form A → β, where a non-terminal symbol A (like NP or VP) expands into a sequence β of terminals (words) and/or non-terminals, enabling systematic generation and recognition of grammatically valid sentences—for example, S → NP VP, NP → Det N, VP → V NP recursively define how a sentence decomposes into subject and predicate, which further decompose into determiner-noun and verb-object structures, directly encoding the hierarchical phrase relationships through rewrite rules that mirror the tree structure of syntactic constituency.

- **(B)** Analyze how recursion in CFGs enables nested constructions and discuss limitations of CFG-based representations in handling structural ambiguity.

**Answer:** Recursion in CFGs enables nested constructions by allowing non-terminals to appear in their own expansions (directly or indirectly), such as NP → NP PP allowing "the cat on the mat in the house" to embed prepositional phrases indefinitely, or S → S Conj S enabling coordinate structures like "John ran and Mary walked and Tom jumped" with arbitrary depth—this recursive capacity captures the creative, unbounded nature of language where finite rules generate infinite sentences. However, CFG-based representations struggle with structural ambiguity because a single sentence can have multiple valid parse trees (e.g., "I saw the man with the telescope" where the PP "with the telescope" can attach to either the VP or the inner NP), and standard CFGs provide no principled mechanism to rank these alternatives without augmentation through probabilistic weighting (PCFGs), lexical preferences, or semantic constraints, making disambiguation require external information beyond the context-free formalism itself, which treats all derivations satisfying the grammar as equally valid regardless of plausibility or meaning.

#### Question 2: Structural Ambiguity and Parsing Decisions

- **(A)** Describe at least two sources of structural ambiguity (e.g., prepositional phrase attachment, coordination scope) and explain why syntactic parsing must resolve them for accurate interpretation.

**Answer:** Two major sources of structural ambiguity are prepositional phrase (PP) attachment and coordination scope. PP attachment ambiguity occurs when a prepositional phrase can modify multiple constituents, as in "I saw the man with the telescope" where "with the telescope" can attach to either the verb phrase (I used a telescope to see) or the noun phrase (the man possessed a telescope). Coordination scope ambiguity arises when conjunctions like "and" or "or" can group constituents in multiple ways, such as "old men and women" which could mean "[old men] and [women]" or "old [men and women]". Syntactic parsing must resolve these ambiguities because different structural interpretations lead to fundamentally different semantic meanings—failing to choose the correct attachment or coordination scope results in misunderstanding speaker intent, incorrect semantic role assignment, and downstream errors in applications like machine translation, question answering, and information extraction where accurate meaning representation is critical.

- **(B)** Compare how phrase structure grammar and dependency grammar represent ambiguous constructions and discuss implications for computational parsing.

Phrase structure grammar represents ambiguous constructions through multiple distinct parse trees with different hierarchical bracketings—for "I saw the man with the telescope," one tree attaches the PP to VP while another attaches it to NP, explicitly encoding structural alternatives through different constituent arrangements. Dependency grammar represents the same ambiguity through different head-dependent relations—the preposition "with" can depend on either "saw" (verb attachment) or "man" (noun attachment)—creating competing dependency arcs rather than competing tree structures. For computational parsing, this distinction has significant implications: phrase structure parsers must search through exponentially many tree configurations and require disambiguation mechanisms like probabilistic scoring (PCFGs) to rank alternatives, while dependency parsers can leverage more efficient graph-based or transition-based algorithms that directly predict head-dependent relations, often achieving better computational complexity (O(n³) for many dependency parsers vs. higher complexity for exhaustive phrase structure parsing) and making them more practical for large-scale applications, though phrase structure representations may better capture certain linguistic phenomena like discontinuous constituents and explicit phrase boundaries.

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

---
