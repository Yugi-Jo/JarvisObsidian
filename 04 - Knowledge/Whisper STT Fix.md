# Whisper / STT Fix (Linux ARM64 VPS)

When Whisper/STT fails on the VPS:

- Gateway and serve processes run from Hermes TOOLS python, **not** the managed venv
- `pm.sync_venv` / `ensure_import` for `stt-whisper` fails because `is_runtime()` is False
- Fix: `uv pip install faster-whisper --python $TOOLS_PY/bin/python3`
- Pin `av` to `18.1.0` (newer `av` 19.x doesn't accept `metadata_errors` kwarg)
- Restart **both** Hermes serve backend and gateway after fix
- Set `security.allow_lazy_installs: true` so `pm.ensure_import` works on first voice message