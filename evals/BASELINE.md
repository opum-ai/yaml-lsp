# The eval baseline

The score a future release compares against. `results/` is gitignored, so a
number kept there cannot survive the next run; this file is where the baseline
lives, the same convention `opum-workflow`'s eval suite uses.

**A partial run is not a smaller baseline, it is a different measurement** —
the run result's `partial` flag says which one you have.

## 0.1.0 — run 2026-10-01T12:09:49Z (claude 2.1.286)

- **Command:** `claude plugin eval . --runs 3 --trust-plugin --no-publish --allow-tools Write Read LSP`
  run from the repository root. The grants are load-bearing: `Write` is not in
  the read-only tool set a case can grant from its own `allowed_tools`, and the
  `LSP` tool needs an explicit grant too. Without them the tools are removed
  from the run entirely, and the with-arm fails against a session that could
  never have used them — which is exactly how the first version of this suite
  failed.
- **Content:** the plugin as committed here; the v0.1.0 tag cuts this same tree
  (the run read it from the working copy).
- **Result:** exit 0. `lsp-tool-answers-for-yaml`: with-arm score 1.00 (3 of 3
  runs), no-plugin arm 0.00 (3 of 3), delta 1.00. `partial: false`, no run
  ended with an error.
- **Cost and duration:** $0.41 estimated, 35s.

The no-plugin arm has no `LSP` tool at all — the tool appears only because a
plugin registering `lspServers` is loaded (measured 2026-10-01 across ~180 kept
eval sandboxes: the only one carrying the LSP tool was the one with this plugin
loaded; sandboxes with other, non-LSP plugins did not). The delta above is
therefore a plugin-fired signal, not a style difference.
