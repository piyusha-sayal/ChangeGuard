# ChangeGuard

**Project Recovery Control Tower**, built for the Microsoft Agent-a-thon Level 2.

A project manager reports a slipping milestone in plain language. A Microsoft Copilot Studio agent reads
the real project baseline, calculates the working-day impact, compares documented recovery options and
saves a change request. A human reviewer approves or rejects it in a Power Apps review app, and only then
can the approved recovery plan be executed, once, with every step written to an audit trail in Dataverse.

**The agent talks, the flows decide, a person approves.**

## Contents

| File | What it is |
|---|---|
| `ChangeGuard_Deck.pptx` | Presentation deck |
| `ChangeGuard_Technical_Submission.pdf` | Detailed technical document |
| `evidence/` | Screenshots, flow run records, conversation transcripts and reports from the live environment |

Start with `evidence/README.md` for the step-by-step journey and where each step is proven.

## Built with

Microsoft Copilot Studio (agent with seven flow tools), Power Automate (ten flows), Power Apps
(model-driven review app) and Dataverse (eleven tables). All data in the demonstration is synthetic.
