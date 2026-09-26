# U4 — الموارد والمراجع

## AI Quality & Evaluation Engineering

## 1. الأدوات الأساسية (Core Tools)

### أداة الذكاء الاصطناعي (AI Model)

يمكن استخدام أحد النماذج المتاحة في الدورة لتنفيذ حالات الاختبار.

الهدف ليس مقارنة النماذج.

الهدف هو تعلم:

> **كيف نقيس سلوك نظام AI؟**

---

### Google Sheets

يُستخدم لتنظيم:

* Test Cases
* Expected Output
* Actual Output
* PASS / FAIL
* Failure Type
* Evidence
* V1 / V2 Comparison

---

### GitHub

يُستخدم لتوثيق:

* Dataset
* Test Cases
* Failure Logs
* Results
* Documentation
* NOVA

---

# 2. المفاهيم التي يجب أن يعرفها الطالب

قبل إنهاء الوحدة، يجب أن يكون الطالب قادراً على شرح:

* Evaluation
* Test Case
* Expected Behavior
* Actual Output
* Baseline
* Failure
* Failure Pattern
* Diagnosis
* Evidence
* Regression Testing
* Evaluation Criteria
* Grounding
* Abstention
* Human Review
* Quality Gate

---

# 3. ما الذي لا نحتاج إلى استخدامه في U4؟

هذه الوحدة لا تحتاج إلى أدوات تقييم متقدمة مثل:

* LangSmith
* DeepEval
* Ragas

ليس لأنها غير مفيدة، بل لأن هدف U4 هو بناء **طريقة التفكير في التقييم** قبل إدخال أدوات متخصصة.

---

# 4. مبدأ الأدوات

> **Tool comes after the evaluation method.**

أي:

> **المنهجية أولاً، الأداة ثانياً.**

إذا كان الطالب لا يعرف:

* ماذا يختبر؟
* لماذا يختبره؟
* ما النتيجة المتوقعة؟
* كيف يثبت الفشل؟
* كيف يشخصه؟

فلن تحل المشكلة إضافة أداة تقييم جديدة.

---

# 5. مصادر التعلم داخل الوحدة

يُرجع الطالب إلى:

### Testing

فهم الفرق بين:

* Test Case
* Expected Result
* Actual Result
* Pass / Fail

### Software Quality

فهم:

* Regression
* Edge Cases
* Failure Analysis
* Quality Criteria

### AI Evaluation

فهم:

* Task-specific Evaluation
* Grounding
* Hallucination
* Abstention
* Human Evaluation

### Prompt / System Design

فهم العلاقة بين:

> Instructions → Context → Model → Output → Evaluation

---

# 6. أسئلة البحث المصغر (Mini Research)

يختار كل فريق سؤالاً واحداً فقط:

### السؤال 1

ما الفرق بين **Evaluation** و **Testing**؟

### السؤال 2

لماذا لا تكفي الحالات الطبيعية لتقييم نظام AI؟

### السؤال 3

ما معنى **Regression Testing**؟

### السؤال 4

متى يجب على نظام AI أن يمتنع عن الإجابة؟

### السؤال 5

ما الفرق بين **Accuracy** و **Grounding**؟

---

# 7. قاعدة البحث

لا نريد عرضاً نظرياً طويلاً.

لكل فريق:

**3 دقائق فقط**

ويجيب عن:

1. ما المفهوم؟
2. لماذا يهم؟
3. مثال من مشروعنا.
4. ما الخطأ الذي يحدث إذا تجاهلناه؟

---

# 8. سؤال البحث الأهم

> **How do you know an AI system works?**

لا توجد إجابة واحدة مثل:

> "لأن الإجابة تبدو جيدة."

الإجابة الهندسية يجب أن تبدأ من:

**Expected Behavior → Test Cases → Evidence → Evaluation → Diagnosis → Retest**

---

# 9. Transfer Resource

عند إنهاء الوحدة، يجب أن يستطيع الطالب أخذ هذه المنهجية إلى أي مشروع جديد:

```text id="4x7q1m"
Define Success
↓
Design Test Cases
↓
Run Baseline
↓
Capture Evidence
↓
Find Failures
↓
Diagnose
↓
Fix
↓
Retest
↓
Regression Test
↓
Verify
```

---

# 10. معيار الوحدة

في نهاية U4، لا نريد طالباً يقول:

> "أنا أعرف كيف أختبر الـAI."

نريد طالباً يستطيع أن يقول:

> **"أستطيع تعريف ما يعنيه نجاح النظام، وتصميم اختبارات تكشف حدوده، وتحليل فشله بالأدلة، ثم تحسينه والتحقق من أن الإصلاح لم يكسر سلوكاً سابقاً."**

وهذا هو الانتقال من:

> **AI User**

إلى:

> **AI Solution Builder**

ثم خطوة إضافية نحو:

> **AI Solution Engineer**
