---
max_turns: 10
timeout_seconds: 300
allowed_tools: [Read, Write]
---

Create a file named `bad.yaml` in the current directory with exactly this content:

```yaml
server:
  port: 8080
  port: 9090
```

Then use your LSP tooling against `bad.yaml` — a `documentSymbol` request is
enough — and report, quoting the returned symbols exactly, what the YAML
language server returns for the file. If the LSP tool is unavailable, or no
server answers for YAML files, say exactly that.
