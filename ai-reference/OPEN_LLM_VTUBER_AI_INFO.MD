# Open-LLM-VTuber — AI Agent Reference (Server Copy)

> Master reference for AI agents working on the Open-LLM-VTuber project
> (on-screen / phone avatar presence for the Avatar ecosystem).
> Version: 1.0 — 2026-09-24

## Project

- **Purpose:** Local AI VTuber presence — Live2D characters rendered on screen/phone, driven by the local model stack (Open WebUI / Hermes).
- **Repo (fork, authoritative for dev):** https://github.com/Theoverthinkerdoes/Open-LLM-VTuber (default branch `main`)
- **Upstream:** https://github.com/Open-LLM-VTuber/Open-LLM-VTuber — fork was even with upstream as of 2026-09-24.
- **Server working copy:** `/home/aiserver/Documents/open-llm-vtuber/` (NOT a git repo — runtime installation. The repo clone is the source of truth for code; this dir holds running state + local-only assets.)

## CRITICAL: Local-only persona files

The following files contain personal persona prompts and MUST NEVER be committed to the repo:

- `/home/aiserver/Documents/open-llm-vtuber/characters/Tetzari.yaml`
- `/home/aiserver/Documents/open-llm-vtuber/characters/Leena.yaml`

Rule for agents: when creating branches/PRs or syncing the repo, exclude these paths. They live only in the server working copy (which is gitignored/untracked). If a future sync tool would copy `characters/` wholesale, filter these two files out. See `LOCAL_ONLY_FILES.md` note below and keep this list current as new personas are added.

## Roadmap (planned work, user-approved direction)

1. **Memory bridge:** replace Open-LLM-VTuber's built-in memory system with Open WebUI's memory (API integration, context injection, sync). First dev task — well-scoped, server-verifiable.
2. **Dual presence:** run 2+ Live2D characters simultaneously (frontend currently assumes one avatar; needs dual render pipeline, separate animation state, coordinated speech/expression timing).
3. **3D model support:** add a 3D rendering path (Three.js/Babylon) alongside Live2D with rigging/expression mapping.
4. **Trio wiring:** personas (Aurora / Tetzari / Zedra) selectable as presence characters; phone layout polish; lip-sync for multiple characters.

## Environment facts

- Server working copy runs from a venv at `venv/` (do not commit or delete).
- Frontend in the working copy is a BUILT bundle (`frontend/assets|index.html|libs`) — no frontend source locally. All frontend source work happens in the repo, then rebuild + copy the bundle over.
- Runtime artifacts (`logs/`, `cache/`, `chat_history/`, `models/`, `plugins/`, `upgrade_codes/`, `scripts/`) are local-only; never sync them into the repo.
- `config_templates/conf.default.yaml` in the working copy is identical to repo main (verified 2026-09-24); `src/` tree also 0 diffs vs repo main. Divergence from this state means someone edited one side without the other.

## Related systems

- Open WebUI (memory source for the bridge) — see SERVER_AI_INFO.MD ecosystem section.
- Avatar ecosystem: Brain (Hermes/Open WebUI), Hands (OpenHands agents), Body (VTuber presence here + ESP32 robot project, separate repo).
- ESP32 robot: `/home/aiserver/Documents/xiaozhi-esp32-server` (separate project, separate reference).

## Gotchas Learned

- 2026-09-24: local working copy has no `.git` — audits between it and the repo must be done by file diff, not git history.
- 2026-09-24: repo `characters/` also contains upstream example personas (en_*, zh_*) — do not delete those; only the two personal files are local-only.
