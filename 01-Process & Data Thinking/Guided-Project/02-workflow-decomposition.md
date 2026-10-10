# 02 — Workflow Decomposition

## 1. Process

**Client Request Intake & Routing Process**

هي عملية استقبال طلبات العملاء وفهمها وتنظيمها والتحقق منها، ثم تحديد الإجراء المناسب لكل طلب.

## 2. Workflow

يتكون سير العمل من الخطوات التالية:

1. Receive Request
2. Understand Request
3. Structure Information
4. Validate Information
5. Route Request
6. Record Results
7. Notify Relevant Person

## 3. Tasks

| Task | Description |
|---|---|
| Receive Request | استقبال طلب العميل وتسجيل بياناته. |
| Understand Request | فهم محتوى الطلب واحتياجات العميل. |
| Structure Information | استخراج المعلومات المهمة وتنظيمها. |
| Validate Information | التحقق من اكتمال المعلومات ووضوحها. |
| Route Request | تحديد المسار المناسب وفق قواعد محددة. |
| Record Results | تسجيل نتائج معالجة الطلب. |
| Notify Relevant Person | إرسال الإشعار المناسب وفق نتيجة المعالجة. |

## 4. Subtasks

### Task 1: Receive Request
- استقبال بيانات العميل من Google Forms.
- تسجيل الطلب في Google Sheets.

### Task 2: Understand Request
- قراءة نص الطلب.
- تحديد الخدمة التي يحتاج إليها العميل.
- تلخيص الطلب.

### Task 3: Structure Information
- استخراج نوع الخدمة.
- استخراج ملخص الطلب.
- تحديد الميزانية والمدة الزمنية إن توفرتا.
- تحديد المعلومات الناقصة.

### Task 4: Validate Information
- التحقق من وجود البيانات المطلوبة.
- التحقق من إمكانية فهم الطلب وتحديد الخدمة.
- تحديد ما إذا كان الطلب يحتاج إلى مراجعة بشرية.

### Task 5: Route Request
- توجيه الطلب المستوفي للشروط إلى مسار المتابعة.
- توجيه الطلب الذي لا يستوفي الشروط إلى المراجعة البشرية.

### Task 6: Record Results
- تحديث سجل الطلب بنتائج المعالجة.
- حفظ حالة الطلب والمسار المحدد.

### Task 7: Notify Relevant Person
- إرسال إشعار بالطلب الجاهز للمتابعة.
- إرسال إشعار بالطلب الذي يحتاج إلى مراجعة.

## 5. Sequence

يجب تنفيذ المهام بالترتيب التالي:

Receive Request
→ Understand Request
→ Structure Information
→ Validate Information
→ Route Request
→ Record Results
→ Notify Relevant Person

لا يمكن تحديد المسار قبل توفر المعلومات اللازمة والتحقق منها.

## 6. Dependencies

| Task | Depends On |
|---|---|
| Understand Request | Receive Request |
| Structure Information | Understand Request |
| Validate Information | Structure Information |
| Route Request | Validate Information |
| Record Results | Route Request |
| Notify Relevant Person | Record Results |

## Expected Outcome

تحديد خطوات العمل وترتيبها واعتماد بعضها على بعض قبل تحويلها إلى نظام أتمتة.
