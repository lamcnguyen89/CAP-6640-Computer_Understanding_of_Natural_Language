# Assignment 8: Bias, Fairness, Privacy, and Responsible NLP

## Overview

This Assignment examines algorithmic bias, formal fairness definitions, auditing methodologies, privacy risks, and governance considerations in NLP systems.

## Questions

### Question 1: Sources of Bias in NLP Systems

Identify and explain the major sources of bias in NLP systems. Discuss how bias can emerge from:

- Data collection
- Annotation processes
- Representation learning
- Deployment context

**Answer:**

Bias in NLP systems emerges from multiple related sources throughout training and inference:

1. data collection introduces sampling bias when training corpora fails to represent diverse populations or overrepresent dominant groups

2. annotation processes embed human biases through labeler demographics, subjective judgments, and inconsistent guidelines

3. representation learning amplifies patterns that reflect real life inequality, leading models to encode stereotypes between protected attributes and outcomes

4. deployment context creates new biases when systems trained on one domain are applied to different populations or when prediction errors have asymmetric consequences across demographics. These sources compound rather than cancel, making bias systematic.

---

### Question 2: Representation Bias and Embedding Geometry

Explain how bias can manifest in learned representations such as word or contextual embeddings. Describe how embedding geometry can encode associations between demographic attributes and semantic concepts.

**Answer:**

Bias manifests in embedding geometry when the distributional patterns that representations capture reflect social stereotypes and inequality present in training data. This causes vectors for demographic to cluster near certain semantic concepts while being distant from others.

For example, word embeddings might position "woman" closer to "nurse" and "man" closer to "programmer," or position names associated with certain ethnic groups closer to negative sentiment words, encoding harmful associations in the continuous vector space. These biases can be measured through cosine similarity, projection onto subspaces defined by attribute pairs, or by examining nearest neighbors, revealing how models associate characteristics with unrelated semantic features.

---

### Question 3: Formal Fairness Definitions

Define at least two formal fairness criteria used in classification systems (e.g., demographic parity, equalized odds).

Address the following:

- How these criteria are computed
- Why satisfying one may violate another

**Answer:**

Demographic parity requires that positive predictions occur at equal rates across groups (P(Ŷ=1|A=a) = P(Ŷ=1|A=b)). Demographic Parity is computed by comparing prediction rates.

Equalized odds require that true positive and false positive rates are equal across groups (P(Ŷ=1|Y=y,A=a) = P(Ŷ=1|Y=y,A=b) for y∈{0,1}). Equalized odds are computed by stratifying error rates by both true label and group membership.

These criteria usually conflict because they create different constraints: satisfying demographic parity when base rates differ across groups violates equalized odds (and vice versa). It is mathematical impossibility proven by Chouldechova's theorem. Designers of the models have to balance the 2 criteria.

---

### Question 4: Fairness Trade-Offs and Threshold Effects

Explain how classification thresholds influence fairness metrics. Discuss:

- How adjustments to decision thresholds can change group-level outcomes
- Why fairness involves normative trade-offs

**Answer:**

Classification thresholds influence fairness metrics because adjusting where predictions transition from negative to positive, changes the balance between false positives and false negatives differently across groups.

Lowering thresholds increases both true and false positive rates. Raising them means that group-specific or global threshold adjustments can improve one fairness metric while worsening another.

Fairness involves trade-offs because different groups have different values. Some may prioritize equal access (demographic parity), others equal treatment conditional on merit (equalized odds or calibration). Others might focus on minimizing harm. You can't satisfy everybody.

---

### Question 5: Bias Auditing and Counterfactual Evaluation

Describe systematic approaches to auditing NLP systems for bias. Explain how the following can reveal asymmetric behavior:

- Counterfactual testing
- Controlled prompts
- Matched template evaluation

**Answer:**

Systematic bias auditing employs counterfactual testing by creating minimal input pairs that differ only in demographic attributes and measuring whether model outputs change inappropriately. This reveals whether decisions are influenced by protected characteristics rather than task-relevant features.

Controlled prompts and matched template evaluation extend this approach by systematically varying demographic markers across sentence templates while holding semantic content constant, then combining predictions to detect asymmetric behavior such as differential sentiment scores, occupation predictions, or toxicity ratings.

These methods quantify bias by measuring disparities in model behavior that cannot be explained by legit differences in input content, providing evidence of learned associations between demographic attributes and task outputs.

---

### Question 6: Memorization and Privacy Risks

Explain how large language models may memorize training data. Discuss:

- How memorization differs from generalization
- The associated privacy risks

**Answer:**

LLMs can memorize training data by encoding specific sequences exactly rather than learning generalizable patterns. This is different from generalization where models extract statistical regularities that can work with novel inputs.

Memorization can be detected when models reproduce exact training examples, including rare or unique strings, despite being evaluated on held-out prompts. This creates serious privacy risks because models may leak sensitive information such as personal identifiers, medical records, proprietary code, or copyrighted content when prompted appropriately.

Extraction attacks, where adversaries strategically query models to elicit memorized content, have recovered individuals' names, addresses, phone numbers, and other private information from deployed models.

---

### Question 7: Dual-Use and Deployment Risk

Define dual-use risk in NLP systems. Discuss:

- How systems designed for beneficial purposes can produce harmful outcomes
- Why deployment decisions require risk assessment

**Answer:**

Dual-use risk is the potential for NLP technologies to be repurposed or misused for harmful ends.

- Text generation models intended to assist writers can produce misinformation or spam at scale
- translation systems can enable surveillance of minority language speakers
- sentiment analysis tools designed for customer feedback can be deployed for employee monitoring or political suppression.

Once deployed, models cannot be easily controlled or removed. Different contexts create different risk profiles (ex. resume screening tool has higher stakes than video game AI). Different populations face more or less vulnerabilities (racial and gender minorities). Unintended uses may emerge after deployment.

These risks require thorough and creative evaluation of potential misuse and continuous monitoring in the real world.

---

### Question 8: Responsible Deployment and Governance

Explain why bias mitigation is not a one-time technical fix. Discuss the role of:

- Documentation
- Monitoring
- Governance mechanisms

in ensuring responsible NLP system deployment.

**Answer:**

Bias mitigation cannot be a one-time technical fix because systems operate in dynamic environments where data distributions shift, user populations change, and societal norms evolve. This requires continuous attention and monitoring.

Documentation practices such as model cards and datasheets establish transparency by recording training data characteristics, known limitations, intended use cases, and fairness evaluations.

Monitoring involves ongoing measurement of deployed system behavior across demographics and tracking performance degradation and emergent biases in the real world.

Governance mechanisms like ethical review boards increase the chances that technical interventions align with organizational values and affected communities.
