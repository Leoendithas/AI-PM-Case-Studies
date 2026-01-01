# Learning Outcomes Over Adoption: Why We Didn’t Ship an Always-On AI Facilitator 🤖

## TL;DR
We explored an **always-on, text-based AI facilitator** for small-group student discussions.  
Signals of desirability were strong (teachers were keen to try it), but **we found no clear evidence of learning gains** and observed **meaningful downside risk** (disrupted discussion flow, distraction/frustration). The biggest product constraint: the facilitator **had to speak every 5–6 messages**—staying quiet wasn’t an option—making it inherently intrusive.

**Decision:** delay shipping “always-on facilitation”, and pivot our exploration toward **less intrusive or more natural modalities** (e.g., on-demand assistance and, longer-term, voice).
---

## Context
Small-group discussion is a high-leverage learning activity—but hard to facilitate:
- uneven participation
- shallow exchange
- off-task behaviour
- limited teacher bandwidth to monitor multiple groups

Hypothesis: An AI facilitator could improve discussion quality by prompting, summarising, nudging participation, and keeping students on-task.

---

## My role
I designed and built the **prototype end-to-end** and led the **go/no-go research**:
- set success measures
- ran teacher + student research loops
- synthesised evidence
- recommended a delay/pivot to the Product Owner

(Research + prototype were executed as a lean, single-builder effort.)

---

## What we tested (feature scope)
**Always-on facilitator in a text chat**, running this loop:
- analyse chat log every **~5–6 messages**
- respond into the group chat with guidance

### Key constraint / chokepoint
The AI needed to speak periodically by design.  
**Staying quiet wasn’t an option**, so it would often intervene even when students were already doing fine.

Additional structural friction:
- The experience was **text-based**, while real classroom discussions are typically **face-to-face and voice-driven**.
- **Latency** made interruptions worse: delayed “help” can land at the wrong moment and still disrupt flow.

This research was intended to validate a critical hypothesis:
> If we cannot show visible learning gains—and risk hindering discussion—we should not proceed with always-on facilitation.

---

## Prototype used for testing
This hypothesis was evaluated using a lightweight Streamlit prototype that simulates a shared group chat with periodic AI interventions.

- Repo: https://github.com/Leoendithas/AIchat  
- Notes: Prototype for user testing (not production-ready). Production prompts and internal evaluation assets are not included.

<img width="792" height="870" alt="image" src="https://github.com/user-attachments/assets/f9c5a506-71a3-4241-be6e-a8bca7d2ebaf" />

---

## Success criteria (pre-committed)
We defined success across three dimensions:

### 1) Teacher willingness (desirability)
Target: ≥60% of respondents show moderate/high interest.

### 2) Effectiveness (discussion quality)
Target: measurable improvement in engagement or depth (chatlog analysis + interviews).

### 3) Adoption indicators
Signal: evidence that teachers already adopt adjacent AI tools in real workflows.

---

## Research design (layered evidence)
We triangulated:

### A) Adjacent feature usage (behavioural signal)
We reviewed usage logs of a related 1:1 assistant feature:
- ~**60.7k API calls** over **~1.5 months**
- conservative estimate suggests **dozens of classes** adopting the feature

**Interpretation:** Teachers are willing to incorporate AI into student workflows.

### B) Teacher poll (innovators/early adopters)
~**55** teacher respondents, multi-select roles for an AI facilitator:
- only **1** respondent selected “I wouldn’t use this”
- most teachers wanted AI to play **multiple roles** (not just one)

**Interpretation:** High desirability among early adopters.

### C) Student prototype testing (effectiveness + risk)
We tested with **6 student groups** (3–4 students each), across levels.
Structure:
1) discussion without AI
2) discussion with AI interventions
3) student interviews
4) independent chatlog review by 3 colleagues

---

## Findings

### 1) Students prefer interventions that are easy to read
- short prompts were more likely to be read
- long-form “summary + question” was often ignored (especially for younger students)

**Product implication:** if we ever intervene, it must be minimal and readable.

---

### 2) Students value AI for a narrow set of “help moves”
Students described usefulness in:
- staying on-task
- triggering thinking / idea generation
- nudging engagement

Less enthusiasm for:
- timekeeping
- “remember to summarise” reminders

**Product implication:** limit facilitation to high-signal moves.

---

### 3) Repetition quickly becomes noise
Repeated or near-repeated questions reduced engagement and trust in the facilitator.

**Product implication:** always-on facilitation requires better state tracking and variation—or it becomes spam.

---

### 4) Intrusive timing disrupts discussion flow
Students wanted help **only when stuck**.  
Always-on prompts arriving at random moments:
- interrupted momentum
- were ignored
- sometimes caused frustration

**Product implication:** timing matters more than prompt quality; “intervention when not needed” is a feature-level failure mode.

---

### 5) Learning impact was weak (correlational at best)
Across 6 chats:
- average **~0.76 new ideas per AI prompt**
- students frequently ignored multiple prompts
- the evidence for broadening/deepening was not consistent

**Interpretation:** we did not meet the effectiveness bar for shipping.

---

### 6) Downside risk is real: distraction & frustration
In **2 of 6** groups we observed negative effects:
- distraction: students tried to “poke” the AI and went off-task
- frustration: students expressed irritation (including vulgarities) when AI spoke

**Interpretation:** in group settings with minors, intrusive AI can amplify off-task behaviours and degrade norms.

---

## Decision & rationale
### Decision: **Delay** always-on text facilitation
Even with strong desirability signals, the product did not show reliable learning gains and introduced disruption risk. In a learning context, **adoption alone isn’t success**.

### Rationale (PM logic)
- Teachers were keen to try it → **desirability is necessary but not sufficient**
- Student experience showed:
  - weak impact signals
  - meaningful negative externalities
- The design constraint (“AI must speak every 5–6 messages”) made the product inherently intrusive.
- Text-based facilitation mismatched the real-world modality of discussions (voice / in-person).

---

## What we did instead (next steps / pivot)
1) **Prototype pivot (current): Lumina**
A classroom small-group facilitator concept that can iterate toward:
- better “when to intervene” logic
- less intrusive UX patterns
- potential modality shift beyond text

2) **Strategic direction (longer-term): voice-first facilitation**
Given classroom reality, a voice-oriented approach may better fit:
- natural turn-taking
- timing
- reduced “chat spam” effect

---

## What I learned
1) **Learning outcomes over adoption**
High willingness to try does not imply positive learning impact.

2) **In group discussions, interruption cost is the tax**
Any extra message competes with peer dialogue.

3) **Always-on behaviour creates unavoidable harm modes**
If “silence” isn’t a valid action, you will interrupt productive flow.

4) **Modality matters**
Text prototypes are convenient, but may under-represent the real environment (voice, face-to-face).

---

## If I revisited the problem
Before building an always-on facilitator again, I would require:
- a clear operational definition of “discussion quality” and “learning gain” proxies
- a mechanism for detecting “stuckness” or user-invoked help
- multi-judge evaluation + human-in-the-loop sampling
- a safety evaluation plan for minors (content + behavioural disruption risks)
- early exploration of voice or hybrid modalities

---

## Sanitisation note
This write-up uses de-identified and aggregated results, and omits internal system prompts, platform identifiers, and school names.
