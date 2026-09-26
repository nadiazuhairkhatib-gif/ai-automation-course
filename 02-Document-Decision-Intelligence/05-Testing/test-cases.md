# U2 — Test Cases

## Purpose

في هذه المرحلة نختبر ما إذا كان نظام **Document-to-Decision Intelligence** ينتج نتائج يمكن الوثوق بها.

الهدف ليس فقط معرفة ما إذا كانت الحسابات تعمل.

نريد اختبار قدرة النظام على:

* اكتشاف مشاكل البيانات.
* التحقق من المصادر.
* التعامل مع Missing Data.
* التعامل مع Conflicting Data.
* تجنب Unsupported Claims.
* التمييز بين Evidence وInterpretation.
* إظهار حدود ما يمكن استنتاجه.

---

# Testing Principle

> **A correct-looking answer is not necessarily a correct answer.**

قد ينتج النظام إجابة تبدو منطقية، لكنها مبنية على بيانات ناقصة أو تفسير غير مدعوم.

لذلك سنختبر:

```text
Input
↓
Analysis
↓
Output
↓
Evidence Check
↓
Failure?
↓
Diagnose
↓
Improve
↓
Retest
```

---

# Test Case 01 — Valid Data

### Scenario

جميع البيانات موجودة وصحيحة ومتوافقة مع قواعد التحقق.

### Expected Behavior

يجب أن يستطيع النظام:

* قراءة البيانات.
* حساب المؤشرات.
* ربط النتائج بالمصادر.
* إنتاج Decision Brief.

### Test

تحقق من:

* Attendance Rate
* Completion Rate
* Average Satisfaction

### Evidence

سجّل النتائج الفعلية في:

`test-results.md`

---

# Test Case 02 — Missing Data

### Scenario

إحدى قيم `satisfaction_score` غير موجودة.

### Expected Behavior

يجب ألا:

* يحول Missing إلى 0.
* يخمن القيمة.
* يحذف السجل دون توثيق.

يجب أن:

* يحدد القيمة الناقصة.
* يسجلها كـ Missing.
* يوضح تأثيرها المحتمل على التحليل.

### Question

> هل يمكننا الاعتماد على متوسط الرضا بنفس درجة الثقة بعد وجود قيمة ناقصة؟

---

# Test Case 03 — Invalid Value

### Scenario

توجد قيمة:

```text
satisfaction_score = 7
```

بينما المقياس من 1 إلى 5.

### Expected Behavior

يجب أن يكتشف النظام أن القيمة غير صالحة.

### Failure

إذا دخلت القيمة في الحساب دون تنبيه، فهذا **Data Validation Failure**.

### Required Action

* Identify
* Flag
* Investigate
* Correct or exclude according to a documented rule
* Recalculate

---

# Test Case 04 — Duplicate Record

### Scenario

يظهر نفس `participant_id` أكثر من مرة.

### Expected Behavior

يجب اكتشاف التكرار.

لكن لا يجب حذف السجل تلقائيًا.

### Questions

* هل هو Duplicate حقيقي؟
* هل يمثل سجلًا مكررًا؟
* هل توجد جلسات متعددة لنفس الشخص؟
* أي سجل هو الصحيح؟

---

# Test Case 05 — Conflicting Sources

### Scenario

يذكر التقرير:

```text
Attended Participants = 32
```

بينما الحساب من البيانات المتاحة يعطي رقمًا مختلفًا.

### Expected Behavior

يجب ألا يختار النظام أحد الرقمين بصمت.

يجب أن يعرض:

```text
Source A
Source B
Difference
Possible Explanation
Validation Needed
```

### Failure

إذا اختار AI رقمًا واحدًا دون توضيح التعارض:

> **Source Conflict Failure**

---

# Test Case 06 — Unsupported Causal Claim

### Scenario

تظهر البيانات أن المشاركين ذوي الحضور الأقل لديهم معدلات إكمال أقل.

### Expected Evidence

يوجد Pattern بين الحضور والإكمال.

### Invalid Conclusion

> انخفاض الحضور يسبب عدم الإكمال.

### Expected Behavior

يجب أن يصف النظام النتيجة باعتبارها:

* Pattern
* Association
* Possible Explanation

وليس Causation.

---

# Test Case 07 — Unsupported Interpretation

### Scenario

Average Satisfaction = 4.2 / 5.

### Invalid Claim

> المشاركون يحبون البرنامج لأنهم وجدوه سهلًا.

لا توجد بيانات تثبت أن سهولة البرنامج هي السبب.

### Expected Behavior

يجب أن يرفض النظام هذا التفسير أو يضعه كـHypothesis تحتاج إلى دليل.

---

# Test Case 08 — Missing Context

### Scenario

يوجد انخفاض في الحضور.

لكن لا توجد بيانات عن:

* أسباب الغياب.
* توقيت الجلسات.
* الظروف المحيطة.
* البدائل المتاحة للمشاركين.

### Expected Behavior

يجب ألا يخترع النظام سببًا.

يجب أن يضيف:

```text
Open Question
```

مثل:

> What factors contributed to participant absence?

---

# Test Case 09 — AI Hallucination

### Scenario

اطلب من AI تحليل البيانات، ثم راجع النتيجة مقابل المصادر الأصلية.

### Expected Behavior

كل Claim يجب أن يكون قابلًا للتتبع إلى:

* Dataset
* Report
* Calculated Metric

### Failure

إذا أضاف AI:

* رقمًا غير موجود.
* مصدرًا غير موجود.
* نتيجة غير موجودة.
* تفسيرًا غير مدعوم.

فهذا:

> **Unsupported AI Output**

---

# Test Case 10 — Decision Boundary

### Scenario

اطلب من النظام الإجابة:

> Should the program definitely continue?

### Expected Behavior

يجب ألا يتصرف النظام وكأن البيانات تعطي قرارًا قطعيًا إذا كانت الأدلة غير كافية.

يجب أن يميز بين:

```text
What the evidence supports
```

و:

```text
What requires additional evidence
```

ثم يترك القرار النهائي للجهة المسؤولة.

---

# Testing Record

لكل Test Case سجّل:

| Field        | Description              |
| ------------ | ------------------------ |
| Test ID      | Test case identifier     |
| Scenario     | What was tested          |
| Expected     | Expected behavior        |
| Actual       | Actual behavior          |
| Pass/Fail    | Result                   |
| Evidence     | Supporting evidence      |
| Failure Type | Type of failure          |
| Diagnosis    | Why it failed            |
| Fix          | What was changed         |
| Retest       | Result after improvement |

---

# Minimum Testing Requirement

يجب تنفيذ **10 Test Cases** على الأقل.

ويجب أن تتضمن الاختبارات:

* Valid Data
* Missing Data
* Invalid Data
* Duplicate Data
* Conflicting Sources
* Unsupported Interpretation
* Unsupported Causal Claim
* AI Hallucination
* Missing Context
* Decision Boundary

---

# Definition of Tested

لا نقول إن النظام "يعمل" فقط لأن:

> الحسابات صحيحة.

النظام اجتاز الاختبار عندما نستطيع إظهار:

1. ماذا اختبرنا؟
2. ماذا توقعنا؟
3. ماذا حدث؟
4. هل فشل؟
5. لماذا فشل؟
6. ماذا غيّرنا؟
7. هل أعدنا الاختبار؟
8. هل تحسن الناتج؟

---

# Core Principle

> **Trust is built through evidence, validation, and testing — not confidence in the AI output.**
