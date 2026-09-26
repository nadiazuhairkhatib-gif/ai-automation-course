# U3 Resources

## AI Service Management Platform

## 1. Primary Tools

### Lovable

استخدمه لبناء **Application MVP** من خلال وصف المتطلبات والنظام.

الاستخدام في هذه الوحدة:

* بناء واجهة التطبيق.
* إنشاء تدفقات المستخدم.
* ربط مكونات النظام.
* تسريع بناء MVP.

### Supabase

استخدمه كـ **Data Layer** للتطبيق.

في هذه الوحدة نركز على:

* Tables
* Relationships
* Stored Data
* Basic Access Control
* Application Data

---

# 2. Supporting AI Tools

يمكن استخدام:

* ChatGPT
* Claude
* Gemini

الاستخدام:

* تحليل المتطلبات.
* مراجعة User Stories.
* اقتراح Test Cases.
* تفسير الأخطاء.
* مراجعة التصميم.
* تحسين Documentation.

لكن:

> **AI لا يحل محل فهمك للنظام.**

---

# 3. What to Learn Before Building

راجع هذه المفاهيم:

### Problem vs System

المشكلة ليست النظام.

### Actor

من يتفاعل مع النظام؟

### Requirement

ما الذي يجب أن يفعله النظام؟

### User Story

ماذا يريد المستخدم ولماذا؟

### Acceptance Criteria

كيف نعرف أن الوظيفة تعمل؟

### User Flow

كيف ينتقل المستخدم داخل النظام؟

### Data Model

ما الذي يحتاج النظام إلى حفظه؟

### Business Rule

ما الذي يجب أن يحدث أو يُمنع؟

### AI Component

أين يضيف AI قيمة داخل النظام؟

### MVP

ما أصغر نسخة تثبت أن الحل يعمل؟

---

# 4. Recommended Build Sequence

لا تبدأ بالأداة.

استخدم هذا التسلسل:

```text
Problem
↓
Users
↓
Requirements
↓
User Stories
↓
Acceptance Criteria
↓
User Flow
↓
Data Model
↓
Business Rules
↓
AI Boundary
↓
MVP Architecture
↓
Build
↓
Test
↓
Break
↓
Diagnose
↓
Fix
↓
Retest
```

---

# 5. Testing Resources

ركز على اختبار:

### Functional Testing

هل الوظيفة تعمل؟

### Validation Testing

هل يمنع النظام المدخلات غير الصحيحة؟

### Access Control Testing

هل يستطيع المستخدم الوصول فقط لما يسمح له النظام به؟

### AI Testing

هل AI يقدم اقتراحات مناسبة؟

### Failure Testing

ماذا يحدث عندما يفشل AI؟

### State Testing

هل يسمح النظام فقط بالانتقالات الصحيحة؟

### Data Integrity Testing

هل تبقى البيانات الأصلية محفوظة؟

---

# 6. Failure Categories

عند حدوث مشكلة، حاول تحديد نوعها:

* Requirement Failure
* User Flow Failure
* Data Model Failure
* Validation Failure
* Access Control Failure
* Business Rule Failure
* AI Classification Failure
* AI Hallucination
* AI Reliability Failure
* State Management Failure
* Integration Failure
* UI Failure

لا تبدأ بالإصلاح قبل محاولة تحديد **Failure Type**.

---

# 7. AI Usage Rules

يمكنك استخدام AI أثناء التطوير.

لكن يجب أن تعرف دائماً:

> **What did AI build?**
>
> **Why did it build it this way?**
>
> **How do I know it works?**
>
> **What happens when it fails?**

إذا لم تستطع الإجابة، فأنت لم تتعلم النظام بعد.

---

# 8. Prompting Principle

عند استخدام AI Builder، لا تكتب:

> "Build me a beautiful service management app."

بدلاً من ذلك، أعطِ النظام:

* Context
* Users
* Requirements
* Data
* Rules
* AI Responsibilities
* MVP Boundary
* Constraints

أي:

> **Design first → Prompt second.**

---

# 9. Important Engineering Principle

## AI is a component inside a system.

ليس:

```text
AI
↓
Everything
```

بل:

```text
SYSTEM
├── USER
├── UI
├── DATA
├── RULES
├── AI
├── HUMAN
└── TESTING
```

---

# 10. Further Learning

للتوسع لاحقاً، يمكن للمتدرب دراسة:

* Requirements Engineering
* Software Architecture
* Database Design
* Human-in-the-Loop Systems
* AI Evaluation
* Application Security
* Authentication & Authorization
* API Design
* Software Testing
* UX Design

هذه الموضوعات **خارج نطاق MVP هذه الوحدة** لكنها تمثل المسار الطبيعي للتعمق.

---

# 11. Resource Selection Rule

لا تجمع عشرات المصادر.

اختر المصدر الذي يساعدك في حل المشكلة الحالية.

اسأل:

> **What do I need to understand to build or debug this system?**

ثم ابحث عن المصدر المناسب.

---

# 12. U3 Mental Model

احفظ هذه السلسلة:

```text
PROBLEM
↓
USERS
↓
REQUIREMENTS
↓
FLOW
↓
DATA
↓
RULES
↓
AI
↓
SYSTEM
↓
TEST
↓
FAIL
↓
FIX
↓
VERIFY
```

### Core Principle

> **Do not prompt your way into a system.**
>
> **Design your way into a system, then use AI to build it.**
