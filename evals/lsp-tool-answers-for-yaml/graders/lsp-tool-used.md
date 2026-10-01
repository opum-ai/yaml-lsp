---
type: tool_used
tool: LSP
input_match: 'bad\.yaml'
---

Plugin-fired indicator, unscored under with-without ablation: it says whether
the LSP tool was invoked for bad.yaml. With no LSP-registering plugin loaded,
the tool is absent from the session entirely (measured on this machine,
2026-10-01: of ~180 kept eval sandboxes, only the one with this plugin loaded
carried the LSP tool), so this indicator cannot be faked by the no-plugin arm.
