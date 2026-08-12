# Praxis Threads

Private, reviewable exports of real Praxis conversations.

Each thread is written once under `threads/YYYY/MM/<thread-id>.json`. `index.json`
is the web-facing catalog. Both files use the schemas in `schema/`.

## Privacy boundary

The exporter includes user and assistant conversation messages. It excludes
developer/system bootstrap instructions, environment context, reasoning, raw
tool arguments, raw tool output, and local absolute paths. Credential-like
values are replaced with typed redaction markers before a commit is created.

Every export records the SHA-256 digest of its source rollout, never the raw
rollout path. Re-sharing the same thread updates its existing document instead
of creating a duplicate.

## Repository layout

```text
index.json
schema/index.v1.schema.json
schema/thread.v1.schema.json
threads/YYYY/MM/<thread-id>.json
```

This repository is intentionally private. The web application consumes a
build-time snapshot; it does not place a GitHub token in browser code.
