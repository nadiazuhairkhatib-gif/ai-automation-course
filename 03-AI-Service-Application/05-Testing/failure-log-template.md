# U3 — Failure Log

## الهدف

الفشل ليس شيئًا نحاول إخفاءه.

الفشل هو مصدر معلومات هندسية.

---

# Failure Loop

```text id="k4l2qf"
FAILURE
   ↓
EVIDENCE
   ↓
DIAGNOSIS
   ↓
FIX
   ↓
RETEST
   ↓
VERIFY
```

---

# Failure Record

## Failure ID

مثال:

`F-001`

---

## Scenario

ما الذي كنت تحاول فعله؟

---

## Expected Behavior

ما الذي كان يجب أن يحدث؟

---

## Actual Behavior

ماذا حدث فعليًا؟

---

## Evidence

ما الدليل؟

مثلاً:

* Screenshot
* Error Message
* Database Record
* Test Result
* Execution Log

---

## Failure Type

اختر:

* Requirement Failure
* User Flow Failure
* Data Model Failure
* Validation Failure
* Access Control Failure
* Business Rule Failure
* AI Classification Failure
* AI Hallucination
* AI Reliability Failure
* State Management Failure
* Integration Failure
* UI Failure
* Other

---

## Diagnosis

ما السبب المحتمل؟

لا تكتب:

> "AI is bad."

حاول تحديد السبب الأقرب.

مثلاً:

> النظام يعتمد على AI Classification دون Validation أو Human Review.

---

## Fix

ما التغيير الذي أجريته؟

---

## Retest

أعد تشغيل نفس الحالة.

### Result

* Pass
* Fail

---

## Verification

هل حللت المشكلة فعلًا؟

هل أدى الإصلاح إلى مشكلة أخرى؟

هل تحتاج إلى Regression Test؟

---

# Example

### Failure

AI صنف طلبًا غامضًا على أنه Technical Support.

### Expected

طلب غير واضح → Human Review.

### Actual

AI أعطى Category بثقة عالية.

### Evidence

Test Case + AI Output.

### Diagnosis

لا توجد آلية للتعامل مع Low-Confidence / Ambiguous Requests.

### Fix

إضافة Rule:

> إذا كانت المعلومات غير كافية → Human Review.

### Retest

إرسال نفس الطلب.

### Result

Pass.

---

# Engineering Principle

> **Do not say "fixed" until you can reproduce the failure, explain the cause, apply a related change, and verify the result.**
