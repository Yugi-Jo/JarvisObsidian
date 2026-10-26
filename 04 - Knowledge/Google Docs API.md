# Google Docs API

Tips and gotchas from working with the Google Docs API.

- `updateTextStyle` does **not** accept a `"fontFamily"` field
- `deleteContentRange` cannot include the final newline — delete up to `endIndex - 1`
- `google-api-python-client` handles token refresh automatically
- Docs API `batchUpdate` safe chunk size: ~50 requests per call

See also: [[Environment & Access#Google OAuth]] for auth flow.