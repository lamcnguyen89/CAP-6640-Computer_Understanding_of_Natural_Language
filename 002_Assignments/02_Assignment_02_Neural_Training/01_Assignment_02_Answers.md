# Assignment 2: Neural Training, Optimization, and Parsing

This assignment examines how neural models are trained for NLP tasks and how syntactic structure is formally represented and computed. All questions are based strictly on the material covered in Lectures 5, 6, and 7. Each question consists of two parts and requires precise, technically grounded answers.

This is an individual assignment. Clarity, correctness, and depth of reasoning are expected.

## Requirements

Unlimited Attempts Allowed
Available: Jan 13, 2026 12:00am until Feb 11, 2026 11:59pm1/13/2026 to 2/11/2026

**Submission Guidelines**
Submit a single PDF document
Clearly label each question and part (A, B)
Answers should be concise, technical, and well-structured
Do not include material beyond Lectures 5–7
Each question is worth 5 pts (total: 40 pts)
Choose a submission type

## Questions

**Question 1: Window-Based NER Classification (Lecture 5)**
(A) Explain how Named Entity Recognition (NER) for location entities is formulated as a binary classification problem using fixed-size context windows.

**Answer:** Named Entity Recognition for location entities is formulated as a binary classification problem by treating each word in context as a candidate entity and predicting whether it belongs to the LOCATION class. A fixed-size context window of k words before and after the target word at position t is constructed: (w*{t-k}, ..., w*{t-1}, w*t, w*{t+1}, ..., w\_{t+k}). This window defines the complete input for classification. The task reduces to: given this context window centered at w_t, determine whether the center word is a location entity. This formulation enforces a local assumption that the semantic interpretation of the target word depends primarily on its immediate neighbors rather than the full sentence, enabling efficient learning/compute.

(B) Using the sentence examples discussed in Lecture 5, explain how changing the content of a context window alters the semantic interpretation of the center word.

**Answer:** The lecture demonstrates context window effects using different sentences about "museums":

- "Not all museums in Paris are amazing."
- "All museums in Paris are amazing."
- "Not all museums in Paris."

Different context windows produce distinct semantic signals:

- ["Not", "all"]: suggests limitation or negativity
- ["All", "amazing"]: implies positivity or universality
- ["Not", "museums", "in"]: incomplete and ambiguous

The same center word "museums" receives different interpretations depending on which neighboring words are included in the fixed window. This illustrates that window content directly affects the semantic features available to the classifier changing how the model interprets and classifies the center word.

**Question 2: Neural Scoring Functions (Lecture 5)**
(A) Describe how a feed-forward neural network is used to compute an unnormalized score for a context window.

**Answer:** A feed-forward neural network computes an unnormalized score for a context window through the following process: First, word embeddings for all words in the context window are retrieved and combined into a single vector x. This combined vector is then passed through the network layers using the function s = f(W · x + b), where W represents learnable weight parameters, b is a bias term, and f is a non-linear activation function. The output s is a scalar compatibility score that shows how well the input window matches the target class (e.g., location entity). This architecture uses neural activations to produce a scalar value representing the window's compatibility with the classification objective.

(B) Explain why these scores are not probabilities and how they are used comparatively during training.

**Answer:** These scores are not probabilities because they are not normalized and lack a probabilistic interpretation on their own and can take any real value without being constrained to the [0,1] range or summing to 1 across classes. Instead, scores serve as relative measures used only for comparison between competing windows. During training, the model compares the score S of a true (correct) context window against the score S_c of a corrupted (incorrect) window. The learning objective enforces that true windows should score higher than corrupted ones by at least a specified margin. This means that absolute score values do not matter; only the relative ordering matters for discriminating between correct and incorrect linguistic contexts.

**Question 3: Max-Margin Loss and Corrupted Windows (Lecture 5)**
(A) Formally describe the max-margin loss function used in Lecture 5, including the roles of the true window score and the corrupted window score.

**Answer:** The max-margin loss function:

J = max(0, 1 - S + S_c)

where S is the score of the true context window (containing the correct entity) and S_c is the score of a corrupted window (modified to be incorrect, such as by removing the entity or altering context). The true window score S should be high, showing compatibility with the target class, while the corrupted window score S_c should be low. The objective enforces a margin of at least 1 between these scores, meaning S must exceed S_c by at least 1. When this margin constraint is satisfied (S ≥ S_c + 1), the loss is zero. When violated (S < S_c + 1), the loss is positive and proportional to the violation degree, triggering parameter updates.

(B) Explain why model parameters are updated only when the margin constraint is violated and how this focuses learning.

**Answer:** Model parameters are updated only when the margin constraint is violated (i.e., when S < S_c + 1) because the hinge loss function produces zero gradient when the constraint is satisfied. When the true window already scores higher than the corrupted window, no learning signal is created. This design focuses learning on examples where the model fails to adequately separate correct from incorrect contexts. Instead of wasting compute on well-separated, easy examples, the model concentrates updates on cases where discrimination is weak. This selective updating improves training efficiency and helps the model learn fine-grained distinctions for accurate classification.

**Question 4: Retraining Word Vectors Pitfall (Lecture 5)**
(A) Using the “TV / telly / television” example, explain what happens to word representations when embeddings are updated during training.

**Answer:** In the "TV / telly / television" example, the training data contains only "TV" and "telly", while "television" appears only at test time. Pre-trained word embeddings initially encode semantic similarity among all three terms, placing them close in vector space. However, during task-specific training with embedding fine-tuning, the embeddings for "TV" and "telly" are updated through backpropagation to optimize task performance. These words shift in vector space to better fit the training objective. Meanwhile, "television" keeps its original pre-trained embedding since it never appears in the training data and therefore receives no gradient updates. This creates semantic drift where words seen during training move away from their original positions while unseen but semantically related words remain in the same place.

(B) Explain why this behavior creates a mismatch between training and testing, and why small datasets exacerbate the problem.

**Answer:** This behavior creates a train-test mismatch because the semantic relationships encoded in pre-trained embeddings become inconsistent: updated words occupy different parts of the vector space than their unseen synonyms. At test time, the model encounters a word with its original embedding, which no longer aligns with the fine-tuned representations of semantically similar words. This breaks the semantic coherence that the model relies on for generalization. Small datasets increase this problem because: (1) they provide a limited size corpus, increasing the chances that test words are unseen during training, and (2) updates based on few examples often overfit, causing larger semantic drift that destroys the global consistency learned during pre-training. The lecture recommends not fine-tuning embeddings on small datasets to preserve semantic structure.

**Question 5: Backpropagation and Computational Graphs (Lecture 6)**
(A) Explain how a neural network can be represented as a computational graph, identifying the roles of source nodes, intermediate nodes, and edges.

**Answer:** A neural network is represented as a directed acyclic computational graph where:

- **Source nodes** represent inputs (features, embeddings, or raw data) that initiate the computation
- **Intermediate nodes** represent operations or transformations (matrix multiplications, activation functions, addition of bias terms) that process values flowing through the network
- **Edges** carry computed values (activations, intermediate results) between nodes during the forward pass and gradients during the backward pass

The graph structure mirrors the network architecture, with information flowing from inputs through hidden layers to outputs during forward propagation. This representation makes the computational dependencies explicit and provides a framework for computing gradients. Each edge tracks both the forward value and the backward gradient, enabling modular computating that can scale with the number of layers in the model.

(B) Explain how gradients are propagated through this graph during backpropagation, distinguishing between local gradients and upstream gradients.

**Answer:** During backpropagation, gradients are propagated backwards through the computational graph from the loss toward the inputs. At each node, two types of gradients interact:

- **Local gradient**: the derivative of the node's output with respect to its input shows how sensitive the node's operation is to changes in its input (such as the derivative of sigmoid activation)
- **Upstream gradient**: the gradient flowing backward from later layers, representing how sensitive the final loss is to changes in the node's output

The **downstream gradient** (passed to earlier layers) is computed as the product:

downstream gradient = upstream gradient × local gradient

This application of the chain rule enables systematic gradient computation. Each node receives an upstream gradient, computes its local gradient, multiplies them together, and passes the result to its predecessors. This modular multiplication propagates error information from the loss back to all parameters, enabling gradient-based optimization.

**Question 6: Gradient Computation and Learning Dynamics (Lecture 6)**
(A) Explain how the chain rule is applied at a single node during backpropagation to compute gradients with respect to model parameters.

**Answer:** At a single node during backpropagation, the chain rule is applied to decompose the gradient of the loss with respect to the node's parameters into manageable components. Consider a node computing y = f(W·x + b) where W and b are parameters. To compute ∂L/∂W (gradient of loss L with respect to weights W):

1. The node receives the upstream gradient ∂L/∂y from later layers
2. The node computes the local gradient ∂y/∂(W·x+b) based on the activation function f
3. The node computes ∂(W·x+b)/∂W = x (how the weighted sum changes with W)
4. By the chain rule: ∂L/∂W = (∂L/∂y) × (∂y/∂(W·x+b)) × (∂(W·x+b)/∂W)

This multiplicative decomposition allows each node to compute parameter gradients using only local information ( such as the input x, the activation derivative) and the upstream gradient, without needing to know the full network structure.

(B) Explain why backpropagation proceeds in the reverse direction of the forward pass and how this enables error minimization.

**Answer:** Backpropagation proceeds in reverse direction because gradient computation requires values from later layers to compute gradients for earlier layers—this is a dependency imposed by the chain rule. The loss is computed at the output layer. To determine how each parameter affects the loss, we trace the error signal backward through all operations that depend on that parameter. Moving forward would not provide the necessary upstream gradients.

This reverse propagation enables error minimization through the following mechanism:

1. The loss quantifies prediction error at the output
2. Backpropagation computes how each parameter contributes to this error (gradients)
3. Parameters are updated in the direction opposite to their gradients (gradient descent)
4. This systematically reduces the loss by adjusting parameters to minimize error

The reverse flow ensures that every parameter receives a gradient signal proportional to its contribution to the total error, enabling coordinated optimization of all layers simultaneously.

**Question 7: Phrase Structure and Structural Ambiguity (Lecture 7)**
(A) Define phrase structure and explain how hierarchical organization gives rise to multiple valid syntactic interpretations.

**Answer:** Phrase structure refers to the hierarchical organization of words into nested phrases that form larger units within a sentence. Words combine to form phrases based oncategories (such as noun phrases, verb phrases, prepositional phrases), and phrases themselves can combine into larger phrases. This nested structure encodes grammar relationships beyond simple word order.

Hierarchical organization gives rise to multiple valid syntactic interpretations because phrases can be grouped and attached in different ways while still forming grammatically correct structures. The hierarchical nature means that the same sequence of words can be bracketed differently, creating distinct phrase structures. Each valid bracketing represents a different syntactic interpretation, and without additional context, grammar rules alone cannot determine which interpretation is intended. The recursive properties of phrase structure multiply the possible ways to organize constituents, leading to sentence ambiguity.

(B) Using prepositional phrase attachment as an example, explain what structural ambiguity is and why it poses challenges for parsing.

**Answer:** Structural ambiguity occurs when a sentence has multiple valid syntactic structures, each corresponding to a different interpretation. Prepositional phrase ambiguity is illustrated by:

"The boy saw the man with the telescope"

This sentence has two valid interpretations:

1. the man possesses the telescope
2. the boy used the telescope to see

This poses challenges for parsing because:

1. Grammar rules alone cannot resolve the ambiguity—both structures are syntactically legal
2. Parsers must choose one structure or represent multiple possibilities
3. Incorrect attachment leads to misinterpretation of meaning
4. Resolution requires semantic knowledge, world knowledge, or statistical preferences beyond pure syntax
5. The number of possible attachments grows with sentence length, increasing compute requirements

**Question 8: Dependency Grammar and Neural Parsing (Lecture 7)**
(A) Describe dependency grammar and explain how syntactic structure is represented as a dependency tree.

**Answer:** Dependency grammar models syntactic structure as a set of binary, asymmetric relations between words called dependencies. Rather than grouping words into phrases, dependency grammar focuses on direct word-to-word relationships. Each dependency connects a head word (governor) to a dependent word (modifier), with the relationship labeled by grammatical function (e.g., subject, object, modifier).

Syntactic structure is represented as a dependency tree where:

- **Nodes** represent individual words in the sentence
- **Directed edges** represent dependency relations, pointing from head to dependent
- **Edge labels** indicate the grammatical relationship type
- The tree has a single root (typically the main verb)
- Each word (except root) has exactly one incoming edge (head)
- No cycles exist—the structure is a true tree

This representation emphasizes relationships of meaning rather than constituent groupings, making it particularly suitable for languages with flexible word order and computationally efficient for processing.

(B) Explain how deep learning–based parsing differs from rule-based grammar parsing, focusing on the role of annotated treebanks.

**Answer:** Deep learning-based parsing differs from rule-based grammar parsing in how syntactic knowledge is learned and represented:

**Rule-based parsing**:

- Relies on manually crafted grammar rules
- Rules encode linguistic heruistics and theoretical knowledge
- Coverage limited by human-specified rules
- Difficult to handle ambiguity and exceptions

**Deep learning-based parsing**:

- Learns syntactic patterns autonomously from data using neural networks
- Uses continuous vector representations (word embeddings) rather than discrete symbols
- Predictions based on learned statistical patterns rather than explicit rules
- Handles ambiguity through probabilistic scoring

**Role of annotated treebanks**:
Annotated treebanks (large corpora of sentences with gold-standard parse trees):

1. Provide training data—neural models learn by optimizing predictions to match annotated structures
2. Enable data-driven learning that captures actual language usage, including frequency and distributional information
3. Offer broader coverage than heuristic grammar can achieve
4. Supply evaluation benchmarks for measuring parser accuracy
5. Make parsing possible without manual rule engineering

Neural parsers trade hand-crafted language rules for learned patterns from annotated examples. They require large treebanks but achieve more robust and adaptable performance.
