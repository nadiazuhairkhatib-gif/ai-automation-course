# U3 — Data Model

## الهدف

نحدد ما الذي يحتاج النظام إلى تخزينه قبل إنشاء قاعدة البيانات.

القاعدة:

> **Do not design the database from the UI.
> Design it from the system's information needs.**

---

# Core Entities

في MVP نحتاج إلى:

```text id="1tqk3r"
Users
Requests
Categories
Assignments
Status History
```

---

# 1. Users

يمثل الأشخاص الذين يستخدمون النظام.

| Field      | Purpose        |
| ---------- | -------------- |
| id         | Unique User ID |
| name       | User name      |
| email      | User contact   |
| role       | User / Staff   |
| created_at | Creation time  |

---

# 2. Requests

يمثل Service Request.

| Field       | Purpose               |
| ----------- | --------------------- |
| id          | Unique Request ID     |
| user_id     | Request creator       |
| title       | Short request title   |
| description | Original request      |
| category_id | Selected category     |
| priority    | Request priority      |
| status      | Current status        |
| assigned_to | Responsible staff     |
| ai_summary  | AI-generated summary  |
| ai_category | AI suggested category |
| ai_priority | AI suggested priority |
| created_at  | Creation time         |
| updated_at  | Last update           |

---

# 3. Categories

تمثل أنواع الخدمات.

مثلاً:

* Technical Support
* Registration
* Training
* General Inquiry
* Other

| Field       | Purpose                    |
| ----------- | -------------------------- |
| id          | Category ID                |
| name        | Category name              |
| description | Category description       |
| active      | Whether category is active |

---

# 4. Assignments

تسجل مسؤولية الطلب.

| Field       | Purpose         |
| ----------- | --------------- |
| id          | Assignment ID   |
| request_id  | Related request |
| staff_id    | Assigned staff  |
| assigned_at | Assignment time |

---

# 5. Status History

نحتاج إلى معرفة كيف تغيرت حالة الطلب.

| Field      | Purpose             |
| ---------- | ------------------- |
| id         | History ID          |
| request_id | Related request     |
| old_status | Previous status     |
| new_status | New status          |
| changed_by | User who changed it |
| changed_at | Change time         |

---

# Relationships

التصور الأساسي:

```text id="5u3x8z"
User
 │
 └────< Requests
             │
             ├──── Category
             │
             ├────< Assignments
             │
             └────< Status History
```

---

# Important Distinction

هناك فرق بين:

### Current State

ما حالة الطلب الآن؟

```text
status = IN_PROGRESS
```

### History

كيف وصل الطلب إلى هذه الحالة؟

```text
NEW
↓
IN_REVIEW
↓
ASSIGNED
↓
IN_PROGRESS
```

هذا الفرق مهم جدًا عند بناء أنظمة حقيقية.

---

# AI Data

يجب ألا نستبدل البيانات الأصلية باقتراح AI.

مثلاً:

```text id="9s9d7f"
Original Description
        +
AI Suggested Category
        +
Human Confirmed Category
```

وليس:

```text id="3v8j2n"
Original Description
        ↓
AI rewrites everything
```

يجب الحفاظ على **Original Data**.

---

# AI vs Confirmed Data

مثال:

| Field       | Meaning                 |
| ----------- | ----------------------- |
| ai_category | AI suggestion           |
| category_id | Final selected category |
| ai_priority | AI suggestion           |
| priority    | Final priority          |

بهذا نستطيع معرفة:

> ماذا اقترح AI؟

و:

> ماذا قرر الإنسان؟

وهذا سيكون مهمًا جدًا لاحقًا في **U4 — Quality & Evaluation**.

---

# MVP Data Boundary

لا نحتاج الآن إلى:

* Audit system متقدم.
* Event sourcing.
* Complex relational architecture.
* Data warehouse.
* Advanced analytics.

نحتاج فقط إلى Data Model واضح يكفي لإثبات النظام.

---

# Engineering Principle

> **If you don't know what data the system needs to remember, you don't fully understand the system yet.**
