Lecture 3: Distributional Semantics and Word Embeddings: Word2Vec and Optimization
This lecture formalizes how meaning is represented computationally in Natural Language Processing. It begins by examining symbolic and one-hot representations of words and explains, at a technical level, why these representations fail to capture semantic similarity. The lecture then develops the distributional hypothesis as a principled alternative and introduces word embeddings as dense, learned representations derived from contextual usage.

The core of the lecture focuses on the Word2Vec framework, detailing its objective function, prediction mechanism, training pipeline, and optimization strategy. By the end of the lecture, word embeddings emerge not as heuristic features, but as the result of a well-defined predictive learning problem optimized over large text corpora.

Key Point: Modern word representations are learned by optimizing predictive objectives over contextual language data.
Lecture Objectives
Explain how one-hot encoding represents words computationally
Analyze why discrete symbolic representations fail to capture similarity
Explain distributional semantics and contextual meaning
Describe how Word2Vec formulates word learning as a prediction task
Explain the role of softmax, loss functions, and gradients in training
Distinguish Skip-Gram and CBOW architectures operationally
Explain why stochastic gradient descent is required for scalability
Usable Meaning in Computers
Early attempts to represent meaning computationally relied on manually curated lexical resources such as WordNet. These resources encode meaning symbolically by organizing words into synonym sets (synsets) and connecting them through predefined semantic relations, most prominently hypernymy and hyponymy. From a linguistic perspective, this structure captures categorical knowledge about words and supports explicit reasoning over lexical relations. However, the semantics are specified declaratively by human experts rather than inferred from data, making the representation external to the learning process itself. From a systems and optimization perspective, symbolic lexical resources fundamentally differ from representations used in modern machine learning. In particular:

No numerical parameterization: Meanings are represented as discrete symbols and graph relations rather than numerical parameters. As a result, there is no vector space in which similarity can be computed using distance or inner products.
No graded similarity: Semantic relations are binary or categorical. A word is either linked to another or not, with no principled way to express degrees of similarity or semantic closeness.
No differentiability: Symbolic relations cannot participate in gradient-based optimization. There is no loss function defined over synsets or edges that can be minimized using gradient descent.
External to learning pipelines: Because the representation is not trainable, it cannot be updated through exposure to data. Any modification requires manual intervention rather than automated parameter updates.
This contrast highlights a fundamental divide between symbolic reasoning and optimization-based learning. Symbolic systems emphasize explicit structure, interpretability, and rule-based inference, but they operate outside the optimization loop that underlies modern machine learning. In contrast, distributional and embedding-based representations treat meaning as a set of parameters learned by minimizing a predictive loss over data. This shift enables continuous adaptation, scalable learning, and seamless integration with neural models, but at the cost of abandoning explicitly encoded symbolic structure. The limitations of symbolic lexical resources thus motivate the transition to numerical, trainable representations of meaning that support similarity computation, optimization, and end-to-end learning.

Words as Discrete Symbols and One-Hot Encoding
In traditional NLP pipelines, words are modeled as discrete, atomic symbols drawn from a fixed vocabulary V of size |V|. One-hot encoding provides a concrete computational realization of this assumption by mapping each word w ∈ V to a vector xw ∈ ℝ|V|, where exactly one component corresponding to w is set to 1 and all other components are 0. Formally, if w is the i-th word in the vocabulary ordering, then xw[i] = 1 and xw[j] = 0 for all j ≠ i.

This representation guarantees uniqueness and simplicity: each word is represented by a distinct basis vector in a |V|-dimensional space. However, this design enforces complete statistical independence between words. For any two distinct words wi and wj, their one-hot vectors are orthogonal, meaning that their dot product satisfies xi · xj = 0 whenever i ≠ j. Consequently, all non-identical words are equally dissimilar under standard similarity measures such as dot product or cosine similarity.

This geometric property has important implications. Because all one-hot vectors lie on the coordinate axes and share no overlapping dimensions, the representation encodes identity but not meaning. Semantically related words such as “hotel” and “motel” are no closer to each other than completely unrelated words such as “hotel” and “quantum.” From an optimization perspective, there is no continuous structure in the space that a learning algorithm can exploit to generalize across words.

Key Point: One-hot encoding represents words as orthogonal basis vectors, which mathematically prevents the expression of similarity or semantic structure.
Why Discrete Representations Fail
The limitations of one-hot representations become evident in downstream tasks such as information retrieval and semantic matching. Consider a query containing the phrase “Seattle motel.” When represented using one-hot vectors, each word is mapped to an orthogonal basis vector in ℝ|V|. As a result, the composite representation of the query shares no overlapping dimensions with a document containing the phrase “Seattle hotel,” even though the two phrases are semantically related. From a geometric perspective, the dot product between the vectors for “motel” and “hotel” is zero, implying complete dissimilarity under standard similarity measures.

This failure is not incidental but structural. Because one-hot representations encode words as independent symbols, similarity cannot emerge through learning or inference. Any notion of semantic relatedness must be injected externally rather than learned from data. A common attempt to address this limitation is to consult synonym lists from lexical resources. However, this approach remains brittle: synonym sets are incomplete, insensitive to context, and incapable of expressing graded similarity. Words are treated as either equivalent or unrelated, with no mechanism to encode that two words may be similar to different degrees depending on usage.

More fundamentally, symbolic synonym substitution operates outside the optimization process. There is no continuous parameter space in which representations can be adjusted based on task-specific loss functions. As a result, systems built on discrete representations cannot generalize beyond explicitly encoded relationships. These limitations motivate a shift toward representations in which similarity is an intrinsic geometric property of the vector space itself, allowing semantic relationships to be learned, compared, and optimized directly from data.

Distributional Semantics
Distributional semantics provides a data-driven definition of meaning by characterizing a word through the linguistic contexts in which it appears. Formally, given a corpus consisting of a sequence of words (w₁, w₂, …, wₜ), the context of a target word wₜ is defined as the set of words that occur within a fixed-size window of radius m around it. That is, the context includes words {wₜ₋ₘ, …, wₜ₋₁, wₜ₊₁, …, wₜ₊ₘ}, excluding the target word itself.

By observing many occurrences of a word across a large corpus, it becomes possible to aggregate contextual information and represent each word as a function of its co-occurrence statistics with other words. Intuitively, words that appear in similar contexts will have similar distributions over neighboring words. This principle, often summarized as “you shall know a word by the company it keeps,” shifts meaning from symbolic definitions to empirically observed usage patterns.

From a computational perspective, distributional semantics induces a geometric structure over words. Each word can be associated with a high-dimensional vector whose components reflect contextual co-occurrence frequencies or learned parameters derived from them. Similarity between words is then defined through vector similarity measures, such as dot product or cosine similarity, rather than symbolic equivalence. As a result, semantic relatedness emerges as a continuous, graded property that can be computed, compared, and optimized.

This framework scales naturally with data and generalizes across vocabularies. As more text is observed, representations are refined automatically without manual intervention. Crucially, meaning is no longer predefined by linguistic rules but learned from data, enabling models to adapt to new domains, evolving language use, and task-specific objectives.

Dense Word Vectors
Word embeddings implement distributional semantics by representing each word w as a dense vector vw ∈ ℝd, where the embedding dimension d is much smaller than the vocabulary size |V|. Unlike one-hot vectors, which occupy a |V|-dimensional space with a single nonzero entry, embeddings lie in a continuous, low-dimensional vector space learned from data.

The learning objective is to place words that occur in similar contexts close to one another in this space. Formally, similarity between words is measured using vector operations such as dot products vw · vw′ or cosine similarity (vw · vw′) / (||vw|| ||vw′||). Semantic and syntactic properties are encoded in a distributed manner across dimensions rather than localized in a single coordinate, allowing similarity to emerge geometrically.

The Word2Vec Framework
Word2Vec formulates word representation learning as a predictive modeling problem over sequences of words. Given a corpus (w₁, w₂, …, wₜ), the model iterates over each position t using a sliding context window of fixed radius m. For each center word wt, the model considers context words wt+j for j ∈ {−m,…,−1,1,…,m}.

Each word is associated with a vector representation, and learning proceeds by predicting context words from a center word (or the reverse). The intuition is that if two words tend to appear in similar contexts, the model must assign them similar vectors in order to make accurate predictions across the corpus.

Objective Function and Prediction Mechanism
The objective of Word2Vec is to maximize the conditional probability of observing a context word given a center word. For a center word c and a context word o, the model defines:

P(o | c) = exp(uo · vc) / Σw∈V exp(uw · vc)

where vc is the vector for the center word and uo is the vector for the context word. This softmax function converts similarity scores into a probability distribution over the vocabulary. The training objective maximizes the log-likelihood of observed word–context pairs, which is equivalent to minimizing a cross-entropy loss.

Key Point: Semantic structure emerges by optimizing predictive likelihood over word–context co-occurrences.
Model Parameters and Training Dynamics
Each word is associated with two distinct vectors: a center (input) vector vw and a context (output) vector uw. This duplication increases model flexibility and simplifies optimization. During training, only the vectors involved in a given context window are updated.

After training converges, the two vectors for each word can be combined (for example, by averaging) to produce a single embedding. The learned vectors encode distributional information implicitly through repeated gradient-based updates driven by prediction errors.

Gradient Descent and Stochastic Optimization
Training Word2Vec requires minimizing a loss function J(θ) over all model parameters θ, which include all word vectors. In principle, computing the full gradient ∇J(θ) over the entire corpus would require processing every word–context pair, which is computationally infeasible for large datasets.

Stochastic Gradient Descent (SGD) addresses this by approximating the gradient using a single context window or a small batch at a time. Parameters are updated after each window, enabling frequent updates, rapid convergence, and scalability to corpora containing billions of tokens.

Skip-Gram and CBOW Architectures
The Skip-Gram and Continuous Bag of Words (CBOW) models differ in how prediction is structured. Skip-Gram predicts each context word independently given a center word, optimizing P(context | center). This formulation is particularly effective for learning representations of infrequent words.

CBOW reverses the direction of prediction by averaging the vectors of surrounding context words and predicting the center word. While computationally more efficient, CBOW emphasizes frequent words and smooths contextual information across the window.

End-to-End Training Pipeline
The training pipeline begins by constructing a vocabulary from the corpus and mapping each word to an index. Context windows are extracted to generate training pairs. One-hot vectors serve as indices into embedding matrices, selecting dense vectors without explicit multiplication.

The selected vectors flow through the prediction function, probabilities are computed via softmax, and the loss is evaluated against observed context words. Backpropagation computes gradients, and SGD updates the embedding matrices iteratively until convergence.

Lecture Takeaway
Word embeddings replace symbolic identity with a learned geometric representation of meaning. By framing word representation as a predictive optimization problem over contextual data, Word2Vec provides a mathematically grounded and computationally scalable foundation for modern NLP systems.

