# Finding format

Use the same source notation as the Claude extraction lane:

- One turn: `P4, msg 145`
- Consecutive turns: `P4, msgs 514–521`
- Kernel text: `Kernel V4 §H`
- If a finding draws from more than one source, list each source in the same `Source` field.

Every finding begins with its conclusion, then states exactly where it came from. Do not infer a speaker, relationship, or mechanism that the cited turns do not establish.

```markdown
## Short finding title

**Source:** P4, msg 145  
**Speaker:** Brenda / ChatGPT / Codex / Claude, if material  
**Status:** 🟢 corroborated · 🟡 modal/candidate · 🟠 overreach found · 🔴 disconfirmed/withdrawn, where applicable

Finding and a brief, faithful explanation.

**Why it belongs here:** category-specific rationale.
```
