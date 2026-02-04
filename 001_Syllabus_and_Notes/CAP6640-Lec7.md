Lecture 7: Syntactic Parsing in NLP: Context-Free Grammars, Dependency Structures, and Neural Parsers
This lecture formalizes syntactic structure as an explicit representation used to analyze and interpret natural language. It introduces grammar-based models that explain how words combine into phrases, how phrases form sentences, and how syntactic structure enables accurate language interpretation. The lecture focuses on both phrase structure grammar and dependency grammar, and explains how these representations are operationalized in modern NLP systems.

The lecture progresses from linguistic definitions of phrase structure to formal context-free grammars (CFGs), examines multiple sources of structural ambiguity, and then introduces dependency parsing as a tree-based representation of syntax. It concludes by showing how annotated data (treebanks) and deep learning models are used to build modern neural parsers.

Key Point: Parsing is the computational task of assigning syntactic structure to sentences, and different grammatical formalisms encode structure in different ways.
Lecture Objectives
Understand phrase structure and structure grammar
Become familiar with context-free grammars (CFGs)
Understand how CFGs work in structure grammar
Understand sentence structure for accurate interpretation
Identify sources of structural ambiguity
Understand dependency parsing as a tree structure
Become familiar with deep learning–based parsing models and tools
Phrase Structure in Linguistics
Phrase structure refers to the way words are organized into nested constituents that form larger, meaningful units within a sentence. This hierarchical organization is fundamental to grammar and syntax.

Phrase structure begins with words, which serve as the smallest meaningful units in language. Examples include:

The
cat
cuddly
by
door
Words combine into phrases, which are categorized based on the role of the head word.

Noun Phrase: The cuddly cat
Prepositional Phrase: by the door
Phrases themselves can combine into larger phrases, increasing descriptive power and clarifying relationships:

The cuddly cat by the door
Key Point: Phrase structure encodes hierarchy, not just word order.
Why Phrase Structure Matters
Understanding phrase structure is critical for:

Sentence parsing: breaking sentences into components
Grammar rules: identifying valid word arrangements
Language learning: understanding how words combine logically
Hierarchical organization underpins syntax and enables the creation of coherent sentences from simple elements.

Structure Grammar and Context-Free Grammars
Phrase structure grammar, often equated with context-free grammars (CFGs), is a formal system used to describe syntax. Grammar specifies how smaller elements (words or categories) combine to form larger structures through production rules.

CFGs operate on the principle that a grammatical rule applies independently of surrounding context.

Example rules of composition:

S → NP VP
NP → DET N
VP → V NP
CFGs are recursive, allowing nested structures such as:

The cat by the door that is open
Categories (Parts of Speech)
Each word is assigned a syntactic category based on its role. These categories are the building blocks of grammar.

NOUN (N): cat, door, freedom
PRONOUN (PRON): he, she, it
VERB (V): run, is, jump
ADJECTIVE (ADJ): cuddly, large
ADVERB (ADV): quickly, very
PREPOSITION (PREP): by, with, under
CONJUNCTION (CONJ): and, but, or
INTERJECTION (INT): wow, ouch
Sentence Structure and Structural Ambiguity
Sentence structure is essential for interpretation. Without structure, language can become ambiguous.

Example:

The boy saw the man with the telescope
Ambiguity arises when it is unclear how constituents are attached. The lecture highlights several ambiguity types:

Prepositional Phrase (PP) attachment ambiguity
Coordination scope ambiguity
Modifier ambiguity
A key parsing decision is how constituents such as PPs, adverbial phrases, participial phrases, and coordination structures are attached.

Dependency Grammar and Dependency Structure
Dependency grammar models syntax as relations between lexical items. Syntactic structure consists of binary, asymmetric relations called dependencies.

Dependencies form a tree structure where:

Words are nodes
Edges represent grammatical relations
Dependency grammar emphasizes word-to-word relationships rather than phrase groupings.

Dependency Grammar: Historical Context
Dependency-based analysis has deep historical roots:

Pāṇini (Sanskrit grammar): ~4th century BCE
Sibawayh (Arabic grammar): ~8th century CE
Lucien Tesnière (1959): formalized Dependency Grammar
Dependency grammar gained prominence in computational linguistics due to its simplicity and suitability for parsing, particularly for free-word-order languages.

Annotated Data and Treebanks
The lecture emphasizes the importance of annotated syntactic data. While building a treebank is costly, it provides:

Reusable linguistic annotations
Broad coverage beyond intuition-based grammars
Frequency and distributional information
A foundation for evaluating NLP systems
Deep Learning–Based Parsing
Neural parsing uses deep neural networks to predict syntactic structure directly from data rather than relying on handcrafted grammar rules.

Key properties:

Data-driven learning from annotated trees
Continuous vector representations (embeddings)
Support for dependency and constituency parsing
Neural architectures used include:

RNNs
Transformers
Graph Neural Networks (GNNs)
Parsing Pipeline
Deep learning–based parsing follows these steps:

Input tokenization and embedding
Sentence encoding
Score prediction for edges or splits
Tree construction
Training using annotated treebanks
Lecture Takeaway
This lecture establishes grammar and parsing as central mechanisms for structured language understanding. By formalizing phrase structure, CFGs, dependency grammar, and neural parsing, it shows how syntactic structure is computed, represented, and learned in modern NLP systems.

