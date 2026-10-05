# 02 — Workflow Decomposition

> **Layer 02 — Decompose the Work**

في الملف السابق فهمنا العمل الذي نريد تحسينه:

> **Client Request Intake & Routing**

حددنا:

* Work
* Problem
* Pain Point
* Current State
* Desired Outcome
* Success Criteria

الآن ننتقل إلى السؤال التالي:

> **كيف يتكون هذا العمل فعليًا؟**

قبل أن نبني أي Automation، نحتاج إلى تفكيك العمل إلى أجزاء واضحة يمكن فهمها وتصميمها واختبارها.

المبدأ:

> **Don't automate a vague process. Decompose it first.**

---

# 1. From Work to Workflow

العمل الذي نريد تحسينه ليس خطوة واحدة.

إنه مجموعة من الأنشطة المرتبطة ببعضها.

سنستخدم التسلسل التالي:

```text
Process
   ↓
Workflow
   ↓
Task
   ↓
Subtask
   ↓
Sequence
   ↓
Dependency
```

كل مفهوم يجيب عن سؤال مختلف.

| Concept    | السؤال                            |
| ---------- | --------------------------------- |
| Process    | ما العمل الأكبر الذي نريد إنجازه؟ |
| Workflow   | ما المسار المحدد الذي سنصممه؟     |
| Task       | ما وحدة العمل التي يجب تنفيذها؟   |
| Subtask    | ما الأجزاء الأصغر داخل الـTask؟   |
| Sequence   | بأي ترتيب تحدث الخطوات؟           |
| Dependency | لماذا تعتمد خطوة على خطوة أخرى؟   |

---

# 2. Process

## ما هو الـProcess؟

الـ**Process** هو مجموعة منظمة من الأنشطة التي تعمل معًا لتحقيق نتيجة معينة.

في مشروعنا:

> **Client Request Intake & Routing Process**

ويمكن تمثيله بشكل عام:

```text
Receive Request
      ↓
Understand Request
      ↓
Process Information
      ↓
Determine Next Step
      ↓
Route Request
      ↓
Follow Up / Take Action
```

هذا هو العمل الأكبر.

لكننا لا نريد أتمتة كل شيء داخل الشركة.

نحتاج إلى تحديد **Workflow** محدد.

---

# 3. Workflow

## ما هو الـWorkflow؟

الـ**Workflow** هو مسار محدد داخل الـProcess، يبدأ من حدث أو **Trigger** وينتهي بنتيجة واضحة.

في مشروعنا سنبني:

> **Client Request Intake & Routing Workflow**

المسار المستهدف:

```text
Client Request
      ↓
Understand
      ↓
Extract
      ↓
Validate
      ↓
Decide
      ↓
Route
      ↓
Record / Notify / Human Review
```

لاحظ الفرق:

```text
Process
= Client Request Intake & Routing Process

Workflow
= المسار المحدد الذي سنقوم بتصميمه وأتمتته
```

---

# 4. Workflow Boundary

حتى لا يتوسع المشروع، نحدد نقطة البداية والنهاية.

## Start

يبدأ الـWorkflow عندما:

> **New Client Request is received.**

## End

ينتهي عندما:

> **The request is appropriately routed, recorded, or escalated to a human.**

إذن:

```text
START
New Client Request
      ↓
      ...
      ↓
END
Request Routed / Recorded / Escalated
```

أي شيء خارج هذه الحدود ليس جزءًا أساسيًا من الـWorkflow الذي نبنيه في U1.

---

# 5. Tasks

الـ**Task** هي وحدة عمل لها نتيجة واضحة.

يمكننا تفكيك الـWorkflow إلى Tasks:

```text
Task 01 — Receive Request
Task 02 — Understand Request
Task 03 — Extract Information
Task 04 — Validate Information
Task 05 — Determine Next Step
Task 06 — Route Request
Task 07 — Record Result
Task 08 — Notify / Escalate
```

كل Task يجب أن يجيب عن:

> **What needs to be accomplished?**

وليس:

> Which tool should I use?

---

# 6. Task 01 — Receive Request

### الهدف

استقبال طلب العميل وإدخاله إلى النظام.

### Input

Client Request.

### Output

طلب يمكن للنظام معالجته.

```text
Client
  ↓
Request
  ↓
System
```

في هذه المرحلة لا نحتاج إلى فهم محتوى الطلب بعد.

---

# 7. Task 02 — Understand Request

### الهدف

فهم ما يريده العميل.

مثال:

> "نحتاج موقعًا لشركتنا الجديدة."

النظام يحتاج إلى فهم أن العميل يتحدث عن:

```text
Service Type → Website
```

هذه Task مناسبة لاستخدام **AI** لأنها تعتمد على فهم اللغة الطبيعية.

لكن في هذا الملف لا نصمم الـAI بعد.

نحن فقط نحدد:

> ما العمل المطلوب؟

---

# 8. Task 03 — Extract Information

بعد فهم الطلب، نحتاج إلى استخراج المعلومات المهمة.

مثلاً:

```text
Service
Timeline
Budget
Company / Client
Description
```

من:

> "نريد موقعًا لشركتنا الجديدة ونحتاجه الشهر القادم، لكن الميزانية لم نحددها بعد."

نحصل مبدئيًا على:

```text
Service → Website
Timeline → Next Month
Budget → Missing
```

هذه الـTask ستصبح مهمة جدًا في **Data Design**.

---

# 9. Task 04 — Validate Information

بعد استخراج البيانات لا نفترض أنها صحيحة وكاملة.

نحتاج إلى التحقق:

```text
Are required fields present?
        ↓
Are values valid?
        ↓
Is information sufficient?
        ↓
Is anything ambiguous?
```

مثال:

```text
Timeline = "soon"
```

هل هذا موعد واضح؟

لا.

إذن:

```text
Ambiguous Information
        ↓
Validation Result
        ↓
Exception / Human Review
```

---

# 10. Task 05 — Determine Next Step

بعد الـValidation نحتاج إلى تحديد ماذا يحدث بعد ذلك.

مثلاً:

```text
Complete + Valid
       ↓
Continue

Missing / Ambiguous
       ↓
Human Review
```

هذه ليست بالضرورة مهمة AI.

إذا كانت القاعدة واضحة، يمكن استخدام:

> **Deterministic Logic**

مثال:

```text
IF required_information is missing
THEN requires_human = true
```

---

# 11. Task 06 — Route Request

بعد اتخاذ القرار، يجب توجيه الطلب.

مثلاً:

```text
Website Request
       ↓
Web Team

Marketing Request
       ↓
Marketing Team

Other / Unclear
       ↓
Human Review
```

في هذه المرحلة نحدد **Routing Logic**.

لكن لا نحدد أداة التنفيذ بعد.

---

# 12. Task 07 — Record Result

نحتاج إلى الاحتفاظ بنتيجة معالجة الطلب.

مثلاً:

```text
Request ID
Client
Request Type
Extracted Information
Validation Status
Routing
Human Review Required
Timestamp
```

الهدف هو أن يكون لدينا **Structured Record** يمكن الرجوع إليه.

---

# 13. Task 08 — Notify / Escalate

في النهاية يجب أن يعرف الشخص أو الفريق المناسب ماذا حدث.

هناك مساران:

### Normal Path

```text
Valid Request
     ↓
Route
     ↓
Record
     ↓
Notify Team
```

### Exception Path

```text
Missing / Ambiguous / Unclear
     ↓
Human Review
     ↓
Record
     ↓
Notify Responsible Person
```

---

# 14. Subtasks

ليست كل Task بسيطة.

يمكن أن تحتوي Task على **Subtasks**.

مثلاً:

## Task — Extract Information

يمكن تفكيكها إلى:

```text
Extract Information
       ↓
Identify Request Type
       ↓
Extract Service
       ↓
Extract Timeline
       ↓
Extract Budget
       ↓
Identify Missing Information
```

مثال آخر:

## Task — Validate Information

```text
Validate Information
       ↓
Check Required Fields
       ↓
Check Data Format
       ↓
Check Missing Information
       ↓
Check Ambiguity
       ↓
Determine Validation Status
```

إذن:

> **Task = وحدة عمل**

بينما:

> **Subtask = جزء أصغر من تنفيذ الـTask.**

---

# 15. Sequence

الـ**Sequence** يصف ترتيب حدوث الخطوات.

في مشروعنا:

```text
1. Receive Request
2. Understand Request
3. Extract Information
4. Validate Information
5. Determine Next Step
6. Route Request
7. Record Result
8. Notify / Escalate
```

لا يمكننا مثلًا أن نقوم بـ:

```text
Route Request
```

قبل أن نعرف:

```text
What is the request?
```

ولا يمكننا اتخاذ قرار نهائي قبل:

```text
Validation
```

إذن الترتيب ليس عشوائيًا.

---

# 16. Dependency

الـ**Dependency** تعني أن خطوة تعتمد على نتيجة أو معلومات من خطوة أخرى.

وهنا يوجد فرق مهم:

> **Sequence tells us the order.**

بينما:

> **Dependency tells us why one step relies on another.**

مثال:

```text
Understand Request
        ↓
Extract Information
```

لماذا تعتمد `Extract Information` على `Understand Request`؟

لأننا نحتاج إلى فهم ما يتعلق به الطلب حتى نعرف ما المعلومات التي نبحث عنها.

مثال آخر:

```text
Extract Information
        ↓
Validate Information
```

الـValidation تعتمد على البيانات التي تم استخراجها.

ومثال:

```text
Validate Information
        ↓
Determine Next Step
```

لا يمكننا تحديد المسار النهائي قبل معرفة حالة البيانات.

---

# 17. Dependency Map

يمكن تمثيل العلاقات الأساسية:

```text
Receive Request
      │
      ▼
Understand Request
      │
      ▼
Extract Information
      │
      ▼
Validate Information
      │
      ▼
Determine Next Step
      │
      ├───────────────┐
      ▼               ▼
   Valid           Exception
      │               │
      ▼               ▼
   Routing       Human Review
      │               │
      └───────┬───────┘
              ▼
        Record Result
              │
              ▼
       Notify / Escalate
```

---

# 18. Normal Path vs Exception Path

من المهم ألا نصمم Workflow وكأن كل الطلبات متشابهة.

لدينا على الأقل مساران.

## Normal Path

```text
Request
   ↓
Understand
   ↓
Extract
   ↓
Validate
   ↓
Valid
   ↓
Route
   ↓
Record
   ↓
Notify
```

## Exception Path

```text
Request
   ↓
Understand
   ↓
Extract
   ↓
Validate
   ↓
Missing / Ambiguous
   ↓
Human Review
   ↓
Record
   ↓
Notify
```

وهذا يمهد مباشرة لمفهوم:

> **Exception → Human-in-the-Loop → Safe Automation**

الذي سنبنيه بالتفصيل في الملف الرابع.

---

# 19. Complete Workflow Decomposition

الآن نستطيع رؤية الـWorkflow كاملًا:

```text
PROCESS
Client Request Intake & Routing
        │
        ▼
WORKFLOW
Client Request Intake & Routing Workflow
        │
        ├── TASK 01
        │   Receive Request
        │
        ├── TASK 02
        │   Understand Request
        │
        ├── TASK 03
        │   Extract Information
        │
        ├── TASK 04
        │   Validate Information
        │
        ├── TASK 05
        │   Determine Next Step
        │
        ├── TASK 06
        │   Route Request
        │
        ├── TASK 07
        │   Record Result
        │
        └── TASK 08
            Notify / Escalate
```

---

# 20. From Workflow to Automation Thinking

حتى الآن لم نقرر:

* أي Tool سنستخدم.
* أين نضع AI.
* ما هو الـPrompt.
* كيف سيكون الـJSON.
* كيف نبني الـZap.

وهذا مقصود.

لقد قمنا أولًا بتحديد:

```text
What work happens?
        ↓
What are the steps?
        ↓
What depends on what?
```

الخطوة التالية هي:

> **What data enters each step, and what data comes out?**

وهنا ننتقل إلى:

# Layer 03 — Understand the Input & Data

سنبدأ في الملف التالي بتحليل:

```text
Trigger
 ↓
Input
 ↓
Unstructured Data
 ↓
Structured Data
 ↓
Missing Information
 ↓
Validation
```

وسنحدد **Data Schema** الذي سيستخدمه النظام فعليًا قبل أن نكتب أي Prompt أو نبني أي Zap.

::
