# Hermes Rescue

An "if the VPS dies" copy of the whole agent, kept in a **private** GitHub repo:
`https://github.com/Yugi-Jo/hermes-rescue`

Set up 9 Nov 2026 because Joel worried about the Oracle box failing and losing the
agent outright.

**The recovery instructions live in the repo itself, at `RESTORE.md`** — written for
both Joel (assumes nothing installed) and for an agent asked to restore itself. Keep
that file accurate; it is the thing that actually gets read when the server is gone.

## What the snapshot contains

- `identity/` — `config.yaml`, `SOUL.md`, `profile.yaml`, `memories/`, all 95
  skills, `plugins/`, `pets/`, `desktop/`, the helper scripts in
  `~/.hermes/scripts/`, the cron job definitions (`cron/jobs.json`) and the small
  state DBs (`kanban.db`, `projects.db`, `shared-state.db`). Plain text, ~1023 files.
- `secrets.tar.gz.gpg` — `.env`, `auth.json`, `google_token.json`,
  `google_client_secret.json`, encrypted with the rescue passphrase (AES-256).
- `backup.sh`, `bootstrap.sh`, `restore.sh`, `MANIFEST.json`, `README.md`.

**Deliberately excluded:** `state.db` (chat history, 78 MB and growing — too heavy
for git), the Hermes source tree and downloaded toolchains (a fresh install
rebuilds them), `cache/`, `logs/`.

## Restoring on a new machine

```bash
git clone https://github.com/Yugi-Jo/hermes-rescue.git ~/hermes-rescue \
  && bash ~/hermes-rescue/bootstrap.sh
```

Installs Hermes if missing, moves any existing `~/.hermes` aside to
`~/hermes-home-before-restore-*.tar.gz`, copies everything back, then asks for the
passphrase to unlock the credentials. Finish with `hermes doctor`.

A brand-new Hermes can also do it itself if told to clone the repo and run
`bootstrap.sh`. The repo is private, so the clone needs a GitHub login with read
access — the gh CLI login works, or any token with `repo` scope.

## The passphrase

The repo now carries `rescue-key.enc` — a password-protected copy of the rescue
passphrase — so the repo alone is enough to recover everything. On a new machine,
before restoring:

```bash
bash rescue-key.sh unlock     # asks for the rescue key password
bash bootstrap.sh
```

`unlock` writes the passphrase to `~/.hermes/.rescue-key`, which `restore.sh` then
uses automatically. `rescue-key.sh protect` rewrites the wrapped copy after a
passphrase change; `rescue-key.sh status` shows which halves exist.

**The unlock password is NOT written here** — this vault pushes to the PUBLIC repo
`Yugi-Jo/JarvisObsidian`, so it would be world-readable. Joel holds it.

**Trade-off accepted deliberately:** anything able to read the repo can attack
`rescue-key.enc` offline with no rate limit, so the secrecy of the saved
credentials now rests on the strength of that one password. It exists to solve
"I've lost the passphrase", not to add security — the point is that it can never be
weaker than the password.

A plaintext copy also sits at `~/.hermes/.rescue-key` on the server so the
scheduled backup runs unattended. That file is excluded from every snapshot.

## Keeping it current

Cron `hermes-rescue-backup` (every 6 hours) runs
`~/.hermes/scripts/hermes_rescue_backup.sh`, which calls `backup.sh`. It is
`no_agent` and stays **silent on success** — a quiet inbox means the copy is
current; any output means something is actually wrong.

It checks two things beyond taking the snapshot, because both can rot invisibly:

- **Wrapped key vs live key** (`rescue-key.fingerprint`). If the passphrase changes
  without re-running `rescue-key.sh protect`, the repo silently stops being able to
  recover. The job says so and names the fix.
- **Which key encrypted the blob** (`secrets_key_fingerprint` in `MANIFEST.json`).
  If a snapshot ever gets taken with a key other than the live one, the repo becomes
  un-unlockable while *everything else still looks healthy* — the worst failure mode
  here. See the near-miss below.

Cron `hermes-rescue-verify` (1st of each month, 4am) runs
`~/.hermes/scripts/hermes_rescue_verify.sh`: it clones the repo **fresh from GitHub**,
restores it into a throwaway home, and diffs the result against the live machine.
Silent on success. This is the only check that proves the copy actually restores
rather than merely looking complete.

Run either by hand any time; `backup.sh --no-push` stages and commits without
uploading.

**Never pass `RESCUE_KEY_FILE` when running `backup.sh` against the live repo.**
On 9 Nov 2026 a stale-key test pointed the real backup at a throwaway key, which
re-encrypted and pushed the real secrets blob with a key that was then deleted —
leaving the repo unrestorable. The monthly verify is what caught it. Test
key-rotation paths against a scratch copy via `RESCUE_REPO`, never the live one.

## Auth note (why this was awkward)

The fine-grained PAT in `~/.git-credentials` (user `Yugi-Jo`, token name
`Yugi-Jo-Index`) is scoped to six specific repositories. It could **create** a new
repo but had no access to it afterwards — so `hermes-rescue` was created and then
invisible to it, returning 404. The same scoping previously blocked deleting the
throwaway `gm-arena-host` repo.

Fixed on 9 Nov 2026 by installing the GitHub CLI and logging in via the device-code
flow (one code typed at github.com/login/device). `gh auth setup-git` wires git to
that login, which carries `repo` scope, so this class of problem is gone.

**Settings changes like this need Joel's own login** — never sign in as him or
touch a password/2FA prompt. Device-code flow is the low-effort route: it needs one
code pasted while he's already signed in, not a token edit (which forces a
password re-entry).

## Related

- [[Environment & Access]] — host, PC and access layout
