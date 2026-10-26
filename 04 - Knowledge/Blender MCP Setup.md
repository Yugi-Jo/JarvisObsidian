# Blender MCP Setup

Hermes ↔ Blender connection via MCP.

- Hermes on VPS ↔ Windows Blender via SSH tunnel + `uvx mcp-for-blender stdio`
- Use `mcp__blender__*` tools to drive live Blender
- Tools: execute_blender_code, get_scene_info, look (screenshot), search_assets, import_asset, generate_3d

## Troubleshooting
- If Blender MCP tools fail, check SSH tunnel is alive
- Restart order: SSH tunnel → Hermes gateway restart → desktop reconnect