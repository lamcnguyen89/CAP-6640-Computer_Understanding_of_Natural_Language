Lecture 2: Foundations of Natural Language Processing: History, Tasks, and Linguistic Levels
Lecture 2: Foundations of Natural Language Processing
This lecture introduces the historical evolution of Natural Language Processing (NLP) and establishes the foundational task categories that define the field. It explains how NLP developed from early rule-based approaches into modern data-driven and neural methods, while highlighting the core challenges that make human language difficult for machines to process.

The lecture also formalizes the major types of NLP tasks, distinguishing between syntactic, semantic, and pragmatic analysis. These task categories provide a conceptual framework that will be used throughout the course to organize methods, models, and applications.

Key Point: NLP combines historical insights, task structure, and linguistic challenges to enable machines to process human language.
Historical Background of NLP
The earliest phase of NLP began in the mid-1950s and 1960s, alongside the emergence of modern linguistics. During this period, language understanding was initially considered an easy problem and relied heavily on hand-coded rules. This optimism was short-lived.

By the late 1960s and 1970s, the field entered a period often referred to as the “dark times.” After early hype faded, many researchers concluded that machine translation and language understanding were infeasible, leading to a significant decline in NLP research activity.

Revival and Evolution of NLP
NLP experienced a gradual revival during the late 1970s and 1980s, with renewed focus on linguistics. A major turning point occurred in the late 1980s and 1990s, when increased computational power enabled statistical modeling approaches.

Data-driven statistical methods using simple representations consistently outperformed complex hand-crafted rules. In the 2000s, linguistically informed statistical models further improved performance, and by the 2010s, learning-based representations emerged that combined statistical, linguistic, and contextual signals automatically.

Major Paradigm Shifts in NLP
Early Beginnings and Rule-Based Systems
Early conceptual foundations were laid in the 1950s, including the proposal of the Turing Test as a measure of machine intelligence. The Georgetown-IBM experiment in 1954 demonstrated early machine translation capabilities.

From the 1960s through the 1980s, NLP was dominated by symbolic systems using hand-crafted rules and grammars. Transformational grammar influenced linguistic modeling, and early conversational systems such as ELIZA demonstrated limited dialogue capabilities.

Statistical and Machine Learning Era
During the 1980s and 1990s, statistical methods began replacing rule-based approaches. Models such as Hidden Markov Models enabled advances in speech and text processing, supported by annotated datasets like the Penn Treebank.

The 1990s and 2000s saw a statistical revolution, with techniques such as n-grams and log-linear models improving tasks like translation and speech recognition. Evaluation metrics such as BLEU became standard, and large-scale systems demonstrated the effectiveness of statistical NLP.

Deep Learning and Transformers
In the 2010s, neural networks transformed NLP by enabling representation learning and contextual understanding. Word embeddings introduced dense vector representations that captured semantic relationships.

The introduction of transformer architectures in 2017 enabled powerful contextual and multitask learning models, forming the basis of modern language systems that exhibit advanced reasoning and language understanding capabilities.

Why NLP Is Hard
Human language is inherently ambiguous and often requires reasoning beyond explicitly stated information. Understanding language frequently depends on world knowledge, context, and inference, making it challenging even for humans.

Ambiguity compounds as sentence complexity increases. For example, sentences containing multiple prepositional phrases can have exponentially many syntactic interpretations, illustrating the difficulty of determining intended meaning.

Key Point: Ambiguity is a fundamental challenge that distinguishes natural language from formal systems.
Core NLP Task Categories
NLP tasks are commonly organized into three major categories: syntactic, semantic, and pragmatic tasks. Each category addresses a different aspect of language understanding and contributes to complete language interpretation.

Syntactic tasks focus on grammatical structure, semantic tasks focus on meaning, and pragmatic tasks focus on context, intent, and discourse-level understanding.

Syntactic Tasks: Understanding Structure
Syntactic analysis focuses on the grammatical structure of language to ensure coherence and correctness. Common tasks include part-of-speech tagging, dependency parsing, sentence splitting, and tokenization.

These tasks are essential for preprocessing and serve as building blocks for higher-level semantic and pragmatic analysis. Applications include grammar checking, sentence restructuring, and preparation for downstream NLP models.

Word Segmentation and Morphology
Word segmentation involves breaking character sequences into meaningful words, which is particularly challenging in languages without explicit word boundaries. Morphological analysis examines the internal structure of words by identifying morphemes, the smallest meaning-bearing units.

Segmenting words into morphemes reveals grammatical features such as tense, plurality, and derivation, which are critical for accurate language understanding.

Semantic Tasks: Understanding Meaning
Semantic analysis aims to capture the meaning of words, sentences, and texts beyond surface structure. Tasks include named entity recognition, word sense disambiguation, text summarization, and sentiment analysis.

Many semantic tasks require selecting the correct meaning of ambiguous words based on context, which is essential for applications such as question answering and machine translation.

Pragmatic Tasks: Context and Intent
Pragmatic analysis focuses on interpreting language in context, accounting for intent, discourse, and implied meaning. Tasks include coreference resolution, dialogue management, speech act recognition, and discourse analysis.

These tasks enable systems to maintain coherent interactions, resolve references across sentences, and respond appropriately in conversational settings.

Computer Languages vs. Natural Languages
A key distinction between natural and computer languages is ambiguity. Natural languages allow multiple interpretations, while programming languages are designed to be unambiguous and deterministic.

Formal languages rely on precisely defined grammars that guarantee unique parses and efficient execution, whereas natural language understanding must manage uncertainty and multiple plausible interpretations.

Usable Meaning in Computers
One traditional approach to representing meaning in computers is the use of structured lexical resources such as WordNet, which organizes words into synonym sets and hierarchical relationships.

While useful, such resources lack nuance, struggle to capture new word meanings, require human labor to maintain, and cannot compute accurate similarity automatically.

Key Point: Capturing usable meaning computationally requires moving beyond static symbolic resources.
Lecture Takeaway
By integrating syntactic structure, semantic meaning, and pragmatic context, NLP systems can analyze and respond to human language effectively. Understanding the historical evolution and task taxonomy of NLP provides the foundation for modern representation learning and modeling techniques introduced in subsequent lectures.

