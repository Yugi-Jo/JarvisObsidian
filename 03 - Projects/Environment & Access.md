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
- Google Cloud project required: enable Docs, Sheets, Drive, Gmail APIs separately
- Re-auth flow: `setup.py --check` → `--auth-url` → paste redirect URL → `--auth-code`
- Publish Cloud project to Production for permanent tokens

## Obsidian Vault
- Path: `OBSIDIAN_VAULT_PATH` = `/home/ubuntu/Documents/Obsidian Vault`
- This is Hermes's extended memory — all personal data lives here

### Standing rule (set 31 Oct 2026)
- Anything saved to Hermes's persistent memory must **also** be mirrored into this vault.
- Judge from the context of each prompt whether extra vault info is genuinely needed, then pull **only that piece**. Don't blanket-scan the vault — it burns tokens for no gain.
- Memory is the bounded index; the vault is the deep store. A quick, targeted lookup when it clearly helps. Not a reflex.

### Self-evaluation loop
When a prompt needed vault context and it wasn't pulled, log the miss in [[Vault Usage Log]] and distil it into a trigger rule there. That log is the calibration record — the goal is that each miss produces a rule that would have fired at the right moment.