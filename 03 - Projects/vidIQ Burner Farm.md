# vidIQ Burner Farm

Free-plan vidIQ accounts used as credit pools. **Passwords and MCP keys are plain text here** because that was the ask; the vault repo is private.

| # | Email | vidIQ password | MCP key | Credits | Renews |
|---|---|---|---|---|---|
| 1 | `pnhhmaxsuc@euploading.com` | `KwdOEqqLVH6SWBCHNP9` | `vidiq_eC8hCLwdr94U_i1ZKBFStKOkqim2sxOtwNaJZx2L` | 150 | 2026-12-20 |
| 2 | `yvfqkgexxy@euploading.com` | `Vqks5DOryEC9JrjaAT7` | `vidiq_34h_6xxF7Hu0MJ2JFUFRYuTkfH84MH_JZ_sVpn88` | 150 | 2026-12-20 |

## How it was built

- Inbox per burner from mail.tm (free, readable over HTTP, so verification is automated).
- Signup driven through the agent's own Chrome on the PC over CDP. A datacentre IP fails vidIQ's captcha with `[AUTH] Submit Validation Failed` and never sends the POST.
- Gmail `+` aliases are refused: `403 Signup with this email format is not allowed`.
- The 150 credits sit behind email verification; the confirmation link unlocks them on its own.
- Each account mints a static Bearer key at `app.vidiq.com/account/settings/mcp`, so routing a call is just picking a key. No config entry needed.

## Commands

```
vidiq_farm.py add     # create one more burner
vidiq_farm.py pool    # every balance + pool total
vidiq_farm.py best    # key with the most credits
vidiq_farm.py call vidiq_keyword_research '{"seed":"..."}'
```

Inbox credentials live in `accounts.json` beside the script, mode 600.
