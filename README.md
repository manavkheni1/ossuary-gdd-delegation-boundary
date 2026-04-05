# The Delegation Boundary: Using LLMs to Author Game Design Documents

**CSYE 7270 — Virtual Environments and Real-Time 3D | Take-Home Midterm**
**Category A — AI Ideation: Design & Code Generation**

---

## Topic Claim

> "After reading this piece, a practitioner will understand using LLMs to generate and critique Game Design Documents well enough to decide which sections of a GDD to delegate to AI vs. protect from it — without making the mistake of treating LLM-generated GDD content as design authority, producing documents that are internally consistent but mechanically unplayable."

---

## What This Repository Contains

| File | Description |
|---|---|
| `ossuary_gdd_demo.ipynb` | Jupyter Notebook — full demo implementation |
| `essay.pdf` | The technical essay (5-section structure) |
| `authors_note.pdf` | 3-page Author's Note (Design Choices, Tool Usage, Self-Assessment) |

---

## How to Run the Demo

### Requirements
```
pip install openai
```

### Setup
1. Clone this repository
2. Open `ossuary_gdd_demo.ipynb` in Jupyter or VS Code
3. Set your OpenAI API key as an environment variable:
   - Mac/Linux: `export OPENAI_API_KEY="your-key-here"`
   - Windows: `set OPENAI_API_KEY="your-key-here"`
   - Or paste your key directly into Cell 1 locally — never commit it to GitHub
4. Run all cells top to bottom

### What You Will See
- **Cell 3 — Call 1:** Underspecified prompt → genre-default accumulation economy (the wrong game)
- **Cell 4 — Call 2:** Constrained prompt → scarcity attempt with shop mechanic back door
- **Cell 5 — Human Decision Node:** Shop mechanic identified and removed — documented with exact AI output and architectural reasoning
- **Cell 6 — Failure Trigger:** Bone-starvation stress test — the model fails to resolve its own tail case
- **Cell 7 — Comparison Table:** Side-by-side summary of what changed across all three calls

---

## The Failure Case (Reproducible in Under 5 Minutes)

Run Cell 6 after Cell 4. The stress test asks the model one question its own economy cannot answer:

> *What happens on floor four if the player has broken every long-bone and no replacements have dropped?*

The model will either fail to resolve the scenario using its own rules, or invent a mechanic (shop, respawn, fallback item) that directly contradicts the economy it just described. Both outcomes demonstrate the delegation boundary the essay argues for.

---

## The Human Decision Node

Located in **Cell 5** of the notebook:

```python
# ============================================
# MANDATORY HUMAN DECISION NODE
#
# AI proposed: A "bone shop" at floor intervals where
#   players trade 3 identical bones for a permanent
#   stat upgrade — present in both Call 1 and Call 2.
#
# I rejected/modified because: A shop reintroduces
#   accumulation logic through the back door. If spare
#   bones can be traded, players will hoard rather than
#   sacrifice — collapsing the scarcity mechanic entirely.
#   The model defaulted to the genre norm even inside a
#   constrained prompt.
#
# My decision: Remove all shop/trade mechanics. Bones
#   are strictly found via enemy drops only. Scarcity
#   is enforced by the drop system alone.
# ============================================
```

---

## The Master Claim

> *AI is a pipeline decision, not a magic layer. Where you put it — and how you constrain it — determines what your game becomes.*

This repository is a demonstrable instance of that claim. The same model, given the same task, produces either a correct or incorrect GDD section depending entirely on where the designer draws the delegation boundary. The model is not the variable. The pipeline decision is.

---

## Tools Used

- **Bookie the Bookmaker** — essay drafting
- **Eddy the Editor** — editorial audit (3 passes, all 5 standards passed)
- **Figure Architect** — diagram generation (3 figures)
- **OpenAI GPT-4o** — demo implementation

---

## Course
CSYE 7270 — Virtual Environments and Real-Time 3D
Northeastern University
