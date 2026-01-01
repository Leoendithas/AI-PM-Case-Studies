# Case Studies — AI Product Management

This repo is a curated set of **public-safe, de-identified** case studies from my work shipping and evaluating **LLM-enabled products**.

I write these to show how I think about:
- **Product quality** (does it work reliably?)
- **Safety & harm prevention** (what can go wrong, especially with minors?)
- **Adoption** (will people actually use it in their workflow?)
- **Outcomes** (did it create measurable value?)

> **Notes on privacy:** Org/platform names, internal prompts, and sensitive details are omitted. Metrics are aggregated or approximate where needed.

---

## Case studies

### 1) Learning outcomes over adoption (no-ship / delay decision)
**Why it matters:** Strong signal for big tech & government — demonstrates product judgement, evaluation discipline, and willingness to say “no” when impact isn’t proven.

- 📄 Read: `learning-outcomes-over-adoption.md`
- 🔗 Prototype used for testing: https://github.com/Leoendithas/AIchat
- Highlights:
  - High teacher interest did not translate to clear learning gains
  - Always-on intervention was inherently disruptive (couldn’t “stay quiet”)
  - Decision: delay shipping; explore less intrusive / more natural modalities

### 2) Sector-specific AI safety for minors (gold dataset + eval pipeline)
**Why it matters:** Shows how to operationalise safety in a high-stakes environment (minors) using defensible evaluation, governance, and stakeholder-aware monitoring.

- 📄 Read: `sector-specific-ai-safety-for-minors.md`
- Highlights:
  - Curated ~5,000 de-identified conversations and built a specialist-annotated **gold dataset**
  - Implemented **LLM-as-judge** evaluation with a second layer to reduce false positives
  - Designed **teacher-in-the-loop monitoring** with severity-aware thresholds and block/replace for severe categories
  - Guardrail installation and alerting are ongoing; focus is on building the measurement system to choose safer models

---

## Frameworks & playbooks

### LLM Eval Playbook (AI PM edition)
Docs + templates for bulk evaluation with **pass/fail rubrics**, **LLM-as-judge**, and **human-in-the-loop sampling** — designed for fast iteration and release gating.

- Repo: https://github.com/Leoendithas/llm-eval-playbook

---

## How to read these
Each case study follows a consistent structure:
- Context & problem
- What success looked like
- Approach (research / evaluation / iteration)
- Findings and trade-offs
- Decision + rationale
- What I learned + what I’d do next

If you’re reviewing me for roles: I’m happy to share deeper details privately where appropriate.

---

## About me
I’m Lance — an AI Product Manager focused on **LLM productization**, especially:
- evaluation & reliability in production
- safety/guardrails (including minors)
- adoption and rollout in complex environments

- GitHub: https://github.com/Leoendithas  
- LinkedIn: https://www.linkedin.com/in/lance-tan  

---

## License
Unless otherwise stated, contents are licensed under **Apache-2.0**.
