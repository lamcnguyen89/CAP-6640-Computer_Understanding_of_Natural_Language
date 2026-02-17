# Assignment 3: Language Modeling and Sequence Learning

> **Available:** Jan 15, 2026 12:00am until Feb 25, 2026 11:59pm

## Overview

This assignment examines probabilistic and neural approaches to language modeling, sequence modeling with recurrent neural networks, and sequence-to-sequence architectures. All questions are based strictly on the material covered in **Lectures 8, 9, and 10**. Each question consists of two parts and requires precise, technically grounded answers.

**Note:** This is an individual assignment. Clarity, correctness, and depth of reasoning are expected.

---

## Questions

### Question 1: Language Modeling Fundamentals (Lecture 8)

**(A)** Define a language model formally and explain how language modeling is framed as a next-word prediction problem.

**(B)** Explain how assigning probabilities to entire sentences follows from next-word prediction.

---

### Question 2: N-Gram Language Models (Lecture 8)

**(A)** Explain the n-gram independence assumption and how it simplifies probability estimation.

**(B)** Using an example, explain how increasing the value of n affects modeling power and data requirements.

---

### Question 3: Sparsity and Smoothing (Lecture 8)

**(A)** Explain why data sparsity is a fundamental problem in n-gram language models.

**(B)** Describe smoothing, backoff, or interpolation and explain how these techniques partially address sparsity.

---

### Question 4: Fixed-Window Neural Language Models (Lecture 8)

**(A)** Describe how fixed-window neural language models predict the next word using a feedforward network.

**(B)** Explain why fixed-window neural models still fail to capture long-range dependencies.

---

### Question 5: Recurrent Language Models (Lecture 9)

**(A)** Explain how recurrent neural networks model sequential dependencies using hidden states.

**(B)** Explain how an RNN language model generates text autoregressively.

---

### Question 6: Training RNNs and Backpropagation Through Time (Lecture 9)

**(A)** Describe backpropagation through time (BPTT) and explain why the RNN must be unrolled during training.

**(B)** Explain why training RNNs is more challenging than training feedforward neural networks.

---

### Question 7: Vanishing Gradients and Gated Architectures (Lecture 9)

**(A)** Explain the vanishing gradient problem in recurrent neural networks.

**(B)** Explain how gated architectures such as LSTMs or GRUs mitigate this problem.

---

### Question 8: Sequence-to-Sequence Models and Attention (Lecture 10)

**(A)** Explain the encoder–decoder architecture and how sequence-to-sequence models perform conditional generation.

**(B)** Explain why attention mechanisms improve sequence-to-sequence models compared to fixed-length context representations.

---

## Submission Guidelines

- Submit a single PDF document
- Clearly label each question and part (A, B)
- Answers should be concise, technical, and well-structured
- Do not include material beyond Lectures 8–10
- Each question is worth 5 pts (total: 40 pts)
