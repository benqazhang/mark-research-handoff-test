# Native ChatGPT write-back and resume — Phase 1 only

Three independent states: (1) upstream dataset sequence/marker, (2) successfully processed ChatGPT receipt, (3) explicit Mark cognitive decision. Neither a Git commit nor a processing receipt implies a cognitive decision.

## Exact first prompt — send to the connected ChatGPT session

In repository `benqazhang/mark-research-handoff-test`, perform the authorized Phase 1 operational write-back test using your native GitHub tools. This authorization is only for one new operational receipt, never a cognitive update.

1. Resolve the current `main` head through the GitHub connection. Record its full SHA as S. Read `handoff/manifest.json`, `handoff/validation/native-receipt.schema.json` and batches 1–3 at S. Confirm dataset `mark-handoff-c3852d063983`, sequence 3, marker `MARK-P01-48e523fc030a:B3`, contiguous previous markers and unique event IDs. Report the events processed through B3. Do not use a cached older SHA as current main. If latest sequence is not 3, stop and report the actual state.
2. Record the Git tree/blob identity of `data/cognition/` at S. Check that `handoff/receipts/chatgpt_native/writeback-b3-01.json` does not exist. If it exists, read it and report that this CREATE test has already run; do not overwrite it or create another receipt.
3. Create exactly ONE new file, `handoff/receipts/chatgpt_native/writeback-b3-01.json`, on main, conforming to the schema, with these fields: schema_version=1; consumer="chatgpt_native"; dataset_id="mark-handoff-c3852d063983"; processed_through_sequence=3; processed_through_marker="MARK-P01-48e523fc030a:B3"; observed_commit_sha=S; validation_type="native_chatgpt_writeback"; artifact_role="operational_validation_only"; cognition_modified=false; created_at=the actual current UTC timestamp. Do not fabricate time or successful processing. Commit message: `Record native ChatGPT B3 operational receipt`.
4. Use a write operation whose base is S, or construct a commit with parent S and update main without force. If the tool cannot safely create only this file, stop and report the limitation. If main has advanced or the result is ambiguous, re-read head and receipt; do not force-push, overwrite, or blindly repeat the write.
5. Do NOT modify data/cognition/, interpretations, evidence, sources, theses, existing batches, manifest, checkpoint files, or any other file. Do not create a proposal or imply Mark approved one.
6. Read the new receipt back from GitHub pinned to the resulting commit W. Compare its exact values with the intended receipt. Inspect the S→W commit diff: exactly one added file at the receipt path, no other changes, and unchanged cognition tree/blob identity. Confirm the manifest still says B3. If you cannot inspect any of these facts, report that check as unverified.
7. Return S, W, the receipt path and content, changed-file list, read-after-write result, cognition-isolation result, and upstream cursor B3. Distinguish successful native tool execution from merely available tools. Stop; do not publish B4.

## B4 publication gate — Codex procedure, NOT executed yet

Wait for actual native write result. Fetch latest public main, inspect the receipt schema, native execution result, parent/observed SHA, exact one-file commit diff, receipt read-back and unchanged cognition. A self-asserted receipt alone is insufficient.

Only after verification, start from the latest public commit (preserving the new receipt). Do not run a whole-repository export over native artifacts.

1. Confirm current manifest still B3 and receipt processes through B3. Verify existing dataset before editing.
2. Copy `handoff/validation/B4.template.json` to `handoff/changes/0004.json`; replace only created_at with actual publication UTC. Template is not a live batch. It references previous B3 and contains one unique validation_ping.
3. Add the existing `handoff/validation/resume-event.json` to manifest.files with SHA-256 and byte length. Add batch 4 to manifest.batches with its actual SHA-256. Set latest_sequence=4, latest_marker=B4 and generated_at to publication time. Preserve all existing file and batch entries.
4. Validate hashes, contiguous chain, unique events and unchanged cognition. Commit only new batch and manifest, push without force. Record B4 publication SHA. Stop on concurrent modification and reconcile before retry.
5. Ask Mark to run the resume prompt below. No collectors, model logic or cognitive write is involved.

## Exact resume prompt — send only AFTER verified B4 publication

Using the native GitHub connection to `benqazhang/mark-research-handoff-test`, resolve current main and pin its SHA. Read `handoff/receipts/chatgpt_native/writeback-b3-01.json` as the selected processing cursor for this acceptance run, and read the current manifest. Verify matching dataset IDs. The receipt must process through sequence 3 / MARK-P01-48e523fc030a:B3; the manifest must now be sequence 4 / MARK-P01-48e523fc030a:B4. If either differs, report the discrepancy and stop.

Read only upstream batches with sequence greater than the receipt cursor. B4 must be the sole unprocessed batch, with previous_marker B3 and event ID MARK-P01-48e523fc030a:resume-native:04. Read its harmless referenced event. Do not reprocess B1–B3. Do not count the receipt commit or preparation/documentation commits as research batches. Report pinned commit, starting cursor, selected batch list, new event IDs and resulting in-memory cursor B4. Do not write any file or modify cognition. Explicitly distinguish in-memory processing through B4 from the persisted B3 receipt; a second invocation still uses B3 unless a later separately authorized receipt persists B4.

## Acceptance limits

This test proves native operational write-back/read-back and resume selection if it succeeds. It does not prove cognitive write authorization, automatic scheduling, unattended invocation, or durable B4 acknowledgement. B4 is withheld until native receipt creation is verified. No native receipt or native checkpoint is fabricated during preparation.
