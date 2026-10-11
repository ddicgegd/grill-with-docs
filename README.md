# Grill With Docs (`grill-with-docs`)

> **Swarm-Powered Deep Architecture & Design Engine for Antigravity (agy)**
> Relentlessly stress-tests plans, designs, and codebases through dynamic contextual inquiry, orchestrating asynchronous scout subagents to mine facts from any project, while capturing glossary terms, architecture decisions (ADRs), and technical specs.

---

## 🌟 Overview

`grill-with-docs` is a high-performance Antigravity skill that unifies deep technical grilling with autonomous distributed codebase reconnaissance. Instead of shallow assumptions or rigid Q&A scripts, it dynamically dispatches swarms of asynchronous scout subagents to gather facts across your repositories, challenges technical assumptions, and writes hardened documentation (`GLOSSARY.md`, ADRs, Technical Specs) directly to disk.

---

## ⚡ Key Capabilities

### 1. Hard Guardrails (Rào chắn an toàn tuyệt đối)
- **Zero Production Code during Inquiry**: During technical grilling and architectural exploration, writing or modifying application source code is strictly forbidden. 
- **Documentation Only**: The only files modified or generated are `GLOSSARY.md`, `docs/adr/*.md`, and `docs/specs/*.md` / `docs/plans/*.md`.
- **Implementation on Demand**: Transitions to implementation only when explicitly instructed by the user.

### 2. Dynamic Contextual Inquiry (Hội thoại mở, Không gò bó)
- **Eliminates Rigid Design Trees**: No artificial frontiers, rounds, or scripted questionnaires.
- **Context-Driven Stress Testing**: Dynamically focuses on implicit assumptions, boundary contracts, state transitions, and edge cases.
- **Actionable Recommendations (`➡️`)**: Every question or critique is accompanied by a concrete recommended path.

### 3. Asynchronous Scout Swarm (Đàn Scout Sub-agent Bất đồng bộ)
- **Dynamic Anchoring**: Automatically detects critical hotspots across models, entities, business rules, configurations, and external contracts.
- **Concurrent Dispatching**: Launches multiple lightweight subagents concurrently using isolated workspaces and micro-tasks.
- **Zero Context Bloat**: Fact retrieval happens asynchronously without polluting the main agent's context window.
- **Persistent Pinning & Messaging**: Reuses pinned scouts via targeted messaging (`send_message`) for follow-up investigations.

### 4. Automated Documentation Engine
- **Business Glossary (`GLOSSARY.md`)**: Single source of truth for domain vocabulary, eliminating ambiguity.
- **Architectural Decision Records (`docs/adr/000X-<slug>.md`)**: Rigorous 3-gate filter (hard to reverse, surprising without context, real trade-off).
- **Technical Specifications (`docs/specs/<feature-name>.md`)**: Complete schema, error codes, validation rules, transaction flows, and test matrices preserved before writing a single line of code.

---

## 📦 Installation

### Global Installation (Available across all projects)
Clone or place this repository under your global Antigravity skills directory:
```bash
# Windows
git clone https://github.com/ddicgegd/grill-with-docs.git "%USERPROFILE%\.gemini\config\skills\grill-with-docs"

# Linux / macOS
git clone https://github.com/ddicgegd/grill-with-docs.git ~/.gemini/config/skills/grill-with-docs
```

### Project-Specific Workspace Installation
Place under your project's `.agents/skills/` directory:
```bash
git clone https://github.com/ddicgegd/grill-with-docs.git .agents/skills/grill-with-docs
```

---

## 🚀 Usage

Trigger the skill in Antigravity chat:
```
/grill-with-docs Hãy chất vấn và làm rõ thiết kế kiến trúc cho tính năng ...
```
or naturally describe your requirement:
```
Phản biện giúp tôi kế hoạch triển khai kiến trúc này và tạo specs / ADRs tương ứng.
```

---

## 📄 License

MIT License.
