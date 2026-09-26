# U3 — System Thinking

## التفكير بالنظم

## السؤال المركزي

> **كيف أحوّل مشكلة حقيقية إلى نظام يمكن للناس استخدامه؟**

في U1 تعلمنا أن ننظر إلى العمل كـ **Process**.

في U2 تعلمنا أن نسأل عن **Evidence**.

في U3 نبدأ بالنظر إلى المشكلة باعتبارها **System**.

---

# 1. Problem vs System

وجود مشكلة لا يعني أننا نحتاج مباشرة إلى تطبيق.

مثال:

> "طلبات الدعم تضيع."

هذه **Problem**.

لكن النظام الذي يعالجها يحتاج إلى معرفة:

* من يرسل الطلب؟
* ماذا يرسل؟
* أين يُخزّن؟
* من يراجعه؟
* كيف يتم تصنيفه؟
* من يستلمه؟
* ما الحالات التي يمر بها؟
* من يستطيع رؤية البيانات؟
* ماذا يحدث عند حدوث خطأ؟

لذلك:

> **Problem ≠ System**

النظام هو مجموعة مكونات مترابطة تعمل معًا لتحقيق نتيجة محددة.

---

# 2. Actors

**Actor** هو شخص أو نظام يتفاعل مع النظام.

مثال:

* Customer
* Staff Member
* Manager
* AI Model
* External Service

لا تبدأ بالسؤال:

> "ما الشاشة التي نحتاجها؟"

ابدأ بالسؤال:

> **"من يحتاج إلى ماذا؟"**

---

# 3. Requirements

**Requirement** يصف شيئًا يجب أن يحققه النظام.

مثال:

> يجب أن يستطيع المستخدم إنشاء Service Request.

ومثال:

> يجب أن يستطيع الموظف تحديث حالة الطلب.

Requirement ليس مجرد Feature جميلة.

يجب أن يكون مرتبطًا بمشكلة أو حاجة حقيقية.

---

# 4. User Story

نحوّل حاجة المستخدم إلى **User Story**.

الصيغة:

> **As a [user], I want [action], so that [value].**

مثال:

> As a user, I want to create a service request so that I can receive help without contacting staff manually.

بالعربية:

> كمستخدم، أريد إنشاء طلب خدمة حتى أتمكن من الحصول على المساعدة دون التواصل يدويًا مع الموظف.

---

# 5. Acceptance Criteria

وجود User Story لا يعني أن الميزة جاهزة.

نحتاج إلى **Acceptance Criteria**.

مثال:

### User Story

المستخدم يستطيع إنشاء طلب خدمة.

### Acceptance Criteria

* يجب أن يحتوي الطلب على وصف.
* يجب أن يتم حفظ الطلب.
* يجب أن يحصل الطلب على ID.
* يجب أن تظهر حالة الطلب.
* يجب أن يستطيع المستخدم رؤية طلبه بعد الإنشاء.

القاعدة:

> **If we cannot define how to know it works, the requirement is incomplete.**

---

# 6. User Flow

**User Flow** يوضح كيف ينتقل المستخدم داخل النظام.

مثال:

```text id="h1x6kf"
Open Platform
      ↓
Create Request
      ↓
Enter Details
      ↓
Submit
      ↓
Request Created
      ↓
View Status
```

User Flow ليس تصميم UI.

هو منطق رحلة المستخدم.

---

# 7. Data Model

كل نظام يحتاج إلى معرفة:

> **ما الأشياء التي يجب أن يتذكرها؟**

في نظامنا يمكن أن نحتاج إلى:

```text id="y1nt5o"
Users
Requests
Categories
Assignments
Status History
```

مثال Request:

```text id="qdb3pc"
Request
├── id
├── user_id
├── title
├── description
├── category
├── priority
├── status
├── assigned_to
└── created_at
```

هذا يسمى **Data Model**.

---

# 8. State

الـRequest لا يبقى في حالة واحدة.

يمكن أن يتحرك بين حالات:

```text id="0k9zch"
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

لكن ليس كل انتقال مسموحًا.

مثلاً:

```text id="bq4jv5"
Resolved → New
```

قد يكون غير مسموح.

وهنا تظهر أهمية **Business Rules**.

---

# 9. Business Rules

**Business Rule** هي قاعدة يجب أن يلتزم بها النظام.

أمثلة:

* لا يمكن إغلاق طلب غير مكتمل.
* المستخدم يرى طلباته فقط.
* الموظف يستطيع تعديل الطلبات المسندة إليه.
* Priority لا تصبح Critical تلقائيًا بدون سبب أو مراجعة.
* الطلب المغلق لا يمكن تعديله إلا بصلاحية محددة.

هذه القواعد لا تحتاج AI.

بل يجب أن تكون **Deterministic Rules** كلما أمكن.

---

# 10. AI Component vs System

هذه من أهم أفكار U3.

لو كان لدينا:

```text id="1xk3on"
User
 ↓
Request
 ↓
AI
 ↓
Response
```

فهذا ليس بالضرورة نظامًا جيدًا.

AI مجرد Component.

النظام الكامل قد يكون:

```text id="4p2h6m"
User
 ↓
Interface
 ↓
Validation
 ↓
Database
 ↓
AI
 ↓
Rules
 ↓
Human Review
 ↓
Action
 ↓
Status
```

لذلك:

> **AI is a component inside a system.**

---

# 11. AI vs Rules vs Human

ليس كل قرار يحتاج AI.

### Rules

استخدم Rules عندما يكون القرار:

* واضحًا
* متكررًا
* Deterministic
* يمكن التعبير عنه بشروط

مثال:

> إذا كان الطلب ناقص البيانات → لا ترسله للموظف.

### AI

استخدم AI عندما تحتاج:

* Classification
* Summarization
* Interpretation
* Extraction
* Natural Language Understanding

مثال:

> تحديد نوع الطلب من وصف مكتوب بلغة طبيعية.

### Human

احتفظ بالإنسان عندما يكون القرار:

* حساسًا
* غامضًا
* عالي المخاطر
* يحتاج مسؤولية بشرية

---

# 12. System Boundary

ليس كل شيء يجب أن يدخل النظام.

اسأل:

> **What is inside the system?**

و:

> **What remains outside?**

مثلاً:

```text id="jln3d9"
              SYSTEM
┌────────────────────────────┐
│ Request Management         │
│ AI Classification          │
│ Assignment                 │
│ Status Management          │
└────────────────────────────┘
          ↑          ↓
       User       External Service
```

هذا يسمى **System Boundary**.

---

# 13. MVP

في U3 لا نبني منصة ضخمة.

نبني **Professional MVP**.

أي أصغر نسخة تعمل وتثبت أن النظام يحل المشكلة الأساسية.

مثلاً:

### MVP

* User creates request.
* Request is stored.
* AI suggests category.
* Staff sees request.
* Staff assigns request.
* Status changes.
* User sees status.

لا نحتاج:

* Mobile App
* Advanced Analytics
* Notifications لكل حالة
* Multi-language system
* Complex roles
* عشرات أنواع الطلبات

---

# 14. Architecture Before UI

لا تبدأ بالسؤال:

> "كيف أجعل التطبيق شكله جميلًا؟"

ابدأ بـ:

```text id="f2yq4w"
Problem
↓
Users
↓
Requirements
↓
Flow
↓
Data
↓
Rules
↓
AI
↓
Architecture
↓
UI
```

الواجهة تأتي بعد فهم النظام.

---

# 15. Mental Model الكامل

احفظ هذا التسلسل:

```text id="6at4o9"
PROBLEM
   ↓
WHO?
   ↓
WHAT DO THEY NEED?
   ↓
REQUIREMENTS
   ↓
USER STORIES
   ↓
ACCEPTANCE CRITERIA
   ↓
USER FLOW
   ↓
DATA MODEL
   ↓
BUSINESS RULES
   ↓
AI COMPONENT
   ↓
MVP
   ↓
TEST
```

---

# Golden Rule

> **Don't prompt your way into a system.
> Design your way into a system, then use AI to build it.**

بالعربية:

> **لا تحاول أن تكتب Prompt حتى تحصل على نظام.
> صمّم النظام أولًا، ثم استخدم AI لتسريع بنائه.**

---

# U3 Engineering Question

عندما ترى أي مشكلة جديدة، لا تسأل:

> "أي AI Tool أستخدم؟"

اسأل بالترتيب:

1. ما المشكلة؟
2. من المستخدم؟
3. ماذا يحتاج؟
4. ما الـRequirements؟
5. ما الـFlow؟
6. ما البيانات؟
7. ما الـRules؟
8. أين يمكن أن يساعد AI؟
9. ما أصغر MVP يمكن بناؤه؟
10. كيف سأعرف أنه يعمل؟

إذا استطعت الإجابة عن هذه الأسئلة، أصبحت مستعدًا للبناء.
