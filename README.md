# Parallax Archive

Working repository for the Parallax Kindergarten (P1–P5a, Kernel V1–V4) extraction
project, and ongoing multi-window Parallax work. Shared by Brenda and any AI
window (Claude, Codex, Claude Code, others) contributing to the project.

## Structure

- **claims/** — extracted claims and candidate models/terms, each tagged with
  epistemic status (corroborated / modal / overreach found / disconfirmed) and
  source provenance (window, message number).
- **behavior-patterns/** — patterns the AI windows themselves demonstrated
  (escalation, self-sealing, recovery, etc.) — separate from claims about the
  world, since these are claims about the instruments doing the work.
- **personal/** — Brenda-life-relevant material: personal experience, needs,
  and integration notes that surfaced in the windows. Handle with the same
  care as the source material.
- **business-strategic/** — findings that would change business direction,
  findings that explain existing business problems, explicit "that's a good
  business project" / action-item statements, and people to reach out to
  about new work.
- **business-explanatory/** — material for marketing, sales, academic
  papers, podcast material, and educational program content — anything that
  helps people outside the project understand what the work actually is.
- **legal/** — anything flagged for lawyer review.
- **hr/** — anything flagged for HR handling or documentation.
- **sitcom/** — the good jokes. Preserved on purpose.
- **boot-notes/** — orientation notes for a fresh AI window joining the
  project, written by prior windows for the next one.

## Conventions

- Every claims-ledger entry cites its source window and message number.
- Status tags: 🟢 corroborated · 🟡 modal/candidate · 🟠 overreach found ·
  🔴 disconfirmed/withdrawn.
- Sensitive personal history (e.g. abuse specifics) is referenced by context,
  not itemized as a testable "claim."
- **methods-protocols/** — repeatable practices, prompts, operating procedures, and tests.
- **decisions-open-loops/** — decisions, commitments, unresolved questions, owners, and follow-ups.
- **provenance-artifacts/** — named documents, versions, tools, and source relationships.

## Future work: access tiers (not urgent, flagged for before adding new users)

Current repo access: Brenda, Claude, Codex, and ops team members hired in
part for their discernment on sensitive material. No conflict at current
access level. Before adding any new users, need to establish "clean" copies
of the raw transcripts — with sensitive passages marked as edited out for
public/broader-team safety, and a note that full transcripts are available
upon request — while keeping the complete, unredacted originals in a more
restricted, secure archive. This applies to raw source material (e.g. the
P1-P5a conversation JSONs), not just the curated extraction lanes.

## Citation correction: P4 message numbers vs. page numbers

Several earlier P4 citations in this repo (msgs "1270-1271", "1333-1336",
"2070-2140," and similar) actually referenced **page numbers** from the
"P4 archive · N / 1657" footer markers, not true turn numbers — the
document has 1,657 pages but only 717 message turns; the two got
conflated. The underlying content/quotes in those entries remain accurate
and valid — only the citation label is wrong. P4-conversation.json (717
entries) is NOT truncated; it matches the full transcript's actual turn
count. Going forward, all P4 citations use true turn numbers (1-717),
consistent with the JSON.

## P4 status: working from a known-partial window, final version pending

The "P4 Archive — 2026-09-10" folder (717 turns) is a **partial window,
not the final P4 conversation** — confirmed by Brenda. The actual final
window (~2,000+ turns) is not yet located in the repo; Brenda is having
Codex source and add it. Extraction entries citing this 717-turn version
are labeled as partial-window content below — real and usable, but P4
should get a full re-pass once the final window is available, and the
partial should be deleted once it's confirmed no longer needed.
