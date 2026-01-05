# Case Studies — AI Product Management

This repo is a curated set of **public-safe, de-identified** case studies from my work shipping and evaluating **LLM-enabled products**.

I write these to show how I think about:
- **Product quality** (does it work reliably?)
- **Safety & harm prevention** (what can go wrong, especially with minors?)
- **Adoption** (will people actually use it in their workflow?)
- **Outcomes** (did it create measurable value?)

> **Privacy note:** Org/platform names, internal prompts, and sensitive details are omitted. Metrics are aggregated or approximate where needed.

---

## Case studies

### 1) Learning outcomes over adoption (no-ship / delay decision)
**Why it matters:** Many pilots look “successful” because users like them. This shows what to do when “lots of interest” isn’t enough.  
**You’ll take away:** an outcome-first evaluation pattern, common failure modes of always-on interventions, and a “pause vs ship” decision rubric.

- 📄 Read: `learning-outcomes-over-adoption.md`  
- 🔗 Prototype used for testing: https://github.com/Leoendithas/AIchat  
- **Key findings:**
  - Strong interest, but no clear learning gains in student tests  
  - The “must speak every ~5–6 messages” constraint made it inherently intrusive  
  - Distraction/frustration showed up → pivoted to less intrusive modalities  

### 2) Sector-specific AI safety (ground-truth dataset + validation pipeline)
**Why it matters:** Most “AI safety” guidance stays abstract. This shows how to operationalise it for minors in a high-stakes setting.  
**You’ll take away:** how to build a ground-truth dataset, run scalable validation, and design severity-aware monitoring that avoids alert fatigue.

- 📄 Read: `sector-specific-ai-safety.md`  
- **What I built:**
  - ~5,000 de-identified conversations → expert-annotated ground-truth dataset  
  - Validation pipeline: LLM-as-judge + second layer to reduce false positives  
  - Teacher-in-the-loop monitoring design with severity thresholds + block/replace for severe cases  

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

---

## About me
I’m Lance — an AI Product Manager focused on **LLM productization**, especially:
- evaluation & reliability in production
- safety/guardrails
- adoption and rollout in complex environments

- GitHub: https://github.com/Leoendithas  
- LinkedIn: https://www.linkedin.com/in/lance-tan  

---

## License
Unless otherwise stated, contents are licensed under **Apache-2.0**.
