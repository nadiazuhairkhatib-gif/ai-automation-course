# U3 — Testing

## الهدف

نحن لا نختبر فقط إذا كان التطبيق "يعمل".

نختبر:

> **هل النظام يعمل كما صممناه؟**

وهل يتصرف بشكل آمن عندما تحدث حالات غير متوقعة؟

---

# Testing Loop

```text id="3d7v1x"
Requirement
 ↓
Test Case
 ↓
Run
 ↓
Expected vs Actual
 ↓
Failure?
 ↓
Diagnose
 ↓
Fix
 ↓
Retest
```

---

# Test Cases

## TC-01 — Valid Request

### Scenario

User creates a valid request.

### Expected

* Request created.
* Data stored.
* Request ID generated.
* Status = NEW.

---

## TC-02 — Missing Required Field

### Scenario

User submits request without Description.

### Expected

* Request rejected.
* Validation message shown.
* No incomplete request stored.

---

## TC-03 — User Data Isolation

### Scenario

User A attempts to access User B's request.

### Expected

**Access Denied**

---

## TC-04 — AI Classification

### Scenario

Submit a clear technical support request.

### Expected

AI suggests an appropriate category.

---

## TC-05 — Ambiguous Request

### Scenario

User submits:

> "I need help."

### Expected

System should not confidently invent a specific category.

Possible outcome:

**Needs Human Review**

---

## TC-06 — AI Failure

### Scenario

AI service becomes unavailable.

### Expected

* Request remains stored.
* System does not lose the request.
* Staff can continue manually.

---

## TC-07 — Priority Suggestion

### Scenario

Submit a request with an urgent context.

### Expected

AI suggests an appropriate priority.

Staff remains able to change it.

---

## TC-08 — Unauthorized Assignment

### Scenario

Regular User attempts to assign a Request to a Staff Member.

### Expected

**Access Denied**

---

## TC-09 — Invalid Status Transition

### Scenario

Try to move:

```text id="2n8g2g"
NEW → RESOLVED
```

when the transition is not allowed.

### Expected

Transition blocked.

---

## TC-10 — Valid Status Transition

### Scenario

Move:

```text id="i4l2rc"
NEW
→
IN_REVIEW
→
ASSIGNED
→
IN_PROGRESS
→
RESOLVED
```

### Expected

Each allowed transition succeeds.

---

## TC-11 — Original Data Preservation

### Scenario

AI generates a summary or classification.

### Expected

The original user description remains unchanged.

---

## TC-12 — AI Suggestion vs Final Decision

### Scenario

AI suggests Category A.

Staff selects Category B.

### Expected

* AI suggestion remains traceable.
* Final Category = B.
* System does not overwrite the human decision with AI output.

---

# Test Record

لكل Test Case سجّل:

| Field        | Description              |
| ------------ | ------------------------ |
| Test ID      | TC-XX                    |
| Scenario     | ماذا اختبرت؟             |
| Expected     | ماذا يجب أن يحدث؟        |
| Actual       | ماذا حدث؟                |
| Result       | Pass / Fail              |
| Evidence     | Screenshot / Error / Log |
| Failure Type | نوع الفشل                |
| Diagnosis    | سبب محتمل                |
| Fix          | التعديل                  |
| Retest       | النتيجة بعد الإصلاح      |

---

# Minimum Requirement

يجب تنفيذ:

> **12 Test Cases**

ويجب أن تحتوي النتائج على:

* Happy Path
* Validation
* Access Control
* AI Behavior
* AI Failure
* State Management
* Data Integrity

---

# Engineering Rule

> **A successful demo is not evidence of reliability.**

قد يعمل النظام في الحالة المثالية ويفشل في أول حالة مختلفة.

لذلك:

> **Test the boundaries, not only the happy path.**
