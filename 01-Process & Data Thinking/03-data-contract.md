# 03 — Data Contract

# عقد البيانات

## 1. ما هو Data Contract؟

الـ Data Contract هو الاتفاق الذي يحدد:

* ما البيانات التي تدخل النظام.
* ما البيانات التي يجب أن ينتجها AI.
* أسماء الحقول.
* نوع كل قيمة.
* ماذا نفعل عندما لا توجد قيمة.
* كيف تستخدم الخطوات التالية هذه البيانات.

الفكرة الأساسية:

> قبل أن نبني Workflow، يجب أن نعرف شكل البيانات التي ستتحرك داخله.

---

# 2. Input Schema

البيانات التي يدخلها العميل:

| Field   | الوصف             | Required |
| ------- | ----------------- | -------- |
| name    | اسم العميل        | Yes      |
| email   | البريد الإلكتروني | Yes      |
| company | اسم الشركة        | No       |
| request | نص طلب العميل     | Yes      |

---

# 3. Example Input

```text
Name:
Ahmad Ali

Email:
ahmad@example.com

Company:
Example Company

Request:
We need a landing page for our new product.
Our budget is $800 and we need it by October 15.
```

---

# 4. AI Output Schema

يجب أن ينتج AI البيانات التالية:

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

# 5. Field Definitions

## client_name

اسم العميل الذي تم استخراجه من الطلب أو من بيانات الإدخال.

مثال:

```text
"Ahmad Ali"
```

---

## request_type

نوع الطلب.

مثال:

```text
"New Service"
```

---

## service

الخدمة التي يطلبها العميل.

أمثلة:

```text
Website
Landing Page
Graphic Design
Marketing
App Development
AI Automation
Unknown
```

---

## description

وصف مختصر لما يريده العميل.

مثال:

```text
Landing page for a new product.
```

---

## deadline

الموعد المطلوب.

إذا كان الموعد محددًا:

```text
2026-10-15
```

إذا لم يتم ذكره:

```text
null
```

إذا كان غامضًا:

```text
null
```

ويجب أن يظهر السبب في:

```text
missing_information
```

أو من خلال حالة التوضيح.

---

## budget

ميزانية العميل.

مثال:

```text
800
```

إذا لم يذكر العميل الميزانية:

```text
null
```

ممنوع اختراع قيمة.

---

## priority

الأولوية المستخرجة من الطلب إذا كانت واضحة.

أمثلة:

```text
High
Medium
Low
Unknown
```

إذا لم توجد معلومات كافية، لا نخترع الأولوية.

---

## dependencies

أي متطلبات أو اعتماديات ذكرها العميل.

مثال:

```text
["Client must provide logo", "Product information required"]
```

إذا لم توجد:

```text
[]
```

---

## missing_information

قائمة بالمعلومات المهمة التي يحتاجها النظام ولم يجدها.

مثال:

```text
["budget"]
```

أو:

```text
["deadline", "budget"]
```

إذا لم توجد معلومات ناقصة:

```text
[]
```

---

## needs_clarification

هل يحتاج الطلب إلى توضيح بشري؟

القيمة يجب أن تكون:

```text
true
```

أو:

```text
false
```

---

## confidence

مستوى الثقة في الفهم.

القيم:

```text
high
medium
low
```

هذه القيمة لا تعني أن AI أصبح "صحيحًا"، بل تعطي إشارة تساعد النظام على معرفة الحالات التي تستحق المراجعة.

---

# 6. Example — Complete Request

### Input

> We need a landing page for our new product. Budget is $800 and we need it by October 15.

### Expected Output

```text
client_name: "Ahmad Ali"
request_type: "New Service"
service: "Landing Page"
description: "Landing page for a new product"
deadline: "2026-10-15"
budget: 800
priority: "Unknown"
dependencies: []
missing_information: []
needs_clarification: false
confidence: "high"
```

---

# 7. Example — Missing Budget

### Input

> We need a landing page by October 15.

### Expected Output

```text
service: "Landing Page"
deadline: "2026-10-15"
budget: null
missing_information: ["budget"]
needs_clarification: true
```

---

# 8. Example — Ambiguous Deadline

### Input

> We need the website next week.

### Expected interpretation

لا نقوم بتحويل "next week" إلى تاريخ مخترع.

بدلًا من ذلك:

```text
deadline: null
needs_clarification: true
```

مع الإشارة إلى أن الموعد غير دقيق.

---

# 9. Example — Hallucination Test

### Input

> We need a website. We haven't decided on the budget yet.

### Correct

```text
budget: null
```

### Incorrect

```text
budget: 1000
```

إذا أعاد AI قيمة غير موجودة، فالاختبار يفشل.

---

# 10. Data Contract Rules

## Rule 1

القيمة الموجودة في النص يمكن استخراجها.

## Rule 2

القيمة غير الموجودة لا يتم اختراعها.

## Rule 3

المعلومة الغامضة لا يتم تحويلها إلى قيمة دقيقة من عند AI.

## Rule 4

القيمة غير المعروفة يمكن أن تكون:

```text
null
```

## Rule 5

القوائم تستخدم Arrays:

```text
[]
```

## Rule 6

الحالات المنطقية تستخدم Boolean:

```text
true / false
```

---

# 11. لماذا هذا مهم؟

بدون Data Contract قد ينتج AI:

```text
The client wants a website and seems to have a reasonable budget...
```

وهذه ليست بيانات يمكن الاعتماد عليها بسهولة داخل Workflow.

أما مع Data Contract:

```text
service = Website
budget = null
deadline = null
needs_clarification = true
```

تصبح البيانات قابلة للاستخدام في:

* Filters
* Paths
* Google Sheets
* Notifications
* Validation
* Routing

---

# 12. Core Principle

الـ AI يفهم اللغة.

لكن الـ Workflow يحتاج بيانات.

لذلك:

```text
Natural Language
       ↓
       AI
       ↓
Structured Data
       ↓
Validation
       ↓
Decision
```
