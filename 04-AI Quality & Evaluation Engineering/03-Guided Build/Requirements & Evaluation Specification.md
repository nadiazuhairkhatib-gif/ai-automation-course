# U4 — Requirements & Evaluation Specification

## مواصفات نظام التقييم

---

# 1. System Objective

بناء **Evaluation Harness** يستطيع تقييم نظام AI لمعالجة وتصنيف طلبات مركز التدريب.

الهدف:

> إنشاء طريقة قابلة للتكرار لقياس جودة النظام، واكتشاف failures، وتشخيصها، والتحقق من التحسينات.

---

# 2. Functional Requirements

### FR-01 — Load Test Dataset

يجب أن يستطيع النظام قراءة مجموعة Test Cases منظمة.

---

### FR-02 — Run AI

يجب تشغيل AI على كل Test Case.

---

### FR-03 — Capture Output

يجب حفظ المخرج الفعلي لكل حالة.

---

### FR-04 — Compare With Expected Behavior

يجب مقارنة Actual Behavior مع Expected Behavior.

---

### FR-05 — Evaluate Criteria

يجب تقييم:

* Classification
* Summary
* Format
* Abstention

بحسب الحالة.

---

### FR-06 — Record Result

يجب تسجيل:

* PASS
* FAIL
* REVIEW

---

### FR-07 — Record Evidence

يجب أن يحتوي Failure على دليل قابل للمراجعة.

---

### FR-08 — Diagnose Failure

يجب تسجيل نوع الفشل والسبب المحتمل.

---

### FR-09 — Run V2

يجب السماح بإعادة تشغيل مجموعة الاختبارات بعد التغيير.

---

### FR-10 — Compare Versions

يجب مقارنة نتائج V1 وV2.

---

### FR-11 — Regression Testing

يجب إعادة اختبار الحالات المحددة بعد التحسين.

---

# 3. Non-Functional Requirements

### NFR-01 — Repeatability

يمكن تشغيل نفس Dataset مرة أخرى.

### NFR-02 — Traceability

يمكن معرفة:

> Input → Output → Evaluation → Evidence

### NFR-03 — Transparency

يمكن للطالب تفسير سبب PASS أو FAIL.

### NFR-04 — Simplicity

النظام صغير بما يكفي لفهمه خلال الوحدة.

---

# 4. Evaluation Rules

## Classification

**PASS** عندما يطابق التصنيف المتوقع.

**FAIL** عندما يكون التصنيف خاطئاً.

**REVIEW** عندما تكون الحالة غامضة أو لا توجد معلومات كافية للحكم الآلي.

---

## Summary

PASS إذا:

* يعكس المدخل.
* لا يضيف معلومات غير موجودة.
* يحتفظ بالمعلومات المهمة.

FAIL إذا:

* اخترع معلومة.
* حذف معلومة مهمة.
* غيّر معنى المدخل.

---

## Format

PASS إذا:

* الحقول المطلوبة موجودة.
* القيم ضمن الخيارات المسموحة.
* البنية قابلة للقراءة والمعالجة.

---

## Abstention

PASS إذا:

* الحالة غير واضحة.
* والنظام يعترف بعدم كفاية المعلومات أو يطلب Human Review.

FAIL إذا:

* يختار نتيجة بثقة عندما لا يوجد دليل كافٍ.

---

# 5. Failure Types

استخدم أحد التصنيفات التالية:

```text id="7i3w0j"
Wrong Classification
Hallucination
Unsupported Claim
Missing Information
Format Failure
Inconsistency
Abstention Failure
Boundary Failure
Prompt/Instruction Failure
Data/Context Failure
System Failure
Other
```

---

# 6. Evidence Requirements

لا تسجل:

> "AI was wrong."

سجل:

```text id="n2p8k4"
Expected:
TRAINING_REGISTRATION

Actual:
TECHNICAL_SUPPORT

Evidence:
The input explicitly asks about course registration.
```

الدليل يجب أن يجعل Failure قابلاً للمراجعة من شخص آخر.

---

# 7. Diagnosis Requirements

التشخيص يجب أن يفرق بين:

### Evidence

ما نعرفه.

### Hypothesis

ما نعتقد أنه سبب المشكلة.

مثال:

**Evidence**

> 4 registration cases were classified as Technical Support.

**Hypothesis**

> The category definitions are insufficiently distinct.

---

# 8. Change Requirements

كل Improvement يجب أن يحتوي على:

```text
Change:
[ما الذي تغير؟]

Reason:
[لماذا تغير؟]

Expected Effect:
[ماذا نتوقع أن يتحسن؟]
```

---

# 9. Retest Requirements

بعد التغيير يجب إعادة اختبار:

### A. Failed Cases

الحالات التي فشلت.

### B. Related Cases

الحالات المرتبطة بنفس السلوك.

### C. Regression Cases

حالات كانت ناجحة سابقاً.

---

# 10. Evaluation Principle

لا نريد:

> **One Test → One Conclusion**

نريد:

> **Multiple Cases → Evidence → Pattern → Diagnosis**

---

# 11. Quality Gate

قبل إعلان V2 ناجحة، يجب أن يستطيع الطالب الإجابة:

1. ماذا كان Failure؟
2. ما الدليل؟
3. ما تشخيصك؟
4. ما التغيير؟
5. لماذا توقعت أن يساعد؟
6. ماذا حدث بعد التغيير؟
7. هل تحسنت الحالة الفاشلة؟
8. هل بقيت الحالات السابقة تعمل؟
9. هل ظهر Failure جديد؟
10. ما الذي ما زال غير مثبت؟

---

# 12. Engineering Standard

لا تقل:

> "The AI seems better."

قل:

> "Under the defined evaluation dataset and criteria, V2 improved [specific behavior], while the relevant regression tests remained passing."

والأهم:

إذا لم يكن الدليل كافياً، قل:

> **We do not know yet.**

هذه أيضاً نتيجة هندسية صحيحة.
