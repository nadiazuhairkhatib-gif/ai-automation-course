# NOVA v0.3 — Requirements & Application

## متطلبات الحل وتصميم التطبيق

### الهدف

في هذه المرحلة تنتقل من:

> **لدي مشكلة وبيانات يجب فهمها**

إلى:

> **أستطيع وصف النظام الذي أحتاج إلى بنائه، ومن سيستخدمه، وما الذي يجب أن يفعله.**

NOVA لا يبدأ بالأداة.

يبدأ بـ:

**Problem → Users → Requirements → Flow → Data → AI/Rules/Human → Application**

---

## 1. Problem Statement — تعريف المشكلة

اكتب المشكلة التي تريد حلها في NOVA بشكل واضح ومحدد.

### اكتب:

* من يعاني من المشكلة؟
* ما الذي يحدث الآن؟
* أين يحدث التعطّل أو التأخير أو الخطأ؟
* ما أثر المشكلة؟
* لماذا تستحق أن تُحل؟

### قالب

```text
The problem is:

[وصف المشكلة]

It affects:

[المستخدمون]

The current process is:

[وصف مختصر للعملية الحالية]

The main pain points are:

1.
2.
3.

The desired outcome is:

[ما النتيجة التي نريد الوصول إليها]
```

---

# 2. Users & Actors — المستخدمون والأطراف

حدد الأشخاص أو الأنظمة التي تتفاعل مع الحل.

| Actor           | Role | Need |
| --------------- | ---- | ---- |
| User            |      |      |
| Staff           |      |      |
| Admin           |      |      |
| AI/System       |      |      |
| External System |      |      |

### سؤال مهم

> هل كل Actor يحتاج نفس الصلاحيات والبيانات؟

---

# 3. Requirements — المتطلبات

حوّل المشكلة إلى متطلبات قابلة للبناء والاختبار.

## Functional Requirements — المتطلبات الوظيفية

ما الذي يجب أن يستطيع النظام فعله؟

مثال:

```text
FR-01: The user can submit a request.
FR-02: The system stores the request.
FR-03: Staff can review the request.
FR-04: The system suggests a category.
FR-05: Staff can modify the AI suggestion.
```

اكتب متطلبات NOVA:

```text
FR-01:

FR-02:

FR-03:

FR-04:

FR-05:
```

---

## 4. Non-Functional Requirements — المتطلبات غير الوظيفية

كيف يجب أن يعمل النظام؟

فكر في:

* Usability — سهولة الاستخدام
* Reliability — الاعتمادية
* Traceability — قابلية التتبع
* Privacy — الخصوصية
* Performance — الأداء
* Maintainability — قابلية الصيانة

اكتب أهم 3 متطلبات:

```text
NFR-01:

NFR-02:

NFR-03:
```

---

# 5. User Stories — قصص المستخدم

اكتب المتطلبات من وجهة نظر المستخدم.

### الصيغة

> As a [user], I want [action], so that [benefit].

### مثال

> As a staff member, I want to review AI suggestions before assigning a request, so that incorrect AI decisions do not directly affect users.

### NOVA

```text
US-01:

US-02:

US-03:

US-04:

US-05:
```

---

# 6. Acceptance Criteria — معايير القبول

لكل وظيفة مهمة، حدد كيف سنعرف أنها تعمل.

### مثال

**User submits a request**

* Required fields must be completed.
* The request is stored.
* A unique ID is generated.
* The user receives confirmation.
* The initial status is `NEW`.

### NOVA

| Requirement | Acceptance Criteria |
| ----------- | ------------------- |
|             |                     |
|             |                     |
|             |                     |
|             |                     |

### القاعدة

> **If you cannot define how to know it works, the requirement is incomplete.**

---

# 7. User Flow — تدفق المستخدم

ارسم الرحلة الأساسية.

```text
User
 ↓
Action
 ↓
Input
 ↓
Validation
 ↓
System Processing
 ↓
AI / Rules / Human
 ↓
Action
 ↓
Output
```

### NOVA Flow

```text
START
 ↓
 
 ↓
 
 ↓
 
 ↓
 
END
```

---

# 8. Data Model — نموذج البيانات

حدد ما الذي يجب أن يتذكره النظام.

### Entities — الكيانات

```text
Entity 1:

Entity 2:

Entity 3:

Entity 4:
```

### أهم الحقول

| Entity | Field | Type | Purpose |
| ------ | ----- | ---- | ------- |
|        |       |      |         |
|        |       |      |         |
|        |       |      |         |

### سؤال هندسي

> إذا حذفنا هذه البيانات غداً، هل سيظل النظام قادراً على أداء وظيفته؟

إذا كانت الإجابة لا، فهذه البيانات مهمة للنظام ويجب أن تُصمم بعناية.

---

# 9. AI / Rules / Human Boundary

لا تجعل AI مسؤولاً عن كل شيء.

حدد بوضوح:

| Task |    AI |  Rule | Human |
| ---- | ----: | ----: | ----: |
|      | ✓ / ✗ | ✓ / ✗ | ✓ / ✗ |
|      | ✓ / ✗ | ✓ / ✗ | ✓ / ✗ |
|      | ✓ / ✗ | ✓ / ✗ | ✓ / ✗ |

### أسئلة القرار

**AI مناسب عندما:**

* المهمة تتطلب فهم لغة أو محتوى غير منظم.
* يمكن تقييم النتيجة.
* الخطأ يمكن اكتشافه أو مراجعته.

**Rules مناسبة عندما:**

* القرار محدد وواضح.
* توجد شروط ثابتة.
* نحتاج إلى سلوك قابل للتنبؤ.

**Human مناسب عندما:**

* القرار حساس.
* المعلومات ناقصة أو متعارضة.
* الخطأ عالي التأثير.
* يحتاج القرار إلى مسؤولية بشرية.

---

# 10. System Boundary — حدود النظام

حدد ما يدخل في NOVA وما لا يدخل.

### داخل MVP

```text
1.
2.
3.
4.
5.
```

### خارج MVP

```text
1.
2.
3.
4.
```

### سؤال

> ما أصغر نسخة من النظام يمكنها إثبات أن فكرتك تعمل؟

هذه هي **MVP Boundary**.

---

# 11. Initial Architecture — التصميم الأولي

ارسم النظام بمستوى عالٍ.

```text
USER
 ↓
INTERFACE
 ↓
APPLICATION LOGIC
 ↓
DATA
 ↓
AI COMPONENT
 ↓
RULES / HUMAN REVIEW
 ↓
OUTPUT
```

عدّل المخطط حسب NOVA.

```text
[USER]
   ↓
[       ]
   ↓
[       ]
   ↓
[       ]
   ↓
[       ]
   ↓
[OUTPUT]
```

---

# 12. Application Choice — اختيار الأداة

الآن فقط، وبعد تصميم المشكلة والنظام، اختر الأداة.

### Tool

```text
Primary Tool:

Supporting Tools:
1.
2.
3.
```

### Why this tool?

```text
I selected this tool because:

1.
2.
3.
```

### ممنوع

> Tool → AI → فكرة مشروع

### المطلوب

> Problem → Requirements → Architecture → Tool

---

# 13. NOVA v0.3 Definition of Done

لا تعتبر NOVA v0.3 مكتملة حتى تستطيع إثبات الآتي:

* [ ] المشكلة محددة.
* [ ] المستخدمون محددون.
* [ ] المتطلبات مكتوبة.
* [ ] User Stories مكتوبة.
* [ ] Acceptance Criteria قابلة للاختبار.
* [ ] User Flow واضح.
* [ ] Data Model أولي.
* [ ] AI / Rules / Human Boundary واضحة.
* [ ] MVP Boundary محددة.
* [ ] Architecture أولية.
* [ ] تم اختيار الأدوات بناءً على المتطلبات، وليس العكس.
* [ ] تستطيع شرح لماذا صممت النظام بهذه الطريقة.

---

# 14. Reflection — التأمل الهندسي

أجب كتابة:

### 1.

ما الشيء الذي كنت سأبنيه مباشرة قبل تعلم System Thinking؟

### 2.

ما الشيء الذي تغير في تصميم NOVA بعد كتابة Requirements؟

### 3.

أين يحتاج النظام إلى AI؟

ولماذا؟

### 4.

أين لا يحتاج النظام إلى AI؟

ولماذا؟

### 5.

ما أكبر مخاطرة في التصميم الحالي؟

### 6.

ما الذي سأختبره أولاً؟

---

## NOVA Principle

> **Do not prompt your way into a system.**
>
> **Design your way into a system, then use AI to build it.**
