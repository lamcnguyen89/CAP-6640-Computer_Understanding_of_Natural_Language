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

The retrieval component typically uses dense vector representations (e.g., from BERT-based encoders) to perform semantic search, selecting top-k documents by similarity, which are then prepended to the prompt or integrated into the model's attention mechanism, effectively expanding the model's accessible knowledge beyond its parametric memory. This approach significantly improves factual grounding because the model can reference specific, up-to-date information from retrieved documents rather than relying solely on patterns memorized during pretraining, which may be outdated, incomplete, or prone to hallucination—particularly valuable for knowledge-intensive tasks like open-domain question answering, fact verification, and specialized domains where in-context evidence reduces the risk of generating plausible-sounding but incorrect information. Additionally, RAG provides interpretability and verifiability since generated outputs can be traced to source documents, enables dynamic knowledge updates without retraining, and reduces the need for massive parametric capacity to store encyclopedic knowledge.

---

## Question 6: Chain-of-Thought and Structured Reasoning

Explain how prompting strategies can influence reasoning behavior in large language models. Discuss how structured intermediate steps affect answer quality and what this reveals about model reasoning.

**Answer:**

Prompting strategies, particularly chain-of-thought (CoT) prompting, dramatically influence reasoning performance by instructing models to generate explicit intermediate reasoning steps before producing final answers, either through few-shot examples demonstrating step-by-step solutions or zero-shot instructions like "Let's think step by step." This structured approach improves accuracy on complex tasks including multi-step arithmetic, commonsense reasoning, and logical inference because it allows models to decompose problems into manageable sub-tasks, maintain relevant context across reasoning chains, and correct potential errors through intermediate verification—performance gains that scale with model size, emerging clearly in models beyond ~100B parameters. The effectiveness of CoT reveals several insights about model reasoning: models possess latent reasoning capabilities that require appropriate scaffolding to manifest, the sequential generation process benefits from explicit intermediate states that serve as working memory, and models can perform sophisticated pattern matching over reasoning templates learned from pretraining data. However, CoT also exposes limitations: models may generate plausible-looking but logically flawed reasoning chains, performance remains sensitive to prompt phrasing and example selection, and improvements often reflect better utilization of memorized patterns rather than true symbolic reasoning or causal understanding, highlighting the gap between surface-level coherence and robust logical inference.

---

## Question 7: Generalization and Out-of-Distribution Behavior

Define generalization in the context of large language models. Explain how distributional training affects robustness to out-of-distribution inputs and why models may fail under slight prompt variations.

**Answer:**

Generalization in large language models refers to the ability to perform accurately on inputs, tasks, or distributions not explicitly encountered during training, extending learned patterns to novel contexts while maintaining coherent and correct outputs—a critical capability since deployment scenarios inevitably differ from training conditions. Models trained on broad internet-scale corpora develop robust representations that often generalize remarkably well to diverse tasks through few-shot or zero-shot learning, yet this distributional training creates inherent limitations: models are fundamentally statistical pattern matchers optimized for data resembling their training distribution, lacking true understanding of causal relationships, formal logic, or consistent world models. Consequently, models exhibit brittleness to out-of-distribution inputs, failing on adversarial examples, unusual phrasings, or domain-specific terminology absent from training data, and show surprising sensitivity to superficial prompt variations—synonymous rephrasings, formatting changes, or example ordering can yield dramatically different outputs because models latch onto spurious correlations and surface-level cues rather than underlying semantics. This fragility reflects that pretraining implicitly encodes distributional biases, tokenization artifacts, and dataset-specific patterns, while the model's learned representations, though powerful for interpolation within the training manifold, provide weak guarantees for extrapolation, revealing the need for more robust learning objectives, systematic evaluation of out-of-distribution behavior, and techniques like adversarial training or compositionality-focused architectures.

---

## Question 8: Evaluation of Reasoning and Perplexity

Explain why perplexity is insufficient as a standalone measure of reasoning ability. Discuss how reasoning tasks require evaluation beyond next-token likelihood.

**Answer:**

Perplexity, which measures how well a language model predicts held-out text by quantifying the exponentiated average negative log-likelihood per token, is insufficient for evaluating reasoning ability because it only assesses statistical fit to text distributions without measuring correctness, logical consistency, or problem-solving capability—a model can achieve low perplexity while generating fluent but factually incorrect or logically invalid outputs. Reasoning tasks require multi-step inference, maintaining consistency across reasoning chains, applying abstract rules to novel situations, and arriving at verifiably correct conclusions, none of which are captured by token-level prediction accuracy; for instance, a model might assign high probability to a plausible-sounding but mathematically wrong solution, or produce contradictory statements that each have locally high likelihood. Consequently, evaluating reasoning demands task-specific metrics: exact match accuracy for question answering, execution correctness for code generation, logical validity for formal reasoning, consistency checks across paraphrased questions, and human evaluation of explanation quality, ideally tested on dedicated benchmarks like GSM8K for mathematical reasoning, BIG-Bench for diverse cognitive tasks, or adversarial datasets designed to expose systematic failures. While perplexity correlates with general language modeling quality and can indicate training progress, it fundamentally measures compression rather than comprehension, making it an inadequate proxy for the compositional generalization, causal reasoning, and systematic problem-solving that characterize genuine reasoning ability.

---
