# AI Skill Library

> Open, reusable skills that extend AI assistants with practical workflows, structured reasoning, and specialized behavior.

**AI Skill Library** is an open-source collection of reusable AI skills designed to make general-purpose AI assistants more useful for specific tasks.

Instead of building another AI wrapper around a model, this project focuses on the **behavior, instructions, workflows, and interaction patterns** that make an AI assistant better at a particular job.

The goal is simple:

> **Build reusable intelligence, not another chatbot UI.**

---

## ✨ Skills

### 🧠 OmniMentor

**OmniMentor** is a practical-first learning coach designed to turn AI assistants into active learning partners rather than passive explanation engines.

It is built around retrieval practice, desirable difficulty, spaced review, interleaving, progressive difficulty, and demonstrated performance.

OmniMentor can be used to:

- Learn programming languages and frameworks
- Practice Data Structures & Algorithms
- Study theoretical concepts
- Build structured learning timelines
- Practice through quizzes and exercises
- Debug and review code
- Work through projects incrementally
- Identify prerequisite gaps
- Revisit previously learned material
- Adapt difficulty based on demonstrated performance

### Supported interfaces

OmniMentor is designed around a shared, host-agnostic core with platform-specific implementations.

| Interface | Purpose |
|---|---|
| Claude Skill | Native skill implementation for Claude |
| ChatGPT | Custom GPT / instruction-based implementation |
| Shared Core | Host-agnostic source of truth |
| Future integrations | Additional AI platforms can derive from the shared core |

---

## 🧩 Repository Structure

```text
ai-skill-library/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
│
└── skills/
    │
    └── omnimentor/
        ├── SKILL.md
        ├── shared-core.md
        └── README.md
