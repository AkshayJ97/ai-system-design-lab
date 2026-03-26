# Capstone AI System

> **The proof.** A production-grade, end-to-end AI-powered system that applies every concept from the other five folders in the repository.

## 🎯 Core Question

**"What does a well-architected AI feature actually look like in a real Node.js backend?"**

This capstone answers that question through a complete, working system.

## 🏗️ Architecture: Four Core Layers

```
API Layer (Express/Fastify endpoints)
        ↓
Orchestration Layer (prompt + model call management)
        ↓
Retrieval Layer (vector store backed RAG)
        ↓
Async Job Queue (for work that exceeds request timeout)
```

### Layer 1: API Layer
- 🔌 Clean HTTP endpoints
- 📊 Structured request/response contracts
- ✅ Proper error handling and status codes

### Layer 2: Orchestration Layer
- 🧠 Prompt management and versioning
- 🤖 Model call routing and retry logic
- 💰 Token budget tracking
- 🔄 State machine orchestration

### Layer 3: Retrieval Layer
- 🔍 Vector search over knowledge base
- 📚 RAG (Retrieval-Augmented Generation) pipeline
- 🎯 Semantic relevance filtering

### Layer 4: Async Job Queue
- ⏳ Long-running model operations
- 🔔 Async result delivery
- 📍 Progress tracking
- 🛡️ Failure recovery

## 📖 Complete Documentation

Every component includes:

| Component | Has |
|-----------|-----|
| **API Layer** | ✅ README | ✅ Test Suite | ✅ ADR (why this design) |
| **Orchestration** | ✅ README | ✅ Test Suite | ✅ ADR (why this design) |
| **Retrieval** | ✅ README | ✅ Test Suite | ✅ ADR (why this design) |
| **Async Queue** | ✅ README | ✅ Test Suite | ✅ ADR (why this design) |

## 🧭 Design Principles

✅ **Separation of concerns** — each layer has one job  
✅ **Observable internals** — metrics and logs at every step  
✅ **Documented tradeoffs** — every decision recorded in ADRs  
✅ **Production-grade** — handles real load, real failures  
✅ **Testable** — comprehensive test coverage at all layers  

## ✔️ The Proof

**If the system holds under realistic load AND the reasoning behind every decision is findable in this repo, then the foundations were right.**

This capstone isn't aspirational — it's the working implementation that validates all the patterns and principles documented in the other five folders.