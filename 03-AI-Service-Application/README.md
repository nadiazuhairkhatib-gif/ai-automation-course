# U3 — AI Service Management Platform

**العنوان بالعربية:** منصة إدارة طلبات الخدمات المدعومة بالذكاء الاصطناعي

**Capability:** System Thinking — التفكير بالنظم
**Primary Tool:** Lovable + Supabase
**Supporting Tools:** AI Model
**NOVA Stage:** Requirements & Application

---

## سؤال الوحدة

> **كيف أحوّل مشكلة حقيقية إلى نظام يمكن للناس استخدامه؟**

---

## لماذا هذه الوحدة؟

في U1 تعلمنا أن نرى العمل كـ **Process**.

في U2 تعلمنا أن نفكر في **Data & Evidence**.

الآن ننتقل إلى بناء نظام يجمع:

* المستخدمين
* العمليات
* البيانات
* القواعد
* الواجهات
* الذكاء الاصطناعي

لكن الهدف ليس أن نتعلم كيف نكتب Prompt جيدًا لـ AI Builder.

الهدف هو أن نتعلم كيف **نصمم النظام أولًا، ثم نستخدم AI لتسريع بنائه.**

---

## المشروع

سنقوم ببناء:

> **AI Service Management Platform**

منصة لإدارة طلبات الخدمات.

### المشكلة

طلبات الخدمات قد تصل عبر:

* WhatsApp
* Email
* Forms
* موظفين
* مستخدمين

وعندما لا يوجد نظام واضح، قد يحدث:

* ضياع الطلبات
* تأخر الاستجابة
* إرسال الطلب للشخص الخطأ
* عدم معرفة حالة الطلب
* تكرار العمل
* صعوبة متابعة الأداء

---

## النظام المقترح

### المستخدم

يمكنه:

* إنشاء طلب خدمة.
* وصف المشكلة.
* متابعة حالة الطلب.
* رؤية الطلبات السابقة.

### الموظف

يمكنه:

* رؤية الطلبات.
* مراجعة الطلب.
* تصنيف الطلب.
* تحديد الأولوية.
* إسناد الطلب.
* تحديث الحالة.

### AI

يساعد في:

* Category Classification
* Priority Suggestion
* Request Summary
* Suggested Assignment

لكن:

> **AI جزء من النظام، وليس النظام نفسه.**

---

# Mental Model

```text
PROBLEM
   ↓
USERS
   ↓
REQUIREMENTS
   ↓
USER FLOW
   ↓
DATA MODEL
   ↓
SYSTEM
   ↓
AI COMPONENT
   ↓
RULES
   ↓
TEST
   ↓
IMPROVE
```

---

# القاعدة الأساسية

> **No AI Builder Before System Design.**

لا تبدأ بـ:

> "Build me an AI service platform."

ابدأ بـ:

**Problem → Users → Requirements → Flow → Data**

ثم استخدم AI Builder للمساعدة في البناء.

---

# Learning Outcomes

بنهاية الوحدة، يجب أن يكون الطالب قادرًا على:

### Understand

* فهم الفرق بين Problem و System.
* تحديد Users / Actors.
* فهم Requirements.
* فهم User Stories.
* فهم Acceptance Criteria.
* فهم User Flow.
* فهم Data Model.
* التمييز بين AI Component و System.

### Design

* تحويل المشكلة إلى Requirements.
* تصميم User Flow.
* تحديد البيانات المطلوبة.
* تحديد Business Rules.
* تحديد حدود AI.

### Build

* بناء MVP باستخدام Lovable و Supabase.
* دمج AI في جزء محدد من النظام.
* إنشاء واجهات أساسية.
* ربط الواجهة بالبيانات.

### Test

* اختبار النظام بحالات مختلفة.
* اكتشاف أخطاء AI.
* اكتشاف أخطاء Rules.
* اكتشاف أخطاء Data / Access / State.
* إصلاح المشكلة وإعادة الاختبار.

### Transfer

تطبيق نفس طريقة التفكير على مشكلة جديدة داخل NOVA.

---

# Project Architecture

```text
User
 ↓
Service Request
 ↓
Database
 ↓
AI Classification
 ↓
Priority Suggestion
 ↓
Assignment
 ↓
Status Management
 ↓
Dashboard
```

---

# What AI Does

AI يمكنه أن يقترح:

```text
Category
Priority
Summary
Suggested Assignment
```

لكن النظام يجب ألا يعتمد على AI في كل شيء.

---

# What Rules Do

Rules تتحكم في:

* Required Fields
* Allowed Statuses
* Access Control
* Valid State Transitions
* Data Validation

---

# What Humans Do

الإنسان مسؤول عن:

* مراجعة الحالات غير الواضحة.
* القرارات الحساسة.
* الحالات التي تتجاوز صلاحيات النظام.
* الموافقة على الإجراءات المهمة.

---

# Core Principle

> **Design the system first.
> Then use AI to build it.**

---

# Definition of Done

تعتبر U3 مكتملة عندما يستطيع الطالب:

* تعريف المشكلة بوضوح.
* تحديد المستخدمين.
* كتابة Requirements.
* كتابة User Stories.
* تحديد Acceptance Criteria.
* رسم User Flow.
* تصميم Data Model أساسي.
* بناء MVP يعمل.
* دمج AI في وظيفة محددة.
* تحديد Business Rules.
* اختبار النظام.
* توثيق Failure.
* إصلاح المشكلة.
* شرح لماذا صُمم النظام بهذه الطريقة.

---

# What This Unit Does NOT Teach

هذه الوحدة لا تهدف إلى تعليم:

* React بشكل عميق.
* Backend Development بشكل عميق.
* Database Engineering المتقدم.
* Advanced Authentication.
* Advanced Cybersecurity.
* Complex APIs.
* Production Deployment.
* Enterprise Architecture.

نحن نبني **Professional MVP** وليس Production System.

---

## السؤال الذي يجب أن يبقى معك

> **إذا اختفى AI Builder غدًا، هل ما زلت تعرف كيف تصمم النظام؟**

إذا كانت الإجابة نعم، فأنت تتعلم **System Thinking** وليس مجرد استخدام أداة.
