# 01 — Business Analysis

> **Layer 01 — Understand the Work**

هذا الملف هو نقطة البداية في المشروع.

قبل أن نستخدم **AI** أو **Zapier** أو نصمم أي **Automation**، يجب أولًا أن نفهم العمل الذي نريد تحسينه.

المبدأ:

> **Think First. Build Later.**

---

# 1. Business Scenario

نحن نعمل مع شركة خدمات تستقبل طلبات العملاء عبر **Email** أو **Form**.

قد يرسل العميل طلبًا مثل:

> "مرحبًا، نريد موقعًا لشركتنا الجديدة، ونفضل أن يكون جاهزًا الشهر القادم، لكننا لم نحدد الميزانية بعد."

الطلب مفهوم للإنسان، لكنه بالنسبة للنظام عبارة عن **Unstructured Data**.

الموظف يحتاج إلى قراءة الطلب وفهمه واستخراج المعلومات المهمة وتحديد ما يجب أن يحدث بعد ذلك.

مع زيادة عدد الطلبات، يصبح هذا العمل متكررًا ويحتاج إلى طريقة أكثر تنظيمًا.

---

# 2. Work

## What is the Work?

الـ**Work** هو العمل الذي تقوم به الشركة للوصول إلى نتيجة معينة.

في حالتنا:

> **استقبال طلبات العملاء وفهمها ومعالجتها وتوجيهها إلى الإجراء أو الشخص المناسب.**

بشكل مبسط:

```text
Receive Client Request
        ↓
Understand Request
        ↓
Collect Required Information
        ↓
Determine Next Step
        ↓
Route Request
        ↓
Follow Up / Take Action
```

### السؤال الذي نطرحه:

> **What work are we improving?**

الإجابة:

> نحن نحسن عملية **Client Request Intake & Routing**.

---

# 3. Problem

## ما المشكلة؟

المشكلة ليست أن الشركة "لا تستخدم AI".

المشكلة هي أن معالجة طلبات العملاء تعتمد بشكل كبير على العمل اليدوي.

حاليًا، الموظف يحتاج إلى:

1. قراءة الطلب.
2. فهم ما يريده العميل.
3. استخراج المعلومات المهمة.
4. معرفة المعلومات الناقصة.
5. تحديد نوع الطلب.
6. تحديد الخطوة التالية.
7. تسجيل البيانات.
8. توجيه الطلب.
9. متابعة الحالات التي تحتاج إلى تدخل بشري.

ومع زيادة الطلبات، قد تصبح العملية:

* بطيئة.
* غير متسقة.
* معرضة للنسيان.
* صعبة التوسع.

### Problem Statement

> **Client requests arrive as unstructured information, requiring employees to manually understand, organize, validate, and route each request.**

---

# 4. Pain Points

المشكلة العامة تحتوي على عدة **Pain Points**.

## Pain Point 01 — Manual Repetitive Work

الموظف يكرر نفس خطوات القراءة والاستخراج والتسجيل لكل طلب.

---

## Pain Point 02 — Unstructured Requests

العملاء لا يرسلون المعلومات دائمًا بنفس الشكل.

مثال:

```text
"أريد موقعًا للشركة."

"نحتاج موقعًا لشركتنا الجديدة ويكون جاهزًا الشهر القادم."

"حابين نعمل موقع، الميزانية لسه مش محددة."
```

المعلومات تختلف من طلب إلى آخر.

---

## Pain Point 03 — Missing Information

قد يحتاج الطلب إلى معلومات غير موجودة.

مثال:

```text
Service: Website
Timeline: Next Month
Budget: Missing
```

المشكلة ليست أن النظام لا يعرف الميزانية.

المشكلة أن:

> **العميل لم يقدمها.**

---

## Pain Point 04 — Inconsistent Decisions

قد يعالج موظفان نفس النوع من الطلبات بطريقة مختلفة.

---

## Pain Point 05 — Delayed Routing

قد يتأخر إرسال الطلب إلى الشخص أو الفريق المناسب.

---

## Pain Point 06 — Risk of Assumptions

عند نقص المعلومات قد يميل الإنسان أو النظام إلى الافتراض.

مثلاً:

```text
Client did not mention budget
        ↓
Assume budget = $1000
```

وهذا غير آمن.

المبدأ الذي سنحافظ عليه في المشروع:

> **Unknown is better than invented.**

---

# 5. Current State

الـ**Current State** يصف كيف يحدث العمل الآن، قبل بناء الحل.

```text
                CURRENT STATE

Client
  ↓
Sends Request
  ↓
Employee Receives Request
  ↓
Reads Request
  ↓
Understands Request
  ↓
Extracts Information
  ↓
Checks Missing Information
  ↓
Decides What To Do
  ↓
Records Information
  ↓
Routes Request
  ↓
Human Follow-up / Action
```

هذه العملية تعتمد بدرجة كبيرة على الإنسان.

وهذا لا يعني أن الإنسان هو المشكلة.

بل يعني أننا نحتاج إلى تحديد:

> **أي أجزاء من العمل يمكن للنظام مساعدتنا فيها؟ وأي أجزاء يجب أن تبقى تحت مسؤولية الإنسان؟**

---

# 6. Desired Outcome

لا نريد أن يكون الهدف:

> "نريد استخدام AI."

هذا ليس **Business Outcome**.

الهدف هو:

> **تحويل طلب العميل غير المنظم إلى معلومات منظمة وقابلة للتحقق، ثم تحديد المسار المناسب للطلب مع إشراك الإنسان عندما تكون هناك حاجة إلى حكم بشري.**

نريد أن تصبح العملية:

```text
Client Request
      ↓
Understand
      ↓
Structure
      ↓
Validate
      ↓
Decide
      ↓
Route
      ↓
Record / Notify / Human Review
```

---

# 7. Success Criteria

نحتاج إلى تحديد كيف سنعرف أن الحل يعمل بشكل جيد.

## SC1 — Information Extraction

يستطيع النظام استخراج المعلومات الموجودة فعلًا في طلب العميل.

---

## SC2 — No Fabrication

إذا كانت المعلومة غير موجودة، لا يتم اختراعها.

مثال:

```text
Client:
"We need a website next month."

Output:

service = website
timeline = next month
budget = null
```

وليس:

```text
budget = $1000
```

---

## SC3 — Structured Information

يتم تحويل الـ**Unstructured Data** إلى **Structured Data** وفق Schema واضح.

---

## SC4 — Missing Information Detection

يستطيع النظام تحديد المعلومات المطلوبة التي لم يقدمها العميل.

---

## SC5 — Validation

لا يتم التعامل مع البيانات غير الكافية كما لو كانت صحيحة وكاملة.

---

## SC6 — Appropriate Routing

يذهب الطلب إلى المسار المناسب بناءً على المعلومات والـRules المحددة.

---

## SC7 — Human Escalation

الحالات التي تحتاج إلى حكم بشري يتم تحويلها إلى **Human-in-the-Loop**.

---

## SC8 — Explainability

يمكننا تفسير سبب اتخاذ النظام للقرار:

> Why did this request go to this path?

---

## SC9 — Testability

يمكن اختبار النظام على حالات مختلفة، وليس فقط الحالة المثالية.

---

# 8. Business Success vs Technical Success

من المهم التفريق بين نوعين من النجاح.

## Technical Success

قد يعني:

> الـZap اشتغل بدون Error.

لكن هذا وحده لا يكفي.

قد يعمل الـZap تقنيًا ويعطي نتيجة خاطئة.

## Business Success

يعني:

> النظام ساعد في تحسين العمل بالطريقة المطلوبة وحقق الـSuccess Criteria.

لذلك:

```text
Technical Success ≠ Business Success
```

وقد يكون:

```text
Zap works
+
Wrong Decision
=
Failed Solution
```

---

# 9. Scope of the Work

نحن لا نبني نظام الشركة بالكامل.

نحدد **Scope** واضحًا.

### داخل نطاق المشروع:

* استقبال Client Request.
* فهم الطلب.
* استخراج المعلومات.
* تحويلها إلى Structured Data.
* اكتشاف Missing Information.
* Validation.
* تحديد المسار.
* Routing.
* Human Review للحالات المناسبة.
* تسجيل النتيجة.
* Notification.

### خارج نطاق المشروع:

* CRM كامل.
* Customer Portal.
* Dashboard.
* Advanced Lead Scoring.
* AI Agent.
* RAG.
* Multi-Agent System.
* Custom Backend.
* Custom Database.
* Advanced API Development.

الهدف:

> **Build one complete, testable Vertical Slice.**

---

# 10. Business Analysis Summary

يمكن تلخيص Layer 01 كالتالي:

```text
WORK
Client Request Intake & Routing

        ↓

PROBLEM
Manual handling of unstructured client requests

        ↓

PAIN POINTS
Repetition
Inconsistency
Missing Information
Delay
Assumptions

        ↓

CURRENT STATE
Human manually reads, understands,
organizes, validates, and routes requests

        ↓

DESIRED OUTCOME
Structured, validated, appropriately routed requests

        ↓

SUCCESS CRITERIA
Correct Extraction
No Fabrication
Structured Data
Validation
Correct Routing
Human Escalation
Explainability
Testability
```

---

# 11. The Engineering Question

بعد إنهاء هذا التحليل، لا ننتقل مباشرة إلى Zapier.

السؤال التالي هو:

> **How can we break this Work into a clear Process and Workflow?**

لأننا عرفنا الآن:

* ماذا نريد أن نحسن.
* ما المشكلة.
* أين توجد الـPain Points.
* كيف يحدث العمل حاليًا.
* ما النتيجة المطلوبة.
* كيف نقيس النجاح.

لكننا لم نحدد بعد:

> **ما هي الخطوات الفعلية التي يتكون منها هذا العمل؟**

وهذا يقودنا إلى:

# Layer 02 — Decompose the Work

في الملف التالي:

`02-workflow-decomposition.md`

سنحوّل هذا العمل من فكرة عامة إلى:

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

ثم نستخدم هذا التصميم كأساس لفهم الـ**Trigger** والـ**Input** والبيانات في الملف الثالث.
