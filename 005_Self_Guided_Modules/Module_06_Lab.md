Module 6 Self-Guided Lab: Structured Meaning, Coreference, and Multi-Task Learning
This lab is a self-directed, ungraded activity designed to help you operationalize the core concepts from Lectures 17, 18, and 19. The goal is to move from theory to practice by experimenting with entity tracking, multi-task learning dynamics, and semantic composition in modern NLP systems.

You are encouraged to experiment freely. There is no submission required. The value comes from running the code, analyzing model behavior, and connecting empirical observations back to the theoretical foundations discussed in the lectures.

Recommended Programming Environment
Use Python with Google Colab for ease of experimentation and GPU access.

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 runtime
Enable GPU (Runtime → Change runtime type → GPU)
Core Libraries
transformers – pretrained contextual models
torch – neural modeling
spacy – dependency parsing and coreference tools
datasets – optional benchmark datasets
matplotlib – visualization

!pip install torch transformers spacy datasets matplotlib
!python -m spacy download en_core_web_sm
Activity 1: Coreference Resolution and Entity Tracking
This activity explores how models track entities across sentences.

import spacy
nlp = spacy.load("en_core_web_sm")

text = "Alice went to the bookstore. She bought a novel because it was recommended."

doc = nlp(text)
for token in doc:
print(token.text, token.dep\_, token.head.text)
Extend: Replace names, pronouns, and plural references. Observe ambiguity.

Think about:

How does pronoun resolution depend on syntactic and semantic cues?
What happens when multiple candidate antecedents exist?
Key Insight: Coreference resolution requires modeling discourse structure, not just local syntax.
Activity 2: Structured Meaning and Role Sensitivity
This activity explores argument structure sensitivity in contextual embeddings.

from transformers import AutoTokenizer, AutoModel
import torch

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
model = AutoModel.from_pretrained("bert-base-uncased")

sent1 = "The dog chased the cat."
sent2 = "The cat chased the dog."

inputs = tokenizer([sent1, sent2], return_tensors="pt", padding=True)

with torch.no_grad():
outputs = model(\*\*inputs)

embeddings = outputs.last_hidden_state.mean(dim=1)
print(torch.cosine_similarity(embeddings[0], embeddings[1], dim=0))
Reflect:

Should these sentences be highly similar?
How does argument reversal affect semantic meaning?
Activity 3: Scope Ambiguity and Logical Structure
Consider the sentence: “All students read a book.”

It admits two interpretations:

1. ∀x ∃y read(x,y)
2. ∃y ∀x read(x,y)
   Experiment: Use a language model to generate continuations for this sentence and analyze whether it resolves toward one interpretation.

from transformers import AutoModelForCausalLM

model_name = "gpt2"
lm = AutoModelForCausalLM.from_pretrained(model_name)

prompt = "All students read a book. This means that"
inputs = tokenizer(prompt, return_tensors="pt")

output = lm.generate(\*\*inputs, max_length=60)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Think about:

Does the model distinguish quantifier scope?
How might distributional training obscure logical ambiguity?
Activity 4: Multi-Task Learning as Shared Representation Learning
This activity explores how a shared encoder supports multiple objectives.

import torch.nn as nn

shared_encoder = nn.Linear(768, 256)

task1_classifier = nn.Linear(256, 2) # e.g., sentiment
task2_classifier = nn.Linear(256, 5) # e.g., topic classification
Conceptual Exercise:

Why might shared representations improve generalization?
When could negative transfer occur?
Activity 5: Compositional Generalization Test
Construct simple compositional commands:

train_examples = [
"jump twice",
"walk and run"
]

test_example = "run twice and jump"
Question: Would a model trained only on primitives generalize correctly to new combinations?

This mirrors compositional split evaluation (e.g., SCAN-style tasks).

Activity 6: Attention as Implicit Composition
Inspect attention patterns in a Transformer model.

from transformers import AutoModel

model = AutoModel.from_pretrained("bert-base-uncased", output_attentions=True)
inputs = tokenizer("The lawyer that the judge admired smiled.", return_tensors="pt")

with torch.no_grad():
outputs = model(\*\*inputs)

attentions = outputs.attentions
print(len(attentions)) # number of layers
Reflect:

Does attention appear to capture hierarchical dependencies?
Is structure explicitly enforced or implicitly learned?
Activity 7: Inductive Bias and Structural Sensitivity
Compare dependency parses:

text = "The lawyer that the judge admired smiled."
doc = nlp(text)

for token in doc:
print(token.text, token.dep\_, token.head.text)
Think about:

How does tree structure differ from flat sequence modeling?
What architectural bias encourages hierarchical interpretation?
Reflection
Why coreference resolution requires discourse-level modeling
How compositional meaning differs from lexical similarity
Why logical operators challenge distributional models
How multi-task learning shapes shared representation spaces
Where modern models interpolate versus truly generalize
Final Insight: True language understanding requires integrating structured reasoning, contextual representation learning, and systematic compositional generalization.
