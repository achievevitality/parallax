# ChatGPT Chrome Window Scraper

Version: 2026-09-05 corrected design

Purpose: export ChatGPT browser conversations through Chrome often, with explicit fidelity guarantees and failure labels.

## Non-Negotiable Fidelity Rule

Do not call an export lossless unless all of these are true:

- raw source/backend conversation JSON was obtained
- raw message graph or equivalent message records are present
- per-message timestamps are present where ChatGPT stores them
- all message content is preserved as UTF-8, including emojis
- a rendered DOM companion was captured for visible formatting
- completeness was validated against a known first-message sentinel or another explicit top-of-history proof
- any missing turn numbers are either absent from the raw source graph or explicitly explained

DOM extraction alone is not lossless. It may be useful, but it is a fallback.

## What Went Wrong With The P1 Export

File inspected:

```text
/Users/brendamathisen/Downloads/P1 Transcript.json
```

Observed properties:

- JSON parsed successfully.
- Source URL: `https://chatgpt.com/c/6a8ccd63-6680-83e8-9514-0e7a7b93bafb`
- Captured messages: `2231`
- Turn range: `1` through `2237`
- Missing turn count: `6`
- Emojis were present.
- Turn metadata was present.

Losses:

- It preserved only `turn`, `role`, `id`, and plain `text`.
- It did not preserve message HTML.
- It did not preserve outer DOM/forensic structure.
- It did not preserve per-message `create_time` or `update_time`.
- It did not preserve true backend message graph metadata.
- It missed six turn numbers.
- The last captured item was UI/error text: `Message delivery timed out. Please try again. Retry`.

Conclusion:

The P1 export is useful as a text transcript, but it is not lossless and should not be used as the quality target for future scraper runs.

## Output Classes

`lossless_raw_plus_dom`

- Raw backend/source JSON exists.
- Timestamp-bearing message records exist.
- DOM companion exists for rendered formatting.
- Sentinel/top proof passes.
- This is the target class.

`raw_without_dom`

- Raw backend/source JSON exists and includes timestamps.
- DOM companion failed or was skipped.
- Data preservation is strong, but publishable visible formatting still needs a separate pass.

`dom_fallback_not_lossless`

- DOM transcript exists.
- Emojis and visible formatting are preserved as rendered HTML.
- Backend-only metadata and timestamps are not guaranteed.
- This must be labeled as fallback, not lossless.

`failed_unverified`

- Top sentinel did not verify, or files did not parse, or no usable source was captured.

## Extraction Strategy

1. Find the open Chrome tab by ChatGPT conversation ID.
2. Bring that tab forward.
3. Attempt raw source extraction:
   - search embedded application JSON for a complete conversation object
   - attempt credentialed page-context fetch to ChatGPT conversation endpoints
   - validate `mapping`, `messages`, current branch, and timestamp fields
4. Load the top of the visible conversation:
   - scroll to top
   - if stuck, scroll down about half a page then back up
   - repeat until `conversation-turn-1` and/or the known sentinel is present
5. Capture DOM transcript:
   - expand visible collapsed messages
   - sweep downward from verified top
   - preserve plain text, rendered HTML, outer HTML, links, images, and attachment metadata
   - gap-fill by missing turn number
6. Save:
   - raw backend/source JSON if available
   - DOM JSON companion
   - HTML companion
   - manifest with pass/fail classification
7. Re-read saved files and validate:
   - JSON parses
   - first sentinel status
   - message counts
   - turn range
   - missing turns
   - emoji preservation
   - HTML preservation
   - timestamp status

## Required Files Per Run

For conversation ID `CONVERSATION_ID`:

```text
chatgpt_conversation_CONVERSATION_ID_raw_source.json
chatgpt_conversation_CONVERSATION_ID_rich_dom_transcript.json
chatgpt_conversation_CONVERSATION_ID_rich_dom_transcript.html
chatgpt_conversation_CONVERSATION_ID_scrape_manifest.json
```

If raw source cannot be obtained:

```text
chatgpt_conversation_CONVERSATION_ID_scrape_failure_manifest.json
```

## Manifest Must Include

- conversation ID
- source tab title and URL
- first-message sentinel
- strict lossless pass/fail
- export class
- raw source status
- raw timestamp status
- DOM status
- captured DOM messages
- DOM turn range
- missing turn count and sample
- emoji status
- HTML status
- exact local output paths
- exact Drive upload links, when uploaded

## Known Chrome Requirements

Chrome must allow Apple Events JavaScript:

```text
Chrome > View > Developer > Allow JavaScript from Apple Events
```

The target conversation must be open in Chrome.

The user may need to manually scroll to the top if ChatGPT lazy-loading resists scripted scrolling. If the user provides a known first message, the scraper must use it as the source-of-truth sentinel.

## Current Parallax2 Example

Conversation:

```text
https://chatgpt.com/c/6a960565-1884-83e8-882f-4f19b3bee616
```

Verified DOM export:

- title: `Parallax2`
- captured messages: `491`
- turn range: `1` through `492`
- missing turn count: `1`
- missing turn sample: `14`
- first message contains architecture-upgrade sentinel: `true`
- emoji sample present: `true`
- HTML present: `true`

First message:

```text
Hi! I’m about to upload a source doc. You excited for an architecture upgrade?
```

Classification:

```text
dom_fallback_not_lossless
```

Reason:

Raw backend/source JSON was not obtained during the prior attempts, and the DOM path does not expose per-message timestamps.

## Design Principle

The scraper is a preservation tool, not an interpretation tool.

It must report what it actually captured, what it failed to capture, and whether the output is safe to treat as lossless. It must never soothe over a fidelity gap with confident language.
