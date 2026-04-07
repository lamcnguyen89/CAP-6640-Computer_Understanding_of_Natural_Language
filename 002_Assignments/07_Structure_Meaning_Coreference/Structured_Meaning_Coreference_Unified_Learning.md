# Review Questions: Structured Meaning, Coreference, and Unified Learning

This assignment examines discourse-level modeling, entity tracking, multi-task learning architectures, and semantic composition in neural NLP systems. All questions must be answered strictly using the material covered in this module. No external sources are required or permitted.

This is an individual assignment. Answers must be technically precise, clearly structured, and conceptually rigorous.

**Available:** Mar 10, 2026 12:00am until Apr 7, 2026 11:59pm

---

## Question 1: Coreference Resolution and Entity Linking

Define coreference resolution and explain why it is necessary for discourse-level language understanding.

Describe how mentions and entities are represented in neural systems and explain the challenges involved in resolving ambiguous references.

**Answer:**

Coreference resolution is the task of identifying when different mentions refer to the same real-world entity. This is essential for conversational level understanding because it enables models to track entities across sentences, track pronouns, and maintain coherent interpretations of paragraphs, chapters and other forms of large text bodies.

In neural , mentions are typically encoded as contextualized span representations using pretrained language models like BERT, while entities are represented as clusters of coreferent mentions or as nodes in an entity graph.

Challenges of coreference are:

1. resolving ambiguous pronouns (e.g., "she" or "it" when multiple people exist in sentence)
2. semantic compatibility constraints
3. entity type mismatches
4. long-distance dependencies across documents
5. distinguishing between similar but distinct entities that share surface features.

## Question 2: Structural Properties of Coreference

Explain the structural constraints involved in coreference resolution.

Discuss how syntactic structure, semantic compatibility, and discourse context influence coreference decisions.

**Answer:**

Coreference resolution needs to respect structural constraints including:

1.  syntactic binding theory (prevents certain pronoun-antecedent configurations based on c-command relationships)
2.  entity type compatibility (ensuring pronouns match their antecedents' semantic categories)
3.  number and gender agreement
4.  conversation accessibility hierarchies (where recent entities are more accessible as antecedents)

Syntactic structure determines which phrases can possibly corefer based on grammar constraints. Semantic compatibility filters based on selection restrictions and world knowledge. Discourse context relates sentences through recency, grammatical role prominence, and topic relevance

## Question 3: Entity Tracking Across Sentences

Describe how neural models maintain entity consistency across multiple sentences.

Explain why local sentence-level modeling is insufficient for discourse coherence and how context-aware representations address this limitation.

**Answer:**

Neural models maintain entity consistency across sentences by building contextualized representations. These representations use cross-sentence information through transformers with extended context windows, memory mechanisms that track states, or recurrent architectures that forward-propagate representations.

Local sentence-level modeling can't resolve cross-sentence anaphora, maintain entity attribute consistency, track coherent narratives, or capture conversation-level things like staying on topic and keeping the subject in focus. Context-aware representations (models using full-document attention) handle this by encoding each token with information from the entire conversation, enabling the model to access prior mentions, build coherent entity representations that accumulate information across references, and make globally decisions about entity identity and relationships.

## Question 4: Unified Modeling in NLP

Explain the motivation behind unified architectures in NLP.

Describe how a single model can support multiple tasks and analyze the advantages of parameter sharing across tasks.

**Answer:**

Unified architectures in NLP were created because NLP tasks share very similar linguistic knowledge and could benefit from shared representations. This reduces redundancy, improvesefficiency, and enables transfer learning across tasks.

A single model can support multiple tasks through shared encoder layers that learn general linguistic representations, with task-specific prediction heads or decoders that specialize the shared representations for tasks like classification, generation, tagging, etc...

The advantages of parameter sharing include improved generalization through multi-task regularization, better sample efficiency by leveraging supervision from similar tasks, reduced compute resources compared to separate models, emergent capabilities from task interactions, and the ability to perform zero-shot or few-shot transfer to new tasks by leveraging shared representations.

## Question 5: Multi-Task Learning as Representation Sharing

Define multi-task learning and explain how shared encoders support multiple objectives.

Discuss the potential benefits and risks of shared representations, including negative transfer.

**Answer:**

Multi-task learning is a training methodology where a single model is optimized to perform multiple related tasks at the same time using shared encoders that produce common representations fed into task-specific prediction layers. This allows the model to leverage common features across tasks while keeping task specialization.

Shared encoders learn representations that capture general patterns useful across tasks. This provides implicit regularization that prevents overfitting and enables knowledge transfer from data-rich to data-poor tasks.

Benefits of Multi-task learning include improved generalization, faster convergence, and better performance on low-resource tasks.

Risks include negative transfer when tasks conflict or have incompatible optimal representations (tasks requiring different levels of abstraction or thate emphasize contradictory features).

---

## Question 6: Multi-Task Learning as Multi-Objective Optimization

Explain how multi-task learning can be framed as optimizing multiple objectives simultaneously.

Describe how task-specific losses are combined and discuss how imbalance between tasks can affect training dynamics.

**Answer:**

Multi-task learning can be framed as simultaneously optimizing multiple loss functions(one per task) requiring the model to find parameters that perform well across all objectives all while balancing potentially competing gradients.

Task-specific losses are typically combined through weighted summation (L_total = λ₁L₁ + λ₂L₂ + ...), where weights determine each task's influence on parameter updates, though alternative schemes include gradient normalization, uncertainty-based weighting, or dynamic weighting depending on task difficulty.

Imbalance between tasks can occur when a particular tasks has a larger loss magnitude, more training data, or faster convergence. This can cause the model to focus more on that task while neglecting others. This hurts multi-task performance.

To mitigate this, loss scaling, gradient clipping, adaptive weighting strategies, or curriculum learning approaches can be used.

## Question 7: Semantic Composition

Explain the principle of compositionality in semantic modeling.

Describe how neural architectures attempt to capture compositional meaning beyond word-level representations.

**Answer:**

The principle of compositionality states that the meaning of a complex expression is determined by the meanings of its parts and the rules used to combine those parts. This ensures that new combinations can be understood through knowledge of parts and how they are combined.

Neural architectures attempt to capture compositional meaning through:

1. RNNs that mirror syntactic tree structures
2. tree-structured LSTMs that propagate information bottom-up
3. attention mechanisms that weight constituent contributions
4. transformer models that learn composition through self-attention and deep layer hierarchies.

These approaches still face challenges in systematic generalization, capturing precise logical composition, and maintaining true recursive structure-sensitivity rather than relying on statistical approximations.

---

## Question 8: Structured Meaning and Logical Sensitivity

Discuss how neural models represent structured meaning involving argument roles, quantification, or hierarchical relationships.

Explain the limitations of purely distributional representations in capturing logical or compositional structure.

**Answer:**

Neural models represent structured meaning involving argument roles through learned embeddings of semantic role labels or implicit attention patterns that capture:

1.  predicate-argument structures
2.  quantification through contextual representations that approximate scope relationships
3.  hierarchical relationships through layered representations

NMs do this with graph neural networks that encode dependency or constituency trees.

Purely distributional representations have limitations:

1. struggle with systematic generalization of the text
2. cannot reliably capture logical phenomena like negation scope or quantifier semantics
3. combines semantically distinct but distributionally similar phrases
4. lacks structures/rules for formal reasoning
5. perform poorly on logical inference requiring precise interpretation rather than similarity-based approximation.
