# Prompt Engineering Playbook

> Prompt engineering as a **rigorous engineering discipline**, not a collection of tricks. Every technique documented with reasoning, failure modes, and empirical notes.

## 🧠 Core Philosophy

**Prompts are code.** They:
- 📝 Need to be **versioned**
- 🔍 Need **review** before shipping
- 📊 Need **testing** against fixed eval sets
- 🐛 **Regress** — changes have consequences

Therefore, they deserve the same rigor as your application code.

## 📚 Core Techniques (Quick Reference)

| Technique | When to Use | See Section |
|-----------|------------|-----|
| **Zero-shot prompting** | Simple, well-defined tasks | Core Techniques |
| **Few-shot prompting** | When examples improve accuracy | Core Techniques |
| **Chain-of-thought** | Complex reasoning required | Core Techniques |
| **Structured output constraints** | When you need parsed JSON/types | Core Techniques |
| **Role and persona framing** | When context matters for tone/style | Core Techniques |
| **Adversarial robustness** | When defending against edge cases | Core Techniques |

## 🏗️ System Prompt Architecture

For production applications:
- ✅ How to structure instructions for **reliability**
- ✅ How to handle **conflicting directives**
- ✅ How to **minimize prompt injection surface**
- ✅ How to make prompts **debuggable and testable**

## 🚀 Versioning & Changelog

Every prompt template:
- 📌 **Gets a version number**
- 📋 **Includes a changelog** documenting what changed and why
- ✅ **Is tested** before deployment
- 🔕 **Alerts on changes** — breaking prompt changes should be explicit

## 🐛 Debugging Guide

When a prompt produces unexpected output:

1. **Decision tree** — diagnose the root cause
2. **Quick wins** — fastest path to fixing it
3. **Common pitfalls** — what usually goes wrong
4. **Testing strategy** — how to verify the fix

## 📖 Each Technique Covers

- ✅ **Reasoning** — why this technique works
- ✅ **Problem class** — what it solves
- ✅ **Empirical notes** — where it breaks down
- ✅ **Examples** — real usage patterns
- ✅ **Tradeoffs** — when to use alternatives