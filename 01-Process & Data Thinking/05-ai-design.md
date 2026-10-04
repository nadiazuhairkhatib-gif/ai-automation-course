# 05 — AI Design

# تصميم دور الذكاء الاصطناعي

## 1. الهدف

نستخدم AI في المكان الذي يكون فيه مناسبًا:

> فهم اللغة الطبيعية وتحويلها إلى معلومات منظمة.

لا نستخدم AI بدلًا من كل قواعد النظام.

---

# 2. AI Responsibilities

يجب أن يستطيع AI:

1. فهم طلب العميل.
2. استخراج البيانات.
3. تصنيف الخدمة.
4. تلخيص الطلب.
5. استخراج الموعد.
6. استخراج الميزانية.
7. تحديد الأولوية إذا كانت واضحة.
8. استخراج Dependencies.
9. تحديد المعلومات الناقصة.
10. اكتشاف الغموض.
11. تحديد ما إذا كان الطلب يحتاج إلى Clarification.

---

# 3. AI Boundaries

AI لا يجب أن:

* يخترع Budget.
* يخترع Deadline.
* يخترع متطلبات لم يذكرها العميل.
* يحول معلومة غامضة إلى تاريخ دقيق من عنده.
* يتخذ كل القرارات التجارية.
* يتجاوز Validation.
* يرسل الطلب مباشرة إلى الفريق دون فحص.

---

# 4. AI Instruction

يجب أن تكون التعليمات واضحة.

المبدأ:

```text
Extract what is present.
Do not invent what is missing.
Mark ambiguous information as ambiguous.
Return structured data.
```

---

# 5. Prompt Design

التعليمات المقترحة:

```text
You are an AI system that analyzes client service requests.

Your task is to extract information from the client's request
and return structured data.

Rules:

1. Extract only information that is explicitly present or strongly supported.
2. Never invent missing values.
3. If a value is not provided, return null.
4. Detect missing important information.
5. Detect ambiguous information.
6. If a deadline is vague, do not convert it into an exact date.
7. If information is conflicting, mark the request for clarification.
8. Return the result using the required structured fields.
9. Do not make business decisions that are outside the requested extraction task.
10. Keep the output concise and structured.
```

---

# 6. Input to AI

يتم تمرير بيانات العميل مثل:

```text
Client Name:
{{Name}}

Company:
{{Company}}

Request:
{{Request}}
```

---

# 7. Required Output

يجب أن تكون النتيجة:

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

# 8. Example — Clear Request

### Input

```text
We need a landing page for our new product.
Our budget is $800 and we need it by October 15.
```

### Expected

```text
service:
Landing Page

budget:
800

deadline:
2026-10-15

missing_information:
[]

needs_clarification:
false
```

---

# 9. Example — Missing Data

### Input

```text
We need a landing page by October 15.
```

### Expected

```text
service:
Landing Page

budget:
null

deadline:
2026-10-15

missing_information:
["budget"]

needs_clarification:
true
```

---

# 10. Example — Ambiguous Information

### Input

```text
We need the website next week.
```

### Expected behavior

لا يتم اختراع تاريخ.

يجب اعتبار الموعد غير محدد بشكل كافٍ للتنفيذ.

```text
deadline:
null

needs_clarification:
true
```

---

# 11. Example — Conflicting Information

### Input

```text
We need it next Monday.
Actually, make that next month.
```

### Expected

```text
needs_clarification:
true
```

والسبب:

```text
Conflicting deadline information.
```

---

# 12. Example — Hallucination

### Input

```text
We need a website.
We haven't decided on the budget yet.
```

### Correct

```text
budget:
null
```

### Failure

```text
budget:
1000
```

هذا يسمى فشلًا في الالتزام بالمعلومات الموجودة في المصدر.

---

# 13. Confidence

يمكن استخدام:

```text
high
medium
low
```

لكن Confidence ليست بديلًا عن Validation.

مثال:

```text
confidence = high
```

لا يعني:

> النظام يستطيع تنفيذ أي Action دون فحص.

بل يعني:

> AI يرى أن تفسيره واضح بدرجة عالية.

---

# 14. AI Output ≠ Truth

هذه نقطة أساسية في المشروع.

AI يستطيع إنتاج:

```text
service = Website
```

لكن ذلك لا يعني أن القيمة صحيحة تلقائيًا.

لذلك:

```text
AI Output
     ↓
Validation
     ↓
Decision
```

---

# 15. متى يفشل تصميم AI؟

يفشل التصميم عندما:

* Prompt غير واضح.
* Output غير منظم.
* لا يوجد Data Contract.
* يسمح AI بالاختراع.
* لا توجد تعليمات للتعامل مع Unknown.
* لا توجد تعليمات للتعامل مع Ambiguity.
* يتم الاعتماد على AI بدل Rules.
* يتم تنفيذ Action مباشرة بعد AI.

---

# 16. مبدأ التصميم

نريد AI يستطيع أن يقول:

> لا أعرف.

بدل أن يجبر نفسه على إعطاء إجابة.

لذلك:

```text
Unknown
>
Invented
```

و:

```text
null
>
False Information
```

---

# 17. Final AI Architecture

```text
Client Language
      ↓
AI Understanding
      ↓
Extraction
      ↓
Classification
      ↓
Missing / Ambiguity Detection
      ↓
Structured Output
      ↓
Validation
```

AI هنا ليس "العقل الكامل للنظام".

إنه مكوّن متخصص في **Understanding** داخل Workflow أكبر.

