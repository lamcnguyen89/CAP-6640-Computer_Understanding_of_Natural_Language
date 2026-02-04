Lecture 6: Training Neural NLP Models: Max-Margin Learning, Embedding Fine-Tuning, and Backpropagation
This lecture formalizes how neural models are trained for NLP tasks by defining classification objectives, scoring functions, and gradient-based optimization procedures. The lecture is grounded in a concrete binary classification task for Named Entity Recognition (NER), focusing on identifying location entities using fixed context windows and neural scoring models.

Rather than introducing new architectures, the lecture emphasizes how learning emerges from the interaction between window construction, unnormalized neural scores, margin-based loss functions, and backpropagation. Each component is introduced operationally and illustrated through worked examples.

Key Point: Neural NLP models are defined by how they score linguistic contexts and how those scores are optimized, not just by network architecture.
Lecture Objectives
Rerun binary classification for NER (location entities)
Apply neural scoring to context windows
Rerun the max-margin loss algorithm
Understand pitfalls of retraining word vectors
Explain backpropagation using computational graphs
Work through a complete backpropagation example
Binary Classification for NER Location
The lecture frames Named Entity Recognition as a binary classification problem over fixed-size context windows. Each window is centered on a target word, and the model predicts whether that word is a location entity.

Using sentence variations such as:

Not all museums in Paris are amazing.
All museums in Paris are amazing.
Not all museums in Paris.
the lecture demonstrates how interpretation depends critically on the surrounding context of the word “museums”.

Different context windows lead to different semantic signals:

["Not", "all"]: suggests limitation or negativity
["All", "amazing"]: implies positivity or universality
["Not", "museums", "in"]: incomplete and ambiguous
Key Point: The choice of context window directly affects semantic interpretation and classification outcomes.
Neural Scoring with Feed-Forward Networks
Each context window is assigned an unnormalized score using a feed-forward artificial neural network. The network uses neural activations solely to produce a scalar score, not a probability.

Operationally, the model computes:

s = score("museum in Paris is amazing")

The scoring function is implemented using a 3-layer neural network. The score represents how compatible the window is with the target class.

Max-Margin Loss Function
To improve classification, the lecture introduces a max-margin objective. The goal is to increase the score of a true context window while decreasing the score of a corrupted one.

Let:

S = score("museum in Paris are amazing")
Sc = score("not all museums in Paris")
The loss function is defined as:

J = max(0, 1 − S + Sc)

This enforces that the true window score must exceed the corrupted window score by at least 1. Optimization is performed using stochastic gradient descent (SGD), and parameters are updated only when the margin constraint is violated.

Key Point: Learning occurs only when true and corrupted contexts are insufficiently separated.
Corrupted Context Windows
Each true context window containing a location entity is paired with multiple corrupted windows that either remove the entity or alter the context.

The training objective requires that every true window score be at least +1 higher than any corrupted window. This forces the model to learn discriminative features specific to valid entity contexts.

Pitfalls of Retraining Word Vectors
The lecture examines the consequences of updating word embeddings during task training through a sentiment classification example.

Training data contains: “TV”, “telly”
Test data contains: “television”
Pre-trained word vectors encode semantic similarity among all three terms. However, during training:

Words seen in training are updated and shift in vector space
Unseen words retain their original embeddings
This creates a mismatch between seen and unseen words at test time.

Guidelines provided in the lecture:

Use pre-trained word vectors: almost always yes
Small datasets: do not fine-tune embeddings
Large datasets: fine-tuning may improve performance
Backpropagation as a Graph
Neural networks are presented as computational graphs:

Source nodes represent inputs
Interior nodes represent operations
Edges carry computed values
Forward propagation computes outputs, while backpropagation traverses the graph backwards, passing gradients along edges to minimize error.

Backpropagation: Single Node
Each node in the graph:

Receives an upstream gradient
Computes a local gradient (output w.r.t. input)
Passes a downstream gradient computed as:
downstream gradient = upstream gradient × local gradient

Activation functions are applied element-wise, and gradients are computed in matrix form.

Backpropagation: Worked Example
The lecture concludes with a complete numerical backpropagation example using:

Two input features
One hidden layer with sigmoid activation
Mean Squared Error (MSE) loss
The example walks through:

Forward computation of activations
Loss calculation
Gradient computation using the chain rule
Weight updates via gradient descent
This step-by-step derivation illustrates how abstract gradient rules translate into concrete parameter updates.

Lecture Takeaway
This lecture establishes training and optimization as the operational core of neural NLP models. By grounding learning in explicit scoring functions, margin-based objectives, and backpropagation, it shows how linguistic distinctions emerge from systematic optimization over structured contexts.