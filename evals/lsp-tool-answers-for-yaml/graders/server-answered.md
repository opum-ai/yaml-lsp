---
type: regex
name: language-server-answered
target: trace
pattern: 'Document symbols:'
match: contains
---

The LSP tool's own result header, formatted by Claude Code from the language
server's documentSymbol response. It cannot appear without a server answering
a request: under ablation the no-plugin arm has no LSP tool at all (measured
on this machine, 2026-10-01: of ~180 kept eval sandboxes, only the one with
this plugin loaded carried the LSP tool), so the string would have to be
fabricated to appear there.
