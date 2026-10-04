# 04 — Workflow Design

# تصميم سير العمل

## 1. الهدف

نصمم الـ Workflow أولًا على الورق، ثم ننفذه في Zapier.

لا نبدأ بفتح Zapier والضغط على الأزرار.

نبدأ بفهم العملية.

---

# 2. High-Level Workflow

```text
Client Request
      ↓
Trigger
      ↓
Input Data
      ↓
AI Understanding
      ↓
Structured Output
      ↓
Validation
      ↓
Decision
      ↓
Routing
      ↓
Record
      ↓
Notification
```

---

# 3. Step 1 — Trigger

### What?

وصول طلب جديد من العميل.

### Tool

Google Forms

### Input

```text
Name
Email
Company
Request
```

### Why?

نحتاج نقطة بداية واضحة للـ Workflow.

### Failure Point

إذا لم يصل الطلب، لن يبدأ الـ Workflow.

---

# 4. Step 2 — Input

يتم تمرير بيانات النموذج إلى الـ Workflow.

```text
Name
Email
Company
Request
```

يجب التأكد من أن:

* الاسم موجود.
* البريد موجود.
* الطلب موجود.

---

# 5. Step 3 — AI Understanding

يتم إرسال نص الطلب إلى AI.

AI مسؤول عن:

* فهم الطلب.
* استخراج المعلومات.
* تصنيف الخدمة.
* تحديد الموعد.
* تحديد الميزانية.
* تحديد الأولوية.
* تحديد Dependencies.
* اكتشاف المعلومات الناقصة.
* اكتشاف الغموض.

---

# 6. Step 4 — Structured Output

يجب ألا نترك AI يعيد نصًا حرًا.

يجب أن ينتج:

```text
client_name
request_type
service
description
deadline
budget
priority
dependencies
missing_information
needs_clarification
confidence
```

---

# 7. Step 5 — Validation

بعد AI مباشرة نضع Validation.

```text
AI Output
   ↓
Validation
```

نراجع:

* هل الخدمة معروفة؟
* هل البيانات المطلوبة موجودة؟
* هل توجد معلومات ناقصة؟
* هل توجد حالة غموض؟
* هل يحتاج الطلب إلى Clarification؟
* هل القيم منطقية؟

---

# 8. Step 6 — Decision

بعد Validation نقرر ماذا يحدث.

### Case A

الطلب واضح:

```text
needs_clarification = false
```

→ Continue

### Case B

الطلب يحتاج توضيحًا:

```text
needs_clarification = true
```

→ Human Review / Clarification

---

# 9. Step 7 — Routing

إذا كان الطلب صالحًا، نحدد الفريق.

```text
Website
→ Web Team

Landing Page
→ Web Team

Graphic Design
→ Design Team

Marketing
→ Marketing Team

AI Automation
→ Automation Team

Unknown
→ Human Review
```

---

# 10. AI vs Rule vs Human

## AI

يستخدم لفهم اللغة.

```text
"نريد موقعًا جديدًا للشركة"
→ Website
```

---

## Rule

يستخدم لاتخاذ قرار حتمي.

```text
IF service = Website
THEN route = Web Team
```

---

## Human

يستخدم عندما لا يكون القرار آمنًا أو واضحًا.

```text
Ambiguous
→ Human
```

---

# 11. Step 8 — Record

يتم تخزين الطلب في:

**Google Sheets** أو **Zapier Tables**

مثال:

| Client    | Service      | Deadline   | Budget | Status    | Team     |
| --------- | ------------ | ---------- | ------ | --------- | -------- |
| Ahmad Ali | Landing Page | 2026-10-15 | 800    | Qualified | Web Team |

---

# 12. Step 9 — Notification

إذا كان الطلب مؤهلًا:

```text
New Qualified Lead
```

ويتم إرسال المعلومات للفريق المناسب.

إذا كان يحتاج توضيحًا:

```text
Lead Needs Clarification
```

ويصل الإشعار إلى الشخص المسؤول عن المراجعة.

---

# 13. Complete Workflow

```text
                    ┌──────────────────┐
                    │   Client Request │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │     Trigger      │
                    │  Google Forms    │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ AI Understanding │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Structured Data  │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │    Validation    │
                    └────────┬─────────┘
                             ↓
                  ┌──────────┴──────────┐
                  ↓                     ↓
          Needs Clarification?          No
                  ↓                     ↓
             Human Review           Routing
                                        ↓
                                   Record Data
                                        ↓
                                   Notification
```

---

# 14. Dependencies

الـ Workflow يعتمد على التسلسل التالي:

```text
Trigger
→ Input
→ AI
→ Structured Output
→ Validation
→ Decision
→ Routing
→ Record
→ Notification
```

لا يمكن تنفيذ Routing قبل أن نعرف الخدمة.

ولا يمكن Validation قبل أن نحصل على AI Output.

ولا يمكن Notification قبل أن نعرف نتيجة القرار.

---

# 15. Failure Points

| Step              | Possible Failure             |
| ----------------- | ---------------------------- |
| Trigger           | Form submission not received |
| Input             | Missing request              |
| AI                | Wrong extraction             |
| Structured Output | Missing field                |
| Validation        | Incorrect condition          |
| Decision          | Wrong branch                 |
| Routing           | Wrong team                   |
| Record            | Wrong field mapping          |
| Notification      | Wrong recipient/message      |

---

# 16. Engineering Principle

لا نسأل فقط:

> هل الـ Zap يعمل؟

نسأل:

> هل كل مرحلة تنتج المخرجات الصحيحة التي تحتاجها المرحلة التالية؟

هذه هي طريقة التفكير الهندسية في Automation.

---

# 17. Final Architecture

```text
Input
  ↓
Understanding
  ↓
Structure
  ↓
Validation
  ↓
Decision
  ↓
Action
```

وهي تمثل جوهر المشروع:

> AI لا يستبدل الـ Workflow؛ AI يصبح جزءًا منه.
