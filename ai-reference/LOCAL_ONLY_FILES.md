# LOCAL-ONLY FILES — never commit to this repo

Persona prompt configs contain personal content and stay on the deployed
working copy (/mnt/storage/tools/open-llm-vtuber/) only:

- characters/tetzari.yaml
- characters/aurora.yaml
- characters/zedra.yaml
- conf.yaml (deployment config: model endpoints, Kokoro wiring)

Persona source of truth: Nextcloud "AI soul files".
When the list grows (new personas), update this file AND
ai-reference/OPEN_LLM_VTUBER_AI_INFO.MD.
