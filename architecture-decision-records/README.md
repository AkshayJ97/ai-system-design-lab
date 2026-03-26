# Architecture Decision Records (ADRs)

> The institutional memory of the repository — a searchable log of "why" behind every significant architectural choice.

## 📝 What Is an ADR?

An **Architecture Decision Record** is a short, structured document that captures:
- **The choice** — what architectural decision was made
- **The context** — what forced this decision, what were the constraints
- **The consequences** — what happens as a result of this choice

**Goal:** Make reasoning visible long after the meeting ends.

## 📋 Format: Nygard Lightweight Standard

Every ADR follows this structure:

```
# [ADR-###] Title

Status: [Proposed | Accepted | Superseded | Deprecated]
Date: [YYYY-MM-DD]

## Context
What is the issue we're addressing? What forces us to make this decision?

## Decision
What is the architectural decision we're making?

## Consequences
What becomes easier? What becomes harder?
What are the tradeoffs?
```

## 🔒 Key Principle: Immutability

- ✅ Once an ADR is **Accepted**, it is **never overwritten**
- 🔄 If a decision is **reversed**, create a new ADR that **supersedes** it
- 📚 This preserves the **full audit trail** — why we chose A, then why we switched to B

## 🎯 Purpose

**Not documentation for its own sake.**

This folder is:
- 🔍 A searchable log of architectural choices
- 🛡️ A guard against repeating rejected decisions
- 📖 The reasoning behind every significant code structure
- 🧭 A guide for future changes with full context

## 💡 Think of It As...

**The diff between the codebase and the reasoning behind it.**