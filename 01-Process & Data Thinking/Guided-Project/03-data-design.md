# 03 — Data Design

## 1. Input Data

سيستقبل النظام طلبات العملاء من Google Forms.

تتضمن بيانات النموذج الحقول التالية:

| Field | Purpose | Required |
|---|---|---|
| client_name | اسم العميل | Yes |
| email | البريد الإلكتروني للعميل | Yes |
| company | اسم الشركة التي يمثلها العميل | No |
| service_type | نوع الخدمة المطلوبة | No |
| request_text | تفاصيل طلب العميل | Yes |
| timeline | المدة الزمنية المتوقعة | No |
| budget | الميزانية المتوقعة | No |

قد تكون بعض المعلومات غير موجودة في الطلب، أو قد لا تكون واضحة بما يكفي لاتخاذ القرار المناسب.

## 2. Unstructured Data

يمثل `request_text` نص الطلب الذي يكتبه العميل بطريقته الخاصة.

مثال:

"I need a website for my small business. I have a limited budget and would like to launch it next month."

هذا النص يحتوي على معلومات مهمة، لكنها ليست منظمة في حقول منفصلة.

## 3. Structured Data

سيستخدم AI by Zapier لاستخراج المعلومات التالية من الطلب:

| Field | Description |
|---|---|
| service_type | نوع الخدمة التي يحتاج إليها العميل |
| request_summary | ملخص واضح لطلب العميل |
| timeline | المدة الزمنية المذكورة في الطلب |
| budget | الميزانية المذكورة في الطلب |
| missing_information | المعلومات المطلوبة التي لم تتوفر أو لم تتضح |

### Allowed service_type Values

يجب أن تكون قيمة `service_type` واحدة من القيم التالية:

- `web_design`
- `digital_marketing`
- `graphic_design`
- `app_development`
- `consulting`
- `ai_services`
- `other`
- `unknown`

تُستخدم `other` عندما تكون الخدمة مفهومة، لكنها لا تنتمي إلى الفئات المحددة.

وتُستخدم `unknown` عندما لا يمكن تحديد الخدمة من المعلومات المتاحة.

## 4. Missing Information

سنستخدم القيم التالية للتمييز بين الحالات:

- `Not provided`: المعلومة لم يقدمها العميل.
- `unknown`: لم يتمكن النظام من تحديد نوع الخدمة.
- `other`: الخدمة مفهومة، لكنها خارج الفئات المحددة.
- `None`: لا توجد معلومات ناقصة ضمن الحقول التي جرى التحقق منها.

لا تعني هذه القيم الشيء نفسه، ويجب استخدامها وفق معناها المحدد.

## 5. Processing Results

بعد التحقق من المعلومات وتحديد مسار الطلب، سيضيف النظام النتائج التالية إلى سجل الطلب:

| Field | Purpose | Example |
|---|---|---|
| validation_status | حالة التحقق من الطلب | VALID |
| requires_human | هل يحتاج الطلب إلى مراجعة بشرية؟ | false |
| routing | المسار الذي حُدد للطلب | web_team |
| processed_at | وقت معالجة الطلب | Timestamp |

القيم المسموح بها:

**validation_status**
- `VALID`
- `NEEDS_REVIEW`

**requires_human**
- `true`
- `false`

**routing**
- `web_team`
- `human_review`

## 6. Google Sheets Structure

سيحتفظ Google Sheets ببيانات النموذج الأصلية، مع إضافة أعمدة لنتائج المعالجة.

تشمل أعمدة النتائج:

- service_type
- request_summary
- timeline
- budget
- missing_information
- validation_status
- requires_human
- routing
- processed_at

يجب تحديث سجل الطلب الأصلي بدلًا من إنشاء سجل جديد للطلب نفسه.

## Expected Outcome

تحديد شكل البيانات التي تدخل إلى النظام، والمعلومات التي يستخرجها AI، والنتائج التي يجب حفظها بعد المعالجة.
