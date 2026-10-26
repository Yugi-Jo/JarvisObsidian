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