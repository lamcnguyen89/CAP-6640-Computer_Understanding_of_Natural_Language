# Assignment 8: Bias, Fairness, Privacy, and Responsible NLP

## Overview

This Assignment examines algorithmic bias, formal fairness definitions, auditing methodologies, privacy risks, and governance considerations in NLP systems.

---

---

## Questions

### Question 1: Sources of Bias in NLP Systems

Identify and explain the major sources of bias in NLP systems. Discuss how bias can emerge from:

- Data collection
- Annotation processes
- Representation learning
- Deployment context

**Answer:**

Bias in NLP systems emerges from multiple interconnected sources throughout the pipeline: data collection introduces sampling bias when training corpora fail to represent diverse populations or overrepresent dominant groups; annotation processes embed human biases through labeler demographics, subjective judgments, and inconsistent guidelines; representation learning amplifies statistical patterns that reflect historical inequities, leading models to encode stereotypical associations between protected attributes and outcomes; and deployment context creates new biases when systems trained on one domain are applied to different populations or when prediction errors have asymmetric consequences across demographic groups. These sources compound rather than cancel, making bias a systemic rather than isolated problem.

---

### Question 2: Representation Bias and Embedding Geometry

Explain how bias can manifest in learned representations such as word or contextual embeddings. Describe how embedding geometry can encode associations between demographic attributes and semantic concepts.

**Answer:**

Bias manifests in embedding geometry when the distributional patterns that representations capture reflect societal stereotypes and inequities present in training data, causing vectors for demographic identifiers (e.g., gender terms, ethnic names) to cluster near certain semantic concepts while being distant from others. For example, word embeddings might position "woman" closer to "nurse" and "man" closer to "programmer," or position names associated with certain ethnic groups closer to negative sentiment words, encoding harmful associations in the continuous vector space that downstream models inherit and potentially amplify. These geometric biases can be measured through cosine similarity, projection onto subspaces defined by attribute pairs, or by examining nearest neighbors, revealing how models systematically associate protected characteristics with unrelated semantic features.

---

### Question 3: Formal Fairness Definitions

Define at least two formal fairness criteria used in classification systems (e.g., demographic parity, equalized odds).

Address the following:

- How these criteria are computed
- Why satisfying one may violate another

**Answer:**

Demographic parity requires that positive predictions occur at equal rates across groups (P(Ŷ=1|A=a) = P(Ŷ=1|A=b)), computed by comparing prediction rates, while equalized odds requires that true positive and false positive rates are equal across groups (P(Ŷ=1|Y=y,A=a) = P(Ŷ=1|Y=y,A=b) for y∈{0,1}), computed by stratifying error rates by both true label and group membership. These criteria often conflict because they impose different structural constraints: satisfying demographic parity when base rates differ across groups necessarily violates equalized odds (and vice versa), a mathematical impossibility proven by Chouldechova's theorem, forcing practitioners to make normative choices about which fairness notion matters most for their specific context rather than achieving all simultaneously.

---

### Question 4: Fairness Trade-Offs and Threshold Effects

Explain how classification thresholds influence fairness metrics. Discuss:

- How adjustments to decision thresholds can change group-level outcomes
- Why fairness involves normative trade-offs

**Answer:**

Classification thresholds directly influence fairness metrics because adjusting where predictions transition from negative to positive changes the balance between false positives and false negatives differently across groups: lowering thresholds increases both true and false positive rates, while raising them has the opposite effect, meaning that group-specific or global threshold adjustments can improve one fairness metric (e.g., moving toward demographic parity) while worsening another (e.g., violating equalized odds). Fairness inherently involves normative trade-offs because different stakeholders prioritize different values—some may prioritize equal access (demographic parity), others equal treatment conditional on merit (equalized odds or calibration), and still others might focus on minimizing worst-case harms—and mathematical impossibility results show these cannot generally be satisfied simultaneously, requiring explicit ethical reasoning rather than purely technical solutions.

---

### Question 5: Bias Auditing and Counterfactual Evaluation

Describe systematic approaches to auditing NLP systems for bias. Explain how the following can reveal asymmetric behavior:

- Counterfactual testing
- Controlled prompts
- Matched template evaluation

**Answer:**

Systematic bias auditing employs counterfactual testing by creating minimal input pairs that differ only in demographic attributes (e.g., swapping male/female names or pronouns) and measuring whether model outputs change inappropriately, revealing whether decisions are influenced by protected characteristics rather than task-relevant features. Controlled prompts and matched template evaluation extend this approach by systematically varying demographic markers across standardized sentence templates while holding semantic content constant (e.g., "[Name] is a skilled [profession]" across diverse names), then aggregating predictions to detect asymmetric behavior such as differential sentiment scores, occupation predictions, or toxicity ratings. These methods quantify bias by measuring statistical disparities in model behavior that cannot be explained by legitimate differences in input content, providing evidence of learned associations between demographic attributes and task outputs.

---

### Question 6: Memorization and Privacy Risks

Explain how large language models may memorize training data. Discuss:

- How memorization differs from generalization
- The associated privacy risks

**Answer:**

Large language models can memorize training data by encoding specific sequences verbatim rather than learning generalizable patterns, a phenomenon distinct from generalization where models extract statistical regularities applicable to unseen inputs—memorization can be detected when models reproduce exact training examples, including rare or unique strings, despite being evaluated on held-out prompts. This creates serious privacy risks because models may leak sensitive information such as personal identifiers, medical records, proprietary code, or copyrighted content when prompted appropriately, even if such data appeared infrequently in training; extraction attacks, where adversaries strategically query models to elicit memorized content, have successfully recovered individuals' names, addresses, phone numbers, and other private information from deployed models, violating expectations that training data remains confidential after model release.

---

### Question 7: Dual-Use and Deployment Risk

Define dual-use risk in NLP systems. Discuss:

- How systems designed for beneficial purposes can produce harmful outcomes
- Why deployment decisions require risk assessment

**Answer:**

Dual-use risk refers to the potential for NLP technologies developed for beneficial applications to be repurposed or misused for harmful ends: text generation models intended to assist writers can produce misinformation or spam at scale; translation systems can enable surveillance of minority language speakers; and sentiment analysis tools designed for customer feedback can be deployed for employee monitoring or political suppression. Deployment decisions require careful risk assessment because model capabilities, once released, cannot be easily controlled or revoked—different contexts create different risk profiles (e.g., a resume screening tool has higher stakes than a game NPC), different populations face asymmetric vulnerabilities (e.g., marginalized groups suffer disproportionate harms from failures), and unintended uses may emerge after deployment, necessitating proactive evaluation of potential misuse, impact assessment across stakeholder groups, and ongoing monitoring rather than one-time technical validation.

---

### Question 8: Responsible Deployment and Governance

Explain why bias mitigation is not a one-time technical fix. Discuss the role of:

- Documentation
- Monitoring
- Governance mechanisms

in ensuring responsible NLP system deployment.

**Answer:**

Bias mitigation cannot be a one-time technical fix because systems operate in dynamic environments where data distributions shift, user populations change, and societal norms evolve, requiring continuous attention rather than deployment-and-forget approaches. Documentation practices such as model cards and datasheets establish transparency by recording training data characteristics, known limitations, intended use cases, and fairness evaluations, enabling downstream users to make informed decisions; monitoring involves ongoing measurement of deployed system behavior across demographic groups, tracking performance degradation and emergent biases in production; and governance mechanisms including ethical review boards, stakeholder consultation, feedback channels, and clear accountability structures ensure that technical interventions align with organizational values and affected communities have meaningful input. Together, these sociotechnical practices create accountable systems where bias mitigation is an ongoing organizational commitment rather than a preprocessing step.

**Answer:**
