# Decision Brief Output Schema

## Purpose

This schema defines the required structure of the final Decision Brief.

The goal is to transform validated data into a decision-support artifact.

The system must not produce an unrestricted summary.

It must produce a structured output that separates:

* Evidence
* Findings
* Insights
* Recommendations
* Limitations

---

# 1. Decision Question

The final output must begin with the question the analysis is trying to answer.

**Required field:**

```text
decision_question
```

Example:

> Does the program performance support continuing the program, and what should be improved?

---

# 2. Executive Summary

A short summary of the most important findings.

**Required field:**

```text
executive_summary
```

Requirements:

* Maximum 5 sentences.
* No unsupported claims.
* Must reflect the evidence presented below.

---

# 3. Key Findings

List the most important measurable findings.

**Required field:**

```text
key_findings[]
```

Each finding should contain:

```text
metric
value
source
evidence_status
```

Example:

```text
metric: Completion Rate
value: 87.5%
source: Participant Dataset
evidence_status: Verified
```

---

# 4. Evidence

Every important claim must be traceable to a source.

**Required field:**

```text
evidence[]
```

Each evidence item should contain:

```text
claim
source
supporting_data
validation_status
notes
```

Example:

```text
claim: 28 participants completed the program.
source: Participant Dataset
supporting_data: completed = Yes
validation_status: Verified
notes: Cross-check against program report required.
```

---

# 5. Insights

Insights must explain what the evidence may mean.

**Required field:**

```text
insights[]
```

Each insight should contain:

```text
insight
supporting_evidence[]
confidence
```

Important:

An insight must not be presented as a fact.

---

# 6. Recommendations

Recommendations should describe possible actions based on the evidence.

**Required field:**

```text
recommendations[]
```

Each recommendation should contain:

```text
recommendation
reason
supporting_evidence[]
priority
```

Recommendations must not introduce unsupported assumptions.

---

# 7. Data Limitations

The system must explicitly identify limitations in the available data.

**Required field:**

```text
data_limitations[]
```

Possible examples:

* Missing values
* Conflicting sources
* Small sample size
* Incomplete records
* Unclear definitions
* Outdated information
* Unverified assumptions

---

# 8. Open Questions

Some questions cannot be answered using the available evidence.

**Required field:**

```text
open_questions[]
```

Example:

> Why did some participants fail to complete the program?

If the available data does not establish the cause, the system must not invent one.

---

# 9. Final Decision Support

The system may summarize what the evidence currently supports.

**Required field:**

```text
decision_support
```

Structure:

```text
supported_by_evidence
requires_more_evidence
```

The system should distinguish between:

### Supported

What the available evidence reasonably supports.

### Requires More Evidence

What cannot yet be concluded.

---

# 10. Output Rules

The final Decision Brief must follow these rules:

1. Every important quantitative claim must have a source.
2. Missing data must not be treated as zero.
3. Conflicting sources must be identified.
4. Facts must be separated from interpretations.
5. Hypotheses must be labeled as hypotheses.
6. Recommendations must be connected to evidence.
7. Unsupported causal claims are not allowed.
8. AI-generated interpretations must be verified.
9. The final decision remains a human responsibility.
10. Uncertainty must be visible.

---

# 11. Quality Check

Before submitting the Decision Brief, verify:

```text
[ ] Decision question is clearly defined.
[ ] All key metrics have sources.
[ ] Data has been validated.
[ ] Missing values are identified.
[ ] Conflicting sources are identified.
[ ] Facts and interpretations are separated.
[ ] Hypotheses are labeled.
[ ] Insights are supported by evidence.
[ ] Recommendations are evidence-based.
[ ] Limitations are documented.
[ ] Open questions are documented.
[ ] Unsupported claims have been removed.
```

---

# Core Principle

> **The strength of a conclusion must not exceed the strength of its evidence.**
