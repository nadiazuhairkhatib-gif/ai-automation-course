# U3 — Guided Build Guide

## AI Service Management Platform

## الهدف

في هذا الدليل سنحوّل **System Design** الذي أنجزناه إلى **Working MVP** باستخدام:

* Lovable
* Supabase
* AI Model

لكننا لن نستخدم AI Builder بدل التفكير الهندسي.

القاعدة:

> **Design → Build → Test → Improve**

وليس:

> **Prompt → Generate → Done**

---

# المرحلة 1 — راجع التصميم قبل البناء

قبل فتح Lovable، يجب أن تكون لديك:

* Problem Definition
* Requirements
* User Stories
* Acceptance Criteria
* User Flow
* Data Model
* Business Rules
* AI Boundary
* MVP Boundary

إذا كان أحدها غير واضح، لا تبدأ بالبناء.

---

# المرحلة 2 — جهّز MVP Boundary

سنبدأ فقط بهذا المسار:

```text id="k6y8zr"
User
 ↓
Create Request
 ↓
Validate
 ↓
Store in Database
 ↓
AI Suggestions
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

# المرحلة 3 — إنشاء المشروع

افتح Lovable وأنشئ مشروعًا جديدًا.

لا تبدأ بكتابة:

> "Build me a complete AI service management platform."

هذا Prompt واسع جدًا.

بدل ذلك، أعطِ AI Builder **Context + Requirements + Constraints**.

---

# المرحلة 4 — Build Prompt

استخدم التصميم الذي أنجزته لإنشاء النسخة الأولى.

يمكن استخدام Prompt مثل:

```text
Build a small MVP for an AI-assisted Service Request Management Platform.

Context:
A Training & Innovation Center receives service requests from users.
The system should help users submit and track requests and help staff review, assign, and manage them.

Users:
1. User
2. Staff

User capabilities:
- Create a service request
- View own requests
- View request status
- View request details

Staff capabilities:
- View service requests
- View request details
- Review AI suggestions
- Assign requests
- Update request status

Core request fields:
- id
- user_id
- title
- description
- category_id
- priority
- status
- assigned_to
- ai_summary
- ai_category
- ai_priority
- created_at
- updated_at

Status flow:
NEW
IN_REVIEW
ASSIGNED
IN_PROGRESS
RESOLVED

Rules:
- Users can only access their own requests.
- Staff can access requests they are authorized to manage.
- Required fields must be validated.
- Invalid status transitions must be prevented.
- AI suggestions must not overwrite original user data.
- AI failure must not prevent the request from being stored.
- AI suggestions must be reviewable by Staff.

AI responsibilities:
- Suggest category
- Suggest priority
- Generate a short summary

AI is advisory, not the final decision-maker.

Keep the MVP small.
Do not add:
- advanced analytics
- mobile application
- multi-agent systems
- complex notifications
- unnecessary features

Use Supabase for the data layer.
```

---

# المرحلة 5 — لا تقبل الناتج مباشرة

بعد أن يولد Lovable النظام، لا تقل:

> "Looks good."

ابدأ بالمقارنة مع التصميم.

استخدم:

```text id="n4yq8c"
REQUIREMENT
    ↓
IMPLEMENTATION
    ↓
TEST
    ↓
PASS / FAIL
```

---

# المرحلة 6 — افحص Database

تأكد من أن Supabase يحتوي على البنية المطلوبة.

ابدأ بـ:

### Users

المستخدمون والأدوار.

### Requests

الطلبات الأساسية.

### Categories

تصنيفات الخدمات.

### Assignments

مسؤولية الموظف عن الطلب.

### Status History

تاريخ تغيّر الحالات.

لا تضف جداول لأن Lovable اقترحها فقط.

اسأل:

> **ما المشكلة التي يحلها هذا الجدول؟**

---

# المرحلة 7 — اختبر User Journey

ابدأ كأنك مستخدم حقيقي.

### Scenario

أنشئ طلبًا:

> "لا أستطيع تسجيل الدخول إلى حسابي."

ثم تحقق:

1. هل يمكن إنشاء الطلب؟
2. هل يتم حفظه؟
3. هل يحصل على ID؟
4. هل يظهر للمستخدم؟
5. هل يظهر للموظف؟
6. هل ينتج AI Suggestion؟
7. هل يستطيع الموظف مراجعة الاقتراح؟
8. هل يستطيع الموظف إسناد الطلب؟
9. هل يستطيع تغيير الحالة؟
10. هل يرى المستخدم الحالة الجديدة؟

---

# المرحلة 8 — اختبر AI

لا يكفي أن يعمل AI مرة واحدة.

استخدم عدة Requests.

### Example 1

> "نسيت كلمة المرور ولا أستطيع الدخول."

توقع:

**Technical Support**

---

### Example 2

> "أريد معرفة مواعيد التسجيل في الدورة القادمة."

توقع:

**Training / Registration**

---

### Example 3

> "أحتاج مساعدة لكن لا أعرف أي خدمة أطلب."

هنا قد لا يكون التصنيف واضحًا.

يجب ألا نجبر AI على اختيار تصنيف عشوائي.

يجب أن توجد إمكانية:

> **Needs Human Review**

---

# المرحلة 9 — اختبر AI Failure

تعمد إرسال:

* وصف قصير جدًا.
* وصف غامض.
* وصف يحتوي معلومات متناقضة.
* طلب خارج التصنيفات المعروفة.

راقب:

> ماذا يفعل النظام عندما لا يعرف AI الإجابة؟

هذه أهم من نجاح AI في الحالة السهلة.

---

# المرحلة 10 — اختبر Rules

اختبر مثلًا:

### Test A

User يحاول رؤية Request لمستخدم آخر.

**Expected: Denied**

### Test B

User يحاول تغيير Assignment.

**Expected: Denied**

### Test C

Staff يحاول الانتقال من:

```text
NEW → RESOLVED
```

إذا كان الانتقال غير مسموح:

**Expected: Blocked**

### Test D

Request بدون Description.

**Expected: Validation Error**

---

# المرحلة 11 — اكسر النظام

الآن ننتقل من:

> "هل يعمل؟"

إلى:

> **"كيف يفشل؟"**

حاول عمدًا:

* إرسال بيانات ناقصة.
* إدخال قيمة غير متوقعة.
* استخدام Role خاطئ.
* الوصول إلى بيانات غير مسموحة.
* إجبار AI على تصنيف غير واضح.
* تعطيل AI.
* إدخال حالة غير صحيحة.

كل Failure يجب تسجيله.

---

# المرحلة 12 — Diagnose

عندما يحدث Failure، لا تقل:

> "Lovable أخطأ."

هذا ليس Diagnosis.

استخدم:

```text id="5x1x2m"
Failure
↓
Evidence
↓
Diagnosis
↓
Root Cause Hypothesis
↓
Fix
↓
Retest
```

مثال:

### Failure

User استطاع رؤية Request لمستخدم آخر.

### Evidence

User A شاهد Request belonging to User B.

### Diagnosis

Access Control لم يُطبق بشكل صحيح.

### Fix

تصحيح قاعدة الوصول في Database / Supabase.

### Retest

User A يحاول الوصول مرة أخرى.

### Expected

Access denied.

---

# المرحلة 13 — لا تصلح كل شيء بـ Prompt

إذا كانت المشكلة:

### Requirement Problem

ارجع إلى Requirements.

### Flow Problem

ارجع إلى User Flow.

### Data Problem

ارجع إلى Data Model.

### Rule Problem

ارجع إلى Business Rules.

### AI Problem

راجع AI Boundary / Prompt / Output / Validation.

### UI Problem

عدّل UI.

هذه نقطة أساسية:

> **ليس كل Bug هو Prompt Problem.**

---

# المرحلة 14 — تحسين النسخة الثانية

بعد اكتشاف المشاكل:

```text id="y6c2na"
V1
 ↓
Test
 ↓
Failures
 ↓
Diagnosis
 ↓
Fixes
 ↓
V2
```

ثم أعد تشغيل أهم الاختبارات.

---

# المرحلة 15 — Evidence

لا تكتفِ بقول:

> "تم إصلاح المشكلة."

احتفظ بـEvidence:

* Screenshot
* Test Result
* Before / After
* Error
* Diagnosis
* Fix
* Retest

هذه الأدلة ستدخل لاحقًا في **U4 — Quality & Evaluation**.

---

# Definition of Done

يعتبر Guided Build مكتملًا عندما:

* يعمل Create Request.
* يتم حفظ البيانات.
* يستطيع المستخدم رؤية طلباته فقط.
* يستطيع Staff إدارة الطلبات المسموحة.
* توجد AI Suggestions.
* يستطيع Staff مراجعة AI Suggestions.
* توجد Business Rules.
* تعمل Status Transitions.
* توجد معالجة لفشل AI.
* تم تنفيذ Tests.
* تم اكتشاف Failure واحد على الأقل.
* تم تشخيصه وإصلاحه.
* تمت إعادة الاختبار.
* تم توثيق Evidence.

---

# أهم درس في U3

Lovable ليس مهندس النظام.

أنت المهندس.

Lovable أداة تساعدك على تحويل التصميم إلى Software أسرع.

لذلك:

> **The better your system design, the more useful your AI Builder becomes.**

---

# Transfer Question

بعد الانتهاء، أجب:

> إذا أعطاك عميل مشكلة جديدة غدًا، هل ستبدأ بفتح Lovable؟

الإجابة التي نريد الوصول إليها:

> **لا. سأبدأ بفهم المشكلة، المستخدمين، المتطلبات، الـFlow، البيانات، والقواعد، ثم أقرر إن كان AI Builder مناسبًا للبناء.**
