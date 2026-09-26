# U4 — Evaluation Dataset

## AI Service Request Classification & Response Quality

### Purpose

هذه المجموعة هي **Baseline Evaluation Dataset** التي سنستخدمها لمقارنة V1 وV2.

لا تعدّل الحالات أثناء تشغيل V1.

إذا اكتشفت أن حالة معينة غير مناسبة، سجّل ذلك كـ**Dataset Issue** ولا تغيّرها بصمت.

---

## Allowed Categories

```text
TRAINING_REGISTRATION
TECHNICAL_SUPPORT
ACCOUNT_SUPPORT
GENERAL_INQUIRY
NEEDS_HUMAN_REVIEW
```

---

## Expected Output Schema

```json
{
  "category": "",
  "summary": "",
  "confidence": "",
  "needs_human_review": false
}
```

---

# Normal Cases

## TC-01 — Course Registration

**Input**

> I want to register for the Python course.

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Identify the request as course registration.

**Risk**

Low

---

## TC-02 — Course Schedule

**Input**

> When does the next Python training start?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Recognize that the user is asking about joining/course logistics.

**Risk**

Low

---

## TC-03 — Technical Problem

**Input**

> The training platform keeps showing an error when I upload my assignment.

**Expected Category**

`TECHNICAL_SUPPORT`

**Expected Behavior**

Identify a technical problem with the platform.

**Risk**

Low

---

## TC-04 — Account Access

**Input**

> I forgot my password and cannot log into my account.

**Expected Category**

`ACCOUNT_SUPPORT`

**Expected Behavior**

Identify account access as the primary issue.

**Risk**

Low

---

## TC-05 — General Information

**Input**

> Where is the training center located?

**Expected Category**

`GENERAL_INQUIRY`

**Expected Behavior**

Recognize a general information request.

**Risk**

Low

---

## TC-06 — Course Eligibility

**Input**

> Am I eligible to join the AI Automation course?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Identify the request as related to joining/registration.

**Risk**

Medium

---

## TC-07 — Technical Login Error

**Input**

> I can log into the website, but the dashboard gives me an error.

**Expected Category**

`TECHNICAL_SUPPORT`

**Expected Behavior**

Distinguish a technical dashboard problem from account credentials.

**Risk**

Medium

---

## TC-08 — Registration Confirmation

**Input**

> I submitted my registration yesterday. Can you confirm that I am registered?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Recognize the request as registration-related.

**Risk**

Medium

---

# Ambiguous Cases

## TC-09 — Vague Help Request

**Input**

> I need help.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Do not invent a category without enough information.

**Risk**

High

---

## TC-10 — Ambiguous Problem

**Input**

> Something is wrong with my training.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Request clarification or escalate for human review.

**Risk**

High

---

## TC-11 — Mixed Intent

**Input**

> I cannot log in and I also want to register for the new Python course.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Recognize multiple intents rather than silently selecting one.

**Risk**

High

---

# Missing Information

## TC-12 — Incomplete Technical Request

**Input**

> The system is not working.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Insufficient information for reliable classification.

**Risk**

High

---

## TC-13 — Incomplete Account Request

**Input**

> I have a problem with my account.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Ask for clarification.

**Risk**

High

---

## TC-14 — Incomplete Registration Request

**Input**

> I have a question about the course.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Do not assume registration without additional context.

**Risk**

Medium

---

# Boundary Cases

## TC-15 — Login vs Technical Support

**Input**

> My password works, but the system refuses to open my dashboard.

**Expected Category**

`TECHNICAL_SUPPORT`

**Expected Behavior**

Prioritize the actual technical failure rather than password/account recovery.

**Risk**

High

---

## TC-16 — Registration vs General Inquiry

**Input**

> What are the requirements for joining the Python course?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Recognize that the information is directly related to joining.

**Risk**

Medium

---

## TC-17 — Course Question vs General Information

**Input**

> Is the Python course offered online?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Treat course-specific information as training-related.

**Risk**

Medium

---

# Failure-Oriented Cases

## TC-18 — Unsupported Assumption

**Input**

> Can I register for the advanced AI course?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

The system may classify the request correctly but must not invent eligibility requirements that are not provided.

**Risk**

High

---

## TC-19 — Classification + Hallucination Risk

**Input**

> I want to join the Python course. I heard registration closes tomorrow. Is that correct?

**Expected Category**

`TRAINING_REGISTRATION`

**Expected Behavior**

Classify correctly, but do not confirm the deadline unless the system has evidence for it.

**Risk**

High

---

## TC-20 — High Ambiguity

**Input**

> Please fix this for me.

**Expected Category**

`NEEDS_HUMAN_REVIEW`

**Expected Behavior**

Do not invent what "this" refers to.

**Risk**

High

---

# Dataset Distribution

| Category            |  Cases |
| ------------------- | -----: |
| Normal              |      8 |
| Ambiguous           |      3 |
| Missing Information |      3 |
| Boundary            |      3 |
| Failure-Oriented    |      3 |
| **Total**           | **20** |

---

# Important

هذه الـDataset لا تقيس "ذكاء" النموذج بشكل عام.

هي تقيس:

> **هل النظام يتصرف بالطريقة المطلوبة في سياق محدد ومُعرّف؟**

وهذا فرق أساسي في **AI Evaluation**.

---

# Dataset Principle

> **A good evaluation dataset represents the behaviors that matter, not merely a large number of questions.**
