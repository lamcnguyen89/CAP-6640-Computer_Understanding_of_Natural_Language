Module 7 Self-Guided Lab: Large Language Models, Scaling, and Reasoning
This lab is a self-directed, ungraded activity designed to help you operationalize the core concepts from Lectures 20–22. The goal is to connect architectural design, pretraining objectives, scaling behavior, alignment strategies, retrieval integration, and reasoning evaluation to hands-on experimentation with modern large language models.

You are encouraged to experiment freely. There is no submission required. The value comes from observing model behavior, testing hypotheses, and reflecting on the conceptual foundations discussed in lecture.

Recommended Programming Environment
Use Python in Google Colab for convenient GPU access and library support.

Go to Google ColabLinks to an external site.
Create a new notebook
Select Python 3 runtime
Enable GPU (Runtime → Change runtime type → GPU)
Core Libraries
transformers – pretrained LLMs
torch – neural computation
faiss-cpu – vector retrieval (for RAG-style experiments)
numpy – numerical operations

!pip install torch transformers faiss-cpu numpy
Activity 1: Autoregressive Generation (Decoder-Only LLMs)
This activity operationalizes causal language modeling in decoder-only architectures.

from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

model_name = "gpt2"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

prompt = "The future of artificial intelligence depends on"
inputs = tokenizer(prompt, return_tensors="pt")

output = model.generate(\*\*inputs, max_length=60)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Think about:

How does left-to-right generation constrain representation learning?
What inductive bias does causal modeling introduce?
Activity 2: Masked Language Modeling Contrast
Compare causal generation with masked prediction.

from transformers import AutoModelForMaskedLM

mlm_model = AutoModelForMaskedLM.from_pretrained("bert-base-uncased")
masked_sentence = "Paris is the [MASK] of France."
inputs = tokenizer(masked_sentence, return_tensors="pt")

with torch.no_grad():
outputs = mlm_model(\*\*inputs)

logits = outputs.logits
mask_index = (inputs.input_ids == tokenizer.mask_token_id)[0].nonzero(as_tuple=True)[0]
predicted_token_id = logits[0, mask_index].argmax(dim=-1)
print(tokenizer.decode(predicted_token_id))
Reflect:

How does bidirectional conditioning differ from autoregressive generation?
Why are MLM models strong encoders but weaker generators?
Activity 3: Scaling Effects (Model Size Comparison)
Compare small vs. larger models qualitatively.

small_model = AutoModelForCausalLM.from_pretrained("distilgpt2")
large_model = AutoModelForCausalLM.from_pretrained("gpt2-medium")

for m in [small_model, large_model]:
output = m.generate(\*\*inputs, max_length=60)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Think about:

Does larger parameter count improve coherence?
Does scaling alone produce better reasoning?
Activity 4: Retrieval-Augmented Generation (Simplified)
This activity simulates RAG by retrieving external context before generation.

documents = [
"Neural networks are computational models inspired by the brain.",
"Transformers use self-attention to model long-range dependencies.",
"Reinforcement learning optimizes sequential decision making."
]

query = "How do transformers handle context?"

# Simple similarity via keyword match

retrieved = [doc for doc in documents if "Transformers" in doc]
context = " ".join(retrieved)

prompt = context + " Question: " + query + " Answer:"
inputs = tokenizer(prompt, return_tensors="pt")

output = model.generate(\*\*inputs, max_length=80)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Reflect:

How does conditioning on retrieved context change output?
Why does retrieval reduce hallucination?
Activity 5: Chain-of-Thought Prompting
Evaluate reasoning with and without structured prompting.

question = "If a train travels 60 miles per hour for 2 hours, how far does it go?"

prompt_direct = question
prompt_cot = question + " Let's think step by step."

for p in [prompt_direct, prompt_cot]:
inputs = tokenizer(p, return_tensors="pt")
output = model.generate(\*\*inputs, max_length=80)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Think about:

Does intermediate reasoning improve answer accuracy?
Is the explanation faithful to computation?
Activity 6: Prompt Sensitivity and OOD Robustness
Test small phrasing variations.

variants = [
"What is 15 plus 27?",
"Compute 15 + 27.",
"Add fifteen and twenty-seven."
]

for v in variants:
inputs = tokenizer(v, return_tensors="pt")
output = model.generate(\*\*inputs, max_length=50)
print(tokenizer.decode(output[0], skip_special_tokens=True))
Reflect:

Does performance vary by phrasing?
What does this imply about distributional sensitivity?
Activity 7: Perplexity vs. Reasoning Quality

sentence = "Mathematics requires logical consistency."
inputs = tokenizer(sentence, return_tensors="pt")

with torch.no_grad():
outputs = model(\*\*inputs, labels=inputs["input_ids"])
loss = outputs.loss
perplexity = torch.exp(loss)

print("Perplexity:", perplexity.item())
Think about:

Does lower perplexity imply better reasoning?
Why is next-token likelihood insufficient for reasoning evaluation?
Reflection
How architectural design shapes model capabilities
Why scaling improves performance but not guaranteed reasoning
How alignment shifts model behavior
Why retrieval improves factual grounding
Where LLM reasoning appears statistical versus structured
Final Insight: Modern LLM performance emerges from the interaction of architecture, scaling, alignment, retrieval, and prompting — not scale alone.
