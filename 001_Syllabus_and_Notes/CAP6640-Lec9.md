Lecture 9: Recurrent Language Models: RNNs, LSTMs, GRUs, and Evaluation
This lecture introduces recurrent neural networks (RNNs) as a foundational architecture for modeling sequential data in Natural Language Processing. The lecture formalizes how language modeling differs from fixed-window approaches by explicitly representing temporal dependencies across arbitrarily long contexts. Unlike feedforward models, RNNs maintain an internal hidden state that evolves over time, allowing predictions to depend jointly on current input and past history.

The lecture develops RNN-based language models from first principles, contrasting them with fixed-window language models and standard feedforward neural networks. It explains how recurrence introduces memory, why this improves modeling power for text, and why training becomes more complex. The lecture then examines the mathematical and algorithmic challenges that arise when optimizing RNNs, setting the stage for later architectural extensions.

Key Point: Recurrent language models explicitly encode temporal dependence by propagating hidden state information across time steps.
Lecture Objectives
Explain the limitations of fixed-window language models
Describe how recurrence enables sequence modeling
Differentiate between feedforward networks and RNNs
Explain how RNNs model conditional word probabilities
Describe how RNN-based language models generate text
Explain why training RNNs is computationally challenging
Fixed-Window Language Models
Fixed-window language models estimate the probability of a word given a limited number of preceding words. Formally, the probability of the next word depends on a fixed-size context window, regardless of how long the sentence is. This design simplifies computation but fundamentally restricts the model’s ability to capture long-range dependencies.

As a result, information outside the window is irretrievably discarded. Even if earlier words are crucial for interpretation, the model cannot condition on them once they fall outside the window. This motivates architectures that can retain information over arbitrarily long sequences.

ANN vs. RNN Architectures
Feedforward artificial neural networks (ANNs) process inputs independently, assuming no ordering or temporal structure. Each input produces an output without reference to prior inputs. This makes ANNs suitable for static tasks such as image classification but poorly suited for language.

Recurrent neural networks introduce directed cycles that allow information to persist across time. At each timestep t, the hidden state h(t) is computed as a function of both the current input and the previous hidden state h(t−1). This recurrence provides the model with memory and context awareness.

Key Point: RNNs differ from ANNs by allowing outputs to depend on past inputs through hidden-state recurrence.
RNN-Based Language Modeling
An RNN language model defines the probability of a word sequence by factorizing it into conditional probabilities, where each probability depends on the entire preceding sequence summarized by the hidden state. The hidden state serves as a compressed representation of all prior context.

At each timestep, the model embeds the input word, updates the hidden state, computes a score over the vocabulary, and applies a decoding mechanism to obtain a probability distribution for the next word. During generation, the predicted word is fed back as input for the next step.

Training RNN Language Models
Training an RNN language model involves minimizing the negative log-likelihood of observed sequences. Computing gradients across entire corpora is computationally infeasible, so training is performed on sentences or mini-batches using stochastic gradient descent.

Because parameters are reused at every timestep, gradients must account for repeated applications of the same weights. This leads to a specialized training algorithm known as Backpropagation Through Time (BPTT), which accumulates gradients across all timesteps where a parameter appears.

Backpropagation Through Time
In BPTT, the RNN is conceptually unrolled across time, converting the recurrent structure into a deep feedforward computation graph. Gradients are computed by summing contributions from each timestep in reverse order.

This procedure enables learning temporal dependencies but introduces numerical instabilities and long-range gradient propagation issues. These challenges motivate later architectural refinements.

RNNs for Text Generation
RNN language models can be used for natural language generation by repeatedly sampling from the predicted distribution and feeding the sampled output back into the model. This autoregressive loop allows the model to generate sequences of arbitrary length.

Such models underpin applications including predictive text, dialogue systems, and story generation, but they are sensitive to training quality and long-distance dependencies.

Lecture Takeaway
Recurrent language models extend fixed-window approaches by introducing memory through hidden-state recurrence. This enables principled modeling of sequential structure in language but also introduces significant optimization challenges that motivate more advanced recurrent architectures.

