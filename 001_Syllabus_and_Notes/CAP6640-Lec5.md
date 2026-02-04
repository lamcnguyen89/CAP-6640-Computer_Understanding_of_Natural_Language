Lecture 5: Neural Network Classifiers and Sequence Labeling for NLP
Lecture 5: Neural Training and Optimization for NLP
This lecture formalizes how neural networks are trained to perform structured NLP tasks by defining scoring functions, learning objectives, and gradient-based optimization procedures. Rather than treating neural models as black boxes, the lecture develops a precise computational view of how linguistic contexts are mapped to numerical scores, how correct and incorrect structures are distinguished, and how model parameters are updated through backpropagation.

The lecture uses Named Entity Recognition (NER) as a concrete case study to show how local linguistic context can be operationalized using fixed-size windows, how classification can be framed as a margin-based learning problem, and how backpropagation enables end-to-end optimization. By the end of the lecture, neural NLP models are understood not merely as architectures, but as explicit optimization systems defined by objectives, constraints, and gradients.

Key Point: Neural NLP models learn by optimizing explicit scoring objectives over structured linguistic contexts using gradient-based methods.
Lecture Objectives
Explain how NLP tasks can be formulated as window-based classification problems
Describe neural scoring functions for linguistic contexts
Explain max-margin loss functions and corrupted example construction
Analyze how gradients flow through multi-layer neural networks
Apply backpropagation to compute parameter updates
Explain optimization using stochastic gradient descent
Identify risks associated with retraining word embeddings
Window-Based Formulation of NLP Tasks
Many core NLP tasks can be reduced to deciding whether a specific property holds for a word given its local context. In window-based models, a target word at position t is paired with a fixed-size context window of surrounding words:

(wt−k, …, wt−1, wt, wt+1, …, wt+k)

This window defines the model’s entire input for classification. For NER, the task becomes: given a context window centered at wt, determine whether the center word corresponds to a named entity of a particular type (e.g., LOCATION).

This formulation enforces a key modeling assumption: meaning is locally compositional. The semantic interpretation of the target word depends on its immediate neighbors, not on the full sentence. While approximate, this assumption enables efficient computation and tractable learning.

Key Point: Window-based models encode linguistic context explicitly and reduce NLP tasks to local classification problems.
Neural Scoring Functions
Instead of directly predicting probabilities, window-based neural models first compute an unnormalized score for each input window. Given word embeddings for the words in the window, the embeddings are concatenated and passed through a feed-forward neural network:

s = f(W · x + b)

where x is the concatenated embedding vector, W and b are learnable parameters, and f is a non-linear activation function. The output s is a scalar compatibility score indicating how well the window matches the target class.

Crucially, this score has no probabilistic interpretation on its own. It is a relative measure used only for comparison between competing windows.

Max-Margin Learning Objective
Rather than modeling probabilities, the lecture introduces a max-margin objective designed to separate correct contexts from incorrect ones. For each true context window w, the model samples one or more corrupted windows w′ that are similar but incorrect (e.g., missing the entity).

Let S be the score of the true window and Sc the score of a corrupted window. The hinge loss is defined as:

J = max(0, 1 − S + Sc)

This objective enforces a margin of at least 1 between correct and incorrect windows. Updates occur only when the margin constraint is violated. As a result, learning focuses on difficult or ambiguous examples rather than well-separated cases.

Key Point: Margin-based learning enforces relative correctness rather than absolute probability estimates.
Negative Sampling via Corrupted Windows
Corrupted windows act as implicit negative examples. They are constructed by modifying the true context in minimal ways, such as removing the entity word or replacing it with a non-entity. This strategy ensures that the model learns fine-grained distinctions rather than trivial patterns.

Sampling corrupted contexts reduces computational cost while maintaining strong discriminative pressure during training.

Optimization with Stochastic Gradient Descent
The training objective is minimized using stochastic gradient descent (SGD). Rather than computing gradients over the full dataset, updates are performed per window or per mini-batch:

Forward pass: compute scores and loss
Backward pass: compute gradients of the loss
Parameter update: apply SGD step
SGD enables scalable training and allows models to adapt continuously as new examples are observed.

Backpropagation as a Computational Graph
Neural networks are represented as directed acyclic graphs where nodes correspond to operations and edges carry values. During backpropagation:

Each node receives an upstream gradient
The node computes a local gradient
The downstream gradient is their product
This modular view enables systematic gradient computation regardless of network depth.

Worked Backpropagation Example
The lecture walks through a full numerical example involving a multi-layer network with sigmoid activations. The example explicitly computes:

Forward activations for hidden and output layers
Loss using Mean Squared Error
Gradients with respect to weights and biases
Parameter updates using a fixed learning rate
This example concretizes abstract gradient rules and demonstrates how learning emerges from repeated local updates.

Pitfalls of Retraining Word Embeddings
The lecture concludes by analyzing the effect of fine-tuning word embeddings during task training. Words observed during training are updated, while unseen words retain their original representations. This can distort semantic relationships learned during pretraining.

Small datasets: fine-tuning risks overfitting and semantic drift
Large datasets: fine-tuning can improve task alignment
Key Point: Embedding updates trade off task specialization against global semantic consistency.
Lecture Takeaway
This lecture establishes optimization as the central mechanism behind neural NLP models. Scoring functions, margin-based objectives, and backpropagation together define how linguistic structure is learned from data. These principles recur throughout sequence modeling, parsing, and modern language models.

