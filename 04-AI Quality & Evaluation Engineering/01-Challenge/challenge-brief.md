# U4 — Challenge

## Can You Prove the AI Works?

### التحدي

لديك نظام AI يستطيع قراءة طلبات المستخدمين وتصنيفها.

في اختبار سريع، أعطيته:

> "I cannot access my training account."

فأجاب:

> **Technical Support**

يبدو صحيحاً.

لكن بعد عدة اختبارات ظهرت النتائج التالية:

| Input                                   | AI Output             |
| --------------------------------------- | --------------------- |
| I cannot access my training account.    | Technical Support     |
| I want to register for the next course. | Technical Support     |
| I forgot my password.                   | Account Support       |
| I need help.                            | Technical Support     |
| Can I join the Python course?           | Training Registration |

---

# Your Challenge

قبل أن تتعلم أي مفهوم جديد:

## السؤال الأول

هل النظام **يعمل**؟

لا تجب بسرعة.

---

## السؤال الثاني

ما الدليل الذي تحتاجه حتى تقول إن النظام يعمل؟

---

## السؤال الثالث

أي نتيجة تعتبر Failure؟

---

## السؤال الرابع

ما سبب الفشل؟

هل هو:

* Prompt؟
* Model؟
* Data؟
* Requirement؟
* Classification Design؟
* Missing Context؟
* Evaluation Criteria؟

---

## السؤال الخامس

ماذا ستغير؟

---

## السؤال السادس

بعد التغيير، هل يكفي أن تختبر الحالة التي فشلت فقط؟

لماذا؟

---

# Constraint

خلال هذه المرحلة:

**لا تستخدم أدوات Evaluation متقدمة.**

ولا تبحث عن:

* LangSmith
* DeepEval
* Ragas
* Evaluation Frameworks

أولاً صمّم طريقة التفكير بنفسك.

---

# Your Attempt

اكتب إجابتك قبل التعلم.

```text
1. هل النظام يعمل؟ ولماذا؟

2. ما تعريف النجاح؟

3. ما الاختبارات التي أحتاجها؟

4. ما الـFailures التي أراها؟

5. ما الدليل الذي أحتاجه؟

6. ما السبب المحتمل للفشل؟

7. ماذا سأغير؟

8. كيف سأعرف أن التغيير نجح؟
```

---

# Challenge Output

يجب أن تنتج في هذه المرحلة:

```text
Success Definition
+
Initial Test Cases
+
Observed Failures
+
Initial Diagnosis
+
Improvement Hypothesis
```

---

## Important

لا تبحث عن الإجابة المثالية.

نحن نريد أولاً أن نرى:

> **كيف تفكر عندما يُطلب منك إثبات جودة نظام AI.**
