# U2 — نظام ذكاء المستندات وتحويل البيانات إلى قرارات

## Document-to-Decision Intelligence System

### Capability

**Evidence Thinking — التفكير بالأدلة**

---

## لماذا هذه الوحدة؟

المعلومات في المؤسسات غالبًا تكون موجودة، لكنها موزعة بين:

* PDF
* Google Sheets
* تقارير
* جداول
* ملاحظات
* ملفات مختلفة

وجود البيانات لا يعني أن المؤسسة تستطيع اتخاذ قرار جيد منها.

في هذه الوحدة يتعلم الطالب كيف ينتقل من:

**Documents + Data**

إلى:

**Evidence → Insight → Recommendation → Decision**

---

# السؤال المركزي

> **What does the evidence actually tell us?**

ماذا تخبرنا الأدلة فعلًا؟

وليس:

> ماذا يستطيع AI أن يقول عن هذه البيانات؟

---

# المشكلة

يملك مركز تدريب وابتكار:

* تقريرًا عن أحد البرامج التدريبية بصيغة PDF.
* بيانات الحضور في Google Sheets.
* بيانات التقييم ورضا المشاركين.
* معلومات عن إكمال التدريب.

تريد الإدارة معرفة:

> هل أداء البرنامج جيد؟ وما الذي يجب تحسينه؟

المعلومات موجودة، لكنها ليست جاهزة مباشرة لاتخاذ القرار.

---

# رحلة الحل

```text
Documents + Spreadsheet
        ↓
     Extract
        ↓
      Clean
        ↓
     Validate
        ↓
     Analyze
        ↓
     Evidence
        ↓
      Insight
        ↓
 Recommendation
        ↓
      Decision
```

---

# ما الذي سيتعلمه الطالب؟

## Understand

* Data vs Information vs Insight
* Evidence
* Data Extraction
* Data Structuring
* Data Cleaning
* Validation
* Missing Data
* Fact vs Interpretation vs Hypothesis

## Design

* ما البيانات المطلوبة؟
* ما مصدر كل معلومة؟
* كيف نتحقق من صحة البيانات؟
* ما الذي يمكن أن يحسبه النظام؟
* ما الذي يمكن أن يساعد AI في تفسيره؟
* ما الذي يجب أن يبقى قرارًا بشريًا؟

## Build

سيبني الطالب نظامًا يحول:

**PDF + Spreadsheet**

إلى:

**Decision Brief**

يتضمن:

* Findings
* Evidence
* Insights
* Recommendations
* Data Limitations

## Test

سيختبر حالات مثل:

* اختلاف رقم في PDF عن Spreadsheet.
* Missing Value.
* Category غير متسقة.
* Unsupported Insight.
* خلط بين Fact وInterpretation.

## Transfer

يحدد الطالب في NOVA:

* ما البيانات التي يحتاجها؟
* ما مصدرها؟
* ما الذي يعتبر Evidence؟
* كيف سيتحقق من صحة البيانات؟

---

# مبدأ الوحدة

> **AI can help interpret evidence.
> AI is not the evidence.**

البيانات والمصادر هي الأساس.

والقرار النهائي مسؤولية الإنسان.

---

# المشروع الرئيسي

**Document-to-Decision Intelligence System**

نظام يساعد فريقًا إداريًا على تحليل معلومات برنامج تدريبي وتحويلها إلى **Decision Brief** قابل للمراجعة.

---

# أدوات الوحدة

### Primary Tool

**Google Sheets**

### Supporting Tools

* ChatGPT
* Gemini
* Claude

---

# ما لا ندرّسه في هذه الوحدة

لا نريد تحويل الوحدة إلى دورة كاملة في Data Science.

لن ندخل بعمق في:

* SQL
* Python Data Analysis
* Power BI
* Tableau
* Machine Learning
* بناء Data Warehouse
* Advanced Statistics

الهدف هو **Evidence Thinking + AI-assisted Data Workflow**.

---

# المخرج النهائي

بنهاية الوحدة، يجب أن يستطيع الطالب الانتقال من:

> **"عندي بيانات، اعمل لي تقريرًا."**

إلى:

> **"هذه هي مصادر البيانات، وهذه طريقة التحقق منها، وهذه الأدلة، وهذه الاستنتاجات التي تدعمها، وهذه حدود البيانات، وهذه التوصية المبنية عليها."**

---

# NOVA

في نهاية الوحدة يضيف الطالب إلى NOVA:

**v0.2 — Data & Evidence**

ويحدد:

* ما البيانات التي يحتاجها؟
* من أين سيحصل عليها؟
* ما البيانات الموثوقة؟
* كيف سيتحقق منها؟
* ما البيانات الناقصة؟
* ما الأسئلة التي يريد أن يجيب عنها؟
