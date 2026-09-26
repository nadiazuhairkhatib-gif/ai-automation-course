# GitHub Guide

This guide explains how to use GitHub during the AI Automation Course.

You do not need to become a Git expert.

You need to understand how to use GitHub to:

* Access course materials
* Save your work
* Track your progress
* Submit projects
* Document your engineering process
* Keep evidence of what you built and improved

---

# 1. How GitHub Is Used in This Course

You will work with two different repositories.

## Course Hub

The Course Hub is the official learning repository for the course.

It contains:

* Challenges
* Concepts
* Guided builds
* Independent practice
* Testing materials
* NOVA activities
* Resources

You mainly **read and use** the Course Hub.

> **Course Hub = What you need to learn**

---

## Student Repository

Your Student Repository is your private workspace.

It contains the work you actually build during the course.

You will use it for:

* Project files
* Documentation
* Test cases
* Failure logs
* Evidence
* NOVA
* Final submissions

> **Student Repository = What you built and can prove**

---

# 2. Repository

A **repository (repo)** is a project space on GitHub.

Think of it as the main container for a project.

For example:

```text
ai-automation-course
```

is the repository for the Course Hub.

Your personal repository will contain your own course work.

---

# 3. Files and Folders

A repository contains files and folders.

Example:

```text
ai-automation-course/
│
├── README.md
│
├── 00-Course-Guide/
│   ├── README.md
│   └── github-guide.md
│
└── 01-AI-Work-Operations/
```

A file contains content.

A folder organizes related files.

---

# 4. README.md

A `README.md` explains what a repository, folder, project, or activity is about.

You will see README files throughout the course.

Before starting a project, read its README.

---

# 5. Commit

A **commit** is a saved point in the history of your repository.

A commit records a change you made.

For example:

```text
docs: add process map
```

or:

```text
feat: add request classification workflow
```

Good commits describe what changed.

Avoid messages such as:

```text
update
changes
final
test
```

---

# 6. Why Commits Matter

Your project is not only the final result.

During this course, your process matters.

Commits can help show:

```text
Build
↓
Test
↓
Failure
↓
Fix
↓
Retest
```

This gives evidence of your engineering process.

> **We care about how you arrived at the solution, not only the final artifact.**

---

# 7. Editing a File

To edit a file on GitHub:

1. Open the file.
2. Select the edit option.
3. Make your changes.
4. Preview the result when appropriate.
5. Write a meaningful commit message.
6. Commit the changes.

---

# 8. Creating a File

To create a new file:

1. Open the repository or target folder.
2. Select **Add file**.
3. Select **Create new file**.
4. Enter the file name.
5. Add the content.
6. Write a meaningful commit message.
7. Commit the changes.

---

# 9. Creating a Folder

GitHub does not normally create an empty folder.

A folder is created when you create a file inside it.

For example:

```text
03-AI-Service-Application/README.md
```

creates:

```text
03-AI-Service-Application/
└── README.md
```

---

# 10. Uploading Files

If you already have a file on your computer:

1. Open the target folder.
2. Select **Add file**.
3. Select **Upload files**.
4. Choose the files.
5. Review the files.
6. Write a meaningful commit message.
7. Commit the changes.

Do not upload unnecessary temporary files.

Examples of files you may upload:

* Markdown documentation
* Images
* CSV files
* JSON files
* Workflow exports
* Project configuration files

---

# 11. Commit Message Style

Use a short message that describes the change.

Examples:

```text
docs: add project README
```

```text
feat: add request classification workflow
```

```text
test: add edge cases for missing data
```

```text
fix: handle missing owner field
```

```text
docs: update failure analysis
```

The goal is not to memorize these prefixes.

The goal is to make your project history understandable.

---

# 12. Recommended Commit Types

### `docs:`

Documentation changes.

Example:

```text
docs: add testing notes
```

### `feat:`

A new capability or feature.

Example:

```text
feat: add AI request classification
```

### `fix:`

A correction to an existing solution.

Example:

```text
fix: handle missing deadline
```

### `test:`

Testing-related changes.

Example:

```text
test: add ambiguous request cases
```

---

# 13. Branches

A **branch** is an independent development path.

Branches are useful when multiple versions of a project need to be developed separately.

For this course, you will normally work directly on your main branch unless the instructor asks you to use a branch.

You do not need advanced Git branching for this course.

---

# 14. Pull Requests

A **Pull Request (PR)** is a request to merge changes from one branch into another.

Pull Requests are commonly used in collaborative software development.

They are not required for every activity in this course.

If a project specifically requires a Pull Request, you will receive instructions.

---

# 15. Do Not Commit Secrets

Never upload:

* API keys
* Passwords
* Access tokens
* Private credentials
* `.env` files containing secrets
* Personal sensitive information

If a project requires a secret, use the appropriate environment-variable or secrets mechanism.

> **A secret should never be stored directly in your repository.**

---

# 16. Course Workflow

For most projects, your workflow will look like:

```text
Read
↓
Challenge
↓
Attempt
↓
Build
↓
Test
↓
Break
↓
Diagnose
↓
Fix
↓
Retest
↓
Document
↓
Commit
```

Your GitHub repository should reflect this process where appropriate.

---

# 17. Before You Commit

Ask yourself:

* What changed?
* Is the change meaningful?
* Is the file in the correct folder?
* Did I accidentally include a secret?
* Does the documentation match the current solution?
* Can another person understand what I changed?

Then commit.

---

# 18. Your Goal

You are not learning GitHub simply because GitHub is part of the course.

You are learning to use version control as part of professional engineering practice.

Your repository should gradually become evidence of your work:

```text
Problem
↓
Design
↓
Build
↓
Test
↓
Failure
↓
Improvement
↓
Evidence
↓
Final Solution
```

> **Your repository is part of your engineering story.**
