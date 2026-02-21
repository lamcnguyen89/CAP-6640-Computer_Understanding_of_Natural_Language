Lecture 4: Learning and Evaluating Word Representations: Optimization, Negative Sampling, and Sense Ambiguity
This lecture extends the Word2Vec framework by examining optimization in greater depth, introducing skip-gram with negative sampling, and contrasting predictive embedding methods with count-based representations. It further explores how word meaning is encoded, the challenges posed by word sense ambiguity, and the principled evaluation of word embeddings.

Together, these topics refine the understanding of word embeddings as optimization-driven representations and clarify how their quality and limitations are assessed in practice.

Key Point: Advanced embedding methods balance computational efficiency, representational power, and evaluability.
Gradient Descent, Revisited
Gradient descent is a general optimization algorithm for minimizing a differentiable objective function f(x). At each iteration, parameters are updated by moving in the direction of the negative gradient. For example, given f(x) = x² with derivative f′(x) = 2x, an initial value x = 4 and learning rate α = 0.1 produce the update x ← 4 − 0.1·8 = 3.2. Repeating this process iteratively drives the parameter toward a local minimum.

In embedding learning, this principle generalizes to high-dimensional parameter vectors. The objective function represents prediction error over word–context pairs, and each update incrementally adjusts word vectors to reduce this error.

Stochastic Gradient Descent
The full Word2Vec objective J(θ) depends on all context windows in the corpus, which may number in the billions. Computing exact gradients over the entire dataset before each update is computationally infeasible.

Stochastic Gradient Descent (SGD) resolves this by approximating the gradient using a single context window or a small subset of data at a time. Each update is noisy but efficient, enabling frequent parameter updates and scalable learning across massive corpora.

Skip-Gram with Negative Sampling
The standard skip-gram model relies on softmax normalization over the entire vocabulary, which is expensive for large vocabularies. Skip-gram with negative sampling replaces this multiclass prediction with a set of binary classification problems.

For each observed (center, context) pair, the model treats it as a positive example and samples k random “noise” words to form negative examples. The training objective maximizes the probability that true context words are classified as real while random word pairs are classified as noise.

Key Point: Negative sampling avoids full softmax computation while preserving semantic learning.
Window-Based Representations
Skip-gram models rely on window-based context definitions. Given a symmetric window of fixed length, words appearing near the target word—regardless of left or right position—are treated as context. This approach captures both syntactic and semantic relationships.

Window-based co-occurrence differs from document-level co-occurrence. While document-level matrices tend to encode topical similarity, window-based representations emphasize functional and contextual similarity, which is more suitable for embedding learning.

Count-Based Representations and Dimensionality Reduction
Count-based methods construct large word–context co-occurrence matrices, where each entry represents the frequency with which a word appears near a context word. These matrices are high-dimensional, sparse, and computationally expensive to store and process.

Dimensionality reduction techniques such as Singular Value Decomposition (SVD) factor the matrix X into UΣVᵀ and retain only the top k singular values. This produces dense, low-dimensional representations that capture the most salient co-occurrence patterns. However, computing SVD at scale is expensive.

Count-Based vs. Direct Prediction Methods
Count-Based	Direct Prediction
Efficient use of global statistics	Efficient training with local context
Primarily capture word similarity	Capture complex semantic patterns
High importance of large counts	Better performance on downstream tasks
Direct prediction methods such as Word2Vec learn embeddings by optimizing predictive objectives, whereas count-based methods rely on matrix factorization. Both approaches encode distributional information, but differ in efficiency and expressiveness.

Encoding Meaning through Co-occurrence Ratios
Meaning can be encoded through ratios of co-occurrence probabilities. Certain semantic components emerge when relative co-occurrence patterns are preserved rather than absolute frequencies. This insight motivates embedding methods that implicitly encode relational meaning in vector space geometry.

Evaluating Word Vectors
Evaluating word embeddings requires distinguishing between intrinsic and extrinsic evaluation. Intrinsic evaluation measures embedding quality on standalone tasks, while extrinsic evaluation measures impact on real NLP applications.

Intrinsic Evaluation
Intrinsic evaluation focuses on tasks such as word similarity, analogy resolution, and clustering. Similarity is often measured by comparing cosine similarity of embeddings against human judgments. Analogy tasks test linear relationships in embedding space.

These evaluations are fast and interpretable but may not correlate with downstream performance.

Extrinsic Evaluation
Extrinsic evaluation measures embedding utility in full NLP systems such as text classification, named entity recognition, machine translation, and question answering. Performance improvements indicate embedding usefulness.

These evaluations are computationally expensive and task-dependent but provide the strongest evidence of practical value.

Word Sense and Ambiguity
Many words have multiple meanings, creating ambiguity. Traditional static embeddings assign a single vector per word, conflating all senses into one representation. This can blur semantic distinctions.

Contextual embedding models address this by generating different vectors for the same word depending on context, dynamically resolving ambiguity during inference.

Global Context Solutions
Several approaches incorporate broader context to improve meaning representation. Attention mechanisms allow models to focus on relevant words across a sequence. Contextual embeddings use entire sentences to generate word representations, while topic models capture document-level themes.

Another approach clusters word contexts and assigns multiple representations to a single word, enabling finer-grained sense modeling.

Lecture Takeaway
Advanced embedding techniques refine both how word vectors are learned and how they are evaluated. By addressing computational efficiency, ambiguity, and evaluation rigor, these methods clarify the strengths and limitations of word embeddings as foundational representations in NLP.

