# Scenario C — NBH Governance Document Engine

System prompt engineering for NBH's institutional document drafting system
(System 6). Converts bullet-point staff input into first-draft governance
documents at NBH's institutional publishing standard.

---

## File Index

| File | Contents |
|------|----------|
| `NBH_Scenario_C_System_Prompt.md` | Full system prompt · Role Mandate sample run · Design rationale |

The system prompt, sample run, and rationale are consolidated in one file for
ease of assessment review. Sections are clearly delineated.

---

## What the Prompt Does

- Accepts: Document Type, Subject, Source Bullets, and optional Reference /
  Classification / Date fields.
- Produces: a first-draft Role Mandate or Board Note in NBH's institutional
  format, with every fact traceable to a specific source bullet.
- Refuses: to invent facts, figures, names, or dates not present in the
  source bullets — missing fields become `[NOT SPECIFIED IN INPUT — CONFIRM
  BEFORE ISSUE]` placeholders, never plausible guesses.

---

## Sample Run 2 — Board Note

The primary sample run (Role Mandate) is in `NBH_Scenario_C_System_Prompt.md`.
Below is a second sample demonstrating the Board Note structure.

**Input:**

```
Document Type: BOARD NOTE
Subject: Q2 2026 Subsidiary Performance — Energy Division
Document Reference: NBH-BN-2026-Q2-001
Classification: BOARD CONFIDENTIAL
Date: June 2026
From: Head of AI & Digital Systems

Source Bullets:
1. Energy Division revenue for Q2 2026 was NGN 1.4 billion, up 12% on Q1 2026.
2. Three operational sites achieved full SLA compliance in Q2; one site
   (Abuja North) missed the 99.5% uptime target, recording 97.1%.
3. The Board approved a capital expenditure of NGN 200 million for grid
   infrastructure at Abuja North in March 2026; procurement has not yet
   commenced as at June 2026.
4. Management recommends the Board note the procurement delay and request a
   revised timeline from the Energy Division GM by 15 July 2026.
```

**Output:**

```
NORTHBRIDGE HOLDINGS — BOARD NOTE
To: The Board
From: Head of AI & Digital Systems
Subject: Q2 2026 Subsidiary Performance — Energy Division
Date: June 2026
Classification: BOARD CONFIDENTIAL

1. Context
Energy Division Q2 2026 performance shows revenue growth of 12% against Q1
2026, with three of four operational sites achieving full SLA compliance.

2. Key Points
– Energy Division revenue for Q2 2026 was NGN 1.4 billion, representing a
  12% increase on Q1 2026.
– Three operational sites achieved full SLA compliance in Q2 2026.
– Abuja North missed the 99.5% uptime target, recording 97.1% for the quarter.
– Capital expenditure of NGN 200 million approved by the Board in March 2026
  for grid infrastructure at Abuja North has not commenced procurement as at
  June 2026.

3. Implications for the Board
The procurement delay at Abuja North presents a risk to the site's ability to
meet the 99.5% uptime target in Q3 2026.

4. Recommended Action
We recommend the Board note the procurement delay and request a revised
timeline from the Energy Division General Manager by 15 July 2026.

Northbridge Holdings NBH-BN-2026-Q2-001 | BOARD CONFIDENTIAL June 2026
```

---

## Design Decisions

The primary rationale is in `NBH_Scenario_C_System_Prompt.md` (Section 3).

The second most important decision is the word-count constraint for Board
Notes (120–250 words). A Board Note exists to reduce reading burden, not to
demonstrate thoroughness — the prompt enforces this as a hard target rather
than a soft guideline, because a verbose Board Note is a defect of the same
kind as a hallucinated fact: it fails the document's institutional purpose.

---

## NDPR Note

If source bullets contain personal data (PM names, performance records,
identity numbers), the system prompt instructs the model to append a closing
note — outside the document body — flagging NDPR-sensitive content for review
before the draft is circulated. The document body itself contains only what
the source bullets explicitly provide.
