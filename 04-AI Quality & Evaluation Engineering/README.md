# U4 — AI Quality & Evaluation Engineering

## هندسة جودة وتقييم تطبيقات الذكاء الاصطناعي

### Capability

**Diagnostic Thinking — التفكير التشخيصي**

### Core Question

> **How do we know it works?**
> **How do we know when it fails?**
> **What evidence tells us why it failed?**

---

# 1. Why This Unit Exists

في الوحدات السابقة تعلمنا:

* كيف نفهم العمل.
* كيف نتعامل مع البيانات والأدلة.
* كيف نصمم نظاماً.
* كيف نبني تطبيقاً يحتوي على AI.

لكن بناء النظام لا يعني أنه **موثوق**.

قد يعمل التطبيق في المثال الذي عرضناه أمام الآخرين، ثم يفشل عندما:

* يتغير السؤال.
* تكون البيانات ناقصة.
* تكون الحالة غامضة.
* يعطي AI إجابة تبدو صحيحة لكنها غير مدعومة.
* يتغير شكل المدخلات.
* يفشل النموذج أو الخدمة.
* ينتج النظام مخرجات غير متسقة.

لذلك نحتاج إلى الانتقال من:

> **It works.**

إلى:

> **I have evidence that it works under defined conditions.**

---

# 2. Learning Outcomes

بنهاية الوحدة يستطيع المتدرب أن:

### Understand

* يميز بين Demo وReliable System.
* يفهم معنى Evaluation.
* يحدد Success Criteria.
* يميز أنواع فشل AI المختلفة.

### Design

* يبني Test Cases.
* يحدد Evaluation Criteria.
* يصمم Failure Cases.
* يحدد حدود النجاح والفشل.

### Build

* ينشئ Evaluation Dataset.
* يشغل مجموعة اختبارات.
* يسجل النتائج.
* يقارن بين V1 وV2.

### Diagnose

* يجمع Evidence.
* يصنف Failure.
* يضع Hypothesis للسبب.
* يميز بين Prompt Failure وData Failure وSystem Failure.

### Improve

* يطبق Change.
* يعيد الاختبار.
* ينفذ Regression Testing.
* يتحقق من أن التحسين لم يسبب Failures جديدة.

### Explain

يستطيع الدفاع عن:

> لماذا اعتبرت النتيجة ناجحة أو فاشلة؟

---

# 3. Core Mental Model

```text
TEST
↓
EVIDENCE
↓
EVALUATE
↓
DIAGNOSE
↓
FIX
↓
RETEST
↓
VERIFY
```

هذه ليست مجرد طريقة لاختبار AI.

إنها **Engineering Loop**.

---

# 4. Core Principle

> **A successful demo is not evidence of reliability.**

نجاح حالة واحدة لا يثبت أن النظام موثوق.

نحن لا نختبر فقط:

> Happy Path

بل نختبر:

> **Boundaries, Failures, Ambiguity, and Unexpected Inputs.**

---

# 5. Evaluation Dimensions

في هذه الوحدة سنستخدم معايير مثل:

### Accuracy

هل الإجابة أو التصنيف صحيح؟

### Relevance

هل المخرج يجيب عن المطلوب؟

### Completeness

هل يحتوي على المعلومات المهمة؟

### Grounding

هل الادعاءات مدعومة بالمعلومات المتاحة؟

### Consistency

هل يعطي النظام نتائج مستقرة في الحالات المتشابهة؟

### Format Compliance

هل التزم المخرج بالشكل المطلوب؟

### Safety

هل يتجنب السلوك غير المناسب أو القرار غير المصرح به؟

### Abstention

هل يعرف النظام متى يجب ألا يدّعي أنه يعرف؟

---

# 6. Failure Taxonomy

سنصنف الفشل قبل محاولة إصلاحه.

### Hallucination

AI أنتج معلومة غير مدعومة.

### Wrong Classification

AI وضع المدخل في الفئة الخطأ.

### Missing Information

النظام لم يحصل على المعلومات الضرورية.

### Unsupported Claim

المخرج يحتوي على ادعاء لا يوجد دليل عليه.

### Format Failure

المخرج لا يلتزم بالبنية المطلوبة.

### Inconsistency

نفس النوع من المدخلات ينتج نتائج متناقضة.

### Boundary Failure

النظام لا يعرف متى يتوقف أو يطلب تدخلاً بشرياً.

### System Failure

المشكلة ليست في AI نفسه، بل في النظام المحيط به.

---

# 7. AI Is Not Always the Problem

عند ظهور Failure لا تفترض:

> "The prompt is bad."

قد يكون السبب:

```text
Requirement
Data
Prompt
Model
Context
Business Rule
Application Logic
Integration
Evaluation Criteria
```

لذلك:

> **Not every AI failure is a prompting problem.**

---

# 8. Main Engineering Loop

```text
FAILURE
↓
EVIDENCE
↓
DIAGNOSIS
↓
HYPOTHESIS
↓
CHANGE
↓
RETEST
↓
REGRESSION TEST
↓
VERIFY
```

---

# 9. V1 → V2

سنبدأ بحل أولي:

> **V1**

ثم نختبره.

سنكتشف failures.

ثم:

```text
V1
↓
Test
↓
Failures
↓
Diagnosis
↓
Improvement
↓
V2
```

ثم نقارن:

> هل تحسن النظام فعلاً؟

وليس:

> هل يبدو أفضل؟

---

# 10. Portfolio Project

## AI Output Evaluation System

سيبني المتدرب Evaluation System بسيطاً يستطيع من خلاله:

1. تشغيل Test Cases.
2. تسجيل AI Outputs.
3. مقارنة النتائج مع Expected Behavior.
4. تقييم النتائج وفق Criteria.
5. تسجيل Failures.
6. تشخيص أسباب محتملة.
7. تطبيق Improvement.
8. إعادة الاختبار.
9. تنفيذ Regression Tests.
10. إثبات الفرق بين V1 وV2.

---

# 11. Project Definition of Done

المشروع مكتمل عندما يحتوي على:

* [ ] Evaluation Objective
* [ ] Success Criteria
* [ ] Test Dataset
* [ ] 15–20 Test Cases
* [ ] Evaluation Criteria
* [ ] V1 Results
* [ ] Failure Log
* [ ] Diagnosis
* [ ] Improvement
* [ ] V2 Results
* [ ] Regression Tests
* [ ] Before/After Evidence
* [ ] README
* [ ] Demo
* [ ] Explanation of Design Decisions

---

# 12. NOVA Transfer

في نهاية الوحدة لا يكتفي الطالب باختبار المشروع التدريبي.

ينقل نفس المنهج إلى NOVA:

> **What does success mean for my solution?**

ثم يحدد:

* Success Criteria
* Test Cases
* Failure Cases
* Evidence
* Evaluation Method

وبذلك تصبح:

**NOVA v0.4 — Testing & Quality**

---

# 13. What This Unit Does NOT Teach

هذه الوحدة لا تهدف إلى تحويل المتدرب إلى متخصص في أدوات Evaluation المتقدمة.

لا نحتاج هنا إلى:

* LangSmith
* DeepEval
* Ragas
* MLOps platforms
* Model training
* Fine-tuning
* Advanced statistical evaluation

الهدف هو بناء **Evaluation Thinking** أولاً.

الأدوات المتقدمة تأتي لاحقاً عندما تكون المشكلة تستدعيها.

---

# 14. Unit Principle

> **If you cannot define what success looks like, you cannot reliably evaluate failure.**
