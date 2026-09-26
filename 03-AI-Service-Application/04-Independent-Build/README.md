# U3 — Independent Build

## المهمة

الآن ستبني نظامًا جديدًا باستخدام نفس طريقة التفكير التي تعلمتها في Guided Build.

لكن:

> **لن تحصل على تصميم جاهز.**

ستحصل على مشكلة، وعليك أن تحوّلها إلى نظام.

---

# السيناريو

اختر أحد السيناريوهات التالية:

### Option A — IT Support

موظفو مؤسسة يرسلون طلبات الدعم التقني، مثل:

* مشكلة في الحساب.
* مشكلة في الجهاز.
* مشكلة في الشبكة.
* مشكلة في برنامج.

---

### Option B — University Student Services

الطلاب يقدمون طلبات مثل:

* التسجيل.
* الوثائق.
* المنح.
* المشاكل الأكاديمية.
* الدعم التقني.

---

### Option C — Community Center Services

المجتمع يرسل طلبات للحصول على خدمات المركز.

مثل:

* التسجيل في نشاط.
* طلب مساعدة.
* الاستفسار عن برنامج.
* حجز خدمة.

---

# Constraint

لا يسمح لك بنسخ Guided Build حرفيًا.

يمكنك استخدام نفس **Engineering Method**، لكن يجب أن يكون:

* Problem مختلفًا.
* Users مختلفين أو Context مختلفًا.
* Requirements مختلفة.
* Data Model مناسبًا للحالة.
* AI Component مبررًا.

---

# المرحلة 1 — Problem

اكتب:

* من يعاني من المشكلة؟
* ما المشكلة؟
* كيف تتم العملية حاليًا؟
* ما الذي لا يعمل؟
* ما النتيجة المطلوبة؟

---

# المرحلة 2 — Users

حدد:

* Actors
* Responsibilities
* Permissions

---

# المرحلة 3 — Requirements

اكتب:

* Functional Requirements
* Non-Functional Requirements

---

# المرحلة 4 — User Stories

اكتب على الأقل:

* 3 User Stories للمستخدم.
* 3 User Stories للموظف أو المسؤول.

---

# المرحلة 5 — Acceptance Criteria

لكل User Story رئيسية، اكتب Acceptance Criteria قابلة للاختبار.

---

# المرحلة 6 — User Flow

ارسم:

```text id="6t1qcx"
User Goal
 ↓
Action
 ↓
System
 ↓
Decision
 ↓
Outcome
```

---

# المرحلة 7 — Data Model

حدد:

* Entities
* Fields
* Relationships
* Current State
* History

---

# المرحلة 8 — AI Boundary

حدد بوضوح:

### AI

ما الذي سيقوم به؟

### Rules

ما الذي ستقوم به القواعد؟

### Human

ما الذي يحتاج قرارًا بشريًا؟

---

# المرحلة 9 — Build

استخدم:

**Lovable + Supabase**

لبناء Professional MVP.

لا تضف Features لا تحتاجها المشكلة.

---

# المرحلة 10 — Test

يجب أن تختبر:

* Happy Path
* Invalid Input
* Missing Data
* Wrong AI Suggestion
* Unauthorized Access
* Invalid State Transition
* AI Failure

---

# المرحلة 11 — Failure

يجب تسجيل **حالة فشل حقيقية واحدة على الأقل**.

لا تبحث عن جعل المشروع يبدو مثاليًا.

نحن نريد أن نرى قدرتك على:

> **Detect → Diagnose → Fix → Retest**

---

# Deliverables

يجب تسليم:

1. Problem Definition
2. Requirements
3. User Stories
4. Acceptance Criteria
5. User Flow
6. Data Model
7. AI / Rules / Human Boundary
8. Working MVP
9. Test Cases
10. Failure Log
11. Improved Version
12. README
13. Demo

---

# Definition of Done

المشروع ليس مكتملًا لأن:

> "Lovable generated the app."

بل عندما تستطيع:

* شرح المشكلة.
* شرح تصميمك.
* تبرير AI.
* شرح Data Model.
* شرح Rules.
* إثبات أن النظام يعمل.
* إثبات أنه يفشل بطريقة مفهومة.
* شرح كيف أصلحت الفشل.

---

# Transfer Question

> **ما الجزء الأصعب في بناء النظام دون إعطائك التصميم مسبقًا؟ ولماذا؟**

هذا السؤال يقيس انتقالك من اتباع Recipe إلى **System Thinking**.
