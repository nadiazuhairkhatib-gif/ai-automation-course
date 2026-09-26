# Submission Guide

This guide explains what a complete project submission looks like in the AI Automation Course.

A project is not considered complete simply because the tool produces an output.

You are expected to demonstrate that you understand the problem, designed the solution intentionally, tested it, learned from failures, and can explain your decisions.

---

# 1. What Makes a Complete Submission?

A strong submission contains:

```text
Artifact
+
Evidence
+
Explanation
+
Defense
+
Transfer
```

---

## 2. Artifact

The **artifact** is the actual thing you built.

Depending on the unit, this may include:

* An AI-assisted workflow
* An application
* A knowledge assistant
* An AI agent
* An automation workflow
* Documentation
* Configuration files
* Workflow exports
* Supporting data

The artifact should be functional within the scope defined by the unit.

---

# 3. Evidence

Evidence shows that your solution actually works and that you tested it.

Examples include:

* Screenshots
* Test results
* Test datasets
* Execution logs
* Before/after outputs
* Evaluation tables
* Failure cases
* Retest results

Do not submit screenshots simply to make the project look complete.

Each piece of evidence should support a claim about your solution.

---

# 4. Explanation

You should be able to explain:

### Problem

What problem were you solving?

### Users

Who experiences this problem?

### Process

How does the work happen?

### Design

How did you decide what the solution should do?

### AI

Where did you use AI?

Why was AI appropriate there?

### Rules

Where did you use deterministic rules instead of AI?

### Human

Where does a human need to remain involved?

### Testing

How did you determine whether the solution works?

### Failure

What went wrong?

### Improvement

What did you change after the failure?

---

# 5. Defense

During selected project reviews, you may be asked to explain your work briefly.

Typical questions include:

1. What problem were you solving?
2. Why did you design the solution this way?
3. Where is AI used, and why?
4. What could fail?
5. Show me one failure you found.
6. What did you change?
7. How do you know the improvement worked?
8. What would you change if the context changed?

The purpose is not to test memorization.

The purpose is to determine whether you understand the system you built.

---

# 6. Transfer

You should be able to apply the underlying idea to a different situation.

For example:

If you learned how to classify service requests, you should be able to explain how the same reasoning could be applied to another service context.

Transfer demonstrates that you learned the capability rather than memorized a single project.

---

# 7. Recommended Project Structure

Your Student Repository may contain a structure such as:

```text
01-AI-Work-Operations/
│
├── README.md
├── problem.md
├── process-map.png
├── ai-rule-human-map.md
├── workflow/
├── test-cases.md
├── failure-log.md
└── evidence/
```

The exact structure may change depending on the unit.

Always follow the submission requirements provided for that unit.

---

# 8. Testing Evidence

When testing a solution, document:

| Field     | Description                  |
| --------- | ---------------------------- |
| Test Case | What are you testing?        |
| Input     | What did you provide?        |
| Expected  | What should happen?          |
| Actual    | What actually happened?      |
| Result    | Pass / Fail                  |
| Evidence  | What proves the result?      |
| Diagnosis | Why did it fail?             |
| Fix       | What did you change?         |
| Retest    | What happened after the fix? |

A simple test should therefore tell a story:

```text
Test
↓
Expected
↓
Actual
↓
Failure
↓
Diagnosis
↓
Fix
↓
Retest
```

---

# 9. Documentation

Your project documentation should allow another technical person to understand:

* The problem
* The solution
* The architecture
* The tools
* The role of AI
* The role of rules
* The role of humans
* The tests
* The failures
* The improvements
* The limitations

Do not document only what the tool does.

Document the reasoning behind the solution.

---

# 10. AI-Assisted Work

AI tools are allowed and expected where the course requires them.

However, using AI does not remove your responsibility for the final work.

You are responsible for:

* Verifying AI-generated information
* Testing generated outputs
* Understanding your implementation
* Checking for errors
* Protecting sensitive information
* Explaining the final solution

You should be able to explain the important parts of anything you submit.

---

# 11. Secrets and Sensitive Data

Never submit:

* API keys
* Passwords
* Access tokens
* Private credentials
* `.env` files containing secrets
* Sensitive personal information
* Confidential organizational information

Use safe test data whenever possible.

---

# 12. Collaboration

Collaboration is part of professional engineering.

You may:

* Discuss concepts
* Ask for technical help
* Review another learner's approach
* Share useful resources
* Discuss debugging strategies
* Give and receive feedback

However, your submission must represent your own understanding and work.

Do not submit another learner's project, documentation, test evidence, or solution as your own.

---

# 13. Commit Your Work

Use Git commits to document meaningful progress.

Examples:

```text
docs: define project problem
```

```text
feat: build request classification workflow
```

```text
test: add missing-data cases
```

```text
fix: handle ambiguous requests
```

```text
docs: document failure analysis
```

Your Git history can provide additional evidence of your development process.

---

# 14. Before Submission

Use this checklist:

* [ ] I understand the problem.
* [ ] I can explain the intended outcome.
* [ ] I can explain my solution design.
* [ ] My artifact works within the project scope.
* [ ] I tested normal cases.
* [ ] I tested edge or failure cases.
* [ ] I documented at least one meaningful failure when required.
* [ ] I diagnosed the failure.
* [ ] I made an improvement.
* [ ] I retested the solution.
* [ ] My evidence supports my claims.
* [ ] My README is complete.
* [ ] I did not commit secrets.
* [ ] I can explain the important parts of my solution.
* [ ] I can transfer the underlying idea to another context.

---

# 15. The Standard

The goal is not:

> "I made something with AI."

The goal is:

> "I identified a real problem, designed a solution, built it, tested it, found where it failed, improved it, and can explain why it works."

That is the standard we are building toward throughout this course.
