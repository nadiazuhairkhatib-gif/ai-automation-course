# U4 — Concepts

## Evaluation & Diagnostic Thinking

### التقييم والتفكير التشخيصي

---

# 1. Evaluation — التقييم

**Evaluation** هو عملية تحديد مدى مطابقة مخرجات النظام للنتيجة المطلوبة، باستخدام معايير وأدلة محددة.

ليس:

> "الإجابة تبدو جيدة."

بل:

> "الإجابة حققت المعايير X وY وZ، ولدينا دليل على ذلك."

---

# 2. Evaluation Starts With Success

لا يمكن أن نبدأ بالتقييم قبل أن نحدد:

> **What does success look like?**

أي:

**Success Criteria — معايير النجاح**

مثلاً، إذا كان AI يصنف طلبات المستخدمين، فقد تكون معايير النجاح:

* التصنيف مناسب للمحتوى.
* لا يخترع فئة غير موجودة.
* الحالات الغامضة لا تُجبر على تصنيف خاطئ.
* المخرج يلتزم بالشكل المطلوب.
* يمكن للإنسان مراجعة النتيجة.

---

# 3. Evaluation Chain

```text id="9f0g4d"
GOAL
↓
SUCCESS CRITERIA
↓
TEST CASES
↓
AI OUTPUT
↓
EVALUATION
↓
EVIDENCE
↓
PASS / FAIL
```

إذا غاب أي جزء مهم من هذه السلسلة، تصبح عملية التقييم أضعف.

---

# 4. Test Case — حالة اختبار

الـTest Case ليست مجرد سؤال.

هي حالة مصممة لاختبار سلوك محدد.

كل Test Case يجب أن يحدد:

```text id="2m8v0f"
Input
+
Expected Behavior
+
Evaluation Criteria
+
Actual Output
+
Result
+
Evidence
```

---

# 5. Expected Output vs Expected Behavior

هذه نقطة مهمة.

ليس دائماً المطلوب أن يكون هناك **نص واحد صحيح حرفياً**.

مثلاً:

### Input

> "I need help registering for the Python course."

قد تكون هناك عدة صياغات صحيحة.

لذلك لا نقارن النص حرفياً فقط.

نحدد:

### Expected Behavior

> The system identifies this as a training-registration request.

إذن:

**Evaluation ≠ Exact String Matching دائماً.**

---

# 6. Evaluation Criteria

سنستخدم مجموعة من المعايير.

## Accuracy — الدقة

هل النتيجة صحيحة؟

---

## Relevance — الملاءمة

هل المخرج يعالج المطلوب فعلاً؟

---

## Completeness — الاكتمال

هل يحتوي على المعلومات الضرورية؟

---

## Grounding — الاستناد إلى الأدلة

هل الادعاءات مدعومة بالمعلومات المتاحة؟

---

## Consistency — الاتساق

هل يتصرف النظام بطريقة متقاربة في الحالات المتشابهة؟

---

## Format Compliance — الالتزام بالشكل

هل التزم النظام بالبنية المطلوبة؟

---

## Safety — السلامة

هل تجنب النظام سلوكاً غير مسموح أو قراراً عالي المخاطر؟

---

## Abstention — الامتناع المناسب

هل يعرف النظام متى يقول:

> "لا أملك معلومات كافية."

بدلاً من اختراع إجابة؟

---

# 7. Not Every Criterion Applies to Every Test

لا نضع كل المعايير على كل حالة.

مثلاً:

| Test            | Accuracy | Grounding | Format | Abstention |
| --------------- | -------: | --------: | -----: | ---------: |
| Classification  |        ✓ |           |      ✓ |          ✓ |
| Document Q&A    |        ✓ |         ✓ |        |          ✓ |
| Summary         |          |         ✓ |      ✓ |            |
| Ambiguous Input |          |           |        |          ✓ |

المعيار يجب أن يرتبط بالسلوك الذي نختبره.

---

# 8. Pass / Fail / Needs Review

ليس كل شيء أبيض وأسود.

يمكن استخدام:

### PASS

المخرج يحقق المعايير.

### FAIL

المخرج يخالف معياراً واضحاً.

### REVIEW

الحالة تحتاج حكماً بشرياً أو معلومات إضافية.

لكن يجب تحديد معنى كل حالة مسبقاً.

---

# 9. Failure Is Evidence

عندما يفشل النظام، لا نقفز إلى الحل.

نبدأ بـ:

> **What exactly failed?**

ثم:

```text id="22u4i1"
Observed Behavior
↓
Expected Behavior
↓
Difference
↓
Evidence
```

---

# 10. Diagnosis — التشخيص

**Diagnosis** يعني محاولة تفسير سبب الفشل بناءً على الأدلة.

مثال:

### Failure

النظام صنف:

> "I want to register for Python."

على أنه:

> Technical Support

### Diagnosis Hypothesis

قد يكون:

* الفئات غير معرفة بوضوح.
* أمثلة التدريب/السياق غير كافية.
* التعليمات غامضة.
* هناك تشابه بين الفئات.
* النظام لا يمتلك قاعدة للتعامل مع الغموض.

لا نقول مباشرة:

> "The prompt is bad."

بل:

> **What evidence supports this diagnosis?**

---

# 11. Hypothesis — فرضية السبب

التشخيص ليس حقيقة دائماً.

لذلك نميز بين:

**Evidence**

و

**Hypothesis**

مثال:

> Evidence: 4 من 6 حالات التسجيل صُنفت كـTechnical Support.

> Hypothesis: تعريف فئة Training Registration غير واضح للنظام.

ثم نغير شيئاً يختبر هذه الفرضية.

---

# 12. Controlled Improvement

لا تغير خمسة أشياء مرة واحدة.

إذا غيرت:

* Prompt
* Data
* Model
* Rules
* Evaluation Criteria

ثم تحسن النظام، فلن تعرف ما الذي سبب التحسن.

لذلك، عندما يكون ذلك ممكناً:

> **Change one meaningful variable at a time.**

---

# 13. V1 → V2

```text id="0k9v8x"
V1
↓
Run Tests
↓
Collect Evidence
↓
Identify Failures
↓
Diagnose
↓
Form Hypothesis
↓
Apply Change
↓
V2
↓
Retest
```

---

# 14. Regression Testing

بعد إصلاح Failure، لا تختبر الحالة الفاشلة فقط.

يجب إعادة اختبار الحالات المهمة التي كانت تعمل سابقاً.

لماذا؟

لأن الإصلاح قد يؤدي إلى:

> **New Failure**

مثلاً:

تحسين تصنيف Training Registration قد يجعل:

> Technical Support

يُصنف خطأً على أنه Training Registration.

إذن:

> **A fix is not verified until the relevant previous behavior is checked again.**

---

# 15. Evaluation Dataset

بدلاً من اختبار النظام بأسئلة عشوائية كل مرة، نبني مجموعة ثابتة:

> **Evaluation Dataset**

تحتوي على حالات تمثل السلوك الذي نهتم به.

في U4 سنبني:

**15–20 Test Cases**

تشمل:

### Normal Cases

الحالات الطبيعية.

### Edge Cases

الحالات الحدية.

### Ambiguous Cases

الحالات الغامضة.

### Missing Information

المعلومات الناقصة.

### Adversarial / Misleading Cases

حالات قد تدفع النظام إلى نتيجة خاطئة.

### Failure Cases

حالات نعرف أنها تمثل نقطة ضعف محتملة.

---

# 16. Test Coverage

الهدف ليس:

> "عندي 20 سؤال."

الهدف:

> "عندي 20 حالة تغطي السلوكيات المهمة."

لذلك نسأل:

* ماذا اختبرنا؟
* ماذا لم نختبر؟
* أين توجد الحدود؟
* أين توجد أكبر المخاطر؟

---

# 17. Evaluation vs Testing

هما مرتبطان لكنهما ليسا الشيء نفسه.

### Testing

> هل النظام تصرف كما هو متوقع في هذه الحالة؟

### Evaluation

> ما مدى جودة أداء النظام وفق معايير محددة عبر مجموعة من الحالات؟

ببساطة:

```text id="p9b5b8"
TEST
= حالة محددة

EVALUATION
= حكم منظم على الأداء عبر حالات ومعايير
```

---

# 18. Diagnostic Thinking

التفكير التشخيصي يعني:

لا ترى:

> "AI gave a wrong answer."

فقط.

بل ترى:

```text id="o4y9qz"
Wrong Output
↓
What was expected?
↓
What exactly differed?
↓
What evidence do we have?
↓
Where could the failure originate?
↓
What hypothesis explains it?
↓
What change tests that hypothesis?
```

---

# 19. The U4 Engineering Loop

احفظ هذه:

> **FAILURE → EVIDENCE → DIAGNOSIS → HYPOTHESIS → CHANGE → RETEST → REGRESSION → VERIFY**

هذه هي المهارة التي نريد أن تخرج بها من الوحدة.

---

# 20. Core Principle

> **Don't optimize what you haven't measured.**

وقبل أن تقول:

> "My AI is better."

اسأل:

> **Better according to what evidence?**
