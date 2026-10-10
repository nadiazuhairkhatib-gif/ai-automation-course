# 🤖 AI Client Intake & Request Routing System

## U1 — Process & Data Thinking

مشروع عملي لتحويل ما تعلمناه في **U1 — Process & Data Thinking** إلى **AI Automation** حقيقية.

سنستخدم:

- **Google Forms**
- **Zapier**
- **AI by Zapier**
- **Google Sheets**
- **Email**

---

# 🎯 هدف المشروع

في هذا المشروع لن يكون هدفنا فقط أن نبني **Zap يعمل**.

هدفنا أن نمر بالرحلة الهندسية الكاملة:

> **Understand → Design → Build → Test → Refine**

وسنطبق الـMental Model التالي:

> **AI → Understand**  
> **Rule / Logic → Control**  
> **Human → Judge**

أي:

- **AI** يفهم الطلب ويستخرج المعلومات.
- **Automation / Logic** تتحكم في مسار العملية.
- **Human** يتدخل عندما تكون المعلومات ناقصة أو غامضة.

وهذا هو الفرق بين:

> **Using AI**

و

> **Engineering with AI**

---

# 01 — الصورة الكاملة

قبل أن نبدأ ببناء الـAutomation، يجب أن نفهم الـWorkflow الذي سنبنيه.

```text
Client
   ↓
Google Form
   ↓
Trigger
   ↓
Unstructured Request
   ↓
AI by Zapier
   ↓
Structured Output
   ↓
Request Status
   ↓
        ┌─────────────────┐
        │                 │
      VALID          NEEDS_REVIEW
        │                 │
        ↓                 ↓
    Web Team            Human
        │                 │
        └────────┬────────┘
                 ↓
          Google Sheets
                 ↓
              Email
```

## لماذا هذا هو التصميم؟

لأننا لا نريد أن نجعل AI يقوم بكل شيء.

نريد توزيع المسؤوليات بوضوح:

```text
AI
↓
Understand

Automation
↓
Control

Human
↓
Judge
```

---

# 02 — إنشاء Google Form

أنشئ Google Form باسم:

**Client Intake Form**

أضف الحقول التالية:

| Field | Type |
|---|---|
| Client Name | Short answer |
| Email | Email |
| Company | Short answer |
| Request | Paragraph |

## لماذا نحتاج الـForm؟

لأننا نحتاج إلى **مصدر حقيقي للبيانات**.

الـForm يمثل نقطة دخول العميل إلى النظام.

وهنا نطبق مفهوم:

> **Input**

أما `Request` فهو:

> **Unstructured Data**

لأن العميل يستطيع كتابة طلبه بحرية.

مثال:

```text
We need a website for our company.
Our budget is $5000.
We need it next month.
```

---

# 03 — إنشاء Zap

في Zapier:

**Create → New Zap**

سمِّ الـZap:

```text
AI Client Intake & Request Routing
```

---

# 04 — Trigger

اختر:

**Google Forms**

ثم:

**New Form Response**

أو الاسم المطابق الذي يظهر في واجهة Zapier.

اربط Google Account والـForm.

ثم نفّذ:

**Test Trigger**

يجب أن تظهر بيانات مثل:

```text
Client Name
Email
Company
Request
```

## Trigger vs Input

من المهم جدًا التمييز بينهما.

### Trigger

هو **الحدث الذي يبدأ الـAutomation**.

في مشروعنا:

```text
New Client Form Submission
```

### Input

هي **البيانات التي وصلت مع الحدث**.

مثل:

```text
Client Name
Email
Company
Request
```

إذن:

> **Trigger ≠ Input**

---

# 05 — AI by Zapier

أضف Action:

**AI by Zapier**

## Data In

أنشئ Input باسم:

```text
request_text
```

واجعل قيمته:

**Request** من Google Forms.

## لماذا؟

لأننا نريد إعطاء AI النص غير المنظم الذي كتبه العميل.

لا نحتاج الآن إلى إرسال كل بيانات العميل إلى AI.

نحن نحدد له بالضبط:

> **ما المهمة التي يحتاج إلى تنفيذها؟**

---

# 06 — AI Task

استخدم الـPrompt التالي:

```text
Analyze the client request and extract structured information.

Use ONLY information explicitly provided by the client. Never invent, assume, infer, estimate, or guess.

### Required information
- service_type
- timeline
- budget

### Extraction rules

**service_type**
- Extract the explicitly requested service.
- Example: "We need a website" → `website`
- If not explicitly provided, return `null`.

**timeline**
- Extract a specific timeframe exactly as stated.
- Examples:
  - "next month" → `next month`
  - "in 3 weeks" → `in 3 weeks`
  - "by December" → `by December`
- These are valid.
- Vague expressions such as "soon", "as soon as possible", "quickly", "urgently", or "in the near future" → `null`.
- Never convert a vague timeframe into a specific timeframe.

**budget**
- Extract the budget only when explicitly provided.
- Example: "$5000" → `$5000`
- If not provided, return `null`.
- Never estimate or guess.

**request_summary**
- Summarize only what the client explicitly requested.
- Do not add assumptions.

**missing_information**
- List required fields that are missing or ambiguous.
- Allowed values: `service_type`, `timeline`, `budget`
- Separate multiple values with commas.
- If nothing is missing, return exactly `NONE`.

### Decision rules

**request_status**
- `VALID` only if service_type, timeline, and budget are all explicitly provided and valid.
- Otherwise return `NEEDS_REVIEW`.
- Return only `VALID` or `NEEDS_REVIEW`.

**routing**
- Determine routing only from request_status:
  - `VALID` → `web_team`
  - `NEEDS_REVIEW` → `human_review`
- Never return null or any other routing value.

### Output

Return these fields separately:

- service_type
- timeline
- budget
- request_summary
- missing_information
- request_status
- routing
```

---

# 07 — AI Output

أنشئ Outputs التالية:

| Output | Type |
|---|---|
| `service_type` | Text |
| `request_summary` | Text |
| `timeline` | Text |
| `budget` | Text |
| `missing_information` | Text |
| `request_status` | Text |

وهنا يحدث التحول الأساسي:

```text
Unstructured Data
        ↓
       AI
        ↓
Structured Data
```

مثال:

### Before

```text
We need a website for our company.
Our budget is $5000.
We need it next month.
```

### After

```text
service_type = website
timeline = next month
budget = $5000
```

وهذا أحد أهم أهداف U1:

> **تحويل المعلومات غير المنظمة إلى بيانات يمكن للنظام التعامل معها.**

---

# 08 — اختبار AI قبل بناء الـPaths

⚠️ **لا نبني الـPaths قبل التأكد من أن AI يعطي النتيجة الصحيحة.**

استخدم Test Request:

```text
We need a website for our company. Our budget is $5000. We need it next month.
```

يجب أن تكون النتيجة:

```text
service_type = website

request_summary = Website for the company

timeline = next month

budget = $5000

missing_information = NONE

request_status = VALID
```

إذا حصلنا على النتيجة الصحيحة:

> **AI PASS ✅**

إذا لم نحصل عليها:

> **Stop → Debug AI**

ولا ننتقل إلى الـPaths.

لأن:

> **Garbage In → Garbage Out**

إذا كان الـAI ينتج Structured Output خاطئًا، فلن تستطيع الـAutomation اتخاذ قرار صحيح.

---

# 09 — Paths by Zapier

بعد التأكد من أن AI يعمل، أضف:

**Paths by Zapier**

سننشئ مسارين:

```text
VALID
   ↓
Valid Request

NEEDS_REVIEW
   ↓
Needs Human Review
```

---

# 10 — Path A: Valid Request

سمِّ المسار:

**Valid Request**

الشرط:

```text
request_status
Exactly matches
VALID
```

## لماذا؟

نريد Signal واضحًا جدًا:

```text
VALID
```

إذا كان:

```text
request_status = VALID
```

فإن الطلب ينتقل إلى:

> **Valid Request**

وهذا هو الـNormal Path.

---

# 11 — Path B: Needs Human Review

سمِّ المسار:

**Needs Human Review**

واجعله:

> **Fallback**

أي أن أي طلب لا يحقق شرط `VALID` ينتقل إلى Human Review.

```text
VALID
   ↓
Normal Path

Anything else
   ↓
Human Review
```

## لماذا؟

لأننا لا نريد أن تتوقف الـException.

نريد أن:

> **Route the exception.**

وهنا نطبق:

> **Exception Handling**

---

# 12 — إنشاء Google Sheet

أنشئ Google Sheet باسم:

**AI Client Intake Records**

الأعمدة:

```text
client_name
email
company
request_text
service_type
request_summary
timeline
budget
missing_information
request_status
requires_human
routing
processed_at
```

## لماذا؟

نحتاج إلى حفظ نتيجة الـAutomation كـ**Record**.

هذا يساعدنا في:

- Tracking
- Review
- Testing
- Debugging
- Human Review

---

# 13 — Valid Request → Google Sheets

داخل:

**Valid Request**

أضف:

**Google Sheets → Create Spreadsheet Row**

اربط البيانات:

```text
client_name
← Google Form → Client Name

email
← Google Form → Email

company
← Google Form → Company

request_text
← Google Form → Request

service_type
← AI → service_type

request_summary
← AI → request_summary

timeline
← AI → timeline

budget
← AI → budget

missing_information
← AI → missing_information

request_status
← AI → request_status
```

القيم الثابتة:

```text
requires_human = false
routing = web_team
```

لأن هذا هو:

> **Normal Path**

والطلب لا يحتاج إلى Human Review.

---

# 14 — Needs Human Review → Google Sheets

داخل:

**Needs Human Review**

أضف:

**Google Sheets → Create Spreadsheet Row**

استخدم نفس الـMapping السابق.

لكن غيّر:

```text
requires_human = true
routing = human_review
```

## لماذا؟

لأن النظام اكتشف أن الطلب لا يستطيع المرور بأمان في المسار الطبيعي.

وهنا نطبق:

> **Human-in-the-Loop**

---

# 15 — Valid Path → Email

داخل:

**Valid Request**

أضف:

**Send Email**

### Subject

```text
New Valid Client Request
```

### Body

```text
A new valid client request has been received.

Client: {{client_name}}
Company: {{company}}
Service: {{service_type}}
Timeline: {{timeline}}
Budget: {{budget}}

Request:
{{request_text}}
```

## الهدف

لا نريد فقط تسجيل البيانات.

نريد أيضًا:

> **Notify the responsible team.**

---

# 16 — Human Review Path → Email

داخل:

**Needs Human Review**

أضف:

**Send Email**

### Subject

```text
Client Request Requires Human Review
```

### Body

```text
A client request requires human review.

Client: {{client_name}}
Company: {{company}}

Missing Information:
{{missing_information}}

Original Request:
{{request_text}}

Please review the request before proceeding.
```

## لماذا؟

لأن الـException يجب ألا تختفي.

إذا لم نستطع إكمال الطلب بأمان:

> **Escalate to Human.**

---

# 17 — الاختبارات

لن نعتبر المشروع مكتملًا بمجرد أن يعمل الـZap مرة واحدة.

سنختبر عدة حالات.

---

## 🧪 TEST 01 — Complete Request

### Input

```text
We need a website for our company.
Our budget is $5000.
We need it next month.
```

### Expected AI Output

```text
service_type = website
timeline = next month
budget = $5000
missing_information = NONE
request_status = VALID
```

### Expected Path

```text
Valid Request
```

### Expected Sheet

```text
request_status = VALID
requires_human = false
routing = web_team
```

### Expected Email

```text
New Valid Client Request
```

### Result

**PASS ✅**

---

## 🧪 TEST 02 — Missing Budget

### Input

```text
We need a website for our company.
We need it next month.
```

### Expected AI Output

```text
service_type = website
timeline = next month
budget = null
missing_information = budget
request_status = NEEDS_REVIEW
```

### Expected Path

```text
Needs Human Review
```

### Expected Sheet

```text
request_status = NEEDS_REVIEW
requires_human = true
routing = human_review
```

### Expected Email

```text
Client Request Requires Human Review
```

### Result

**PASS ✅**

---

## 🧪 TEST 03 — Ambiguous Timeline

### Input

```text
We need a website soon.
Our budget is $5000.
```

### Expected AI Output

```text
service_type = website
timeline = null
budget = $5000
missing_information = timeline
request_status = NEEDS_REVIEW
```

### Expected Path

```text
Needs Human Review
```

### Result

**PASS ✅**

---

## 🧪 TEST 04 — Multiple Missing Fields

### Input

```text
We need a website for our company.
```

### Expected AI Output

```text
service_type = website
timeline = null
budget = null
missing_information = timeline, budget
request_status = NEEDS_REVIEW
```

### Expected Path

```text
Needs Human Review
```

### Result

**PASS ✅**

---

# 18 — Test Matrix

| Test | Scenario | Expected Status | Expected Path |
|---|---|---|---|
| 01 | Complete request | `VALID` | Valid Request |
| 02 | Missing budget | `NEEDS_REVIEW` | Human Review |
| 03 | Ambiguous timeline | `NEEDS_REVIEW` | Human Review |
| 04 | Multiple missing fields | `NEEDS_REVIEW` | Human Review |

يجب أن تكون النتيجة:

```text
TEST 01 → PASS ✅
TEST 02 → PASS ✅
TEST 03 → PASS ✅
TEST 04 → PASS ✅
```

---

# 19 — كيف نختبر الـAutomation؟

لا نعيد بناء الـZap لكل Test.

نغيّر فقط الـInput.

في كل Test:

1. افتح Google Form.
2. أدخل Test Case.
3. اضغط Submit.
4. راقب الـTrigger.
5. راقب AI Output.
6. راقب `request_status`.
7. راقب الـPath.
8. راقب Google Sheets.
9. راقب Email.
10. قارن النتيجة.

نريد دائمًا:

```text
Expected
    VS
Actual
```

إذا تطابقا:

> **PASS ✅**

إذا لم يتطابقا:

> **FAIL ❌ → Debug**

---

# 20 — Debugging by Layer

إذا حدث Failure، لا نغيّر كل شيء عشوائيًا.

نبحث عن **أول نقطة فشل**.

```text
Trigger
   ↓
Input
   ↓
AI
   ↓
Structured Output
   ↓
Request Status
   ↓
Path
   ↓
Google Sheets
   ↓
Email
```

ثم نسأل:

> **أين كانت أول نتيجة غير صحيحة؟**

### مثال 1

AI أعطى:

```text
request_status = VALID
```

لكن الـPath لم يعمل.

إذن المشكلة غالبًا في:

> **Path Logic**

---

### مثال 2

AI أعطى:

```text
timeline = next month
```

لكن:

```text
request_status = NEEDS_REVIEW
```

إذن نراجع:

> **AI Task / Prompt**

---

### مثال 3

الـPath صحيح، لكن Google Sheet يحتوي بيانات خاطئة.

إذن نراجع:

> **Data Mapping**

---

### مثال 4

الـSheet صحيح، لكن Email لم يصل.

إذن نراجع:

> **Email Action**

وهكذا نتعلم:

> **Debugging by Layer**

---

# 21 — Exception vs Error

من المهم أن نفرّق بين الاثنين.

## Exception

الطلب نفسه يحتاج إلى معالجة مختلفة.

مثال:

```text
budget is missing
```

هذا ليس System Error.

إنه:

> **Business Exception**

ولذلك نرسله إلى:

> **Human Review**

---

## Error

النظام نفسه لم يعمل كما يجب.

مثل:

```text
AI Action failed
Google Sheets failed
Email failed
```

هذا:

> **Technical Error**

ويحتاج إلى:

> **Debugging**

---

# 22 — لماذا لم نجعل AI يقوم بكل شيء؟

لأن هدفنا ليس جعل AI يدير العملية كاملة.

نحن نوزع المسؤوليات:

```text
AI
↓
Understand

Automation / Logic
↓
Control

Human
↓
Judge
```

AI مناسب لفهم النص غير المنظم واستخراج المعلومات.

لكن القرار التشغيلي يجب أن يكون واضحًا وقابلًا للاختبار.

والحالات غير الواضحة يجب ألا يتم تمريرها تلقائيًا بدون مراجعة.

---

# 23 — لماذا نستخدم `request_status`؟

نحتاج إلى Signal واضح تستطيع الـAutomation التعامل معه.

بدلًا من أن يحاول الـPath تفسير:

```text
budget = null
timeline = null
missing_information = timeline, budget
```

نعطيه قيمة واضحة:

```text
request_status = VALID
```

أو:

```text
request_status = NEEDS_REVIEW
```

وهذا يجعل الـDecision Logic:

- أبسط
- أوضح
- أسهل في الاختبار
- أسهل في الـDebugging

---

# 24 — لماذا لم نستخدم Filter by Zapier؟

لا نحتاج إلى Filter في هذه النسخة.

نحن لا نريد إيقاف الطلبات التي تحتوي على مشكلة.

نريد توجيهها إلى المسار المناسب.

```text
VALID
   ↓
Valid Request

Anything else
   ↓
Human Review
```

الهدف ليس:

> **Stop the exception.**

بل:

> **Route the exception.**

---

# 25 — ما الذي تعلمناه من المشروع؟

بعد إكمال المشروع، يجب أن تستطيع شرح:

| Concept | تطبيقه في المشروع |
|---|---|
| Work | التعامل مع طلبات العملاء |
| Process | طريقة معالجة الطلب من البداية للنهاية |
| Trigger | New Form Response |
| Input | بيانات الـGoogle Form |
| Unstructured Data | Client Request |
| AI Task | فهم الطلب واستخراج المعلومات |
| Structured Output | الحقول المنظمة الناتجة من AI |
| Missing Information | البيانات المطلوبة غير الموجودة أو الغامضة |
| Decision | تحديد المسار المناسب |
| Rule / Logic | تحديد `VALID` أو `NEEDS_REVIEW` |
| Exception | طلب لا يمكن إكماله بأمان |
| Human-in-the-Loop | مراجعة الإنسان للطلبات غير المكتملة |
| Automation | تنفيذ الخطوات تلقائيًا |
| Record | Google Sheets |
| Notification | Email |
| Testing | مقارنة Expected vs Actual |
| Debugging | تحديد أول Layer فشل |

---

# 26 — Definition of Done

يعتبر المشروع مكتملًا عندما:

- [ ] Google Form يعمل.
- [ ] Trigger يستقبل الطلب.
- [ ] AI يفهم الطلب.
- [ ] Structured Output صحيح.
- [ ] `request_status` صحيح.
- [ ] Valid Path يعمل.
- [ ] Needs Human Review Path يعمل.
- [ ] البيانات تُسجل في Google Sheets.
- [ ] Valid Email يُرسل.
- [ ] Human Review Email يُرسل.
- [ ] Test 01 = PASS.
- [ ] Test 02 = PASS.
- [ ] Test 03 = PASS.
- [ ] Test 04 = PASS.
- [ ] تستطيع شرح سبب وجود كل خطوة.

---

# 🧠 الفكرة الأساسية

لا نريد أن تنهي المشروع وأنت تقول:

> "تعلمت كيف أبني Zap في Zapier."

نريد أن تكون قادرًا على القول:

> **"تعلمت كيف أفهم الـWork، أحلل الـInput، أحدد ما يحتاج AI وما يحتاج Logic وما يحتاج Human، أصمم الـWorkflow، أبنيه، أختبره، وأعمل له Debugging."**

لأن:

> **Tools implement the design.  
> Tools do not replace the design.**

والرحلة الهندسية الكاملة هي:

```text
UNDERSTAND
     ↓
DESIGN
     ↓
BUILD
     ↓
TEST
     ↓
REFINE
```

## 🚀 This is the real goal of U1.

**Think First. Build Later.**
