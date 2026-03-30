# Conversational Modeling and Decoding Strategies

These questions examine conversational modeling, conversational question answering, and decoding strategies for language models.

---

## Question 1: Multi-Turn Dialogue Modeling

**Question:** Explain how multi-turn dialogue modeling conditions a response on prior conversational turns. Define the conditional probability objective used for dialogue generation and describe how conversational history is incorporated into the model input.

**Answer:** Multi-turn dialogue modeling generates responses by conditioning on the entire conversational history, ensuring context-aware and coherent replies across multiple exchanges. The conditional probability objective is typically formulated as $P(y_t | x_1, y_1, x_2, y_2, ..., x_t)$, where $y_t$ is the current response and $x_1, y_1, ..., x_t$ represent the previous user utterances and system responses. Conversational history is incorporated by concatenating prior turns as a single sequence input to the model, often separated by special tokens (e.g., [SEP] or [USER]/[SYSTEM] markers), allowing the encoder or decoder to attend to relevant context when generating each token of the response. This approach enables the model to resolve coreferences, maintain topic continuity, and generate contextually appropriate responses that build upon earlier dialogue turns.

---

## Question 2: Dialogue State Tracking

**Question:** Define dialogue state tracking. Describe what constitutes the dialogue state, how it is updated across turns, and how it supports coherent task-oriented dialogue.

**Answer:** Dialogue state tracking (DST) is the process of monitoring and maintaining a structured representation of the user's goals, constraints, and preferences throughout a conversation, particularly in task-oriented dialogue systems. The dialogue state typically consists of slot-value pairs representing domain-specific information (e.g., {destination: "Paris", date: "June 15", hotel_type: "budget"}), along with the current dialogue act and user intent. This state is updated incrementally after each user turn by extracting new information, modifying existing slots, or confirming values through natural language understanding components. DST supports coherent task-oriented dialogue by providing a persistent memory of what has been discussed, enabling the system to track partial information across turns, handle clarifications and corrections, generate contextually relevant system prompts, and ultimately fulfill the user's request by maintaining a complete picture of their requirements throughout the conversation.

---

## Question 3: Conversational Question Answering

**Question:** Define conversational question answering. Explain how conversational history is incorporated to resolve context-dependent questions, including ellipsis and coreference.

**Answer:** Conversational question answering is a task where systems answer a sequence of related questions by leveraging the conversational context, rather than treating each question independently. The system incorporates conversational history by encoding previous question-answer pairs along with the current question and context document, enabling it to resolve anaphoric references (e.g., "What about him?" referring to a person mentioned earlier), handle ellipsis (incomplete questions like "And his age?" that omit the subject), and maintain topic continuity across turns. This is typically implemented by concatenating the dialogue history with the current question as input to a reading comprehension model, or by using explicit coreference resolution and question rewriting modules that transform context-dependent questions into standalone ones by substituting pronouns and completing elliptical phrases based on previous turns, allowing the model to ground references and provide accurate answers even when questions lack explicit context.

---

## Question 4: Extractive vs. Generative Conversational Models

**Question:** Compare extractive and generative approaches to conversational question answering. Describe their architectural differences and explain how their output generation mechanisms differ.

**Answer:** Extractive conversational question answering models identify and extract answer spans directly from a given context document by predicting start and end positions of the answer within the source text, typically using architectures like BERT with span prediction heads that output two distributions over token positions. In contrast, generative conversational models produce answers by generating tokens sequentially using encoder-decoder architectures (like T5 or BART) or decoder-only models (like GPT), where the model learns to synthesize responses token-by-token through autoregressive generation conditioned on the question and context. The key architectural difference lies in the output mechanism: extractive models use classification heads to select existing spans (limiting answers to verbatim text from the document), while generative models use a language modeling head with a vocabulary-sized softmax to produce free-form text, enabling them to paraphrase, summarize, or generate answers not explicitly present in the source, though at the cost of potentially introducing hallucinations or factual errors.

---

## Question 5: Sequence Generation Objective

**Question:** Write and explain the conditional probability objective used for sequence generation. Explain how next-token prediction leads to full sequence generation.

**Answer:** The conditional probability objective for sequence generation is formulated as $P(y|x) = \prod_{t=1}^{T} P(y_t | y_{<t}, x)$, where $x$ is the input sequence (e.g., context or prompt), $y = (y_1, y_2, ..., y_T)$ is the target output sequence, and $y_{<t}$ represents all previously generated tokens. This objective decomposes the probability of generating the entire sequence into a product of conditional probabilities for each token given all previous tokens and the input. During training, the model maximizes this likelihood by learning to predict each token given the ground truth history, while during inference, next-token prediction leads to full sequence generation through autoregressive decoding: the model predicts the first token $y_1$ conditioned on the input $x$, then predicts $y_2$ conditioned on both $x$ and $y_1$, and continues iteratively until a special end-of-sequence token is generated or a maximum length is reached, thereby constructing the complete output sequence one token at a time.

---

## Question 6: Greedy Decoding and Beam Search

**Question:** Describe greedy decoding and beam search. Explain how beam search improves upon greedy decoding and how beam width affects the search process and output selection.

**Answer:** Greedy decoding is the simplest generation strategy where at each timestep the model selects the single highest-probability token according to $\arg\max_{y_t} P(y_t | y_{<t}, x)$, making locally optimal choices without considering future implications, which can lead to suboptimal overall sequences. Beam search improves upon this by maintaining a fixed number of $k$ candidate sequences (the beam width) at each step, expanding each candidate by considering the top tokens, scoring complete partial sequences by their cumulative log-probability, and keeping only the $k$ highest-scoring sequences for the next iteration. The beam width directly controls the exploration-exploitation tradeoff: larger beams (e.g., $k=10$) explore more diverse hypotheses and are more likely to find globally better sequences but require more computation, while smaller beams (e.g., $k=1$, equivalent to greedy) are faster but more prone to local optima; at the end of generation, the sequence with the highest overall probability among the surviving beams is selected as the final output, typically resulting in higher-quality, more coherent text than greedy decoding.

---

## Question 7: Sampling-Based Decoding

**Question:** Explain temperature scaling, top-k sampling, and nucleus (top-p) sampling. Describe how each method modifies the probability distribution during decoding and how this influences output diversity.

**Answer:** Temperature scaling modifies the probability distribution by dividing logits by a temperature parameter $\tau$ before applying softmax: $P(y_t) = \frac{\exp(z_t/\tau)}{\sum_j \exp(z_j/\tau)}$, where higher temperatures ($\tau > 1$) flatten the distribution increasing randomness and diversity, while lower temperatures ($\tau < 1$) sharpen it making high-probability tokens more dominant. Top-k sampling restricts sampling to only the $k$ most probable tokens at each step, setting all other probabilities to zero and renormalizing, which prevents the model from selecting very unlikely tokens while maintaining diversity among the top candidates (though it may include low-probability tokens when the distribution is flat or exclude reasonable options when it's peaked). Nucleus (top-p) sampling dynamically selects the smallest set of tokens whose cumulative probability exceeds threshold $p$ (e.g., 0.9), then samples from this set, adapting the number of candidates based on the model's confidence: when the model is certain, fewer tokens are considered, and when uncertain, more options are included, providing more contextually appropriate diversity control than fixed top-k and generally producing more natural, varied outputs than deterministic methods while avoiding the incoherence of pure random sampling.

---

## Question 8: Decoding and Output Behavior

**Question:** Explain how decoding strategy affects generated output behavior. Discuss its influence on diversity, repetition, and variability in generated text.

**Answer:** The decoding strategy fundamentally shapes the characteristics of generated text by controlling the balance between quality, diversity, and creativity in the output. Deterministic methods like greedy decoding and beam search tend to produce safe, high-probability sequences that are often fluent and coherent but can suffer from repetition (especially in longer texts), generic phrasing, and lack of creativity since they consistently favor the same high-likelihood paths. Sampling-based methods introduce stochasticity that increases output diversity and variability, with higher temperatures or larger top-p values producing more creative and varied text but risking incoherence or factual errors, while lower temperatures or smaller sampling windows maintain quality but reduce novelty. Repetition is particularly affected by the strategy: beam search can create repetition loops when the same n-grams receive high scores repeatedly (often mitigated with repetition penalties), while sampling methods naturally avoid exact repetition through randomness but may still exhibit semantic or structural repetition patterns, making the choice of decoding strategy crucial for matching generation behavior to the specific application requirements, whether prioritizing factual accuracy and consistency (beam search), creative variety (sampling with higher temperature), or a middle ground (nucleus sampling with moderate p values).

---
