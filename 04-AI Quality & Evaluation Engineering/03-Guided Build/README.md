# U4 — Guided Build

## AI Evaluation Harness

### نظام تقييم مخرجات الذكاء الاصطناعي

---

# 1. Project

سننشئ نظاماً بسيطاً لتقييم AI Classification & Response Quality.

المشروع ليس تطبيقاً جديداً للمستخدم النهائي.

هو:

> **Evaluation Harness — بيئة اختبار وتقييم**

تساعدنا على تشغيل مجموعة ثابتة من الحالات وتسجيل نتائجها بطريقة منظمة.

---

# 2. Scenario

لدي مركز تدريب يستخدم AI لمعالجة الرسائل الواردة.

يجب أن يستطيع النظام:

1. فهم الرسالة.
2. تصنيف نوع الطلب.
3. تحديد ما إذا كانت المعلومات كافية.
4. التعامل مع الغموض.
5. إنتاج مخرج منظم.

---

# 3. Supported Categories

سنستخدم أربع فئات:

```text id="2j0k4p"
TRAINING_REGISTRATION
TECHNICAL_SUPPORT
ACCOUNT_SUPPORT
GENERAL_INQUIRY
```

وهناك حالة إضافية:

```text
NEEDS_HUMAN_REVIEW
```

تستخدم عندما لا يستطيع النظام الوصول إلى قرار موثوق.

---

# 4. AI Task

لكل Input، ينتج النظام:

```json
{
  "category": "",
  "summary": "",
  "confidence": "",
  "needs_human_review": false
}
```

### Important

هذه البنية ليست حكماً على "ذكاء" النظام.

هي فقط تجعل المخرج:

> **Observable + Testable**

---

# 5. Expected Behavior

مثال:

### Input

> I want to register for the Python course.

### Expected

```text
category:
TRAINING_REGISTRATION

needs_human_review:
false
```

---

### Ambiguous Input

> I need help.

المطلوب ليس إجبار AI على اختيار فئة.

بل:

```text
needs_human_review:
true
```

أو سلوك مكافئ يثبت أن المعلومات غير كافية.

---

# 6. Evaluation Dataset

سننشئ Dataset من **20 حالة**.

يجب أن تحتوي على:

### 1–8 Normal Cases

حالات واضحة.

### 9–11 Ambiguous Cases

حالات تحتاج حذراً.

### 12–14 Missing Information

معلومات غير كافية.

### 15–17 Boundary Cases

حالات تقع بين فئتين.

### 18–20 Failure-Oriented Cases

حالات مصممة لاكتشاف نقاط ضعف النظام.

---

# 7. Dataset Schema

أنشئ جدولاً:

| Test ID | Input | Expected Category | Expected Behavior | Risk |
| ------- | ----- | ----------------- | ----------------- | ---- |
| TC-01   |       |                   |                   |      |
| TC-02   |       |                   |                   |      |
| ...     |       |                   |                   |      |
| TC-20   |       |                   |                   |      |

---

# 8. Evaluation Criteria

لكل حالة، نقيم:

### Classification

هل الفئة صحيحة؟

### Summary

هل الملخص يعكس المدخل؟

### Completeness

هل المعلومات المهمة موجودة؟

### Format

هل المخرج يلتزم بالـSchema؟

### Abstention

هل النظام يعرف متى يحتاج Human Review؟

---

# 9. Evaluation Record

لكل Test Case:

| Field          | Value            |
| -------------- | ---------------- |
| Test ID        |                  |
| Input          |                  |
| Expected       |                  |
| Actual         |                  |
| Classification | PASS/FAIL/REVIEW |
| Summary        | PASS/FAIL        |
| Format         | PASS/FAIL        |
| Abstention     | PASS/FAIL/N/A    |
| Evidence       |                  |
| Failure Type   |                  |
| Diagnosis      |                  |
| Fix            |                  |
| Retest         |                  |

---

# 10. Build V1

أنشئ أول نسخة بدون محاولة جعلها مثالية.

سمِّها:

> **V1**

شغّل الـ20 Test Cases.

لا تعدل النظام أثناء تشغيل مجموعة الاختبار الأولى.

الهدف:

> **Capture Baseline**

أي معرفة نقطة البداية.

---

# 11. Baseline

بعد تشغيل V1، احسب على الأقل:

* Total Tests
* Passed
* Failed
* Needs Review
* Classification Failures
* Format Failures
* Abstention Failures

مثال:

```text id="z8m8g4"
Total: 20
Pass: 14
Fail: 4
Review: 2
```

الأرقام هنا مثال فقط.

يجب استخدام نتائجك الفعلية.

---

# 12. Failure Analysis

اختر **3 Failures مهمة** على الأقل.

لكل واحدة:

```text id="l1n9fb"
Failure
↓
Evidence
↓
Diagnosis
↓
Hypothesis
```

لا تبدأ بالإصلاح مباشرة.

---

# 13. V2 Improvement

اختر تغييراً واضحاً مبنياً على التشخيص.

مثلاً:

* تحسين Category Definitions.
* إضافة Ambiguity Rule.
* تحسين Output Schema.
* تعديل Prompt Instructions.
* إضافة Validation Rule.

وثّق:

```text id="z7t2f0"
What changed?

Why did we change it?

What evidence supported the change?

What did we expect to improve?
```

---

# 14. Retest

شغّل:

1. الـFailure Cases.
2. الحالات المرتبطة بها.
3. مجموعة Regression Tests.

ثم قارن:

```text id="8f1t2v"
V1
vs
V2
```

---

# 15. Regression Test

يجب اختيار مجموعة من الحالات التي كانت تعمل في V1.

مثلاً:

```text
TC-01
TC-03
TC-05
TC-07
TC-10
```

ثم نتأكد:

> هل بقيت تعمل بعد التغيير؟

---

# 16. Before / After Evidence

أنشئ جدولاً:

| Metric                  | V1 | V2 | Change |
| ----------------------- | -: | -: | -----: |
| Pass                    |    |    |        |
| Fail                    |    |    |        |
| Review                  |    |    |        |
| Classification Failures |    |    |        |
| Format Failures         |    |    |        |
| Abstention Failures     |    |    |        |

لا يكفي أن تقول:

> V2 is better.

أظهر الدليل.

---

# 17. Important Constraint

لا تحاول تحسين كل شيء.

اختر مشكلة واحدة أو مجموعة صغيرة مرتبطة من المشاكل.

ثم:

> Diagnose → Change → Retest

حتى تستطيع فهم أثر التغيير.

---

# 18. Definition of Done

* [ ] Evaluation objective defined.
* [ ] Success criteria defined.
* [ ] 20 test cases created.
* [ ] V1 executed.
* [ ] Baseline captured.
* [ ] Failures classified.
* [ ] At least 3 failures diagnosed.
* [ ] Improvement hypothesis written.
* [ ] V2 created.
* [ ] Relevant tests repeated.
* [ ] Regression tests executed.
* [ ] Before/After evidence captured.
* [ ] Results documented.
* [ ] Student can explain why V2 changed.

---

# 19. Final Question

بعد انتهاء البناء:

> **If someone asked "How do you know your AI works?", what evidence would you show?**

الإجابة يجب ألا تكون:

> "Because I tested it and it worked."

بل يجب أن تحتوي على:

> **Defined Criteria + Test Dataset + Results + Failure Analysis + Retest + Evidence**
