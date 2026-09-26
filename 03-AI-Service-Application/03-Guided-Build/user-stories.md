# U3 — User Stories

## الهدف

نحوّل Requirements إلى احتياجات واضحة من منظور المستخدم.

الصيغة:

> **As a [user], I want [action], so that [value].**

---

# User Stories — User

## US-01 — Create Request

> As a User, I want to create a service request so that I can ask for help through one organized system.

---

## US-02 — Describe Request

> As a User, I want to describe my problem so that staff can understand what I need.

---

## US-03 — View My Requests

> As a User, I want to see my previous requests so that I can track what I have submitted.

---

## US-04 — Track Status

> As a User, I want to see the current status of my request so that I know whether it is being processed.

---

# User Stories — Staff

## US-05 — View Requests

> As a Staff Member, I want to see incoming service requests so that I can review and process them.

---

## US-06 — Understand Request Quickly

> As a Staff Member, I want an AI-generated summary so that I can understand a request quickly.

---

## US-07 — Review AI Classification

> As a Staff Member, I want to see the AI's suggested category so that I can review it before processing the request.

---

## US-08 — Review Priority

> As a Staff Member, I want to see the AI's suggested priority so that I can decide whether it is appropriate.

---

## US-09 — Assign Request

> As a Staff Member, I want to assign a request to the appropriate person so that responsibility is clear.

---

## US-10 — Update Status

> As a Staff Member, I want to update the request status so that the user can know its progress.

---

# User Stories — System / AI

## US-11 — Classify Request

> As a System, I want AI to suggest a category based on the request description so that staff can process requests more efficiently.

---

## US-12 — Suggest Priority

> As a System, I want AI to suggest a priority based on the request context so that staff can identify potentially urgent requests.

---

# Important Design Principle

User Stories describe **needs and value**.

They do not dictate implementation.

مثلاً:

> "The system must use OpenAI."

ليست User Story.

لأنها تتحدث عن **Tool** وليس **User Need**.

نحن نريد أولًا أن نعرف:

> **What does the user need?**

ثم نقرر:

> **How should we build it?**

---

# Prioritization

## Must Have

* Create Request
* Store Request
* View Own Requests
* Staff Dashboard
* Assignment
* Status Management

## Should Have

* AI Classification
* AI Summary
* AI Priority Suggestion

## Not in MVP

* Advanced Notifications
* Analytics
* Chatbot
* Multi-Agent Features
* Mobile App
* Complex Integrations

---

# Engineering Question

لكل User Story اسأل:

> **كيف سأعرف أن هذه القصة أصبحت مكتملة فعلًا؟**

الإجابة ستقودنا إلى:

**Acceptance Criteria.**
