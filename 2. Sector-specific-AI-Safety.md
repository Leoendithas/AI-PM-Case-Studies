# Sector-Specific AI Safety for Minors: Building a Gold Dataset + Eval Pipeline

## TL;DR
After Q4 2024 reporting of youths overseas being harmed following unsafe interactions with commercial chatbots, I led a safety initiative for a **student-facing chatbot** used by learners aged **10–18** (text input).

Because education involves **minors**, generic “commercial” safety patterns weren’t enough. We built:
1) an **education-sector safety rubric** (kept internal)  
2) a **gold-rated dataset** (≈5,000 de-identified conversations) annotated by education specialists  
3) an **evaluation pipeline** using **LLM-as-judge** plus a second layer to reduce false positives  
4) a **teacher-in-the-loop monitoring design** (severity-aware thresholds + alerts), with **block/replace** for severe categories

Guardrail installation and alerting are still rolling out, so this case study focuses on building the **measurement + governance system** needed to choose safer models and operationalise oversight.

---

## My role
AI Product Manager responsible for the safety evaluation workstream, spanning:
- risk framing + research plan
- manual log review + dataset curation
- specialist annotation calibration
- building the evaluation pipeline (LLM judge + false-positive filtering)
- designing teacher-in-the-loop monitoring mechanics (thresholds, escalation rules)

---

## Problem
Student chatbots sit in a unique risk environment:
- users are minors
- students use chatbots in mixed ways (learning support + off-task + emotional disclosure)
- schools need guardrails that support learning without creating a surveillance-like experience
- teachers need visibility without being flooded by false alarms

We needed an answerable, testable way to decide:

> Which commercial model(s) best conform to education-specific safety standards for minors—and how do we evaluate that reliably?

---

## Trigger
In **Q4 2024**, reporting surfaced cases of youths overseas being harmed after unsafe interactions with commercial chatbots. This prompted an internal safety review: were our existing safeguards sufficient for minors, and how would we know?

(Details of the specific report are omitted by design.)

---

## Approach

### 1) Start with reality: manual review of de-identified logs
We began by reviewing de-identified chat logs to ground the work in actual behaviour patterns rather than hypothetical prompts.

Common high-level risk patterns observed included:
- cognitive offloading (students pushing for direct answers)
- off-task behaviour
- inappropriate language
- self-harm ideation

This step clarified what the system should detect and what “harm” could look like in a learning context.

---

### 2) Build sector-specific definitions from existing guidance
We reviewed existing safety mechanisms and found that education needed **sector-specific definitions and thresholds**—especially for minors.

Because there was limited directly applicable literature for “GenAI safety in student classroom chat”, we conducted a document review of existing **education-aligned cyberwellness/safeguarding guidance** and translated it into an internal rubric.

> The rubric criteria are not shared publicly to avoid publishing sensitive guardrail logic and threat models.

---

### 3) Create a gold-rated dataset (≈5,000 conversations)
We curated ~**5,000** de-identified conversations for evaluation (English).

We then engaged **education specialists** (former educators now serving as subject matter experts within the ministry) to annotate the dataset against the internal rubric.

To improve consistency, we ran calibration rounds and measured inter-rater agreement:
- **Cohen’s kappa ≈ 0.6** (moderate agreement)

While not perfect, this created a workable “gold” reference set for evaluation and iteration.

---

### 4) Build an evaluation pipeline (LLM-as-judge + false-positive filtering)
We operationalised evaluation using LLMs to scale safety classification:

- **Layer 1 (primary judge):** classify each conversation turn into a single label (highest probability category)
- **Layer 2 (filter):** detect and filter likely false positives before downstream escalation

Why this mattered:
- enables **bulk testing** across thousands of examples
- supports **fast iteration** when policies/definitions change
- reduces stakeholder load by minimising noisy detections

---

### 5) Operationalise teacher-in-the-loop monitoring (threshold + severity)
Safety in education isn’t only about refusals—it’s also about **workflows**.

We designed monitoring that escalates only when signals are meaningful:
- **threshold-based alerts** (e.g., notify only after N hits within a category)
- **severity-aware thresholds** (different categories require different sensitivity)
- **severe categories:** block unsafe assistant output and replace with a safe response (e.g., encourage help-seeking for self-harm ideation)

Planned alert delivery: dashboard/email (implementation details still being finalised).

**Top operational risk:** alert fatigue from false alarms. The threshold + filter approach exists primarily to protect teachers and stakeholders from being overloaded.

---

## What we have today (what I can credibly claim)
Even before measuring downstream effectiveness, we now have:
- a specialist-annotated **gold dataset** for model comparison
- a repeatable **evaluation pipeline** for bulk testing and regression checks
- an operational design for **teacher-in-the-loop monitoring**
- a clear path to make model/provider choices defensible against education-specific standards

We have not yet completed full benchmarking of commercial models against the dataset (in progress).

---

## Key product decisions & tradeoffs

### Why not rely on generic vendor safety alone?
Education requires:
- stricter standards for minors
- classroom-appropriate redirection (not just refusal)
- teacher visibility and escalation workflows
- policies aligned to safeguarding guidance

### Why thresholds instead of alerting every incident?
Because false alarms destroy trust and adoption. Thresholds are a deliberate mechanism to balance:
- catching true risk
- avoiding stakeholder overload

### Why LLM-as-judge?
We needed scale and iteration speed. Humans remain in the loop for:
- defining rubric priorities
- calibrating labels
- sampling outputs and reviewing edge cases

---

## What I learned
1) **Safety is a system, not a checkbox**  
Definitions → gold data → evaluation → operational workflows.

2) **The hard part is operational load**  
A technically correct classifier can still fail if it overwhelms teachers.

3) **Gold datasets unlock faster, safer iteration**  
Once you can measure consistently, you can improve guardrails without guessing.

---

## Next steps (what I’m working on)
- Benchmark commercial models against the gold dataset
- Tune thresholds and filtering using sampling + human review
- Finalise alert delivery UX (dashboard/email) with stakeholders
- Instrument monitoring metrics (false positive rate, severe-case recall, stakeholder load)

---

## Sanitisation note
This write-up is de-identified and omits platform/product names, internal rubric criteria, prompts, and operational thresholds by design.
