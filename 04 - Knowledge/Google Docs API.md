# Google Docs API

Tips and gotchas from working with the Google Docs API.

- `updateTextStyle` does **not** accept a `"fontFamily"` field
- `deleteContentRange` cannot include the final newline — delete up to `endIndex - 1`
- `google-api-python-client` handles token refresh automatically
- Docs API `batchUpdate` safe chunk size: ~50 requests per call

See also: [[Environment & Access#Google OAuth]] for auth flow.

## replaceAllText — the traps that actually bite

- It matches the **exact string only**, never a substring or regex. A partial or loose
  match does not error: it silently no-ops, returns no `occurrencesChanged`, and applies
  to nothing.
- A global blanket replace is the dangerous move. Renaming a title everywhere
  (e.g. "Megas XLR" -> "Megas") also rewrites the title and SEO sections. Restore those
  in a **second** `batchUpdate` call afterwards, because replacements inside one batch
  are atomic and cannot depend on each other.
- Bulk contraction auto-passes over-match and can produce broken grammar
  ("here's smarter", "that'd've", "that'dn't"). Re-read the whole doc and fix by hand
  after any scripted contraction pass.
- `occurrencesChanged` in the reply is the verification. Zero means the old text was not
  found — re-read the document rather than assuming success.

Procedure lives in the `gws-docs` skill.
