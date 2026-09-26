# U3 — System Requirements

## الهدف

تحويل المشكلة إلى مجموعة واضحة من **Functional Requirements** و **Non-Functional Requirements** قبل البناء.

---

# 1. Users

لدينا نوعان رئيسيان من المستخدمين:

### User

يحتاج إلى:

* إنشاء طلب.
* متابعة طلباته.
* معرفة حالة الطلب.

### Staff

يحتاج إلى:

* مشاهدة الطلبات.
* مراجعة الطلب.
* إدارة التصنيف والأولوية.
* إسناد الطلب.
* تحديث الحالة.

---

# 2. Functional Requirements

## FR-01 — Create Request

يجب أن يستطيع المستخدم إنشاء Service Request.

يجب أن يحتوي الطلب على الأقل على:

* Title
* Description
* Category
* Created By
* Created At
* Status

---

## FR-02 — Store Request

يجب أن يتم حفظ الطلب في Database بعد نجاح التحقق من البيانات.

---

## FR-03 — View Own Requests

يجب أن يستطيع المستخدم رؤية الطلبات التي أنشأها فقط.

---

## FR-04 — View Request Details

يجب أن يستطيع المستخدم رؤية تفاصيل طلبه وحالته الحالية.

---

## FR-05 — Staff Dashboard

يجب أن يستطيع Staff رؤية الطلبات التي تحتاج إلى مراجعة أو معالجة.

---

## FR-06 — AI Classification

يجب أن يستطيع AI اقتراح Category للطلب اعتمادًا على وصفه.

مثال:

```text
"لا أستطيع الدخول إلى حسابي"
→ Technical Support
```

AI هنا يقدم **Suggestion** وليس قرارًا نهائيًا.

---

## FR-07 — AI Priority Suggestion

يجب أن يستطيع AI اقتراح Priority.

مثال:

```text
Low
Medium
High
```

ويجب أن يكون الاقتراح قابلًا للمراجعة من الموظف.

---

## FR-08 — AI Summary

يجب أن يستطيع AI إنشاء Summary قصير للطلب لمساعدة الموظف على فهمه بسرعة.

---

## FR-09 — Assignment

يجب أن يستطيع Staff إسناد الطلب إلى Staff Member مناسب.

---

## FR-10 — Status Management

يجب أن يستطيع Staff تحديث حالة الطلب ضمن الحالات المسموحة.

مثال:

```text
New
↓
In Review
↓
Assigned
↓
In Progress
↓
Resolved
```

---

## FR-11 — User Status Visibility

يجب أن يرى المستخدم الحالة الحالية لطلبه.

---

## FR-12 — Human Review

يجب أن يستطيع Staff مراجعة AI Suggestions قبل الاعتماد عليها عندما يكون ذلك مطلوبًا.

---

# 3. Business Rules

### BR-01

لا يمكن إنشاء Request بدون المعلومات المطلوبة.

### BR-02

المستخدم يستطيع رؤية طلباته فقط.

### BR-03

AI لا يملك القرار النهائي في الحالات التي تحتاج Human Judgment.

### BR-04

لا يمكن الانتقال إلى Status غير مسموح.

### BR-05

لا يمكن اعتبار Request Resolved قبل تنفيذ الإجراء المطلوب.

### BR-06

إذا كان AI غير متأكد، يجب أن تكون هناك إمكانية للمراجعة البشرية.

---

# 4. Non-Functional Requirements

## Usability

يجب أن يستطيع المستخدم فهم كيفية إنشاء الطلب دون تدريب طويل.

## Reliability

يجب ألا يؤدي فشل AI إلى فقدان الطلب الأساسي.

## Traceability

يجب أن نستطيع معرفة:

* من أنشأ الطلب؟
* متى أنشئ؟
* من عدّله؟
* ما حالته الحالية؟

## Data Protection

يجب ألا يستطيع المستخدم الوصول إلى بيانات مستخدم آخر.

---

# 5. AI Boundary

AI مسؤول عن:

```text
Classification
Summarization
Suggestion
```

AI ليس مسؤولًا عن:

```text
Authentication
Access Control
Data Storage Rules
Status Permissions
Final Sensitive Decisions
```

---

# 6. MVP Boundary

سننفذ فقط:

```text
Create Request
↓
Store
↓
AI Suggestion
↓
Staff Review
↓
Assignment
↓
Status Update
↓
User Tracking
```

أي Feature خارج هذا المسار يتم تأجيلها.

---

# Design Check

قبل فتح Lovable، يجب أن نكون قادرين على الإجابة:

> **ما المشكلة التي يحلها النظام؟**

> **من يستخدمه؟**

> **ما أهم User Journey؟**

> **ما البيانات التي يحتاجها؟**

> **ما الذي يقرره AI؟**

> **ما الذي تقرره Rules؟**

> **ما الذي يبقى بيد الإنسان؟**

إذا لم تكن الإجابة واضحة، لم نصل بعد إلى مرحلة البناء.
