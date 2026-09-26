# U3 — Acceptance Criteria

## الهدف

**Acceptance Criteria** تحدد الشروط التي يجب تحققها حتى نعتبر الـUser Story مكتملة.

القاعدة:

> **If we cannot define how to know it works, the requirement is incomplete.**

---

# US-01 — Create Request

### User Story

> As a User, I want to create a service request so that I can ask for help through one organized system.

### Acceptance Criteria

* يستطيع المستخدم فتح نموذج إنشاء الطلب.
* يجب إدخال الحقول المطلوبة.
* لا يمكن إرسال الطلب إذا كانت البيانات المطلوبة ناقصة.
* عند الإرسال الناجح يتم إنشاء Request جديد.
* يحصل الطلب على ID.
* تظهر للمستخدم رسالة نجاح.
* تظهر حالة الطلب الحالية.

---

# US-02 — Describe Request

### Acceptance Criteria

* يستطيع المستخدم إدخال وصف للمشكلة.
* لا يقبل النظام وصفًا فارغًا.
* يتم حفظ الوصف كما أدخله المستخدم.
* لا يتم تغيير معنى الوصف أثناء التخزين.

---

# US-03 — View My Requests

### Acceptance Criteria

* يستطيع المستخدم رؤية طلباته.
* لا تظهر له طلبات مستخدمين آخرين.
* يستطيع فتح تفاصيل الطلب.
* تظهر حالة كل طلب.

---

# US-04 — Track Status

### Acceptance Criteria

* يظهر Status واضح لكل Request.
* يتم تحديث الحالة عند تغييرها من Staff.
* يرى المستخدم آخر حالة محفوظة.

---

# US-05 — View Requests

### Acceptance Criteria

* يستطيع Staff الوصول إلى Dashboard.
* تظهر الطلبات التي يستطيع معالجتها.
* يمكن فتح تفاصيل أي Request مسموح له برؤيته.
* تظهر المعلومات الأساسية للطلب.

---

# US-06 — AI Summary

### Acceptance Criteria

* يستطيع النظام إنشاء Summary للطلب.
* يجب ألا يضيف الـSummary معلومات غير موجودة في الطلب.
* إذا فشل AI، يبقى الطلب محفوظًا.
* يستطيع Staff الرجوع إلى النص الأصلي.

---

# US-07 — AI Classification

### Acceptance Criteria

* يقترح AI Category.
* يظهر الاقتراح بوضوح على أنه AI Suggestion.
* يستطيع Staff قبول الاقتراح أو تغييره.
* لا يؤدي خطأ التصنيف إلى فقدان الطلب.

---

# US-08 — AI Priority

### Acceptance Criteria

* يقترح AI Priority.
* يظهر سبب أو سياق الاقتراح عندما يكون ذلك متاحًا.
* يستطيع Staff تعديل الأولوية.
* لا ينفذ النظام إجراءً حساسًا اعتمادًا على الاقتراح وحده.

---

# US-09 — Assign Request

### Acceptance Criteria

* يستطيع Staff اختيار المسؤول.
* يتم حفظ Assignment.
* تظهر المسؤولية الحالية للموظفين المخولين.
* لا يستطيع مستخدم عادي تغيير Assignment.

---

# US-10 — Update Status

### Acceptance Criteria

* يستطيع Staff تحديث الحالة.
* يسمح النظام فقط بالانتقالات المسموحة.
* يتم حفظ الحالة الجديدة.
* تظهر الحالة الجديدة للمستخدم.

---

# US-11 — AI Classification Failure

### Acceptance Criteria

إذا كان AI غير قادر على تحديد Category بثقة مناسبة:

* لا يخترع النظام Category بشكل غير موثوق.
* يتم وضع الطلب للمراجعة البشرية.
* يبقى الطلب محفوظًا.
* يستطيع Staff اتخاذ القرار يدويًا.

---

# US-12 — AI Failure

### Acceptance Criteria

إذا فشل AI لأي سبب:

* لا يفشل إنشاء الطلب الأساسي.
* لا تضيع بيانات المستخدم.
* تظهر إمكانية المتابعة يدويًا.
* يستطيع Staff الوصول إلى الطلب الأصلي.

---

# Acceptance Criteria Quality Check

لكل Criteria اسأل:

1. هل يمكن اختبارها؟
2. هل هي واضحة؟
3. هل يوجد تفسير واحد لها؟
4. هل يمكن إثبات Pass أو Fail؟

إذا كانت الإجابة لا، فالـCriteria تحتاج إلى إعادة صياغة.

---

# Engineering Principle

> **Requirements tell us what the system should do.
> Acceptance Criteria tell us how we know it actually does it.**
