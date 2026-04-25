Module 2 Self-Guided Lab: Neural Training, Optimization, and Parsing
This lab is a self-directed, ungraded activity designed to operationalize the core concepts from Lectures 5–7. The goal is to move from abstract formulations of neural training and grammar-based parsing to concrete computational experiments that expose how context windows, scoring functions, loss objectives, syntactic structure, and parsing models behave in practice.

There is no submission or grading associated with this lab. You are encouraged to experiment freely, modify the code, and observe how changes in modeling assumptions affect outputs. The value of this lab comes from hands-on exploration and conceptual alignment with the lecture material.

Recommended Programming Environment
The recommended environment for this lab is Python using Google Colab. Colab provides a ready-to-use setup with no local installation and supports common NLP and deep learning libraries.

To get started:

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 as the runtime
Core Libraries
The following libraries will be used:

numpy – numerical computation
scikit-learn – basic models and utilities
torch – neural networks and backpropagation
spaCy – dependency parsing
matplotlib – visualization
Install (or confirm) these libraries in Colab:

!pip install numpy scikit-learn torch spacy matplotlib
!python -m spacy download en_core_web_sm
Standard Datasets
This lab uses small, controlled examples rather than large benchmarks. You may optionally experiment with:

Manually constructed sentences (recommended)
spaCy demo texts
Small NER datasets (optional)
Activity 1: Context Windows for NER Classification
This activity operationalizes the window-based formulation of NER from Lecture 5.

Steps:

Define sentence variants
Extract fixed-size context windows
Observe how window content changes interpretation

sentences = [
"Not all museums in Paris are amazing",
"All museums in Paris are amazing",
"Not all museums in Paris"
]

def extract_window(tokens, index, k=2):
return tokens[max(0, index-k): index+k+1]

for s in sentences:
tokens = s.split()
idx = tokens.index("museums")
print(s)
print(extract_window(tokens, idx))
Think about:

Which windows suggest limitation or positivity?
Which windows are incomplete or ambiguous?
Why is NER sensitive to local context?
Activity 2: Neural Scoring of Context Windows
This activity mirrors the unnormalized neural scoring function used in Lecture 5.

Steps:

Encode a window as a numeric vector
Apply a small feed-forward neural network
Produce a scalar score

import torch
import torch.nn as nn

model = nn.Sequential(
nn.Linear(10, 16),
nn.ReLU(),
nn.Linear(16, 1)
)

window_vector = torch.randn(10)
score = model(window_vector)
score
Think about:

Why is the output not a probability?
What does a higher score represent?
Activity 3: Max-Margin Loss with Corrupted Windows
This activity implements the max-margin loss used to separate true and corrupted contexts.

Steps:

Define scores for true and corrupted windows
Compute the hinge loss
Observe when updates occur

S = torch.tensor(2.3) # true window score
Sc = torch.tensor(1.8) # corrupted window score

loss = torch.clamp(1 - S + Sc, min=0)
loss
Think about:

When does the loss become zero?
Why are updates conditional?
Activity 4: Pitfall of Retraining Word Vectors
This activity simulates the embedding update pitfall discussed in Lecture 5.

Steps:

Initialize embeddings for related words
Update only words seen in training
Compare representations

embeddings = {
"tv": torch.randn(5),
"telly": torch.randn(5),
"television": torch.randn(5)
}

# simulate training update

embeddings["tv"] += 0.5
embeddings["telly"] += 0.5

embeddings
Think about:

Which words drift in vector space?
Why does this affect test-time performance?
Activity 5: Phrase Structure and CFG Rules
This activity operationalizes phrase structure and CFG composition from Lecture 7.

Steps:

Define simple CFG rules
Manually analyze a sentence

grammar = {
"S": [["NP", "VP"]],
"NP": [["DET", "ADJ", "N"]],
"VP": [["V", "PP"]],
"PP": [["PREP", "NP"]]
}
Think about:

Which rules introduce hierarchy?
Where does recursion arise?
Activity 6: Structural Ambiguity Exploration
Analyze ambiguity using sentence structure.

sentence = "The boy saw the man with the telescope"
sentence
Think about:

What are the possible attachments?
Why does grammar alone not resolve this?
Activity 7: Dependency Parsing in Practice
This activity demonstrates dependency parsing as a tree structure.

import spacy
nlp = spacy.load("en_core_web_sm")

doc = nlp("The cuddly cat sat by the door")
for token in doc:
print(token.text, token.dep\_, token.head.text)
Think about:

How are dependencies represented?
Which word acts as the root?
Activity 8: Neural Parsing Observation
Use a neural parser to observe how structure is predicted.

Steps:

Parse multiple ambiguous sentences
Compare dependency trees
Think about:

How does context influence attachment?
Why is annotated data critical?
Reflection
As you complete this lab, reflect on the following:

How optimization shapes neural decisions
Why margin-based objectives focus learning
How syntactic structure constrains interpretation
Why parsing is essential for meaning beyond word sequences
This lab prepares you for subsequent modules on language modeling, sequence learning, and neural architectures that operate over longer contexts and richer structures.
