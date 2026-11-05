# Vault Usage Log

**Purpose:** calibration record for vault-context usage. When a prompt needed vault context and I didn't pull it, that miss gets logged here and distilled into a trigger rule so it doesn't repeat.

**Set up:** 31 Oct 2026

---

## How this works

Two sections:

1. **Misses** — raw entries. One per failure. Logged when Joel flags a miss, or when I catch one myself.
2. **Trigger rules** — the distilled lessons. This is the part that actually improves the behaviour. Each miss should produce or sharpen one rule here, or be noted as already covered.

A miss only counts as fixed once a trigger rule exists that would have fired at the right moment.

### The retrospective check (primary detection method)

Waiting for Joel to flag a miss is unreliable — if I didn't know the vault was needed, I won't know I skipped it.

The better trigger: **whenever the vault is accessed mid-conversation, stop and look back over that conversation.** Ask whether any earlier prompt should have pulled the same context and was answered without it. The vault access proves the context was relevant to the thread, which is exactly what makes an earlier omission visible.

So the routine is:

1. Vault gets pulled for prompt N.
2. Scan prompts 1 to N-1 in the same conversation.
3. Any that clearly needed that context → log as a miss.
4. Distil the trigger rule.
5. Apply the rule for the rest of the conversation.

This runs on vault access, not on being told.

---

## Misses

*None logged yet. The loop starts now.*

---

## Trigger rules (distilled)

Working set from the 31 Oct 2026 conversation:

1. **Channel-specific YouTube questions → pull `03 - Projects/Yugi Jo Channel.md` first.** Stats, strategy, niche, "what should I film", "why did this flop", format questions. The note already holds the answers; re-deriving wastes tokens.

2. **Video topic research → always pull the channel note.** The relevant context is not the topic's facts but whether it fits the nostalgia-crossover lane, whether the channel has covered it, which proven format applies, and whether it trips the anti-AI rule. Same facts, different answer for a different creator.

3. **General YouTube/platform questions → vault adds nothing.** Skip it. Algorithm mechanics, thumbnail theory, platform policy.

4. **Everything else → judge from the prompt.** If the answer depends on Joel's preferences, setup, history or rules, pull the specific note. If it stands on its own, don't.

5. **Never blanket-scan.** One targeted note, not the whole vault. Read the note that matters, skip the rest.

---

## Standing rule

Anything written to Hermes's persistent memory is mirrored here. This log is the calibration record for how well the vault gets used. See `03 - Projects/Environment & Access.md` for the base rule.
