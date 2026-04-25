Module 5 Self-Guided Lab: Decoding, Entropy Control, and Generation Dynamics
This lab is a self-directed, ungraded activity designed to help you operationalize the core concepts from Lecture 16: Decoding Strategies for Language Models. The goal is to move from theory to practice by experimenting with decoding algorithms, entropy control mechanisms, and generation dynamics in large language models.

You will observe how greedy search, beam search, sampling, temperature scaling, and nucleus sampling influence output quality, diversity, and coherence. There is no submission required. The value comes from experimentation and reflection.

Recommended Programming Environment
The recommended environment for this lab is Python using Google Colab. Colab provides a ready-to-use runtime with optional GPU support and no local installation requirements.

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 as the runtime
Enable GPU (Runtime → Change runtime type → GPU)
Core Libraries
The following libraries will be used:

torch – neural modeling
transformers – pretrained language models
numpy – numerical computation
matplotlib – visualization
datasets – optional dataset utilities

!pip install torch transformers datasets matplotlib
Activity 1: Greedy vs. Beam Search
This activity explores decoding as approximate inference over an exponential search space.

import torch
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "gpt2"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

prompt = "Artificial intelligence will transform"
inputs = tokenizer(prompt, return_tensors="pt")

# Greedy decoding

greedy_output = model.generate(\*\*inputs, max_length=40)
print(tokenizer.decode(greedy_output[0], skip_special_tokens=True))

# Beam search

beam_output = model.generate(\*\*inputs, max_length=40, num_beams=5, early_stopping=True)
print(tokenizer.decode(beam_output[0], skip_special_tokens=True))
Think about:

Why does beam search often produce more complete sentences?
Does maximizing likelihood always produce better text?
Activity 2: Length Bias and Normalization
Sequence probability is multiplicative, which can bias search toward shorter outputs.

for beams in [1, 3, 5, 10]:
output = model.generate(\*\*inputs, max_length=60, num_beams=beams, length_penalty=1.0)
text = tokenizer.decode(output[0], skip_special_tokens=True)
print(f"Beams={beams}, Length={len(text.split())}")

output = model.generate(\*\*inputs, max_length=60, num_beams=5, length_penalty=2.0)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Reflect: Why does increasing length penalty affect output length?

Activity 3: Sampling vs. Deterministic Search

sample_output = model.generate(\*\*inputs, max_length=40, do_sample=True)
print(tokenizer.decode(sample_output[0], skip_special_tokens=True))
Think about:

Why does sampling produce diverse outputs?
When might stochastic decoding be preferable?
Activity 4: Top-k and Top-p Sampling

# Top-k sampling

topk_output = model.generate(\*\*inputs, max_length=40, do_sample=True, top_k=50)
print(tokenizer.decode(topk_output[0], skip_special_tokens=True))

# Top-p (nucleus) sampling

topp_output = model.generate(\*\*inputs, max_length=40, do_sample=True, top_p=0.9)
print(tokenizer.decode(topp_output[0], skip_special_tokens=True))
Compare:

Which produces more natural text?
Which produces more surprising continuations?
Activity 5: Temperature and Entropy

for temp in [0.5, 1.0, 1.5]:
output = model.generate(
\*\*inputs,
max_length=40,
do_sample=True,
temperature=temp,
top_p=0.9
)
print(f"\nTemperature={temp}")
print(tokenizer.decode(output[0], skip_special_tokens=True))
Reflect:

What happens when temperature < 1?
What happens when temperature > 1?
Activity 6: Degeneration and Repetition

long_output = model.generate(\*\*inputs, max_length=150)
print(tokenizer.decode(long_output[0], skip_special_tokens=True))
Think about:

Why does repetition occur?
How does likelihood maximization encourage safe outputs?
Activity 7: Perplexity vs. Human Quality

import torch.nn.functional as F

sentence = "Language models assign probabilities to sequences."
inputs = tokenizer(sentence, return_tensors="pt")

with torch.no_grad():
outputs = model(\*\*inputs, labels=inputs["input_ids"])
loss = outputs.loss
perplexity = torch.exp(loss)

print("Perplexity:", perplexity.item())
Reflect:

Does lower perplexity guarantee better generation?
Why does training objective differ from inference behavior?
Reflection
Why decoding is fundamentally a search problem
Why maximum likelihood training does not fully determine generation quality
How entropy control shapes creativity and coherence
Why degeneration arises from inference dynamics
Key Insight: Decoding strategy is not a minor implementation detail; it fundamentally shapes language model behavior.
