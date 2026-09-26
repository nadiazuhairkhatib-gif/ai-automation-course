# U5 — متطلبات التسليم والدفاع

## 1. الملفات المطلوبة

```text id="u5m8c2"
05-Grounded-Knowledge-Assistant/
├── README.md
├── 01-Challenge/
│   ├── challenge-brief.md
│   └── attempt.md
├── 02-Concepts/
│   └── grounding-thinking.md
├── 03-Guided-Build/
│   ├── README.md
│   ├── knowledge-sources.md
│   ├── assistant-scope.md
│   └── build-guide.md
├── 04-Independent-Build/
│   └── README.md
├── 05-Testing/
│   ├── evaluation-dataset.md
│   ├── test-cases.md
│   └── failure-log.md
├── 06-NOVA/
│   └── nova-v0.5-template.md
├── 07-Submission/
│   └── README.md
└── 08-Resources/
    └── tools-and-references.md
```

---

# 2. مخرجات المشروع

يجب أن تسلّم:

* Knowledge Base.
* Grounded Assistant.
* 5–8 مصادر.
* Source Authority Map.
* Scope Definition.
* Citations.
* 10–15 Evaluation Questions.
* Failure Log.
* Evidence.
* Retest Results.
* Known Limitations.
* NOVA v0.5.

---

# 3. العرض العملي (Demo)

مدة العرض:

**5–7 دقائق**

### الجزء الأول — السؤال الطبيعي

اعرض سؤالاً يمكن للمساعد الإجابة عنه.

### الجزء الثاني — المصدر

أظهر من أين جاءت الإجابة.

### الجزء الثالث — سؤال غير موجود

اختبر Abstention.

### الجزء الرابع — حالة تعارض أو نسخة قديمة

أظهر كيف تعامل النظام معها.

### الجزء الخامس — Failure

أظهر خطأ حقيقياً اكتشفته.

### الجزء السادس — Fix

اشرح ماذا غيّرت.

### الجزء السابع — Retest

أظهر النتيجة بعد الإصلاح.

---

# 4. أسئلة الدفاع (Defense Questions)

يجب أن تستطيع الإجابة عن:

### Q1

ما الفرق بين Chatbot وGrounded Assistant؟

### Q2

ما الفرق بين Retrieval وGeneration؟

### Q3

إذا كانت الإجابة خاطئة، كيف تعرف أين حدث الخطأ؟

### Q4

لماذا لا يكفي وجود Citation؟

### Q5

ماذا تفعل عند تعارض مصدرين؟

### Q6

كيف تتعامل مع المعلومات القديمة؟

### Q7

متى يجب على النظام أن يمتنع عن الإجابة؟

### Q8

ما أكبر Failure اكتشفته؟

### Q9

ما الدليل على أن الإصلاح نجح؟

### Q10

هل كل مشروع يحتاج RAG؟ ولماذا؟

---

# 5. Definition of Done

يعتبر المشروع مكتملًا عندما:

* [ ] توجد Knowledge Base.
* [ ] المصادر محددة.
* [ ] Source Authority واضحة.
* [ ] Scope محدد.
* [ ] المساعد يستطيع الاسترجاع.
* [ ] الإجابات مرتبطة بالمصادر.
* [ ] Citation تعمل.
* [ ] Abstention تم اختباره.
* [ ] Versioning تم اختباره.
* [ ] Conflict تم اختباره.
* [ ] Failure تم اكتشافه.
* [ ] Failure تم تشخيصه.
* [ ] تم إجراء Fix.
* [ ] تم إجراء Retest.
* [ ] تم توثيق Limitations.
* [ ] تم تحديث NOVA v0.5.
* [ ] يستطيع الطالب الدفاع عن قراراته.

---

# 6. المعيار الحقيقي

لا نقيّم الطالب على:

> "هل صنع Chatbot باستخدام Dify؟"

بل على:

> **هل استطاع تصميم نظام يعرف من أين يأخذ المعرفة، وما الذي يسمح له باستخدامه، ومتى يجيب، ومتى يمتنع، وكيف يثبت أن الإجابة مدعومة؟**

---

# 7. الخلاصة

في U3 تعلم الطالب:

> **AI is a component inside a system.**

في U4 تعلم:

> **A system must be tested and evaluated.**

وفي U5 نضيف:

> **A system must know what evidence it is allowed to rely on.**

وبذلك يصبح التسلسل:

```text id="g6j2v8"
U3
SYSTEM
↓
U4
QUALITY
↓
U5
KNOWLEDGE
```

وهذا يمهد مباشرة إلى U6:

> **إذا أصبح لدينا نظام + جودة + معرفة، فماذا يحدث عندما نضيف AI يستطيع اختيار الأدوات واتخاذ خطوات وتنفيذ أفعال؟**

وهنا ندخل إلى:

# U6 — Controlled AI Operations Agent

## وكيل ذكاء اصطناعي مضبوط للعمليات
