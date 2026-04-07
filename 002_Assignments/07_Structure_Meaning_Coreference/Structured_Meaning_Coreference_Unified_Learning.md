# Review Questions: Structured Meaning, Coreference, and Unified Learning

This assignment examines discourse-level modeling, entity tracking, multi-task learning architectures, and semantic composition in neural NLP systems. All questions must be answered strictly using the material covered in this module. No external sources are required or permitted.

This is an individual assignment. Answers must be technically precise, clearly structured, and conceptually rigorous.

Available: Mar 10, 2026 12:00am until Apr 7, 2026 11:59pm

---

## Question 1: Coreference Resolution and Entity Linking

Define coreference resolution and explain why it is necessary for discourse-level language understanding.

Describe how mentions and entities are represented in neural systems and explain the challenges involved in resolving ambiguous references.

**Answer:**

## Coreference resolution is the task of identifying when different linguistic expressions (mentions) refer to the same real-world entity, which is essential for discourse-level understanding because it enables systems to track entities across sentences, resolve pronouns, and maintain coherent interpretations of multi-sentence texts. In neural systems, mentions are typically encoded as contextualized span representations using pretrained language models like BERT, while entities are represented as clusters of coreferent mentions or as nodes in an entity graph. The primary challenges include resolving ambiguous pronouns (e.g., "she" or "it" when multiple candidates exist), handling semantic compatibility constraints, dealing with entity type mismatches, managing long-distance dependencies across documents, and distinguishing between similar but distinct entities that share surface features.

## Question 2: Structural Properties of Coreference

Explain the structural constraints involved in coreference resolution.

Discuss how syntactic structure, semantic compatibility, and discourse context influence coreference decisions.

**Answer:**

## Coreference resolution must respect structural constraints including syntactic binding theory (which prohibits certain pronoun-antecedent configurations based on c-command relationships), entity type compatibility (ensuring pronouns match their antecedents' semantic categories), number and gender agreement, and discourse accessibility hierarchies (where recent, salient entities are more accessible as antecedents). Syntactic structure determines which nominal phrases can potentially corefer based on grammatical constraints; semantic compatibility filters candidates based on selectional restrictions and world knowledge (e.g., "the company" cannot corefer with "John"); and discourse context establishes salience through recency, grammatical role prominence, and topicality, with entities in subject positions or recently mentioned being more likely antecedents.

## Question 3: Entity Tracking Across Sentences

Describe how neural models maintain entity consistency across multiple sentences.

Explain why local sentence-level modeling is insufficient for discourse coherence and how context-aware representations address this limitation.

**Answer:**

## Neural models maintain entity consistency across sentences by building contextualized representations that incorporate cross-sentence information through transformers with extended context windows, memory mechanisms that explicitly track entity states, or recurrent architectures that propagate entity representations forward. Local sentence-level modeling is insufficient because it cannot resolve cross-sentence anaphora, maintain entity attribute consistency, track narrative coherence, or capture discourse-level phenomena like topic continuity and entity centrality. Context-aware representations (like those from models using full-document attention or entity-centric memory networks) address this by encoding each token with information from the entire discourse context, enabling the model to access prior mentions, build coherent entity representations that accumulate information across references, and make globally informed decisions about entity identity and relationships.

## Question 4: Unified Modeling in NLP

Explain the motivation behind unified architectures in NLP.

Describe how a single model can support multiple tasks and analyze the advantages of parameter sharing across tasks.

**Answer:**

## Unified architectures in NLP are motivated by the observation that many NLP tasks share underlying linguistic knowledge and could benefit from shared representations, reducing redundancy, improving data efficiency, and enabling transfer learning across tasks. A single model can support multiple tasks through shared encoder layers that learn general linguistic representations (like BERT or T5), with task-specific prediction heads or decoders that specialize the shared representations for particular outputs (classification, generation, tagging, etc.). The advantages of parameter sharing include improved generalization through multi-task regularization, better sample efficiency by leveraging supervision from related tasks, reduced computational and memory costs compared to separate models, emergent capabilities from task interactions, and the ability to perform zero-shot or few-shot transfer to new tasks by leveraging the rich shared representations.

## Question 5: Multi-Task Learning as Representation Sharing

Define multi-task learning and explain how shared encoders support multiple objectives.

Discuss the potential benefits and risks of shared representations, including negative transfer.

**Answer:**

Multi-task learning is a training paradigm where a single model is optimized to perform multiple related tasks simultaneously, typically using shared encoders that produce common representations fed into task-specific prediction layers, allowing the model to leverage commonalities across tasks while maintaining task-specific specialization. Shared encoders learn representations that capture general patterns useful across tasks, providing implicit regularization that prevents overfitting to any single task and enabling knowledge transfer from data-rich to data-poor tasks. The benefits include improved generalization, faster convergence, and better performance on low-resource tasks, but risks include negative transfer when tasks conflict or have incompatible optimal representations (e.g., tasks requiring different levels of abstraction or contradictory feature emphases), which can degrade performance below single-task baselines if task relationships are not carefully considered.

---

## Question 6: Multi-Task Learning as Multi-Objective Optimization

Explain how multi-task learning can be framed as optimizing multiple objectives simultaneously.

Describe how task-specific losses are combined and discuss how imbalance between tasks can affect training dynamics.

**Answer:**

## Multi-task learning can be framed as simultaneously optimizing multiple loss functions—one per task—requiring the model to find parameters that perform well across all objectives, balancing potentially competing gradients. Task-specific losses are typically combined through weighted summation (L_total = λ₁L₁ + λ₂L₂ + ...), where weights determine each task's influence on parameter updates, though alternative schemes include gradient normalization, uncertainty-based weighting, or dynamic weighting based on task difficulty. Imbalance between tasks—where one task dominates due to larger loss magnitude, more abundant data, or faster convergence—can cause the model to focus predominantly on that task while neglecting others, leading to suboptimal multi-task performance; this is addressed through loss scaling, gradient clipping, adaptive weighting strategies, or curriculum learning approaches that adjust task emphasis during training.

## Question 7: Semantic Composition

Explain the principle of compositionality in semantic modeling.

Describe how neural architectures attempt to capture compositional meaning beyond word-level representations.

**Answer:**

The principle of compositionality states that the meaning of a complex expression is systematically determined by the meanings of its constituent parts and the rules used to combine them, ensuring that novel combinations can be understood through knowledge of components and compositional operations. Neural architectures attempt to capture compositional meaning through recursive neural networks that mirror syntactic tree structures, tree-structured LSTMs that propagate information bottom-up, attention mechanisms that weight constituent contributions, and transformer models that implicitly learn compositional patterns through self-attention and deep layer hierarchies. While these approaches move beyond simple word-level bag-of-words representations by modeling interactions between constituents, they still face challenges in systematic generalization, capturing precise logical composition (like quantifier scope), and maintaining true recursive structure-sensitivity rather than relying on statistical approximations.

---

## Question 8: Structured Meaning and Logical Sensitivity

Discuss how neural models represent structured meaning involving argument roles, quantification, or hierarchical relationships.

Explain the limitations of purely distributional representations in capturing logical or compositional structure.

**Answer:**

## Neural models represent structured meaning involving argument roles through learned embeddings of semantic role labels or implicit attention patterns that capture predicate-argument structures, quantification through contextual representations that approximate scope relationships, and hierarchical relationships through layered representations or graph neural networks that encode dependency or constituency trees. However, purely distributional representations have significant limitations: they struggle with systematic compositional generalization (failing on unseen combinations of known elements), cannot reliably capture logical phenomena like negation scope or quantifier semantics, conflate semantically distinct but distributionally similar expressions, lack the discrete symbolic structure needed for formal reasoning, and perform poorly on logical inference requiring precise interpretation rather than similarity-based approximation. This motivates hybrid approaches combining neural representations with structured symbolic components or explicit logical forms.
