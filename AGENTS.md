# Project Rules

This is a cross-language event bus SDK built around RabbitMQ.

Priorities:

- Keep the public API small and boring.
- Prefer explicit message envelopes: { meta, data }.
- Preserve correlationId, causationId, streamId, source, timestamp, kind, type, version.
- The canonical protocol spec (schema, transport docs, conformance fixtures) lives in [conduit-protocol](https://github.com/Conduit-Events/conduit-protocol), consumed as a real dependency (`node_modules/conduit-protocol`, pinned via `package-lock.json`) rather than copied into this repo. Don't reintroduce a local `protocol/` directory — update the schema by bumping the dependency, not by editing files here.
- Do not introduce framework-specific DI requirements.
- Tests should be readable and focused.
- Use plain JavaScript unless TypeScript is already present.
- Do not hide RabbitMQ semantics when they matter: exchanges, queues, bindings, ack/nack, retry, DLQ.

Before editing:

- Explain the intended change.
- Prefer small diffs.
- Run relevant tests after changes.

Git workflow:

- `main` is branch-protected: direct pushes are rejected. Always branch off `origin/main`, push the branch, and open a PR (`gh pr create`).
- Use the `gh` CLI for push/PR/merge operations rather than the GitHub web UI.
- Keep unrelated changes on separate branches/PRs rather than bundling them.
- Squash-merge is this repo's convention (`gh pr merge --squash --delete-branch`).
