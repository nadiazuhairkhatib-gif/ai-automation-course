# Guided Build — Document-to-Decision Intelligence System

## الهدف

في هذا البناء سنحوّل مصادر معلومات حقيقية إلى **Decision Brief** يمكن للإدارة استخدامه لفهم أداء برنامج تدريبي واتخاذ قرار مبني على الأدلة.

لن نبدأ بالسؤال:

> ماذا يستطيع AI أن يفعل؟

سنبدأ بالسؤال:

> ما القرار الذي نحتاج إلى دعمه؟

---

# 1. Business Problem

لدى مركز تدريب وابتكار برنامج تدريبي انتهى مؤخرًا.

الإدارة تريد معرفة:

> **هل أداء البرنامج يبرر الاستمرار فيه، وما الذي يحتاج إلى تحسين؟**

المعلومات موزعة بين:

* تقرير PDF
* Google Sheet للحضور
* بيانات رضا المشاركين
* بيانات إكمال البرنامج

المشكلة ليست نقص المعلومات فقط.

المشكلة أن المعلومات:

* موزعة
* غير موحدة
* قد تحتوي على قيم ناقصة
* قد تحتوي على تعارضات
* تحتاج إلى تحليل قبل استخدامها في القرار

---

# 2. System Goal

نبني نظامًا يساعدنا على الانتقال من:

```text
Raw Documents + Spreadsheet
        ↓
Structured Data
        ↓
Validated Evidence
        ↓
Analysis
        ↓
Insights
        ↓
Recommendations
        ↓
Decision Brief
```

---

# 3. Guided Build Architecture

سنقسم البناء إلى مراحل.

### Stage 1 — Collect

جمع المصادر:

* PDF
* Google Sheet
* Satisfaction Data
* Completion Data

### Stage 2 — Extract

استخراج المعلومات المهمة من المستندات والملفات.

### Stage 3 — Structure

تحويل البيانات غير المنظمة إلى جداول أو حقول واضحة.

### Stage 4 — Clean

معالجة:

* Missing values
* Duplicate records
* Inconsistent categories
* Invalid values

### Stage 5 — Validate

مقارنة البيانات بين المصادر واكتشاف التعارضات.

### Stage 6 — Analyze

حساب المؤشرات والإجابة عن أسئلة القرار.

### Stage 7 — Interpret

تحويل النتائج إلى Insights مع الفصل بين:

* Fact
* Interpretation
* Hypothesis

### Stage 8 — Recommend

اقتراح إجراءات مبنية على الأدلة.

### Stage 9 — Decision Brief

تجميع النتيجة في وثيقة قصيرة ومفهومة للإدارة.

---

# 4. Roles of the Tools

لن نستخدم AI لكل شيء.

| المهمة            | الأداة/الطريقة   |
| ----------------- | ---------------- |
| استخراج نص من PDF | AI               |
| تنظيم البيانات    | Google Sheets    |
| الحسابات          | Formulas / Rules |
| تنظيف البيانات    | Rules + Human    |
| اكتشاف الأنماط    | AI + Human       |
| تفسير النتائج     | AI-assisted      |
| التحقق من الأدلة  | Human            |
| القرار النهائي    | Human            |

القاعدة:

> **AI يساعدنا على فهم الأدلة، لكنه لا يصبح مصدر الأدلة.**

---

# 5. Guided Workflow

سيبني المدرب والطلاب النظام معًا:

```text
PDF Report
    │
    ├── Extract
    ↓
Structured Evidence
    │
    ├── Validate
    ↓
Validated Data
    │
    ├── Combine with Google Sheets
    ↓
Unified Dataset
    │
    ├── Analyze
    ↓
Key Findings
    │
    ├── Interpret
    ↓
Insights
    │
    ├── Recommend
    ↓
Decision Brief
```

---

# 6. Questions the System Must Answer

في نهاية البناء يجب أن نستطيع الإجابة عن أسئلة مثل:

1. ما نسبة الحضور؟
2. ما نسبة إكمال البرنامج؟
3. ما متوسط رضا المشاركين؟
4. هل توجد علاقة واضحة بين الحضور والإكمال؟
5. ما أبرز نقاط القوة؟
6. ما أبرز نقاط الضعف؟
7. ما البيانات التي لا نستطيع الاعتماد عليها؟
8. ما التوصيات التي تدعمها الأدلة؟
9. ما الذي ما زلنا لا نعرفه؟

---

# 7. Evidence Table

سننشئ جدولًا موحدًا:

| Metric                  | Value | Source | Status | Notes |
| ----------------------- | ----: | ------ | ------ | ----- |
| Registered Participants |       |        |        |       |
| Attended Participants   |       |        |        |       |
| Completed Participants  |       |        |        |       |
| Average Satisfaction    |       |        |        |       |
| Attendance Rate         |       |        |        |       |
| Completion Rate         |       |        |        |       |

كل قيمة يجب أن يكون لها:

* مصدر
* حالة تحقق
* ملاحظة عند الحاجة

---

# 8. Validation Rules

قبل استخدام أي قيمة في القرار، نتحقق من:

### Completeness

هل البيانات موجودة؟

### Consistency

هل القيم متوافقة بين المصادر؟

### Validity

هل القيمة منطقية؟

### Accuracy

هل نستطيع ربطها بالمصدر الأصلي؟

### Timeliness

هل البيانات تخص الفترة المطلوبة؟

---

# 9. Insight Rules

لا نسمح للنظام بتحويل كل رقم إلى استنتاج.

مثال:

**Evidence:**

> Attendance Rate = 80%

**Valid interpretation:**

> 20% من المسجلين لم يحضروا.

**Unsupported claim:**

> المشاركون غير مهتمين بالبرنامج.

السبب:

لا توجد أدلة كافية على سبب الغياب.

---

# 10. Decision Brief Structure

سيكون المخرج النهائي:

## Executive Summary

ملخص قصير للنتائج.

## Key Findings

أهم النتائج المدعومة بالأرقام.

## Evidence

مصادر الأدلة المستخدمة.

## Insights

ما الذي تعنيه النتائج؟

## Recommendations

ما الإجراءات المقترحة؟

## Data Limitations

ما الذي قد يؤثر على دقة القرار؟

## Open Questions

ما الذي نحتاج إلى معرفته لاحقًا؟

---

# 11. Definition of Done

يُعتبر Guided Build مكتملًا عندما يستطيع الطالب:

* استخراج البيانات من أكثر من مصدر.
* تنظيم البيانات.
* اكتشاف Missing Data.
* اكتشاف تعارض بين مصدرين.
* التحقق من البيانات.
* حساب المؤشرات الأساسية.
* فصل Fact عن Interpretation.
* تحديد Hypothesis غير مثبتة.
* استخدام AI للمساعدة دون اعتباره مصدر الحقيقة.
* إنتاج Decision Brief.
* الدفاع عن كل استنتاج بالدليل الذي يدعمه.

---

# 12. Engineering Lesson

المشروع ليس:

> PDF → AI → Summary

بل:

> **Question → Evidence → Validation → Analysis → Insight → Recommendation → Decision**

وهذا هو جوهر **Evidence Thinking**.
