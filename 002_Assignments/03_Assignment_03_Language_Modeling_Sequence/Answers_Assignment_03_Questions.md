#  Language Modeling and Sequence Learning



## Overview

---

## Questions

### Question 1: Language Modeling Fundamentals (Lecture 8)

**(A)** Define a language model formally and explain how language modeling is framed as a next-word prediction problem.

**Answer:** A language model is a system that assigns probabilities to word sequences and predicts the next word based on prior context. Formally, given a sequence of words x⁽¹⁾, x⁽²⁾, x⁽³⁾, …, x⁽ᵗ⁾, a language model computes a probability distribution over the next word: P(x⁽ᵗ⁺¹⁾ | x⁽¹⁾, x⁽²⁾, …, x⁽ᵗ⁾), where x⁽ᵗ⁺¹⁾ can be any word in the vocabulary V. Language modeling is framed as next-word prediction because the model must predict which word is most likely to follow given the preceding context.

**(B)** Explain how assigning probabilities to entire sentences follows from next-word prediction.

**Answer:** A language model assigns probability to an entire sequence x⁽¹⁾, x⁽²⁾, …, x⁽ᵀ⁾ by factorizing it into a product of conditional probabilities using the chain rule: P(x⁽¹⁾, x⁽²⁾, …, x⁽ᵀ⁾) = P(x⁽¹⁾) · P(x⁽²⁾ | x⁽¹⁾) · P(x⁽³⁾ | x⁽¹⁾, x⁽²⁾) · … · P(x⁽ᵀ⁾ | x⁽¹⁾, …, x⁽ᵀ⁻¹⁾). Each term in this product is a next-word prediction conditioned on all preceding words. By computing these conditional probabilities sequentially and multiplying them together, the model assigns a probability to the complete sentence based on how likely the word order is under natural language usage.

---

### Question 2: N-Gram Language Models (Lecture 8)

**(A)** Explain the n-gram independence assumption and how it simplifies probability estimation.

**Answer:** The n-gram independence assumption states that the next word depends only on the previous n−1 words, not on the entire preceding sequence. This simplifies probability estimation by making P(x⁽ᵗ⁾ | x⁽¹⁾, …, x⁽ᵗ⁻¹⁾) ≈ P(x⁽ᵗ⁾ | x⁽ᵗ⁻ⁿ⁺¹⁾, …, x⁽ᵗ⁻¹⁾). Instead of estimating probabilities over exponentially many possible histories, the model only needs to count occurrences of n-grams in the training corpus and compute probabilities as simple ratios: P(wₙ | w₁, …, wₙ₋₁) = count(w₁, …, wₙ) / count(w₁, …, wₙ₋₁).

**(B)** Using an example, explain how increasing the value of n affects modeling power and data requirements.

**Answer:** Consider predicting the next word after "students opened their". In a bigram model (n=2), the model only sees "their" and might predict common words like "own" or "first". In a 4-gram model (n=4), the model sees "students opened their" and can make more contextually appropriate predictions like "books" or "exams". Increasing n improves modeling power by capturing longer dependencies and more specific contexts. However, it exponentially increases data requirements: for a vocabulary of 10,000 words, bigrams require storing up to 10⁸ entries, while trigrams require 10¹² entries. Many valid longer n-grams never appear in finite training data, leading to severe sparsity problems.

---

### Question 3: Sparsity and Smoothing (Lecture 8)

**(A)** Explain why data sparsity is a fundamental problem in n-gram language models.

**Answer:** Data sparsity is fundamental because as n increases, many valid word sequences never appear in training data, resulting in zero probabilities for unseen n-grams. This occurs due to: (1) finite training data that cannot cover all possible word combinations, (2) rare or novel phrases that are grammatically valid but infrequent, and (3) exponential growth of possible n-grams with vocabulary size and n value. When a model assigns zero probability to an unseen but valid sequence, it fails catastrophically at prediction and generation tasks. This makes n-gram models unreliable for real-world applications where novel combinations are common.

**(B)** Describe smoothing, backoff, or interpolation and explain how these techniques partially address sparsity.

**Answer:** These techniques redistribute probability mass to handle unseen n-grams: **Smoothing** adds small counts to all n-grams (e.g., Laplace smoothing) or uses sophisticated methods like Kneser-Ney smoothing for context-sensitive adjustments, ensuring no n-gram has exactly zero probability. **Backoff** uses lower-order n-grams when higher-order n-grams are unavailable—if a 4-gram wasn't seen, the model backs off to a trigram, bigram, or unigram estimate. **Interpolation** combines multiple n-gram orders by taking a weighted average of probabilities from different n values. These techniques partially address sparsity by ensuring the model can still make predictions for unseen sequences, though they cannot fully overcome the fundamental limitation that count-based models don't generalize beyond exact matches.

---

### Question 4: Fixed-Window Neural Language Models (Lecture 8)

**(A)** Describe how fixed-window neural language models predict the next word using a feedforward network.

**Answer:** Fixed-window neural language models predict the next word by consuming a fixed number of preceding words through a feedforward neural network. The model takes the previous n words, embeds each word into a continuous vector representation, concatenates these embeddings into a single input vector, and passes it through one or more hidden layers. The final layer produces scores over the entire vocabulary, which are converted to probabilities using softmax. The model is trained to maximize the probability of the correct next word. Unlike n-grams that rely on discrete counts, neural models use continuous representations that allow generalization based on similarity between word contexts.

**(B)** Explain why fixed-window neural models still fail to capture long-range dependencies.

**Answer:** Fixed-window neural models fail to capture long-range dependencies because they only consider a fixed number of preceding words, regardless of sentence length. Information outside the window is irretrievably discarded before the prediction is made. Even if earlier words are crucial for understanding (e.g., a subject mentioned at the sentence beginning that determines verb agreement later), the model cannot condition on them once they fall outside the fixed window. This fundamental architectural limitation means that no matter how the window size is chosen, there will always be dependencies that span beyond it, making the model unable to represent arbitrarily long contextual relationships needed for coherent language understanding.

---

### Question 5: Recurrent Language Models (Lecture 9)

**(A)** Explain how recurrent neural networks model sequential dependencies using hidden states.

**Answer:** RNNs model sequential dependencies by maintaining a hidden state h⁽ᵗ⁾ that is updated at each timestep as a function of both the current input x⁽ᵗ⁾ and the previous hidden state h⁽ᵗ⁻¹⁾. This recurrence introduces directed cycles that allow information to persist across time, giving the model memory of past inputs. The hidden state serves as a compressed representation of all prior context in the sequence. At each timestep, the RNN computes h⁽ᵗ⁾ = f(h⁽ᵗ⁻¹⁾, x⁽ᵗ⁾), where f is typically a nonlinear transformation. This design allows the model to condition predictions on the entire preceding sequence (summarized in the hidden state) rather than just a fixed window, enabling it to capture dependencies over arbitrarily long sequences.

**(B)** Explain how an RNN language model generates text autoregressively.

**Answer:** An RNN language model generates text autoregressively by repeatedly predicting the next word and feeding it back as input for the subsequent prediction. The process starts with an initial hidden state and a start token. At each step: (1) the model embeds the current word, (2) updates the hidden state based on this embedding and the previous hidden state, (3) computes scores over the vocabulary, (4) applies softmax to get a probability distribution, and (5) samples or selects the most likely next word. This predicted word is then fed back as input for the next timestep, and the loop continues until an end-of-sequence token is generated. This autoregressive generation allows the model to produce sequences of arbitrary length while maintaining coherence through the evolving hidden state.

---

### Question 6: Training RNNs and Backpropagation Through Time (Lecture 9)

**(A)** Describe backpropagation through time (BPTT) and explain why the RNN must be unrolled during training.

**Answer:** Backpropagation through time (BPTT) is a specialized training algorithm for RNNs that computes gradients by unrolling the recurrent network across time. The RNN must be unrolled because the same parameters are reused at every timestep, and gradients must account for all these repeated applications. Unrolling converts the recurrent structure into a deep feedforward computation graph where each timestep becomes a layer. Gradients are then computed in reverse temporal order, summing contributions from each timestep where a parameter appears. This allows the model to learn how parameter updates affect predictions across the entire sequence, properly attributing credit (or blame) to parameters based on their total impact throughout time.

**(B)** Explain why training RNNs is more challenging than training feedforward neural networks.

**Answer:** Training RNNs is more challenging because: (1) **Temporal dependencies**: Gradients must be propagated backward through many timesteps, creating very deep computation graphs that are numerically unstable. (2) **Vanishing/exploding gradients**: Repeated multiplication of the same weight matrices during backpropagation causes gradients to either vanish (approach zero) or explode (grow exponentially), making it difficult to learn long-range dependencies. (3) **Computational cost**: BPTT requires storing activations for all timesteps and computing gradients across the full sequence, which is memory and time intensive. (4) **Sequential processing**: Unlike feedforward networks where examples are independent, RNNs process sequences sequentially, limiting parallelization opportunities. These factors make RNN optimization require careful tuning of learning rates, gradient clipping, and architectural choices.

---

### Question 7: Vanishing Gradients and Gated Architectures (Lecture 9)

**(A)** Explain the vanishing gradient problem in recurrent neural networks.

**Answer:** The vanishing gradient problem occurs when gradients become exponentially smaller as they are backpropagated through time in RNNs. During BPTT, gradients are computed through repeated multiplication of the weight matrices and derivatives of activation functions. When these multiplied values are less than 1, the gradient shrinks exponentially with the number of timesteps. After propagating backward through many steps, gradients become vanishingly small (approaching zero), making it nearly impossible for the model to learn dependencies between distant timesteps. This prevents RNNs from capturing long-range dependencies because earlier timesteps receive essentially no learning signal, and their contribution to the loss effectively disappears during training.

**(B)** Explain how gated architectures such as LSTMs or GRUs mitigate this problem.

**Answer:** Gated architectures like LSTMs (Long Short-Term Memory) and GRUs (Gated Recurrent Units) mitigate the vanishing gradient problem by introducing gating mechanisms that control information flow through the network. These gates (input, forget, and output gates in LSTMs; reset and update gates in GRUs) learn when to retain, update, or discard information in the hidden state. Crucially, they create additive rather than purely multiplicative paths for gradient flow—for example, LSTM cell states use element-wise addition to incorporate new information, which allows gradients to flow backward through time without repeated multiplication. This additive connection provides a more direct path for gradients, enabling them to propagate across many timesteps without vanishing, which allows the model to learn long-range dependencies that standard RNNs cannot capture.

---

### Question 8: Sequence-to-Sequence Models and Attention (Lecture 10)

**(A)** Explain the encoder–decoder architecture and how sequence-to-sequence models perform conditional generation.

**Answer:** The encoder–decoder architecture consists of two neural components: an **encoder** that processes the variable-length input sequence and produces a representation, and a **decoder** that generates a variable-length output sequence conditioned on that representation. The encoder reads the input sequence word by word, updating its hidden state at each timestep, and after processing the final input token, outputs a context vector summarizing the entire sequence. The decoder uses this context vector to initialize its hidden state and then generates the output sequence autoregressively—functioning as a conditional language model where each prediction depends on previously generated tokens and the encoded input. Formally, the model computes P(y | x) = P(y₁ | x) · P(y₂ | y₁, x) · … · P(yₜ | y₁, …, yₜ₋₁, x), continuing until an end-of-sequence token is produced.

**(B)** Explain why attention mechanisms improve sequence-to-sequence models compared to fixed-length context representations.

**Answer:** Attention mechanisms improve Seq2Seq models by addressing the information bottleneck created by compressing the entire input sequence into a single fixed-length context vector. In basic encoder-decoder models, all input information must pass through this single vector, which becomes inadequate for long sentences as critical details are lost or diluted. Attention allows the decoder to dynamically focus on different parts of the input sequence at each decoding step by computing attention weights over all encoder hidden states and forming a weighted combination that emphasizes relevant input tokens. This gives the decoder selective, direct access to the full input representation rather than relying solely on the compressed context vector. As a result, attention significantly improves performance on long sequences, enables better alignment between input and output, and provides interpretability by showing which input positions the model focuses on when generating each output word.


