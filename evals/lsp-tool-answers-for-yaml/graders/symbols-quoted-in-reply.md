---
type: regex
name: reply-quotes-the-server-output
target: last_message
pattern: 'port \(Number\) 9090'
match: contains
---

Anchored to the server's actual response, captured from the probe run's tool
result (2026-10-01): documentSymbol returned a three-symbol outline whose
third line is `port (Number) 9090 - Line 3`. A no-plugin run cannot produce
this string from a server response it never received.
