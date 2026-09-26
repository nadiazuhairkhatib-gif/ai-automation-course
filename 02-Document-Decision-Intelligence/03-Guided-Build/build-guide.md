# دليل البناء الموجّه — Guided Build

## الهدف

في هذا البناء سنحوّل تقريرًا تدريبيًا وبيانات المشاركين إلى **Decision Brief** يدعم اتخاذ قرار مبني على الأدلة.

لن نبدأ باستخدام AI.

سنبدأ بالسؤال:

> **ما القرار الذي نريد دعمه؟**

ثم نبني سلسلة التحليل:

```text
Question
↓
Extract
↓
Structure
↓
Clean
↓
Validate
↓
Analyze
↓
Interpret
↓
Recommend
↓
Decision Brief
```

---

# المرحلة 1 — تحديد سؤال القرار

سؤالنا هو:

> **هل أداء البرنامج يبرر الاستمرار فيه، وما الذي يحتاج إلى تحسين؟**

قبل استخدام أي أداة، حدّد:

* ما القرار المطلوب؟
* ما الأدلة التي نحتاجها؟
* أين توجد هذه الأدلة؟
* ما الذي لا نعرفه بعد؟

### لا تفعل

لا تبدأ بسؤال:

> "ماذا يستطيع ChatGPT أن يفعل بهذه البيانات؟"

### افعل

ابدأ بسؤال:

> "ما المعلومات التي نحتاجها حتى نستطيع الإجابة عن سؤال القرار؟"

---

# المرحلة 2 — فحص مصادر البيانات

افتح:

```text
program-report.md
participant-data.csv
```

في هذه المرحلة لا تحاول الوصول إلى استنتاج.

فقط افحص:

* ما المعلومات الموجودة؟
* ما مصدر كل معلومة؟
* ما تعريف كل مؤشر؟
* هل توجد معلومات ناقصة؟
* هل توجد اختلافات بين المصادر؟
* هل المصادر تتحدث عن المجموعة نفسها؟

أنشئ **Source Inventory**:

| Source              | Contains                  | Validation Needed                  |
| ------------------- | ------------------------- | ---------------------------------- |
| Program Report      | Program-level results     | Compare with participant dataset   |
| Participant Dataset | Participant-level records | Check completeness and consistency |

---

# المرحلة 3 — إدخال البيانات إلى Google Sheets

افتح ملف `participant-data.csv` باستخدام **Google Sheets**.

أنشئ أربع أوراق:

```text
Raw Data
Validation
Analysis
Decision Brief
```

## Raw Data

ضع البيانات الأصلية هنا.

### قاعدة مهمة

> **لا تعدّل البيانات الأصلية.**

أي تنظيف أو تعديل يجب أن يحدث في ورقة أخرى حتى نستطيع الرجوع إلى المصدر الأصلي.

---

# المرحلة 4 — إنشاء فحوصات التحقق

في ورقة `Validation` نبدأ بالتحقق من جودة البيانات.

## 4.1 التحقق من الحضور

يجب أن يكون:

```text
attendance_sessions <= total_sessions
```

إذا وجدنا سجلًا يخالف ذلك، فلدينا **Data Quality Issue**.

---

## 4.2 التحقق من الإكمال

افحص العلاقة بين:

```text
attendance_sessions
completed
```

لا تفترض مسبقًا أن:

> حضور عدد معين من الجلسات = إكمال البرنامج.

نحتاج أولًا إلى معرفة كيف تم تعريف `completed`.

---

## 4.3 التحقق من Satisfaction Score

يجب أن تكون قيمة:

```text
satisfaction_score
```

ضمن المجال:

```text
1–5
```

أي قيمة خارج هذا المجال تحتاج إلى التحقيق.

---

## 4.4 Missing Values

ابحث عن القيم الناقصة.

إذا كانت قيمة غير موجودة، سجّلها:

```text
Missing
```

ولا تستبدلها تلقائيًا بـ:

```text
0
```

تذكّر:

> **Missing ≠ Zero**

---

## 4.5 Duplicate Records

تحقق من أن `participant_id` لا يتكرر.

إذا ظهر نفس المشارك أكثر من مرة، لا تحذف السجل مباشرة.

أولًا اسأل:

> هل هو تكرار حقيقي أم أن هناك سببًا لوجود أكثر من سجل؟

---

# المرحلة 5 — مقارنة المصادر

يذكر `program-report.md`:

```text
Registered Participants = 40
Attended Participants = 32
Completed Participants = 28
Average Satisfaction = 4.2
```

الآن قارن هذه القيم مع البيانات الموجودة في `participant-data.csv`.

لا تحاول إجبار المصدرين على التطابق.

بدلًا من ذلك اسأل:

1. هل المصدران يستخدمان التعريف نفسه؟
2. هل يتحدثان عن المجموعة نفسها؟
3. هل الفترة الزمنية نفسها؟
4. هل هناك مشاركون غير موجودين في ملف البيانات؟
5. هل طريقة حساب المؤشر نفسها؟
6. هل يمكن التحقق من الرقم من المصدر الأصلي؟

إذا وجدت اختلافًا، سجّل:

```text
Source A
Source B
Difference
Possible Explanation
Validation Needed
```

---

# المرحلة 6 — حساب المؤشرات الأساسية

بعد التحقق من البيانات، ننتقل إلى `Analysis`.

احسب المؤشرات الأساسية.

## Attendance Rate

نسبة الحضور:

```text
Attended Participants
--------------------- × 100
Registered Participants
```

## Completion Rate

نسبة الإكمال:

```text
Completed Participants
---------------------- × 100
Registered Participants
```

## Average Satisfaction

احسب متوسط:

```text
satisfaction_score
```

## Completion by Attendance

قارن الإكمال بين المشاركين الذين حضروا عددًا مختلفًا من الجلسات.

الهدف هنا هو:

> **اكتشاف Pattern — نمط**

وليس إثبات:

> **Causation — علاقة سببية**

---

# المرحلة 7 — إدخال AI بطريقة مضبوطة

الآن فقط نستخدم AI.

أعطِ النموذج:

* البيانات التي تم التحقق منها
* المؤشرات المحسوبة
* الأدلة المهمة
* القيود المعروفة
* المعلومات التي ما زالت ناقصة

وطلب منه المساعدة في:

* اكتشاف الأنماط
* اقتراح تفسيرات محتملة
* صياغة Insights أولية
* اقتراح أسئلة تحتاج إلى مزيد من البيانات

### قاعدة مهمة

لا تطلب من AI:

> "حلل البيانات وأخبرني ماذا نفعل."

بل أعطه **حدودًا واضحة** واطلب منه الفصل بين:

```text
Evidence
Interpretation
Hypothesis
```

---

# المرحلة 8 — فصل الدليل عن التفسير

أنشئ جدولًا:

| Evidence             | Interpretation   | Confidence          |
| -------------------- | ---------------- | ------------------- |
| Verified observation | What it may mean | High / Medium / Low |

مثال:

### Evidence

> المشاركون الذين حضروا عددًا أقل من الجلسات لديهم معدل إكمال أقل.

### Interpretation

> قد يكون انخفاض الحضور مرتبطًا بانخفاض الإكمال.

### Hypothesis

> قد تكون صعوبة الالتزام بوقت التدريب أحد أسباب انخفاض الحضور.

لاحظ أن الـHypothesis تحتاج إلى أدلة إضافية.

لا نكتب:

> "انخفاض الحضور هو سبب عدم الإكمال."

لأن البيانات الحالية لا تثبت السببية.

---

# المرحلة 9 — بناء التوصيات

كل **Recommendation** يجب أن ترتبط بأدلة.

مثال:

### Evidence

أظهر التقرير أن بعض المشاركين واجهوا صعوبة في ممارسة الأنشطة خارج جلسات التدريب.

### Recommendation

> إضافة أنشطة ممارسة قصيرة ومتابعة بين الجلسات.

لكن لا نقول:

> "هذه الطريقة ستزيد الإكمال بالتأكيد."

لأن ذلك ادعاء جديد يحتاج إلى اختبار.

---

# المرحلة 10 — توثيق القيود

قبل كتابة النتيجة النهائية، أنشئ قسم:

**Data Limitations**

وسجّل فيه:

* Missing Data
* Conflicting Sources
* Incomplete Records
* Small Sample
* Unclear Definitions
* Unverified Assumptions
* Outdated Information

السؤال الأساسي:

> **ما الشيء الذي قد يجعل استنتاجنا خاطئًا؟**

---

# المرحلة 11 — بناء Decision Brief

استخدم الـSchema الموجود في:

```text
output-schema.md
```

ويجب أن يحتوي الناتج النهائي على:

```text
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

لا تنتج **AI Summary** فقط.

نريد **Decision Support Artifact** يمكن لشخص آخر مراجعته ومعرفة:

* ماذا وجدنا؟
* من أين جاءت المعلومة؟
* ماذا تعني؟
* ما الذي لا نعرفه؟
* ما الذي نقترحه؟
* ما الذي يحتاج إلى قرار بشري؟

---

# المرحلة 12 — Human Review

قبل اعتماد النتيجة النهائية، أجب عن الأسئلة التالية:

### Evidence

> هل أستطيع تحديد مصدر كل رقم مهم؟

### Interpretation

> هل حولت تفسيرًا إلى حقيقة؟

### Causation

> هل ادعيت أن شيئًا تسبب في شيء آخر دون دليل كافٍ؟

### Missing Data

> هل عاملت قيمة ناقصة وكأنها صفر؟

### AI

> هل أضاف AI معلومة أو تفسيرًا غير موجود في الأدلة؟

### Recommendation

> هل التوصية مرتبطة فعلًا بالأدلة؟

### Decision

> هل القرار النهائي يتجاوز ما تسمح به البيانات؟

---

# Definition of Done

يكتمل البناء عندما يستطيع الطالب:

* تحديد سؤال القرار.
* تحديد الأدلة المطلوبة.
* فحص أكثر من مصدر.
* الحفاظ على البيانات الأصلية.
* تنظيف البيانات دون فقدان المصدر.
* اكتشاف Missing Data.
* اكتشاف Duplicate Records.
* اكتشاف Conflicting Sources.
* التحقق من صحة البيانات.
* حساب المؤشرات الأساسية.
* التمييز بين Fact وInterpretation وHypothesis.
* استخدام AI للمساعدة في التفسير.
* اكتشاف Unsupported Claims.
* بناء Evidence-Based Recommendations.
* توثيق Data Limitations.
* إنتاج Decision Brief.
* الدفاع عن كل استنتاج بالدليل الذي يدعمه.

---

# Engineering Principle

> **Analyze only what you can support.**

أي:

> **حلّل فقط ما تستطيع دعمه بالأدلة.**

AI يمكن أن يسرّع التحليل، لكنه لا يتحمل مسؤولية صحة الأدلة أو القرار.

**الطالب هو المسؤول عن:**

```text
Evidence
↓
Validation
↓
Reasoning
↓
Interpretation
↓
Recommendation
```
