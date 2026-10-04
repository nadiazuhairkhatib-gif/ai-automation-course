# 06 — Zapier Implementation

# تنفيذ المشروع باستخدام Zapier

## 1. الهدف

تحويل الـ Workflow المصمم في الملفات السابقة إلى Automation حقيقي باستخدام Zapier.

الأدوات:

* Google Forms
* Zapier
* AI by Zapier أو AI Model مناسب
* Google Sheets أو Zapier Tables
* Gmail أو Slack للإشعارات
* Filters / Paths
* Formatter عند الحاجة

---

# 2. قبل البدء

يجب أن تكون لدينا:

* Google Form
* Google Sheet أو Table لتسجيل النتائج
* AI instructions
* Data Contract
* Routing Rules
* Test Cases

لا نبدأ التنفيذ قبل فهم العملية.

---

# 3. Step 1 — Create Google Form

أنشئ نموذجًا يحتوي على:

### Name

اسم العميل.

### Email

البريد الإلكتروني.

### Company

اسم الشركة.

### Request

النص الكامل لطلب العميل.

---

# 4. Step 2 — Create the Zap

أنشئ Zap جديد.

الهيكل الأساسي:

```text
Trigger
→ AI
→ Validation
→ Paths
→ Record
→ Notification
```

---

# 5. Step 3 — Configure Trigger

اختيار:

**Google Forms**

ثم:

**New Form Response**

أو الحدث المكافئ المتاح في حساب Zapier.

اختر النموذج الذي أنشأناه.

---

# 6. Step 4 — Test Trigger

أرسل Submission تجريبي من Google Form.

استخدم:

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

اختبر أن Zapier استقبل:

* Name
* Email
* Company
* Request

---

# 7. Step 5 — Add AI Step

أضف خطوة AI.

يمكن استخدام:

**AI by Zapier**

أو AI Model متاح داخل البيئة المستخدمة.

الغرض:

تحويل Request من Natural Language إلى Structured Data.

---

# 8. Step 6 — Configure AI Instructions

استخدم التعليمات الموجودة في:

`05-ai-design.md`

ويجب أن يتضمن الـPrompt:

* مهمة AI.
* الحقول المطلوبة.
* عدم الاختراع.
* التعامل مع null.
* اكتشاف Missing Information.
* اكتشاف Ambiguity.
* التعامل مع Conflicting Information.
* Structured Output.

---

# 9. Step 7 — Pass Form Data to AI

داخل الـPrompt مرر:

```text
Name:
{{Name}}

Company:
{{Company}}

Request:
{{Request}}
```

يجب أن تكون البيانات Dynamic Data القادمة من Trigger.

---

# 10. Step 8 — Test AI

اختبر خطوة AI قبل بناء باقي الـWorkflow.

تحقق من:

### Service

هل تم التعرف على الخدمة؟

### Deadline

هل تم استخراج الموعد؟

### Budget

هل تم استخراج الميزانية فقط إذا كانت موجودة؟

### Missing Information

هل تم اكتشاف البيانات الناقصة؟

### Needs Clarification

هل تم ضبطها بشكل صحيح؟

### Structured Output

هل تستطيع الخطوات التالية استخدام كل حقل؟

---

# 11. Step 9 — Validation

بعد AI نضيف خطوة Validation.

الهدف:

```text
AI Output
→ Check
```

مثال:

إذا:

```text
needs_clarification = true
```

يجب ألا نرسل الطلب مباشرة إلى فريق التنفيذ.

---

# 12. Step 10 — Paths

نستخدم Paths لتقسيم الحالات.

## Path A — Qualified

Condition:

```text
needs_clarification = false
```

ثم:

```text
→ Routing
→ Record
→ Notification
```

---

## Path B — Needs Clarification

Condition:

```text
needs_clarification = true
```

ثم:

```text
→ Human Review
→ Record
→ Notification
```

---

# 13. Step 11 — Routing

داخل مسار Qualified:

### Web

```text
service = Website
OR
service = Landing Page
```

→ Web Team

### Design

```text
service = Graphic Design
```

→ Design Team

### Marketing

```text
service = Marketing
```

→ Marketing Team

### AI Automation

```text
service = AI Automation
```

→ Automation Team

### Unknown

→ Human Review

---

# 14. Step 12 — Store the Data

أضف Google Sheets أو Zapier Tables.

الحقول المقترحة:

```text
Timestamp
Client Name
Email
Company
Request
Service
Description
Deadline
Budget
Priority
Dependencies
Missing Information
Needs Clarification
Confidence
Status
Team
```

---

# 15. Step 13 — Mapping

يجب ربط كل حقل بالمصدر الصحيح.

مثال:

```text
Budget column
← AI Budget

Deadline column
← AI Deadline
```

وليس:

```text
Budget column
← AI Deadline
```

هذه مشكلة Data Mapping وليست مشكلة AI.

---

# 16. Step 14 — Notification

## Qualified Lead

يمكن إرسال رسالة مثل:

```text
New Qualified Lead

Client:
{{client_name}}

Service:
{{service}}

Deadline:
{{deadline}}

Budget:
{{budget}}

Team:
{{team}}
```

---

## Needs Clarification

يمكن إرسال:

```text
Lead Needs Clarification

Client:
{{client_name}}

Service:
{{service}}

Missing Information:
{{missing_information}}

Please review and clarify the request.
```

---

# 17. Step 15 — End-to-End Test

لا يكفي اختبار كل Step منفردًا.

أرسل طلبًا من Google Form.

ثم تابع:

```text
Form
 ↓
Zapier Trigger
 ↓
AI
 ↓
Structured Output
 ↓
Validation
 ↓
Path
 ↓
Routing
 ↓
Record
 ↓
Notification
```

يجب أن تعمل الرحلة كاملة.

---

# 18. Implementation Checklist

### Trigger

* [ ] Form connected
* [ ] Test response received

### AI

* [ ] Prompt added
* [ ] Input mapped
* [ ] Output tested

### Validation

* [ ] Missing data handled
* [ ] Ambiguity handled
* [ ] Conflicts handled

### Paths

* [ ] Qualified path
* [ ] Clarification path
* [ ] Unknown service path

### Storage

* [ ] Columns created
* [ ] Mapping verified

### Notification

* [ ] Qualified notification
* [ ] Review notification

### Final

* [ ] End-to-end test passed

