# MurderbotV2 — Machine-readable archive

Start with **MurderbotV2-conversation.md** to read the saved active conversation: 39 entries covering user messages, assistant replies, progress messages, and any generated images, with speakers, UTC timestamps, formatting, and emojis. **MurderbotV2-conversation.json** pairs the readable view with exact original source text and complete content objects.

Use **MurderbotV2-original-source.json** for complete archival processing. It preserves the exact captured bytes and every returned field, including 143 graph nodes, 142 message records, alternate branches, tool records, original content types, timestamps, and metadata. This is the preservation master.

**MurderbotV2-all-records.jsonl** contains one complete graph node per line. The **records/** directory contains the same nodes in 3 smaller files without splitting nodes. **MurderbotV2-record-index.json** lists chunks and the active branch in conversation order. Source file order is not conversation order.

**MurderbotV2-conversation-metadata.json** retains every top-level field except mapping. Combining it with the JSONL nodes keyed by id reconstructs the entire original JSON object. This round-trip was verified. Keep the original JSON for exact byte fidelity.

**MurderbotV2-all-content.md** retains every original message content object as an additional reading aid. Full metadata remains in the original JSON and JSONL files.

**readable-parts/** contains the same active conversation split at message boundaries for smaller uploads. Read in numbered order; **MurderbotV2-reading-index.json** records every message ID in each part. Relative artifact links in these parts resolve against the archive root.

**artifacts/** contains written blocks and embedded visuals recovered from the source. Equations appear as images in the PDF, while their complete original TeX remains in the conversation files and equations/index.json. Recovered images preserve unmodified bytes served by ChatGPT; this does not establish byte identity with an original upload that ChatGPT may have re-encoded. File links and attachment metadata do not themselves include external file bytes; consult artifact-index.json and file-reference-index.json for recovered items and references.

The source snapshot ends at node **861031b7-6534-4c0f-b7f6-ca764b74ace9**, and the last readable message is **861031b7-6534-4c0f-b7f6-ca764b74ace9**. Later live changes and data not returned by ChatGPT are outside this snapshot. Readable Markdown is not the full metadata archive.

**MurderbotV2-machine-verification.json** records source, graph, field, ordering, timestamp, and reconstruction checks. **SHA256SUMS.json** records checksums for every other package file.
