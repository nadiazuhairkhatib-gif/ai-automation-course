# Failure Log Template

## Purpose

هذا الملف يوثّق ما يحدث عندما لا يعمل التحليل أو النظام كما هو متوقع.

الهدف ليس إخفاء الأخطاء.

الهدف هو تحويل الخطأ إلى دليل يساعدنا على تحسين النظام.

النمط الأساسي:

```text id="5r0w8h"
FAILURE
↓
EVIDENCE
↓
DIAGNOSIS
↓
FIX
↓
RETEST
↓
VERIFY
```

---

# Failure Record

## Failure ID

```text
F-001
```

---

## 1. Scenario

ما الحالة التي كنا نختبرها؟

```text
Describe the test scenario.
```

---

## 2. Expected Behavior

ماذا كنا نتوقع أن يحدث؟

```text
Describe the expected result.
```

---

## 3. Actual Behavior

ماذا حدث فعليًا؟

```text
Describe the actual result.
```

---

## 4. Evidence

ما الدليل الذي يثبت وجود المشكلة؟

يمكن أن يكون:

* قيمة خاطئة.
* نتيجة حسابية غير صحيحة.
* Claim غير مدعوم.
* مصدران متعارضان.
* Missing Value تم التعامل معها بشكل خاطئ.
* Screenshot.
* Formula result.
* AI output.

```text
Evidence:
```

---

## 5. Failure Type

اختر النوع المناسب:

* Data Quality Failure
* Missing Data Failure
* Validation Failure
* Source Conflict
* Calculation Failure
* Interpretation Failure
* Unsupported Claim
* AI Hallucination
* Causation Error
* Recommendation Failure
* Other

```text
Failure Type:
```

---

## 6. Diagnosis

ما سبب الفشل؟

لا تكتب:

> "AI made a mistake."

حاول تحديد السبب الحقيقي.

اسأل:

* هل كانت البيانات ناقصة؟
* هل كان المصدر غير واضح؟
* هل كانت قاعدة التحقق غير موجودة؟
* هل كان الحساب خاطئًا؟
* هل تم تفسير البيانات بشكل زائد؟
* هل كان Prompt غير واضح؟
* هل استخدم AI معلومة غير موجودة؟
* هل كانت هناك مشكلة في تصميم العملية؟

```text
Diagnosis:
```

---

## 7. Fix

ما التغيير الذي قمنا به؟

قد يكون:

* تصحيح البيانات.
* إضافة Validation Rule.
* تعديل Formula.
* إضافة Source Reference.
* تعديل Prompt.
* إضافة Instruction.
* فصل Fact عن Interpretation.
* إضافة Human Review.
* تغيير طريقة التحليل.

```text
Fix:
```

---

## 8. Retest

أعد تنفيذ الاختبار بعد الإصلاح.

```text
Retest Result:
Pass / Fail
```

---

## 9. Verification

كيف تأكدت أن المشكلة عولجت فعلًا؟

```text
Verification Evidence:
```

---

# Example

## Failure ID

```text
F-001
```

## Scenario

A participant has a missing satisfaction score.

## Expected Behavior

The system should identify the value as Missing and exclude it from the average unless a documented rule says otherwise.

## Actual Behavior

The AI treated the missing value as 0.

## Evidence

The generated average decreased because the missing value was included as zero.

## Failure Type

```text
Missing Data Failure
```

## Diagnosis

The analysis instructions did not define how Missing Values should be handled.

## Fix

Added an explicit rule:

> Missing values must not be converted to zero.

## Retest

The analysis was executed again.

```text
Pass
```

## Verification

The average was recalculated using only valid available values, and the missing record was documented separately.

---

# Failure Log Table

يمكن استخدام الجدول التالي لتتبع جميع المشكلات:

| ID    | Failure Type | Expected | Actual | Diagnosis | Fix | Retest |
| ----- | ------------ | -------- | ------ | --------- | --- | ------ |
| F-001 |              |          |        |           |     |        |
| F-002 |              |          |        |           |     |        |
| F-003 |              |          |        |           |     |        |

---

# Engineering Rule

لا تعتبر المشكلة محلولة لأنك غيّرت الـPrompt.

المشكلة محلولة عندما:

1. عرفت لماذا حدث الفشل.
2. غيّرت شيئًا له علاقة بالسبب.
3. أعدت الاختبار.
4. حصلت على نتيجة أفضل.
5. استطعت إثبات التحسن.

> **If you cannot explain the failure, you are not ready to claim that you fixed it.**
