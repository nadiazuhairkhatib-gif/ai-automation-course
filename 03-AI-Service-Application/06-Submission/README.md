# U3 Submission

## AI Service Management Platform

### هدف التسليم

في هذه الوحدة لا يتم تقييم قدرتك على جعل **Lovable** يبني تطبيقاً بسرعة.

يتم تقييم قدرتك على:

> **Design → Build → Test → Break → Diagnose → Fix → Explain**

أي أنك لا تقدم تطبيقاً فقط؛ بل تقدم **دليلاً هندسياً** على أنك تفهم النظام الذي بنيته.

---

# 1. Required Submission

يجب أن يحتوي تسليمك على:

```text
01 Problem Definition
02 Requirements
03 User Stories
04 Acceptance Criteria
05 User Flow
06 Data Model
07 AI / Rules / Human Boundary
08 Working MVP
09 Test Cases
10 Failure Log
11 Improved Version
12 README
13 Demo
```

---

# 2. Problem Definition

اشرح:

* المشكلة.
* المستخدمون.
* العملية الحالية.
* نقاط الألم.
* النتيجة المطلوبة.

لا تبدأ بشرح الأداة.

---

# 3. System Design

أرفق:

* Requirements
* User Stories
* Acceptance Criteria
* User Flow
* Data Model
* Business Rules
* AI Boundary

يجب أن تكون هذه العناصر متسقة مع بعضها.

مثلاً:

إذا كان Requirement يقول:

> Staff can assign requests.

فيجب أن يظهر ذلك في:

* User Story
* Acceptance Criteria
* User Flow
* Data Model
* Application

---

# 4. Working MVP

يجب أن يستطيع الـMVP تنفيذ الرحلة الأساسية.

### Minimum Flow

```text
Create Request
      ↓
Validate
      ↓
Store
      ↓
AI Suggestions
      ↓
Staff Review
      ↓
Assignment
      ↓
Status Update
      ↓
User Tracking
```

---

# 5. AI Boundary

وضح:

### What AI does

```text
1.
2.
3.
```

### What AI does NOT do

```text
1.
2.
3.
```

### What Rules control

```text
1.
2.
3.
```

### What requires Human Review

```text
1.
2.
3.
```

---

# 6. Testing Evidence

يجب تنفيذ **12 اختباراً على الأقل**.

ويجب أن تشمل الاختبارات:

* Happy Path
* Validation
* Access Control
* AI Success
* AI Ambiguity
* AI Failure
* Business Rules
* State Management
* Data Integrity

لكل اختبار:

```text
Test ID
Scenario
Expected Result
Actual Result
Evidence
Result
```

---

# 7. Failure Evidence

يجب أن يحتوي المشروع على **Failure Log** واحد على الأقل.

ليس المطلوب أن يكون النظام مثالياً.

بل المطلوب أن تثبت أنك استطعت:

```text
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

### ممنوع

> "عدلت الـprompt وصار يعمل."

### المطلوب

> "حدث الفشل في الحالة X، وكانت النتيجة Y بدلاً من Z. حددت السبب بأنه ... ثم غيّرت ... وأعدت الاختبار، فنجح في ..."

---

# 8. Demo

مدة العرض:

**5–7 minutes**

يجب أن يتضمن:

### 1. Problem

ما المشكلة؟

### 2. System

كيف صممت الحل؟

### 3. Demo

اعرض المسار الأساسي.

### 4. AI

أين استخدمت AI؟

### 5. Failure

اعرض حالة فشل أو Boundary Case.

### 6. Fix

ماذا غيّرت؟

### 7. Evidence

كيف أثبت أن الإصلاح نجح؟

---

# 9. Defense Questions

يجب أن تكون قادراً على الإجابة:

1. لماذا اخترت هذه المشكلة؟
2. من هم المستخدمون؟
3. ما أهم Requirement؟
4. لماذا اخترت هذا User Flow؟
5. ما البيانات التي يحتاجها النظام؟
6. أين تستخدم AI؟
7. لماذا لا تستخدم AI في كل شيء؟
8. ماذا يحدث إذا فشل AI؟
9. كيف تمنع User من الوصول إلى بيانات User آخر؟
10. ما Status Transitions المسموحة؟
11. ما أكبر Failure وجدته؟
12. كيف عرفت سبب الفشل؟
13. ماذا غيّرت؟
14. كيف أثبت أن الإصلاح نجح؟
15. ماذا ستغير لو كان لديك وقت إضافي؟

---

# 10. Definition of Done

يُعتبر المشروع مكتملاً عندما:

* [ ] النظام يعمل.
* [ ] المشكلة واضحة.
* [ ] التصميم موثق.
* [ ] MVP Boundary واضحة.
* [ ] AI Boundary واضحة.
* [ ] Business Rules مطبقة.
* [ ] 12+ Test Cases منفذة.
* [ ] Failure موثق.
* [ ] Diagnosis موثق.
* [ ] Fix مطبق.
* [ ] Retest ناجح.
* [ ] Evidence موجود.
* [ ] README مكتمل.
* [ ] Demo جاهز.
* [ ] الطالب يستطيع الدفاع عن قرارات التصميم.

---

# 11. What Is Being Evaluated?

لا يتم تقييمك فقط على:

> "هل التطبيق يعمل؟"

بل على:

### Thinking

هل فهمت المشكلة؟

### Design

هل صممت النظام قبل البناء؟

### Engineering

هل قسمت المسؤوليات بين AI وRules وHuman؟

### Testing

هل اختبرت الحدود وليس فقط Happy Path؟

### Debugging

هل تستطيع تشخيص الفشل؟

### Evidence

هل تستطيع إثبات أن الحل يعمل؟

### Explanation

هل تستطيع شرح لماذا بنيته بهذه الطريقة؟

---

## Final Principle

> **A successful demo is not evidence of reliability.**

المشروع الجيد ليس المشروع الذي لم يفشل.

المشروع الجيد هو المشروع الذي:

> **يفشل → يكشف الفشل → يشخّص السبب → يُصلح → يُعاد اختباره → ويثبت التحسن.**
