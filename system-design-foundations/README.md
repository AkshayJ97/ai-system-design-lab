# System Design Foundations

> The foundation that every other folder in this repository builds on. Core vocabulary, mental models, and the reasoning behind every architectural layer.

## 🧭 What You'll Learn

The **core vocabulary and mental models** every system designer must internalize before touching a whiteboard:

- 📈 **Scalability** — handling growing load without performance degradation
- 🔄 **Availability** — keeping systems running despite failures
- 🤝 **Consistency** — maintaining correctness across distributed components
- ⏱️ **Latency** — request speed and user-facing performance
- 💰 **Cost** — infrastructure cost at scale

## 📊 Progressive Architecture Journey

The foundation progresses from simple to complex architecture:

```
Single Server
  ↓ (breaks under load)
Load Balancer + Multiple Servers
  ↓ (data consistency issues)
Database + Replication
  ↓ (queries getting slow)
Caching Layer
  ↓ (complexity increases)
Message Queues + Async Processing
  ↓ (geographic distribution needed)
Globally Distributed Architecture
```

Each step is a **deliberate decision**, not an accident of growth.

## 🔍 Break Point Analysis

Each topic includes a "**break point** analysis":
- 🤔 **Exactly when** does the current layer stop being sufficient?
- 📊 **What metrics** indicate you've hit the limit?
- 🚀 **What's the next architectural move?**
- 💡 **Why that move?** (tradeoffs included)

## 📚 Organization: Concept-First, Not Tutorial-First

**Need to reason about caching?** Jump straight to that concept.  
**Wondering about distributed consensus?** Read that section.  
**Not a tutorial** — it's a reference organized by concept so you can find what you need when you need it.

## 🎯 How to Use This Folder

1. **When starting a new system** — scan the progression to pick your starting point
2. **When hitting bottlenecks** — jump to the relevant concept section
3. **When designing tradeoffs** — use break point analysis to make decisions
4. **When questioning a decision** — revisit the section for full context

## ⚠️ Important

**Revisit this folder whenever a higher-level architectural decision feels unclear.** The patterns and systems in other folders are built on these foundations — understanding why matters more than memorizing what.