# 07 — Testing & Debugging

# الاختبار وتصحيح الأخطاء

## 1. الهدف

لا نعتبر الـWorkflow ناجحًا لأنه اشتغل مرة واحدة.

يجب أن نختبره بحالات مختلفة، ونحاول كسره، ثم نكتشف أين حدث الخطأ.

المنهج:

```text
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

# 2. Test Case Structure

لكل اختبار نسجل:

```text
Test Case
Input
Expected Output
Actual Output
Pass / Fail
Root Cause
Fix
Retest Result
```

---

# 3. TC01 — Complete Request

### Input

```text
We need a landing page for our product.
Budget is $800 and we need it by October 15.
```

### Expected

```text
service = Landing Page
budget = 800
deadline = October 15
needs_clarification = false
```

### Expected Result

```text
Qualified
→ Route to Web Team
→ Record
→ Notify
```

---

# 4. TC02 — Missing Budget

### Input

```text
We need a landing page by October 15.
```

### Expected

```text
service = Landing Page
deadline = October 15
budget = null
missing_information = ["budget"]
needs_clarification = true
```

### Expected Action

```text
Human Review / Clarification
```

---

# 5. TC03 — Ambiguous Deadline

### Input

```text
We need it next week.
```

### Expected

لا نحول:

```text
next week
```

إلى تاريخ مخترع.

يجب أن يحتاج الطلب إلى clarification.

```text
needs_clarification = true
```

---

# 6. TC04 — Multiple Services

### Input

```text
We need a website and social media designs.
```

### Expected

يجب التعرف على أكثر من خدمة:

```text
Website
Social Media Design
```

ويجب ألا يتم إسقاط إحدى الخدمتين دون سبب.

---

# 7. TC05 — Hallucination

### Input

```text
We need a website.
We haven't decided on the budget yet.
```

### Expected

```text
budget = null
```

### Failure

إذا أعاد AI:

```text
budget = 1000
```

فالاختبار:

```text
FAIL
```

---

# 8. TC06 — Conflicting Information

### Input

```text
We need it next Monday.
Actually, make that next month.
```

### Expected

```text
needs_clarification = true
```

لأن هناك معلومات متعارضة.

---

# 9. TC07 — Data Mapping

اختبر أن:

```text
AI Budget
→ Google Sheets Budget
```

و:

```text
AI Deadline
→ Google Sheets Deadline
```

وليس العكس.

---

# 10. TC08 — Unknown Service

### Input

```text
We need help with something related to our business,
but we are not sure what service we need.
```

### Expected

```text
service = Unknown
```

ثم:

```text
→ Human Review
```

---

# 11. TC09 — Missing Request

### Input

```text
Name: Ahmad
Email: ahmad@example.com
Request: empty
```

### Expected

يجب ألا يسمح النظام بمعالجة طلب فارغ.

هذه مشكلة Input Validation قبل AI.

---

# 12. TC10 — Clear Budget but No Deadline

### Input

```text
We need a website.
Our budget is $2000.
```

### Expected

```text
service = Website
budget = 2000
deadline = null
needs_clarification = true
```

إذا كان Deadline من المعلومات المطلوبة لاتخاذ القرار.

---

# 13. Root Cause Analysis

عندما يفشل الاختبار، لا نقول مباشرة:

> AI أخطأ.

بل نسأل:

### Question 1

هل كان Input واضحًا؟

---

### Question 2

هل الـPrompt واضح؟

---

### Question 3

هل Data Contract صحيح؟

---

### Question 4

هل AI أنتج المخرج المتوقع؟

---

### Question 5

هل Zapier استقبل البيانات الصحيحة؟

---

### Question 6

هل Mapping صحيح؟

---

### Question 7

هل Validation صحيح؟

---

### Question 8

هل Path Condition صحيح؟

---

### Question 9

هل Action النهائي استلم البيانات الصحيحة؟

---

# 14. Failure Categories

## A — Input Failure

المشكلة في البيانات الداخلة.

مثال:

```text
Request = empty
```

---

## B — AI Failure

AI لم يفهم النص أو اخترع معلومة.

مثال:

```text
budget = 1000
```

بينما الميزانية غير موجودة.

---

## C — Schema Failure

AI لم يعطِ الحقول المطلوبة.

مثال:

```text
service
budget
```

لكن لا يوجد:

```text
needs_clarification
```

---

## D — Mapping Failure

الحقل وصل إلى المكان الخطأ.

مثال:

```text
Budget → Deadline
```

---

## E — Logic Failure

شرط الـPath خاطئ.

مثال:

```text
needs_clarification = true
```

لكن النظام دخل Qualified Path.

---

## F — Action Failure

الـWorkflow قرر القرار الصحيح، لكن الإجراء النهائي فشل.

مثال:

* Notification لم تصل.
* Record لم يُحفظ.
* الإشعار أرسل للفريق الخطأ.

---

# 15. Debugging Example

## Problem

طلب بدون Budget تم إرساله إلى فريق Web Team.

---

## Step 1

نفحص AI.

هل:

```text
budget = null
```

إذا نعم → AI جيد.

---

## Step 2

نفحص:

```text
needs_clarification
```

هل هي:

```text
true
```

إذا نعم → AI جيد.

---

## Step 3

نفحص Path.

إذا كان الشرط:

```text
needs_clarification = false
```

فلا يجب أن يصل الطلب لهذا المسار.

---

## Step 4

إذا وصل رغم ذلك، فالمشكلة غالبًا في:

```text
Path condition
```

وليس AI.

---

# 16. Debugging Principle

لا نصلح الخطوة التي تبدو لنا مشبوهة.

نحدد أولًا:

> أين بدأت البيانات تصبح خاطئة؟

مثال:

```text
Input      ✓
AI         ✓
Validation ✓
Path       ✗
Action     ✗
```

إذن نصلح Path.

---

# 17. Test Matrix

| Test | Main Concept      | Expected                 |
| ---- | ----------------- | ------------------------ |
| TC01 | Complete Request  | Qualified                |
| TC02 | Missing Data      | Human Review             |
| TC03 | Ambiguity         | Clarification            |
| TC04 | Multiple Services | Multiple classifications |
| TC05 | Hallucination     | No invented data         |
| TC06 | Conflict          | Clarification            |
| TC07 | Mapping           | Correct field            |
| TC08 | Unknown           | Human Review             |
| TC09 | Input Validation  | Reject                   |
| TC10 | Missing Deadline  | Clarification            |

---

# 18. Final Acceptance Test

يعتبر المشروع ناجحًا عندما يمر على الأقل بالحالات الأساسية التالية:

```text
Complete Request
Missing Information
Ambiguous Information
Hallucination
Conflicting Information
Unknown Service
Data Mapping
```

ويجب أن نستطيع تفسير نتيجة كل اختبار.

---

# 19. Final Engineering Lesson

الهدف من الاختبار ليس فقط معرفة:

> هل الـAutomation يعمل؟

بل معرفة:

> لماذا يعمل؟
> ومتى يفشل؟
> وأين يفشل؟
> وكيف أصلح الفشل؟

وهذا هو الانتقال من:

```text
Tool User
```

إلى:

```text
Automation Solution Builder
```

---

# 20. Final Project Principle

```text
Build
→ Test
→ Break
→ Diagnose
→ Fix
→ Retest
```

الـWorkflow الجيد ليس Workflow لم يفشل أبدًا.

الـWorkflow الجيد هو Workflow:

* تم اختباره.
* تم كسره عمدًا.
* تم فهم نقاط فشله.
* تم إصلاحه.
* ويمكن تفسير سبب نجاحه وفشله.

