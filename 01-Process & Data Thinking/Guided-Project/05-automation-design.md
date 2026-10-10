# 05 — Automation Design

## 1. Automation Goal

بناء نظام يساعد الشركة على معالجة طلبات العملاء بصورة منظمة، بدءًا من استقبال الطلب وحتى تسجيل نتيجة المعالجة وإرسال الإشعار المناسب.

## 2. Automation Flow

Google Forms
→ Google Sheets
→ AI by Zapier
→ Decision & Routing
→ Update Google Sheets
→ Send Email Notification

## 3. Step 1 — Receive Request

**Tool:** Google Forms + Google Sheets

عندما يرسل العميل النموذج:

1. يستقبل النظام بيانات العميل.
2. تُحفظ البيانات في Google Sheets.
3. يبدأ تدفق الأتمتة عند وصول سجل جديد.

يجب الاحتفاظ بمعرّف السجل الأصلي حتى يتم تحديث الطلب نفسه لاحقًا.

## 4. Step 2 — Extract Information

**Tool:** AI by Zapier

يستقبل AI نص الطلب والبيانات المتاحة، ثم يستخرج المعلومات المطلوبة:

- service_type
- request_summary
- timeline
- budget
- missing_information

يجب أن يلتزم AI بالمعلومات التي قدمها العميل، وألا يخترع ميزانية أو مدة زمنية أو تفاصيل غير موجودة.

إذا لم يقدم العميل معلومة، تُسجل بوصفها `Not provided` بدلًا من تخمينها.

## 5. Step 3 — Validate & Route

تُطبّق قواعد التحقق المحددة في:

`04-decision-and-exception-design.md`

يوجد مساران:

### Path A — Ready for Follow-up

يُستخدم عندما يستوفي الطلب جميع شروط التحقق.

النتيجة:

- `validation_status = VALID`
- `requires_human = false`
- `routing = web_team`

### Path B — Human Review

يُستخدم عندما لا يستوفي الطلب شرطًا مطلوبًا، أو عندما تكون المعلومات غير واضحة بما يكفي.

النتيجة:

- `validation_status = NEEDS_REVIEW`
- `requires_human = true`
- `routing = human_review`

يجب أن تتطابق شروط المسارين، بحيث لا يُوجّه الطلب نفسه إلى المسارين معًا.

## 6. Step 4 — Update the Record

**Tool:** Google Sheets

بعد تحديد المسار:

1. يُحدّث النظام سجل الطلب الأصلي.
2. تُحفظ المعلومات المستخرجة.
3. تُحفظ حالة التحقق والمسار المحدد.
4. يُسجل وقت المعالجة عند توفر قيمة وقت مناسبة من Zapier.

يجب ألا يؤدي التحديث إلى إنشاء سجل مكرر للطلب نفسه.

## 7. Step 5 — Send Notification

**Tool:** Email by Zapier

### For Path A

إرسال إشعار يفيد بأن الطلب استوفى شروط المتابعة، مع تضمين المعلومات المنظمة التي يحتاج إليها الموظف.

### For Path B

إرسال إشعار يفيد بأن الطلب يحتاج إلى مراجعة بشرية، مع توضيح المعلومات الناقصة أو غير الواضحة.

## 8. Technical Failures

إذا فشلت خطوة تقنية، مثل استخراج المعلومات أو تحديث السجل أو إرسال الإشعار، فلا ينبغي تسجيل هذا الفشل تلقائيًا على أنه `NEEDS_REVIEW`.

في هذه النسخة، تتم مراجعة سجل التنفيذ في Zapier لتحديد الخطوة الفاشلة وتصحيحها.

## Expected Outcome

تصميم تدفق أتمتة واضح يربط استقبال الطلب بمعالجته والتحقق منه وتسجيل نتيجته وإرسال الإشعار المناسب.
