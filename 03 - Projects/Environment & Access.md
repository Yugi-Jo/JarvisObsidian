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

### Two accounts, deliberately split
- **joelleeproductions@gmail.com** — Drive, Docs, Sheets, Gmail, Calendar. Also owns the Cloud project `cosmic-keep-511806-e0`. This is the token everything currently uses.
- **joelvizard@gmail.com** — owns the **Yugi Jo YouTube channel**. Has its own second token, **connected 13 Nov 2026**. (Same username as the Windows PC account.)
- Because they're split, the YouTube scopes stay off the main token. The second auth only needs YouTube scopes, so Drive/Docs don't get scope creep.
- Design note: pull YouTube data with the joelvizard token, write the results Sheet with the joelleeproductions Drive token, so the analytics output lands in the Drive already in use.

### Token on disk
- `~/.hermes/google_token.json` — the joelleeproductions token, auto-refreshing.
- Scopes on it: Gmail, Calendar, Drive, Contacts, Sheets, Docs. YouTube scopes are deliberately absent; those live on the joelvizard token.
- `~/.hermes/google_token_youtube.json` — the joelvizard token, auto-refreshing. Scopes: `youtube.readonly`, `yt-analytics.readonly`, `youtube.upload`, `youtube.force-ssl`.
- Verified against the live API: channel **Yugi Jo** `UC3lTROT3W1SPPX3lhRAStDg`, and channel analytics respond. `channels.list?mine=true` returns exactly one channel, so no brand-account ambiguity.
- Never use the Hermes connector picker for Google Workspace — go straight to the script.

### Making a second token (the working recipe)
`setup.py` gained two flags for this, because it originally hardcoded one token path and the workspace scope list:
- `--token-path PATH` — read/write the token somewhere other than the workspace default. Also relocates the in-flight OAuth session file (`google_oauth_pending_<stem>.json`), so starting a YouTube auth can't clobber a pending workspace auth.
- `--scopes default|youtube|youtube-manage` — `youtube` = readonly + analytics; `youtube-manage` adds `youtube.upload` and `youtube.force-ssl`.

So the full YouTube auth is:
`setup.py --auth-url --scopes youtube-manage --token-path ~/.hermes/google_token_youtube.json`
then the same with `--auth-code '<pasted>'`. Sign in as **joelvizard@gmail.com**.

Caveat: those flags live in the bundled skill script (`skills/productivity/google-workspace/scripts/setup.py`), so a Hermes update that replaces the skill could quietly drop them. If `--scopes`/`--token-path` ever report as unknown arguments, re-apply the override helper (`_apply_overrides`) — the two tokens themselves keep working either way, since they're plain files the script only reads.

### Console config
- Client `422217702558-scbcjcqfhtoblic9bg05comf7n5pnar4`, project `cosmic-keep-511806-e0`
- Enable APIs separately in the API Library (Docs, Sheets, Drive, Gmail, Calendar — plus YouTube Data v3 + YouTube Analytics API when Studio is wanted)
- **Publishing status must be In production** — Testing mode kills refresh tokens after 7 days, which is what caused the recurring weekly failures. Verify the status rather than assuming.
- **2-step verification is now required for Cloud Console access** (enforced from 31 Oct 2026). Enable MFA on the Google account or the console is unreachable.
- App is production but **unverified**, so the consent screen shows an "unverified app" warning — tap Advanced → Go to app.
- YouTube Data v3 + YouTube Analytics API are now **enabled** (done 13 Nov 2026). They were off, which is what blocked the first live call.
- **Trap: a scope error masks a disabled API.** Google checks scopes before API enablement, so calling YouTube with a token that lacks YouTube scopes returns "insufficient authentication scopes" and tells you nothing about whether the API is on. Only once the scopes were granted did the real error appear ("has not been used in project … or it is disabled"). Never conclude an API is enabled from a scope error.
- **Unverified app + uploads:** videos pushed through this (unaudited) project get locked to **private** on YouTube until the project passes Google's audit. Reading stats and managing existing content works regardless.
- **Trap: a redirect URL pasted without its scheme.** `localhost:1/?state=…&code=…` does not start with `http`, so the script used to treat the whole blob as the auth code and Google answered `invalid_grant: Malformed auth code`. Fixed in the script (it now rewrites a scheme-less redirect to `http://…`), but if it ever recurs, pass the bare `4/0A…` code instead.

### The recovery route (check first, always)
1. `setup.py --check` — **run this before any diagnosis or guesswork.** It settles the question in two seconds.
2. If broken: `setup.py --auth-url` → open the link → approve → the browser lands on a dead `localhost:1` page → **copy that page's full URL** → paste it back.
3. `setup.py --auth-code '<pasted URL>'`
4. Verify with a real call (`google_api.py drive search ...`), not just `--check`.

Full procedure, traps and prevention: skill **`google-auth-recovery`**.

### Prevention
- Daily cron `google-token-healthcheck` runs `setup.py --check` **on both tokens**, then tests the **CLI credential copy** by refreshing it directly, and stays silent when healthy. It alerts on Telegram with the recovery route only when a token breaks — so failures are known before a task needs Google, not during one. A missing YouTube token counts as broken (silence would hide a half-configured box).
- The CLI copy (`~/.config/gws/credentials.json`) needs its **own** check: it shares the OAuth client with the workspace token but carries a separate refresh token, so it dies independently (happened 14 Nov 2026 — a Doc-writing task failed with `invalid_grant` while `setup.py --check` reported the workspace token healthy). Fix is a one-liner, no browser: `cp ~/.hermes/google_token.json ~/.config/gws/credentials.json`. Don't test it via `gws auth status` or a `gws` call — both serve a cached access token and report healthy while the refresh token is dead.
- **Never re-auth "just in case"** — each re-auth issues a new refresh token for the same client/account/scopes, and exceeding ~50 invalidates the oldest (the likely cause of the 14 Nov CLI breakage).


## Hermes Rescue (backup & restore)
- Full agent snapshot in the **private** repo `Yugi-Jo/hermes-rescue`: config, skills, memory, cron jobs, plugins, scripts, small DBs, plus the credentials in an encrypted blob. Restores onto any new machine with one line.
- Cron `hermes-rescue-backup` runs every 6 hours, silent unless it fails.
- The rescue passphrase is **not** in this vault (the vault pushes to a public repo) — it lives in Joel's password manager and at `~/.hermes/.rescue-key` on the server.
- Detail, restore steps and the token-scoping trap that made this fiddly: [[Hermes Rescue]]

## Hosting large files (video)
- `Yugi-Jo/JarvisObsidian` doubles as a scratch host for big media. Files go up as **GitHub release assets** (2GB per asset) because a normal `git push` refuses anything over 100MB.
- The PAT in `~/.git-credentials` (user `Yugi-Jo`, repo admin) can create and delete releases there.
- These uploads are **temporary by intent** — delete the release *and* its tag when Joel says wipe, so nothing lingers on the repo.
- **The repo is public**, so any download link handed over is public too. Say so plainly each time.
- After deleting a release, the download URL can still serve a **CDN-cached 200** for a while — re-check with a cache-buster before concluding a file is still live.
- Procedure and the list of free hosts that actually work from this VPS: skill **`short-array`** (formerly `host-large-video-publicly` — renamed 2026-11-09, old name kept as an alias).

## Voice / TTS
- **Never use edge-tts here.** It is IP-blocked: Microsoft rejects the WSS handshake with 403 from this datacenter IP, and retries never fix it.
- **Piper local TTS is the working default** (`tts.provider=piper`, voice `en_US-lessac-medium`), free and keyless.
- `piper-tts` must be present in BOTH the live session venv and the pm-synced venv. After a `pm` rebuild the running session still reports it missing — install into the running venv with the bundled uv (that venv has no pip).
- Gemini / GPT-4o-mini / ElevenLabs providers exist in config but have **no API keys** in `.env`.
- Full setup, voice catalog and custom-voice wiring: skill **`hermes-agent`** -> `references/local-tts-piper.md`.

## Long-term memory (Hindsight)
- Runs as a local embedded daemon (port 9177) launched as `uvx hindsight-api`. `uv`/`uvx` are **not** on the shipped PATH, which is why memory ran dead from setup until 2026-11-09 — see [[2026-11-09]].
- Pass-through shims in `~/.local/bin` (canonical copies in `~/.hermes/scripts/shims/`) resolve the newest bundled uv by glob, so a version bump can't break it again.
- Fact extraction runs on `qwen/qwen3.5-9b`; it must have reasoning disabled in the daemon config or it burns its budget "thinking" and the retain times out.
- Daily-ish cron `hindsight-memory-healthcheck` self-heals a missing shim or missing key and alerts only when memory is genuinely broken.
- Writes are **async**: a queued write is only findable after the extraction stage finishes. Never judge a write by an immediate recall.
- **Memory layers:** the always-on notes are the bounded index; this vault is the deep store; Hindsight holds distilled cross-session facts. Heavy detail belongs in a skill or this vault, with a short pointer in the notes.

## Obsidian Vault
- Path: `OBSIDIAN_VAULT_PATH` = `/home/ubuntu/Documents/Obsidian Vault`
- This is Hermes's extended memory — all personal data lives here

### Standing rule (set 31 Oct 2026)
- Anything saved to Hermes's persistent memory must **also** be mirrored into this vault.
- Judge from the context of each prompt whether extra vault info is genuinely needed, then pull **only that piece**. Don't blanket-scan the vault — it burns tokens for no gain.
- Memory is the bounded index; the vault is the deep store. A quick, targeted lookup when it clearly helps. Not a reflex.

### Hard rule (added 9 Nov 2026): the notes must never carry stale detail
- The notes are an **index**, not a store. Rules and pointers only.
- Before adding or editing a note, check whether an existing entry or vault note already covers it, and update or remove that one **in the same pass**. Two entries saying slightly different things is worse than one.
- **Never evict or overwrite a note until the detail is confirmed to survive elsewhere** (vault, skill, or long-term memory). Removing something is only safe once it exists somewhere better.
- When trimming, re-read the entry being cut and check each fact off against its new home. Detail that was unique to the notes is exactly what gets silently lost.
- Pairs with the trigger-rule calibration loop below: a stale note is a miss that already happened.

### Config file edits
- `config.yaml` is hard-blocked from the agent's own file tools, deliberately: an injected agent editing it could quietly disable exec approvals. No setting toggles this.
- **Route when a change is genuinely wanted:** Joel instructs it explicitly, then the agent edits via the shell, backs the file up first, changes only the named lines, and diffs against the backup to prove nothing else moved.
- Prefer `hermes config set <key> <value>` for values. It cannot touch comments, which is why stale inline comments get left behind — noted on 9 Nov 2026 when the `# ~800 tokens` comment outlived the real 12,000-char value. Both comments were corrected the same day on Joel's instruction, so that example is history, not a live gap.

### Self-evaluation loop
When a prompt needed vault context and it wasn't pulled, log the miss in [[Vault Usage Log]] and distil it into a trigger rule there. That log is the calibration record — the goal is that each miss produces a rule that would have fired at the right moment.