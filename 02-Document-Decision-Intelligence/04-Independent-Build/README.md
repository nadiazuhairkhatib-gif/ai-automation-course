# Independent Build — Evidence-to-Decision Case

## الهدف

بعد أن بنينا معًا نظامًا لتحليل أداء برنامج تدريبي، ينتقل الطالب الآن من **Guided Build** إلى **Independent Build**.

لن نعطيه نفس المشكلة ونفس الخطوات.

سيحصل على **Case جديد**، وعليه أن يطبق طريقة التفكير التي تعلمها.

الهدف:

> **لا تنفذ الوصفة. أعد استخدام طريقة التفكير.**

---

# The Case

## Context

يعمل الطالب مع مركز مجتمعي يقدم ورشًا تقنية للشباب.

خلال الأشهر الثلاثة الماضية، نفذ المركز عدة ورش.

الإدارة تريد معرفة:

> **ما الذي يمكننا قوله بثقة عن أداء الورش، وما الذي نحتاج إلى معرفته قبل اتخاذ قرار بشأن البرنامج القادم؟**

يتوفر للطالب:

* Workshop Report
* Participant Dataset
* Satisfaction Data

لكن البيانات ليست مثالية.

قد تحتوي المصادر على:

* Missing Values
* Inconsistent Values
* Different Definitions
* Conflicting Information
* Unsupported Conclusions

---

# Your Task

ابنِ **Evidence-to-Decision Analysis** يساعد الإدارة على فهم البيانات واتخاذ قرار أفضل.

لا تبدأ باستخدام AI.

ابدأ بـ:

```text id="u8m0lw"
Decision Question
↓
Required Evidence
↓
Data Sources
↓
Validation
↓
Analysis
↓
Insights
↓
Recommendations
↓
Decision Support
```

---

# Step 1 — Frame the Problem

حدد:

### Decision Question

ما القرار الذي تريد مساعدة الإدارة في اتخاذه؟

### Users

من سيستخدم النتيجة؟

### Desired Outcome

ما الذي يحتاج المستخدم إلى معرفته أو فعله بعد قراءة التحليل؟

---

# Step 2 — Identify the Evidence

حدد الأدلة التي تحتاجها للإجابة عن سؤال القرار.

لكل دليل، سجّل:

| Evidence | Source | Why Needed | Validation |
| -------- | ------ | ---------- | ---------- |

لا تجمع البيانات لمجرد وجودها.

اسأل:

> **هل هذه البيانات تساعد فعلًا في الإجابة عن سؤال القرار؟**

---

# Step 3 — Validate

افحص البيانات بحثًا عن:

* Missing Values
* Invalid Values
* Duplicate Records
* Inconsistent Categories
* Conflicting Sources
* Unclear Definitions

وثّق أي مشكلة تجدها.

---

# Step 4 — Analyze

احسب المؤشرات المناسبة لسؤال القرار.

لا تستخدم مؤشرات لمجرد سهولة حسابها.

لكل Metric اسأل:

> **ما القرار الذي يمكن أن تساعد هذه القيمة في دعمه؟**

---

# Step 5 — Separate the Reasoning

لكل نتيجة مهمة، صنّفها:

```text id="r1h1zw"
Fact
Interpretation
Hypothesis
```

### Fact

شيء تدعمه البيانات مباشرة.

### Interpretation

ما قد تعنيه البيانات.

### Hypothesis

تفسير محتمل يحتاج إلى مزيد من الأدلة.

---

# Step 6 — Use AI Carefully

يمكنك استخدام AI للمساعدة في:

* تحليل الأنماط.
* اقتراح Insights.
* تصنيف الملاحظات.
* صياغة النتائج.
* اقتراح أسئلة إضافية.

لكن يجب أن تتحقق من كل نتيجة مقابل البيانات الأصلية.

### AI must not:

* invent missing values
* invent sources
* invent causal relationships
* hide uncertainty
* make unsupported recommendations

---

# Step 7 — Build Decision Support

أنشئ **Decision Brief** يحتوي على:

```text id="q8qkdu"
Decision Question
Executive Summary
Key Findings
Evidence
Insights
Recommendations
Data Limitations
Open Questions
Decision Support
```

---

# Step 8 — Test Your Own Analysis

لا تسلّم النتيجة مباشرة.

أنشئ على الأقل **5 Test Cases** تشمل:

* Missing Data
* Conflicting Data
* Invalid Data
* Unsupported Claim
* AI-generated Interpretation

لكل اختبار سجّل:

```text id="rj1k7k"
Expected
Actual
Pass/Fail
Evidence
Failure
Diagnosis
Fix
Retest
```

---

# Deliverables

يجب أن تسلّم:

### 1. Decision Question

سؤال القرار.

### 2. Evidence Map

مصادر الأدلة وما الذي تثبته.

### 3. Validated Dataset

البيانات بعد التحقق، مع الحفاظ على المصدر الأصلي.

### 4. Analysis

المؤشرات والحسابات المستخدمة.

### 5. Evidence / Interpretation / Hypothesis Map

فصل واضح بين مستويات الاستدلال.

### 6. Decision Brief

الناتج النهائي.

### 7. Test Results

نتائج الاختبارات.

### 8. Failure Log

المشكلات التي اكتشفتها وكيف عالجتها.

---

# Definition of Done

يكتمل الـIndependent Build عندما يستطيع الطالب أن يثبت أنه:

* بدأ من مشكلة وليس من أداة.
* حدد سؤال القرار.
* حدد الأدلة المطلوبة.
* فحص جودة البيانات.
* تعامل مع Missing Data بشكل صحيح.
* اكتشف التعارضات.
* اختار مؤشرات مرتبطة بالقرار.
* فصل Fact عن Interpretation وHypothesis.
* استخدم AI بطريقة مضبوطة.
* رفض Unsupported Claims.
* بنى Decision Brief.
* اختبر تحليله.
* وثّق الأخطاء والتحسينات.
* يستطيع شرح سبب كل استنتاج.

---

# Transfer Question

في نهاية البناء، أجب:

> **إذا أعطيتك غدًا مشكلة مختلفة تمامًا، كيف ستعرف ما البيانات التي تحتاجها قبل أن تستخدم AI؟**

الإجابة المتوقعة ليست اسم أداة.

يجب أن تبدأ بـ:

> **أحدد القرار أولًا، ثم أحدد الأدلة المطلوبة، ثم أتحقق من البيانات قبل تحليلها.**
