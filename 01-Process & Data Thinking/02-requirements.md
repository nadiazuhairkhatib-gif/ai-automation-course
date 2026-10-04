# 02 — Requirements

# متطلبات النظام

## 1. الهدف

يجب أن يحول النظام طلب العميل غير المنظم إلى معلومات منظمة وقابلة للتحقق، ثم يقرر الإجراء المناسب بناءً على البيانات والقواعد المحددة.

---

# 2. Functional Requirements

## FR-01 — استقبال طلب العميل

يجب أن يستطيع النظام استقبال طلب جديد من العميل.

### Input

* Name
* Email
* Company
* Request

### Expected

إنشاء عملية جديدة لمعالجة الطلب.

---

## FR-02 — فهم الطلب

يجب أن يستخدم النظام AI لفهم النص الطبيعي الذي كتبه العميل.

يجب أن يستطيع AI تحديد:

* نوع الخدمة.
* وصف الطلب.
* الموعد.
* الميزانية.
* الأولوية.
* المتطلبات أو Dependencies.
* المعلومات الناقصة.
* المعلومات الغامضة.

---

## FR-03 — استخراج البيانات

يجب تحويل الطلب من Natural Language إلى Structured Data.

مثال:

### Input

> نحتاج Landing Page لمنتج جديد، الميزانية 800 دولار ونريدها قبل 15 أكتوبر.

### Output

```text
service = Landing Page
budget = 800
deadline = 2026-10-15
```

---

## FR-04 — عدم اختراع البيانات

إذا لم يذكر العميل معلومة، يجب ألا يخترع AI قيمة لها.

مثال:

### Input

> نحتاج موقعًا جديدًا قبل 15 أكتوبر.

يجب أن تكون:

```text
budget = null
```

وليس:

```text
budget = 1000
```

---

## FR-05 — اكتشاف المعلومات الناقصة

يجب على النظام تحديد المعلومات المهمة غير الموجودة.

مثال:

```text
missing_information = ["budget"]
```

---

## FR-06 — اكتشاف الغموض

يجب أن يميز النظام بين:

### Missing

المعلومة غير موجودة.

مثال:

> لم نحدد الميزانية.

### Ambiguous

المعلومة موجودة ولكنها غير دقيقة بما يكفي للتنفيذ.

مثال:

> نريد المشروع الأسبوع القادم.

---

## FR-07 — Structured Output

يجب أن ينتج AI بيانات وفق Data Contract محدد.

لا تعتبر فقرة نصية طويلة مخرجًا مقبولًا.

---

## FR-08 — Validation

يجب فحص المخرجات قبل اتخاذ الإجراء.

يجب التحقق من:

* وجود الحقول المطلوبة.
* صحة أنواع البيانات.
* عدم وجود قيم مخترعة.
* وجود معلومات الغموض.
* وجود معلومات النقص.
* حالة `needs_clarification`.

---

## FR-09 — Routing

يجب توجيه الطلب إلى الفريق المناسب بناءً على الخدمة.

مثال:

```text
Website
→ Web Team

Graphic Design
→ Design Team

Marketing
→ Marketing Team

AI Automation
→ Automation Team
```

إذا لم يكن نوع الخدمة واضحًا:

```text
Unknown
→ Human Review
```

---

## FR-10 — تسجيل الطلب

يجب تسجيل الطلب النهائي في:

* Google Sheets
  أو
* Zapier Tables

بحيث يمكن الرجوع إليه لاحقًا.

---

## FR-11 — Notification

يجب إرسال إشعار بناءً على نتيجة المعالجة.

### حالة مؤهلة

إرسال الطلب للفريق المناسب.

### حالة تحتاج توضيحًا

إرسال إشعار للإنسان لمراجعة الطلب أو التواصل مع العميل.

---

# 3. Non-Functional Requirements

## NFR-01 — Reliability

لا يجب أن يؤدي النظام إلى قرار خاطئ فقط لأن AI أعاد قيمة تبدو منطقية.

---

## NFR-02 — No Fabrication

أي معلومة غير موجودة يجب أن تبقى:

```text
null
```

أو يتم وضعها ضمن:

```text
missing_information
```

---

## NFR-03 — Structured Output

يجب أن تكون المخرجات منظمة وقابلة للاستخدام في الخطوات التالية.

---

## NFR-04 — Traceability

يجب أن نستطيع معرفة:

```text
Input
→ AI Output
→ Validation
→ Decision
→ Action
```

حتى نستطيع تشخيص المشكلة.

---

## NFR-05 — Human Oversight

الحالات الغامضة أو المتعارضة أو غير المكتملة لا يجب أن تنتقل مباشرة إلى إجراء consequential.

---

## NFR-06 — Testability

يجب أن نستطيع اختبار النظام باستخدام حالات مختلفة ومتوقعة.

---

# 4. Success Criteria

## SC-01 — Extraction

يستخرج النظام المعلومات الموجودة فعليًا في الطلب.

---

## SC-02 — No Fabrication

لا يخترع النظام معلومات غير موجودة.

مثال:

```text
Budget not mentioned
→ budget = null
```

---

## SC-03 — Ambiguity Detection

يكتشف النظام المعلومات التي تبدو موجودة لكنها غير دقيقة.

مثال:

```text
"next week"
→ ambiguous deadline
```

---

## SC-04 — Structured Output

يجب أن تكون نتيجة AI في Schema واضح.

---

## SC-05 — Validation

الحالات التي تحتوي على معلومات حرجة ناقصة أو غير صالحة لا تمر مباشرة إلى الإجراء النهائي.

---

## SC-06 — Human Escalation

الحالات التالية يجب أن تصل إلى الإنسان:

* Missing critical information
* Ambiguous information
* Conflicting information
* Unknown service
* Low confidence

---

# 5. Business Rules

## Rule 01

إذا لم توجد الميزانية:

```text
budget = null
```

---

## Rule 02

إذا كانت معلومة مهمة ناقصة:

```text
needs_clarification = true
```

---

## Rule 03

إذا كان الموعد غامضًا:

```text
needs_clarification = true
```

---

## Rule 04

إذا كانت الخدمة غير معروفة:

```text
route = Human Review
```

---

## Rule 05

لا يتم إرسال الحالة للفريق مباشرة إذا كانت:

```text
needs_clarification = true
```

---

# 6. Decision Principle

القرار ليس مسؤولية AI وحده.

نستخدم:

```text
AI
→ Understand

Rules
→ Validate / Decide deterministic conditions

Human
→ Resolve ambiguity and accountability
```

---

# 7. Definition of Done

نعتبر المشروع مكتملًا عندما:

* [ ] يستطيع استقبال طلب.
* [ ] يستطيع AI فهم الطلب.
* [ ] يتم استخراج البيانات.
* [ ] البيانات منظمة.
* [ ] لا يتم اختراع البيانات.
* [ ] يتم اكتشاف Missing Information.
* [ ] يتم اكتشاف Ambiguity.
* [ ] يتم تطبيق Validation.
* [ ] يتم Routing.
* [ ] يتم تسجيل البيانات.
* [ ] يتم إرسال Notification.
* [ ] تعمل حالات الاختبار الأساسية.
* [ ] نستطيع اكتشاف سبب الفشل عند حدوثه.
