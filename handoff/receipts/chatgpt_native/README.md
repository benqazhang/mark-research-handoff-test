# Native operational receipts

Only actual native ChatGPT write operations create receipts here. No receipt has been pre-created by Codex. Schema: ../../validation/native-receipt.schema.json.

First test filename: `writeback-b3-01.json`. CREATE only. Never overwrite an existing receipt; after an ambiguous write result, read this path first and report the existing commit instead of retrying a write blindly.

These are operational validation artifacts, not cognitive decisions or upstream research batches. `cognition_modified: false` is a claim to verify against the Git diff, not authentication. Verify native execution via Mark's actual ChatGPT result and GitHub commit/read-back evidence. Creating a JSON file with consumer=chatgpt_native alone does not prove native execution.

The valid, verified B3 receipt is the resume cursor for this acceptance run. Do not update the legacy handoff/checkpoints/chatgpt_native.json during this test. These two artifacts must not be combined by taking a blind maximum. This run explicitly selects writeback-b3-01.json; the legacy zero checkpoint remains an unused historical fixture.
