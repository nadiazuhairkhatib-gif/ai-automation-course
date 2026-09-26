# سجل الفشل والتحسين — Failure Log

## الهدف

الفشل في نظام AI ليس مجرد خطأ يجب تجاهله.

نستخدم الفشل كدليل يساعدنا على فهم النظام وتحسينه.

النمط الذي نستخدمه:

**Failure → Evidence → Diagnose → Fix → Retest**

---

## Failure Record

### Test Case

> ...

### Expected Output

> ...

### Actual Output

> ...

### Evidence

أرفق Screenshot أو Output أو أي دليل يوضح الفشل.

> ...

### Failure Type

اختر النوع الأقرب:

* Wrong Extraction
* Missing Information
* Hallucination
* Wrong Classification
* Unsupported Assumption
* Format Failure
* Ambiguity
* Other

### Possible Cause

ما السبب المحتمل للفشل؟

> ...

### Fix

ما التغيير الذي أجريته؟

> ...

### Retest

ماذا حدث بعد التعديل؟

> ...

### Final Result

* [ ] Passed
* [ ] Still Failing
* [ ] Needs Human Review

---

# مثال

### Expected

Owner = Walaa

### Actual

Owner = Nadia

### Evidence

AI assigned the task to Nadia although the source says Walaa.

### Failure

Wrong Extraction

### Possible Cause

The instruction did not clearly require the system to preserve the exact owner from the source.

### Fix

Improved the extraction instruction and added a rule:

> Never infer or replace the owner. Use only the person explicitly associated with the action in the source.

### Retest

The system correctly extracted Walaa.

### Final Result

Passed.

---

# قاعدة

لا تكتب:

> "AI made a mistake."

اكتب:

> **What failed? What evidence shows the failure? Why might it have happened? What changed? Did the change work?**

هذا هو **Diagnostic Thinking**.
