# U1 — نظام استقبال طلبات العملاء وتحليلها وتوجيهها بالذكاء الاصطناعي

## AI Client Intake & Request Routing System

نظام أتمتة عملي يحوّل طلبات العملاء غير المنظمة إلى **Structured Data** قابلة للمعالجة، ثم يتحقق من البيانات، يكتشف المعلومات الناقصة أو الغامضة، ويحدد الإجراء المناسب باستخدام **AI + Rules + Human-in-the-Loop**.

المشروع مصمم خصيصًا لتطبيق مفاهيم:

> **U1 — Process & Data Thinking**

والهدف منه ليس تعلم **Zapier** بحد ذاته، بل تطبيق طريقة التفكير التي تسبق بناء أي **AI Automation Solution**.

---

# 1. فكرة المشروع

تخيل شركة خدمات تستقبل طلبات العملاء عبر البريد الإلكتروني أو نموذج إلكتروني.

قد يصل الطلب بهذه الصورة:

> "مرحبًا، نريد موقعًا لشركتنا الجديدة، ونفضل أن يكون جاهزًا الشهر القادم، لكننا لم نحدد الميزانية بعد."

بالنسبة للإنسان، الرسالة مفهومة.

لكن بالنسبة للنظام، البيانات ما زالت **Unstructured**.

يحتاج النظام إلى فهم الطلب وتحويله إلى بيانات يمكن استخدامها:

```text
Unstructured Request
        ↓
AI Understanding
        ↓
Structured Data
        ↓
Validation
        ↓
Decision
        ↓
Routing
        ↓
Action / Human Review
```

لذلك لا نبني مجرد AI يقوم بـ **Summarization** للرسالة.

نحن نبني **Vertical Slice** من عملية عمل حقيقية:

> **من لحظة وصول طلب العميل حتى تحديد ما يجب أن يحدث معه.**

---

# 2. Business Scenario

الشركة تستقبل عددًا متزايدًا من طلبات العملاء.

في الوضع الحالي:

```text
Client
   ↓
Request
   ↓
Employee reads it
   ↓
Understands the request
   ↓
Extracts information
   ↓
Checks missing information
   ↓
Decides what to do
   ↓
Records the request
   ↓
Routes it to the right person
```

ومع زيادة عدد الطلبات تظهر **Pain Points** مثل:

* العمل اليدوي المتكرر.
* اختلاف طريقة معالجة الطلبات.
* نسيان بعض المعلومات.
* صعوبة التعامل مع الرسائل غير المنظمة.
* تأخر توجيه الطلبات.
* الاعتماد على افتراضات عند نقص المعلومات.
* عدم وجود طريقة موحدة لتحديد الحالات التي تحتاج إلى إنسان.

---

# 3. المشكلة التي سنحلها

المشكلة ليست:

> "نريد استخدام AI."

بل:

> **كيف يمكننا تحويل طلب العميل غير المنظم إلى طلب مفهوم ومنظم، والتحقق من أنه يحتوي على المعلومات الكافية، ثم توجيهه إلى المسار المناسب دون اتخاذ قرارات غير آمنة؟**

وهنا يبدأ التفكير الهندسي.

---

# 4. Desired Outcome

نريد الوصول إلى عملية يستطيع فيها النظام:

```text
Receive Request
      ↓
Understand Request
      ↓
Extract Information
      ↓
Structure Data
      ↓
Validate Data
      ↓
Detect Missing / Ambiguous Information
      ↓
Decide Next Step
      ↓
Route Request
      ↓
Record Result
      ↓
Notify / Escalate
```

الهدف ليس إزالة الإنسان بالكامل.

الهدف هو:

> **Automate what is safe to automate, and involve humans where judgment is required.**

---

# 5. المشروع والـ7 Layers

هذا المشروع يطبق **7-Layer Mental Model** للوحدة.

---

## Layer 01 — Understand the Work

نبدأ بفهم العمل قبل التفكير في الأداة.

```text
Work
 ↓
Problem
 ↓
Pain Point
 ↓
Current State
 ↓
Desired Outcome
 ↓
Success Criteria
```

في المشروع سنحدد:

* ما هو **Work**؟
* ما هي المشكلة؟
* أين توجد **Pain Points**؟
* كيف تتم العملية حاليًا؟
* ما النتيجة المطلوبة؟
* كيف سنعرف أن الحل نجح؟

### Core Question

> **What work are we improving, and what does success look like?**

---

# Layer 02 — Decompose the Work

بعد فهم العمل، نقسمه إلى أجزاء يمكن تحليلها وأتمتتها.

```text
Process
 ↓
Workflow
 ↓
Task
 ↓
Subtask
 ↓
Sequence
 ↓
Dependency
```

سنحدد:

* ما هو الـ **Process**؟
* ما هو الـ **Workflow** الذي سنبنيه؟
* ما هي الـ **Tasks**؟
* ما هي الـ **Subtasks**؟
* ما ترتيب الخطوات؟
* ما الـ **Dependencies** بينها؟

مثال:

```text
Receive Request
      ↓
Understand Request
      ↓
Extract Information
      ↓
Validate Information
      ↓
Decide
      ↓
Route
```

### Core Question

> **How can we break this work into clear, manageable steps?**

---

# Layer 03 — Understand the Input & Data

هنا ننتقل من العمل إلى البيانات التي يحتاجها النظام.

```text
Trigger
 ↓
Input
 ↓
Unstructured Data
 ↓
Structured Data
 ↓
Missing Information
 ↓
Validation
```

سنحدد:

### Trigger

ما الحدث الذي يبدأ الـWorkflow؟

مثل:

* New Form Submission
* New Email
* New Request

### Input

ما البيانات التي تدخل إلى النظام؟

### Unstructured Data

مثل:

> "نريد موقعًا للشركة ونحتاجه الشهر القادم."

### Structured Data

نريد تحويلها إلى شيء مثل:

```json
{
  "service_type": "website",
  "timeline": "next_month",
  "budget": null
}
```

### Missing Information

مثلاً:

```text
budget = null
```

لا يعني أن النظام يجب أن يخمن الميزانية.

بل يجب أن يعرف أن:

> **Information is missing.**

### Validation

نتحقق:

* هل البيانات موجودة؟
* هل هي صحيحة؟
* هل هي كافية؟
* هل يمكن الانتقال إلى الخطوة التالية؟

### Core Question

> **What data enters the system, and is it sufficient for the next step?**

---

# Layer 04 — Design the Decision

هنا نقرر:

> أين نستخدم AI؟ وأين نستخدم Rule؟

المبدأ:

```text
AI
 ↓
Understand / Extract / Classify
 ↓
Structured Output
 ↓
Rule
 ↓
Decision
```

### AI

نستخدم AI للمهام التي تحتاج فهم اللغة الطبيعية، مثل:

* Classification
* Information Extraction
* Summarization
* Detecting ambiguity
* Understanding the request

### Rule

نستخدم **Deterministic Logic** عندما يكون الشرط واضحًا.

مثال:

```text
IF required_information is missing
→ Needs Review
```

### AI Task

لن نجعل AI مسؤولًا عن النظام كله.

بل نعطيه **Bounded Task** واضحًا:

> "Analyze the client request and return the required fields according to the defined schema."

### Structured Output

يجب أن يكون ناتج AI منظمًا وقابلًا للاستخدام من الـWorkflow.

مثلاً:

```json
{
  "request_type": "website",
  "service_needed": "website development",
  "timeline": "next month",
  "budget": null,
  "missing_information": [
    "budget"
  ],
  "requires_human": true
}
```

### Core Question

> **What should AI understand, and what should deterministic logic decide?**

---

# Layer 05 — Handle Exceptions Safely

ليس كل Request يمكن أن يسير في المسار الطبيعي.

قد يكون:

* Missing Information
* Ambiguous Information
* Conflicting Information
* Low Confidence
* Sensitive Request
* Case requiring human judgment

لذلك نضيف:

```text
Exception
   ↓
Human-in-the-Loop
   ↓
Safe Automation
```

مثلاً:

```text
Valid Request
     ↓
Continue Automation
```

بينما:

```text
Missing / Ambiguous / Unclear
     ↓
Human Review
```

المبدأ:

> **The system should know when not to act alone.**

### Core Question

> **When should automation stop and a human take over?**

---

# Layer 06 — Design the Automation

بعد فهم العمل والبيانات والقرارات والاستثناءات، نصمم الـAutomation.

التصميم قد يكون:

```text
Trigger
   ↓
Receive Input
   ↓
AI Analysis
   ↓
Structured Output
   ↓
Validation
   ↓
Decision
   ↓
 ┌───────────────┐
 │               │
Valid          Exception
 │               │
 ↓               ↓
Route        Human Review
 │
 ↓
Record
 │
 ↓
Notify
```

هنا لا نستخدم Zapier بعد.

نحن نحدد:

> **What should happen?**

### Core Question

> **What should the automation do from Trigger to Outcome?**

---

# Layer 07 — Implement the Design

الآن فقط ننتقل إلى الأداة.

سنستخدم:

## Zapier

لتحويل التصميم السابق إلى Workflow فعلي.

قد نستخدم:

* Google Forms
* Gmail
* Google Sheets أو Zapier Tables
* AI by Zapier أو AI Model
* Filters
* Paths
* Formatter
* Gmail / Slack للإشعارات

هنا السؤال يتغير من:

> What should happen?

إلى:

> **How do we build what we designed?**

المبدأ الأساسي:

> **Tools implement the design. Tools do not replace the design.**

---

# 6. النظام النهائي

النظام الذي سنبنيه يمثل:

```text
                 Client Request
                       │
                       ▼
                    Trigger
                       │
                       ▼
                 Input / Data
                       │
                       ▼
                AI Understanding
                       │
                       ▼
                Structured Output
                       │
                       ▼
                   Validation
                       │
                ┌──────┴──────┐
                │             │
             Valid        Exception
                │             │
                ▼             ▼
             Routing      Human Review
                │
                ▼
              Record
                │
                ▼
           Notification
```

وهذا يمثل تطبيقًا عمليًا للـMental Model كاملًا.

---

# 7. AI vs Rule vs Human

لن نضع AI في كل خطوة.

سنستخدم أبسط آلية موثوقة لكل مهمة.

| الحاجة                        | الآلية |
| ----------------------------- | ------ |
| فهم رسالة العميل              | AI     |
| استخراج المعلومات             | AI     |
| تصنيف نوع الطلب               | AI     |
| التحقق من وجود حقل            | Rule   |
| التحقق من شرط واضح            | Rule   |
| تحديد مسار بناءً على شرط ثابت | Rule   |
| حالة غامضة                    | Human  |
| قرار يحتاج حكمًا بشريًا       | Human  |

المبدأ:

> **Use the simplest reliable mechanism that solves the task.**

---

# 8. Data Flow

أحد أهم أهداف المشروع هو رؤية رحلة البيانات:

```text
Unstructured Input
        ↓
AI Processing
        ↓
Structured Data
        ↓
Validation
        ↓
Decision
        ↓
Action
```

مثال:

### Input

> "نريد موقعًا لشركتنا الجديدة، ونحتاجه الشهر القادم، لكننا لم نحدد الميزانية بعد."

### Structured Output

```json
{
  "service_type": "website",
  "timeline": "next month",
  "budget": null,
  "missing_information": [
    "budget"
  ],
  "requires_human": true
}
```

لاحظ:

**لا يوجد تخمين.**

إذا لم يقدم العميل معلومة:

```text
Unknown → null
```

وليس:

```text
Unknown → invented value
```

المبدأ:

> **Unknown is better than invented.**

---

# 9. Validation

لن نثق بمخرجات AI لمجرد أنها تبدو صحيحة.

سنضع **Validation** قبل تنفيذ الإجراءات المهمة.

مثلاً:

```text
AI Output
   ↓
Are required fields present?
   ↓
Is the data valid?
   ↓
Is there ambiguity?
   ↓
Is human review required?
```

إذا كانت الإجابة غير مناسبة:

```text
→ Exception
→ Human Review
```

أما إذا كانت البيانات سليمة:

```text
→ Continue Workflow
```

---

# 10. Safe Automation

المشروع لا يهدف إلى:

> Automate Everything

بل إلى:

> **Automate Safely.**

لذلك:

```text
Safe + Clear + Deterministic
        ↓
Automation
```

بينما:

```text
Missing
Ambiguous
Sensitive
Low Confidence
Requires Judgment
        ↓
Human-in-the-Loop
```

وهذه نقطة أساسية في تصميم **AI Automation Solutions**.

---

# 11. Success Criteria

يعتبر النظام ناجحًا عندما:

### SC1 — Correct Extraction

يستخرج المعلومات الموجودة فعلًا في طلب العميل.

### SC2 — No Fabrication

لا يخترع معلومات غير موجودة.

### SC3 — Structured Output

يخرج AI البيانات وفق Schema محدد.

### SC4 — Missing Information Detection

يكتشف المعلومات المطلوبة التي لم يقدمها العميل.

### SC5 — Validation

لا يسمح للبيانات غير الصالحة بالانتقال مباشرة إلى إجراء مهم.

### SC6 — Correct Routing

يتم توجيه الطلب إلى المسار المناسب.

### SC7 — Human Escalation

الحالات التي تحتاج حكمًا بشريًا تصل إلى الإنسان.

### SC8 — Explainable Workflow

يمكننا فهم:

> لماذا ذهب هذا الطلب إلى هذا المسار؟

### SC9 — Testable System

يمكن اختبار النظام باستخدام حالات مختلفة وليس حالة واحدة فقط.

---

# 12. Testing Mindset

المشروع لا ينتهي عندما يظهر:

> **Zap is successful**

الـAutomation قد يعمل تقنيًا لكنه يكون خاطئًا منطقيًا.

لذلك سنستخدم:

```text
Build
 ↓
Test
 ↓
Break
 ↓
Diagnose
 ↓
Fix
 ↓
Retest
```

وسنختبر حالات مثل:

### Case 01 — Complete Request

كل المعلومات موجودة.

### Case 02 — Missing Information

معلومة أساسية غير موجودة.

### Case 03 — Ambiguous Information

المعلومة موجودة لكنها غير واضحة.

### Case 04 — Unexpected Request

الطلب لا ينتمي للمسارات المتوقعة.

### Case 05 — AI Incorrect Output

مخرجات AI لا تطابق الـSchema أو تحتوي على بيانات غير مناسبة.

الهدف ليس فقط اكتشاف أن النظام فشل.

بل السؤال:

> **Why did it fail?**

ثم:

> **Where should we fix it?**

---

# 13. حدود المشروع

حتى يبقى المشروع مناسبًا لـU1، لن نبني:

* CRM كامل.
* Customer Portal.
* Dashboard.
* AI Agent.
* RAG.
* Multi-Agent System.
* Backend مخصص.
* Custom Database.
* API Development متقدم.
* نظام Lead Scoring معقد.

نحن نبني:

> **One complete, testable Vertical Slice.**

---

# 14. الأدوات

الأداة الأساسية:

**Zapier**

ويمكن أن نستخدم معها:

* Google Forms
* Gmail
* Google Sheets أو Zapier Tables
* AI by Zapier / AI Model
* Filters
* Paths
* Formatter
* Gmail / Slack

أما:

* JSON
* APIs
* Data Mapping
* Structured Data

فسنتعامل معها كمفاهيم مهمة لفهم كيفية انتقال البيانات داخل الأنظمة، وليس كموضوع برمجي مستقل.

---

# 15. ملفات المشروع

سيتم تنظيم المشروع إلى ملفات، بحيث يكون لكل جزء من عملية البناء مكان واضح:

```text
AI-Client-Intake/
│
├── README.md
│
├── 01-business-analysis.md
├── 02-workflow-decomposition.md
├── 03-data-design.md
├── 04-decision-and-exception-design.md
├── 05-automation-design.md
├── 06-zapier-implementation.md
└── 07-testing-debugging.md
```

### 01 — Business Analysis

تطبيق **Layer 01**:

```text
Work
Problem
Pain Point
Current State
Desired Outcome
Success Criteria
```

### 02 — Workflow Decomposition

تطبيق **Layer 02**:

```text
Process
Workflow
Task
Subtask
Sequence
Dependency
```

### 03 — Data Design

تطبيق **Layer 03**:

```text
Trigger
Input
Unstructured Data
Structured Data
Missing Information
Validation
```

### 04 — Decision & Exception Design

تطبيق:

```text
Layer 04
AI vs Rule
Deterministic Logic
AI Task
Structured Output

+

Layer 05
Exception
Human-in-the-Loop
Safe Automation
```

### 05 — Automation Design

تطبيق **Layer 06**:

> تصميم الـAutomation قبل فتح الأداة.

يحدد:

```text
Trigger
→ Input
→ Processing
→ Decision
→ Validation
→ Action
→ Exception Handling
→ Outcome
```

### 06 — Zapier Implementation

تطبيق **Layer 07**:

> تحويل التصميم إلى Workflow فعلي باستخدام Zapier.

### 07 — Testing & Debugging

تطبيق دورة:

```text
Build
→ Test
→ Break
→ Diagnose
→ Fix
→ Retest
```

---

# 16. العلاقة بين ملفات المشروع والـ7 Layers

```text
01 Business Analysis
        ↓
Layer 01
Understand the Work
        ↓
02 Workflow Decomposition
        ↓
Layer 02
Decompose the Work
        ↓
03 Data Design
        ↓
Layer 03
Understand Input & Data
        ↓
04 Decision & Exception Design
        ↓
Layer 04 + Layer 05
Design the Decision
Handle Exceptions Safely
        ↓
05 Automation Design
        ↓
Layer 06
Design the Automation
        ↓
06 Zapier Implementation
        ↓
Layer 07
Implement the Design
        ↓
07 Testing & Debugging
        ↓
Test → Diagnose → Refine
```

وهكذا يصبح المشروع **ترجمة عملية مباشرة للوحدة**، وليس مشروعًا منفصلًا عنها.

---

# 17. النتيجة التعليمية

بعد إنهاء المشروع، لا نريد أن تكون إجابة المتدرب:

> "تعلمت كيف أعمل Zap في Zapier."

بل:

> **"أستطيع أن أفهم عملية عمل، أحدد المشكلة والنتيجة المطلوبة، أفكك الـProcess إلى Workflow وTasks، أفهم الـInput والبيانات، أحدد أين أستخدم AI وأين أستخدم Rule وأين يحتاج النظام إلى Human، أصمم Structured Output وValidation، أصمم Automation، ثم أنفذها وأختبرها وأشخص أخطاءها وأحسنها."**

وهذا هو جوهر:

# U1 — Process & Data Thinking

> **Think First. Build Later.**

> **Understand the Work. Understand the Data. Design the Decision. Handle Exceptions. Design the Automation. Then Build It.**
