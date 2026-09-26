# U3 — User Flow

## الهدف

نحدد كيف يتحرك المستخدم داخل النظام قبل أن نصمم الواجهة.

نحن لا نرسم UI هنا.

نحن نصمم **User Journey**.

---

# Primary User Flow

```text id="9r3p4e"
User Opens Platform
        ↓
Create Service Request
        ↓
Enter Request Details
        ↓
Submit
        ↓
Validate Input
        ↓
Is Data Valid?
     ↙       ↘
   NO         YES
   ↓           ↓
Show Error   Save Request
               ↓
          Generate AI Suggestions
               ↓
          Request Created
               ↓
          User Sees Status
```

---

# Staff Flow

```text id="8l6d6x"
Staff Opens Dashboard
        ↓
View Requests
        ↓
Open Request
        ↓
Review Original Request
        ↓
Review AI Suggestions
        ↓
Accept / Modify Suggestions
        ↓
Assign Request
        ↓
Update Status
        ↓
Process Request
        ↓
Resolve
```

---

# AI Failure Flow

```text id="q7l1sx"
Request
   ↓
AI Processing
   ↓
AI Success?
 ↙          ↘
NO           YES
↓             ↓
Keep Request  Show Suggestions
Saved         ↓
↓          Human Review
Human Review
```

القاعدة:

> **AI Failure must not become System Failure.**

---

# Status Flow

```text id="0gjz0u"
NEW
 ↓
IN_REVIEW
 ↓
ASSIGNED
 ↓
IN_PROGRESS
 ↓
RESOLVED
```

ويجب أن نحدد لاحقًا الحالات التي يسمح النظام بالانتقال بينها.

---

# Invalid Transition Example

مثلاً:

```text id="n2a8h7"
NEW → RESOLVED
```

قد يكون غير مسموح لأن الطلب لم يمر بالمراحل المطلوبة.

النظام يجب أن يمنع الانتقال غير الصحيح.

---

# Main User Journey

نريد أن تكون الرحلة الأساسية قصيرة:

```text id="9g5lra"
Create
  ↓
Submit
  ↓
Track
```

بينما رحلة الموظف:

```text id="n7i6tb"
Review
  ↓
Decide
  ↓
Assign
  ↓
Act
  ↓
Resolve
```

---

# Design Check

قبل بناء UI اسأل:

* هل يستطيع المستخدم الوصول إلى هدفه؟
* هل توجد خطوات غير ضرورية؟
* أين يمكن أن يفشل المستخدم؟
* أين يمكن أن يفشل AI؟
* أين يحتاج الإنسان إلى التدخل؟
* هل يمكن اختبار كل خطوة؟

---

# Engineering Principle

> **Design the journey before designing the screen.**
