# ai-system-design-lab

> 90 days. 0 to production-grade AI architect.  
> Node.js · AWS · Anthropic · System Design · LLM Integration

---

## The Goal

By Day 90, I will have designed, documented, and partially built a 
production-grade AI-first fintech advisory platform — from a blank 
whiteboard to a system with real architecture decisions, real trade-off 
records, real prompt engineering, and real Node.js integrations with 
LLM APIs. This is not a tutorial clone. Every component in this repo 
exists because I reasoned through why it should exist, what it replaces, 
and what it costs.

---

## The 5 Core Principles

These principles govern every file committed to this repo.  
If a decision violates one of them, it gets an ADR explaining why.

### 1. Design before code
No implementation file exists in this repo without a corresponding 
design document. The diagram and the trade-off analysis come first. 
Code is the last step, not the first.

### 2. Constraints drive architecture
Good architecture is not about choosing the best technology —  
it is about understanding the constraints (latency budget, team size, 
budget, SLA, data volume) and letting those constraints make the 
decision. Every design here starts with numbers: DAU, RPS, P99 latency 
targets, storage at 5 years.

### 3. AI-first
Phase 1 builds system design foundations. Phase 2 applies them 
specifically to AI systems — RAG pipelines, LLM routing, semantic 
caching, agent orchestration, prompt versioning. AI is not bolted on 
as a feature; it is a first-class architectural concern with its own 
failure modes, cost model, and operational complexity.

### 4. Every decision has trade-offs
There are no objectively correct architecture decisions — only 
decisions that are right given a specific context. Every significant 
choice in this repo has an ADR documenting what was considered, what 
was rejected, and why. By Day 90 this repo will contain 14+ ADRs.

### 5. Systems fail — design for it
Availability, resilience, and graceful degradation are not 
afterthoughts. Every design document in this repo includes a failure 
modes section: what breaks first, what the blast radius is, and how 
the system recovers without a human.

---

## The 90-Day Map

| Phase | Days | Focus | Folder |
|---|---|---|---|
| **Phase 1** | 1 – 30 | System design foundations | `system-design-foundations/` |
| **Phase 2** | 31 – 60 | AI-first architecture + LLM integration | `ai-architecture-patterns/` · `prompt-engineering-playbook/` · `llm-integration-nodejs/` |
| **Phase 3** | 61 – 90 | Capstone: production AI-first SaaS | `capstone-ai-system/` |

Architecture Decision Records run across all 3 phases → `architecture-decision-records/`

---

## Folder Structure
```
ai-system-design-lab/
├── system-design-foundations/     # Fundamentals: scaling, DBs, caching, queues, observability
├── architecture-decision-records/ # Every major design choice, documented with context + consequences
├── ai-architecture-patterns/      # RAG, routing, agents, semantic caching, fallback strategies
├── prompt-engineering-playbook/   # Versioned prompt templates, techniques, debugging guide
├── llm-integration-nodejs/        # Production Node.js SDK integrations, streaming, cost tracking
└── capstone-ai-system/            # End-to-end AI-first fintech advisory platform
```

---

## Daily Rhythm

| Block | Time | Activity |
|---|---|---|
| Read | 30 min | Study the linked resource. Take 5 bullet-point notes. |
| Design | 45 min | Paper sketch first, then Excalidraw. Think out loud. |
| Write | 30 min | Commit a markdown file in your own words. |
| Code *(optional)* | 30 min | Node.js + TypeScript. Always add a test file. |

---

## Stack

- **Runtime:** Node.js · TypeScript
- **Cloud:** AWS (Lambda · DynamoDB · ElastiCache · SQS · CloudWatch)
- **AI / LLM:** Anthropic Claude API · Embeddings · Vector stores
- **Design tools:** Excalidraw · draw.io
- **Documentation:** Markdown ADRs (Nygard format)

---

## Progress

- [ ] Phase 1 complete — System Design Foundations (Day 30)
- [ ] Phase 2 complete — AI Architecture + LLM Integration (Day 60)
- [ ] Phase 3 complete — Capstone shipped (Day 90)

---

## Why This Is Public

Building in public forces clarity. If I cannot explain a design 
decision in a README, I do not understand it well enough yet.  
Every commit here is a checkpoint — not polished portfolio work,  
but honest evidence of reasoning getting sharper over 90 days.

---

*Akshay Jadhav — Senior Node.js + AWS Engineer*