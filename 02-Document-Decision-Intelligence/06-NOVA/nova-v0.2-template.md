# NOVA v0.2 — Data & Evidence

## Purpose

في U1 حددت المشكلة والعملية الحالية.

في U2 ستنتقل إلى السؤال التالي:

> **ما الأدلة والبيانات التي أحتاجها حتى أفهم المشكلة وأدعم القرار؟**

لا تبدأ بالأداة.

لا تبدأ بـAI.

ابدأ بما يحتاجه القرار.

---

# 1. Your Problem

انسخ مشكلة NOVA من:

`U1 → nova-v0.1.md`

### User

من هو المستخدم أو المستفيد؟

```text
User:
```

### Problem

ما المشكلة التي يعاني منها؟

```text
Problem:
```

### Current Process

كيف تتم العملية حاليًا؟

```text
Current Process:
```

### Desired Outcome

ما النتيجة التي تريد الوصول إليها؟

```text
Desired Outcome:
```

---

# 2. Decision to Support

ما القرار الذي تريد أن تساعد صاحب المشكلة على اتخاذه؟

```text
Decision Question:
```

إذا لم يوجد قرار واضح، أعد صياغة المشكلة.

### Example

ضعيف:

> نريد تحليل بيانات العملاء.

أقوى:

> ما الأسباب الأكثر ارتباطًا بتأخر متابعة العملاء، وأين يجب أن نتدخل أولًا؟

---

# 3. Evidence Needed

ما الأدلة التي تحتاجها للإجابة عن سؤال القرار؟

| Evidence Needed | Why Needed | Possible Source |
| --------------- | ---------- | --------------- |
|                 |            |                 |
|                 |            |                 |
|                 |            |                 |

لا تجمع البيانات لمجرد توفرها.

لكل عنصر اسأل:

> **هل أحتاج هذه المعلومة فعلًا للإجابة عن سؤال القرار؟**

---

# 4. Data Sources

حدد المصادر التي يمكن أن توفر الأدلة.

أمثلة:

* Google Sheets
* Forms
* Documents
* Emails
* Database
* CRM
* Surveys
* Existing Reports
* Interviews
* Manual Records

| Source | Data Available | Owner | Reliability | Access |
| ------ | -------------- | ----- | ----------- | ------ |
|        |                |       |             |        |

---

# 5. Data Quality Risks

ما المشكلات المحتملة في البيانات؟

حدد ما ينطبق:

```text
[ ] Missing Data
[ ] Duplicate Records
[ ] Inconsistent Values
[ ] Conflicting Sources
[ ] Outdated Data
[ ] Unclear Definitions
[ ] Incorrect Values
[ ] Biased Data
[ ] Incomplete Records
[ ] Other
```

اشرح أهم خطرين أو ثلاثة:

```text
Risk 1:
Why it matters:

Risk 2:
Why it matters:

Risk 3:
Why it matters:
```

---

# 6. What We Know vs What We Assume

افصل بين:

### Known

ما الذي نعرفه حاليًا من الأدلة؟

```text
Known:
```

### Assumed

ما الذي نفترضه لكنه لم يُثبت بعد؟

```text
Assumed:
```

### Unknown

ما الذي لا نعرفه بعد؟

```text
Unknown:
```

---

# 7. Evidence → Insight

اختر دليلًا واحدًا على الأقل وحاول تحويله إلى Insight.

### Evidence

```text
Evidence:
```

### Possible Insight

```text
Insight:
```

### Confidence

```text
High / Medium / Low
```

### Why?

اشرح لماذا اخترت مستوى الثقة هذا.

---

# 8. Hypotheses to Test

اكتب فرضيات يمكن اختبارها بالبيانات.

```text
Hypothesis 1:

Hypothesis 2:

Hypothesis 3:
```

لكل فرضية:

> ما البيانات التي يمكن أن تؤيدها أو تضعفها؟

---

# 9. Human vs AI vs Rules

في هذه المرحلة لا تبنِ النظام بعد.

فقط حدد أين يمكن أن تساعد الأدوات لاحقًا.

| Activity          | Human | AI | Rules |
| ----------------- | ----- | -- | ----- |
| Data collection   |       |    |       |
| Data extraction   |       |    |       |
| Validation        |       |    |       |
| Calculation       |       |    |       |
| Pattern detection |       |    |       |
| Interpretation    |       |    |       |
| Final decision    |       |    |       |

لا تفترض أن AI هو الخيار الافتراضي.

---

# 10. Data Required Before Building

حدد ما الذي تحتاج إلى جمعه أو الوصول إليه قبل بناء الحل.

```text
Required Data:
```

ثم حدد:

```text
Available Data:
```

و:

```text
Missing Data:
```

---

# 11. Revised Problem Statement

بعد هذا التحليل، أعد صياغة المشكلة:

> نحن نحاول مساعدة **[user]** على **[desired outcome]** من خلال فهم **[evidence/data]** لأن **[problem]**، مع وجود المخاطر التالية: **[data risks]**.

```text
Revised Problem Statement:
```

---

# 12. NOVA v0.2 Gate

لا تنتقل إلى U3 قبل أن تستطيع الإجابة بوضوح:

### Problem

> هل المشكلة واضحة؟

### Decision

> ما القرار الذي نحاول دعمه؟

### Evidence

> ما الأدلة المطلوبة؟

### Sources

> من أين سنحصل عليها؟

### Quality

> هل نثق بالبيانات؟ ولماذا؟

### Unknowns

> ماذا لا نعرف بعد؟

### AI Boundary

> أين يمكن أن يساعد AI، وأين لا نحتاجه؟

---

# Definition of Done

يُعتبر NOVA v0.2 مكتملًا عندما يكون لدى الطالب:

* Decision Question واضح.
* Evidence Map.
* Data Sources.
* Data Quality Risks.
* Known / Assumed / Unknown.
* Initial Insights.
* Testable Hypotheses.
* Human / AI / Rules boundaries.
* Missing Data list.
* Revised Problem Statement.

---

# Core Principle

> **Do not ask "What data do I have?" first. Ask "What evidence do I need to support the decision?"**
