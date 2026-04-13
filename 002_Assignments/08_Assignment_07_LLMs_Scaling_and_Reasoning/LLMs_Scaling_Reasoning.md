# Assignment 7: Large Language Models, Scaling, and Reasoning

## Overview

This Assignment examines large language model architectures, scaling behavior, alignment strategies, retrieval integration, and reasoning capabilities.

---

## Question 1: Transformer-Based Large Language Models

Describe the architectural structure of large language models based on the Transformer. Explain the role of self-attention, positional encoding, and stacked layers in enabling long-range dependency modeling.

**Answer:**

Large language models built on the Transformer architecture consist of stacked layers of multi-head self-attention mechanisms and feed-forward networks, with residual connections and layer normalization throughout the layers.

Self-attention allows each token to attend to all other tokens in the sequence, computing weighted combinations based on learned query, key, and value projections. Self-attention enables the model to capture long-range dependencies with no penalty to distance in sequence. Since Transformers lack inherent sequential structure, positional encodings are added to input embeddings to inject info about token positions.

Multiple stacked layers allow the model to build hierarchical representations:

- lower layers capture local patterns and syntactic features
- higher layers capture abstract semantic relationships and long-range discourse structure

This hierarchy of specific to more abstract allows these transformers to capture all levels of texts, images, video, etc...

---

## Question 2: Pretraining Objectives

Explain the autoregressive pretraining objective used in decoder-only large language models. Describe how next-token prediction leads to full sequence modeling and how training differs from inference.

**Answer:**

Decoder-only large language models are pretrained using an autoregressive objective. This means the model learns to predict the next token in a sequence given all previous tokens. This next-token prediction, given enough good data, teaches the model grammar, facts, reasoning patterns, and linguistic structures because accurate prediction requires understanding context, semantics, and patterns in natural language.

During training, the model processes entire sequences in parallel using causal masking to prevent tokens from attending to future positions. The model also computes losses for all positions at the same time using teacher forcing where ground-truth previous tokens are used as input.

During inference, the model generates text autoregressively by sampling or selecting one token at a time. It then feeds its own predictions back as input for subsequent steps. This creates a sequential generation process where errors can compound but can also enable open-ended generation of sequences of varying lengths.

---

## Question 3: Scaling Behavior

Discuss the relationship between model size, training data scale, and performance improvements. Explain why increasing parameters and data can lead to emergent improvements, and describe the limitations of scaling alone.

**Answer:**

Research has demonstrated that language model performance follows predictable scaling laws: loss decreases as a power-law function of model parameters, training data size, and compute budget. Optimal performance requires balanced scaling of both model size and training data rather than increasing just one dimension.

Increasing parameters expands the model's capacity to memorize patterns and represent complex functions. More training data provides diverse examples that improve generalization and reduce overfitting. Together both enable models to capture increasingly wider and deeper linguistic phenomena and world knowledge.

Certain things like few-shot learning, complex reasoning, and instruction following emerge suddenly at specific scale thresholds rather than improving gradually. However, scaling alone has fundamental limitations: it yields diminishing returns as models approach non-removable loss from data noise and ambiguity. It doesn't guarantee factual accuracy or reasoning correctness without alignment techniques. Finally, scaling creates exponential computational and environmental costs, and it cannot overcome inherent architectural limitations or systematic biases present in training data.

---

## Question 4: Advanced Architectural and Scaling Techniques

Describe architectural or system-level techniques used to improve scalability and efficiency in large language models. Explain how these techniques affect training cost, inference efficiency, or model capacity.

**Answer:**

Modern LLMs use various architectural and system-level optimizations to reduce computational needs:

1. sparse attention mechanisms reduce the quadratic complexity of self-attention from O(n²) to O(n√n) or O(n) enabling longer context windows
2. mixture-of-experts (MoE) architectures activate only a subset of parameters per token, increasing model capacity while keeping inference costs manageable
3. quantization techniques represent weights and activations in lower precision (e.g., int8 or int4) reducing memory requirements and increases speed without too much accuracy loss.
4. gradient checkpointing trades computation for memory by recomputing activations during backpropagation rather than storing them
5. model parallelism strategies distribute layers across devices while tensor parallelism splits individual layers and allow multiple GPUs
6. pipeline parallelism processes different micro-batches at different stages at the same time using multiple GPUs
7. KV-cache optimization stores previously computed key-value pairs during autoregressive generation to reduce redundant computation. T

---

## Question 5: Retrieval-Augmented Generation

Explain how retrieval-augmented generation integrates external knowledge into language model outputs. Describe how conditioning on retrieved documents modifies the generation process and why this can improve factual grounding.

**Answer:**

Retrieval-augmented generation (RAG) enhances language models by using an external retrieval system that retrieves relevant documents from a knowledge base (like Wikipedia) based on the input query It then conditions the language model's generation on both the original input and the retrieved context.

The retrieval component normally uses dense vector representations to perform semantic search, selecting top-k documents by similarity. These documents are then added to the prompt or integrated into the model's attention mechanism. This expands the model's accessible knowledge beyond its parametric memory.

RAG improves factual grounding because the model can reference specific, up-to-date information from retrieved documents rather than relying solely on patterns memorized during pretraining, which may be outdated, incomplete, or prone to hallucination. Additionally, RAG provides human use and human fact checking since generated outputs can be traced to source documents Finally, RAG enables dynamic knowledge updates without retraining, and reduces the need for huge storage to keep knowledge.

---

## Question 6: Chain-of-Thought and Structured Reasoning

Explain how prompting strategies can influence reasoning behavior in large language models. Discuss how structured intermediate steps affect answer quality and what this reveals about model reasoning.

**Answer:**

Prompting strategies influence reasoning performance by instructing models to generate explicit intermediate reasoning steps before producing final answers. Prompt strategies can do that through few-shot examples demonstrating step-by-step solutions or zero-shot instructions like "Let's think step by step." This structured approach improves accuracy on complex tasks including math logic, common-sense reasoning, and logical inference because it allows models to break down problems into smaller tasks that are more manageable yet still allow it to maintain context over the various steps.

CoT reveals several things about model reasoning:

1. models possess latent reasoning capabilities that require some human supervision to bring out
2. the sequential generation process benefits from intermediate states that serve as working memory
3. models can perform sophisticated pattern matching over reasoning templates learned from pretraining data.

However, CoT also exposes limitations:

1. models may generate reasoning that on the surface looks good but is actually flawed.
2. performance remains sensitive to prompt phrasing and example selection
3. improvements often reflect better utilization of memorized patterns rather than true reasoning and understanding. Sort of like the difference between wisdom and experience versus memorizing something in a book from school.

---

## Question 7: Generalization and Out-of-Distribution Behavior

Define generalization in the context of large language models. Explain how distributional training affects robustness to out-of-distribution inputs and why models may fail under slight prompt variations.

**Answer:**

Generalization in large language models is:

1. the ability of performing accurately on inputs, tasks, or distributions not encountered during training
2. extending learned patterns to novel contexts while maintaining coherent and correct outputs

Models trained on the internet and other large scale data develop robust representations that generalize very well to many tasks.

There are limitations in this type of brute force learning:

1. models are fundamentally statistical pattern matchers optimized for data resembling their training distribution
2. there is a lack of true understanding of cause and effect, formal logic, or consistent world models.

These weaknesses cause models to:

1. mess up on unexpected inputs
2. fail on adversarial examples
3. odd phrasings
4. lack of domain-specific lingo that isn't in the training data
5. sensitivity to superficial prompt variations.

---

## Question 8: Evaluation of Reasoning and Perplexity

Explain why perplexity is insufficient as a standalone measure of reasoning ability. Discuss how reasoning tasks require evaluation beyond next-token likelihood.

**Answer:**

Perplexity measures how well a language model predicts held-out text by quantifying the exponentiated average negative log-likelihood per token. Perplexity is insufficient for evaluating reasoning ability because:

1. it only assesses statistical fit to text distributions without measuring correctness, logical consistency, or problem-solving capability. A model can achieve low perplexity while generating fluent but false and illogical output.
2. Reasoning tasks require multi-step inference, maintaining consistency across reasoning chains, applying abstract rules to novel situations, and arriving at verifiably correct conclusions, none of which are captured by token-level prediction accuracy.

Therefore, evaluating reasoning demands task-specific metrics:

1. exact match accuracy for question answering, execution correctness for code generation
2. logical validity for formal reasoning
3. consistency checks across paraphrased questions
4. human evaluation of explanation quality.

Although Perplexity correlates with general LM quality, it fundamentally measures amount of data memorized rather than comprehension.

---
