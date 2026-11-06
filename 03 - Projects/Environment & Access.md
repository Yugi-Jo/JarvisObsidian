# Environment & Access

Key facts about my computing setup, hosts, and remote access.

## Hermes Host
- Runs on an Oracle Linux VPS (7.0.0-1013-oracle)
- Profiles: active is `default` at `/home/ubuntu/.hermes/`
- Desktop app connects via Hermes serve backend + gateway

## Windows PC
- Slow Windows PC, home drive: `F:\`
- Drive Inbox for deliverables, Outbox for uploads
- **SSH:** `ssh Joel-PC@100.103.183.44` (Tailscale) | Host: `DESKTOP-6DSDA1L`
- **Computer Use:** Routes through Alan's Way plugin → real desktop (not VPS). Can list apps, take screenshots, drive via `computer_use` tool. Terminals read via capture mode='ax'.
- Blender MCP: wired through Hermes VPS → SSH tunnel → Windows Blender via `uvx mcp-for-blender stdio` [[Blender MCP Setup]]

## Shell Rules
- PowerShell only
- Single-line, semicolon-joined commands
- Close apps before file moves

## Google & OAuth
- Google Cloud project: `cosmic-keep-511806-e0` (client `422217702558-scbcjcqfhtoblic9bg05comf7n5pnar4`)
- Enable APIs separately in the API Library (Docs, Sheets, Drive, Gmail, Calendar — plus YouTube Data v3 + YouTube Analytics API when Studio is wanted)
- **Publishing status must be In production** — Testing mode kills refresh tokens after 7 days, which is what caused the recurring weekly failures. Verify the status rather than assuming.
- **2-step verification is now required for Cloud Console access** (enforced from 31 Oct 2026). Enable MFA on the Google account or the console is unreachable.
- App is production but **unverified**, so the consent screen shows an "unverified app" warning — tap Advanced → Go to app.

### The recovery route (check first, always)
1. `setup.py --check` — **run this before any diagnosis or guesswork.** It settles the question in two seconds.
2. If broken: `setup.py --auth-url` → open the link → approve → the browser lands on a dead `localhost:1` page → **copy that page's full URL** → paste it back.
3. `setup.py --auth-code '<pasted URL>'`
4. Verify with a real call (`google_api.py drive search ...`), not just `--check`.

Full procedure, traps and prevention: skill **`google-auth-recovery`**.

### Prevention
- Daily cron `google-token-healthcheck` runs `setup.py --check` and stays silent when healthy. It alerts on Telegram with the recovery route only when the token breaks — so failures are known before a task needs Google, not during one.
- **Never re-auth "just in case"** — each re-auth issues a new refresh token for the same client/account/scopes, and exceeding ~50 invalidates the oldest.

## Obsidian Vault
- Path: `OBSIDIAN_VAULT_PATH` = `/home/ubuntu/Documents/Obsidian Vault`
- This is Hermes's extended memory — all personal data lives here

### Standing rule (set 31 Oct 2026)
- Anything saved to Hermes's persistent memory must **also** be mirrored into this vault.
- Judge from the context of each prompt whether extra vault info is genuinely needed, then pull **only that piece**. Don't blanket-scan the vault — it burns tokens for no gain.
- Memory is the bounded index; the vault is the deep store. A quick, targeted lookup when it clearly helps. Not a reflex.

### Self-evaluation loop
When a prompt needed vault context and it wasn't pulled, log the miss in [[Vault Usage Log]] and distil it into a trigger rule there. That log is the calibration record — the goal is that each miss produces a rule that would have fired at the right moment.