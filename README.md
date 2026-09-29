# 🩺 SaaS Health Check Skill

[![Skills.sh](https://img.shields.io/badge/skills.sh-compatible-blue?style=flat-square)](https://skills.sh)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

An AI Agent Skill designed to run a **preliminary technical health check** on early-stage SaaS codebases. 

Instead of noisy, 50-page audits or cosmetic linting debates, this skill inspects your repository, identifies up to **5 high-impact technical risk signals** across 6 key dimensions, and highlights what deserves immediate attention before growth turns technical debt into production incidents or delivery bottlenecks.

---

## ⚡ Installation

Install this skill into your favorite AI agent CLI or IDE extension via [Skills.sh](https://skills.sh):

```bash
npx skills add LucasEscavia/saas-health-checker
```

### Compatible Environments & Tools
This skill works seamlessly with all modern agent environments supporting the `skills` standard:
- **Claude Code** (`claude`)
- **Cursor**
- **Windsurf / Codeium**
- **GitHub Copilot CLI**
- **Antigravity / Gemini CLI**
- **Codex**

*(Alternatively, you can clone or copy `SKILL.md` directly into your workspace's `.skills/`, `.cursor/rules/`, or agent system prompt).*

---

## 🚀 How to Run the Skill

Once installed in your project or agent environment, simply trigger the skill by asking your AI agent in natural language or with a prompt like:

```text
Run a SaaS health check on this codebase.
```

### Example Prompt Triggers
- `"Audit this repository's backend and architecture for scalability risks."`
- `"Can you do a technical health check of this project before our next launch?"`
- `"Fais un bilan de santé technique de ce SaaS et donne-moi les signaux critiques."`

The agent will automatically locate `SKILL.md`, detect your stack, inspect your repository against the 6 analysis dimensions, and generate a standardized markdown report.

---

## 📥 Input / Scope

The skill automatically analyzes the files present in your repository.

### Supported V1 Tech Stack
- **Backend:** Node.js, TypeScript, Java, Spring Boot
- **Full-stack:** Next.js (API Routes, Route Handlers, Server Actions, Server/Client components)
- **Data & Cache:** PostgreSQL, Supabase, Redis
- **Infrastructure:** AWS, Vercel, Docker, Supabase

### What the Skill Evaluates (6 Dimensions)
1. **Architecture:** Component coupling, separation of concerns, domain leaks in routes/controllers, circular dependencies.
2. **Performance:** N+1 queries, unbounded loops, missing pagination, synchronous bottlenecks in request paths.
3. **Data Growth:** Large table access patterns, missing indexes, unsafe/destructive migrations, retention policies.
4. **Resilience:** Missing timeouts/retries, non-idempotent webhook/payment handlers, long-running jobs in transactions.
5. **Delivery & CI/CD:** Test coverage on critical paths, secret leaks, missing CI/CD pipelines, risky deployment flows.
6. **Observability:** Structured logging, request tracing, error tracking, operational visibility.

---

## 📤 Output

The skill produces a clean, factual **Markdown report** formatted as follows:

```markdown
# SaaS Engineering Health Check

## 1. Repository snapshot
- **Backend:** Node.js / TypeScript
- **Framework:** Next.js
- **Database:** PostgreSQL / Supabase
- **Infrastructure:** Vercel
- **Architecture:** Next.js application with server-side API routes
- **Scope analyzed:** relevant application, database and infrastructure files

---

## 2. Key signals
> I found **3 signals worth investigating**.

### 🔴 [Finding Title]
**Severity:** HIGH  
**Confidence:** CONFIRMED  
**Growth impact:** HIGH

**What I found**
Precise observation grounded in code (pointing to files/functions).

**Why it matters**
Concrete potential consequence (e.g. database locks, memory exhaustion under 10x traffic).

**What I cannot confirm**
Missing production context (e.g. real-world traffic volume, p99 latency).

---

## 3. What this check cannot tell you
Clear boundary explaining what cannot be verified without live metrics (runtime latency, real user volume, production error rates).

---

## 4. Suggested next step
Recommendation to move from potential risks to prioritized fixes, including a discovery call link.
```

---

## 🎯 Core Principles

- **Strict Evidence over Assumptions:** Findings are 100% grounded in code observed in the repo. No invented traffic, database sizes, or metrics.
- **Max 5 Signals:** Quality over quantity. Zero low-value linter or cosmetic complaints.
- **Facts vs Hypotheses:** Every finding is categorized with **Severity** (`HIGH`/`MEDIUM`/`LOW`), **Confidence** (`CONFIRMED`/`LIKELY`/`UNKNOWN`), and **Growth impact** (`HIGH`/`MEDIUM`/`LOW`).

---

## 📄 License

MIT © [Lucas Escavia](https://github.com/LucasEscavia)
