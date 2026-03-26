# AI Architecture Patterns

> Repeatable structural patterns for building production AI systems, documented with the rigor of Gang of Four design patterns but applied to AI pipelines.

## 📖 What This Folder Contains

This module catalogs **proven, production-tested patterns** for AI system design. Each pattern documents:
- **Problem statement** — the challenge it solves
- **Solution sketch** — architectural approach and tradeoffs
- **Known failure modes** — when and how it breaks
- **`When NOT to use`** — equally important as when to use it
- **Visual diagrams** — structure visible at a glance

## 🎯 Patterns Covered

- 🔍 **RAG (Retrieval-Augmented Generation)** — grounding models with external knowledge
- ⚡ **Semantic Caching** — reducing redundant model calls and latency
- 🔄 **Model Routing** — intelligent dispatch to optimal models
- 👤 **Human-in-the-Loop Checkpoints** — maintaining control over AI decisions
- 🤝 **Multi-Agent Orchestration** — coordinating multiple AI agents
- *And more...*

## 🌟 Core Philosophy

**Operability first** — Every pattern is evaluated not just for correctness at demo time, but for survivability at 3am when the pipeline drifts.

### Common Mistakes We Avoid
- ❌ Reaching for complex patterns when simpler ones would hold the load
- ❌ Optimizing for happy paths instead of failure modes
- ❌ Building systems that work once but can't be debugged in production

## 📊 Each Pattern Includes

✅ Clear problem context  
✅ Architectural diagram  
✅ Implementation considerations  
✅ Known limitations and tradeoffs  
✅ When to use and when NOT to use