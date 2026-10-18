<!-- gitbook-agent-instructions:start -->

## GitBook Documentation Editing

This repository contains documentation synced with GitBook via Git Sync.

Before editing GitBook-synced Markdown, YAML, or asset files, make sure the GitBook skill is available and up to date in your local agent environment. Prefer installing or updating it with:

```bash
npx skills add gitbookio/gitbook-skills
```

This command may add or update local agent skill files. Use them only as local agent instructions; do not commit those installed skill files or any tool-generated agent configuration unless the user explicitly asks for it.

If `npx` is unavailable, load the skill from:

https://gitbook.com/docs/skill.md

When making changes, preserve GitBook sync metadata such as frontmatter, `SUMMARY.md`, `gitbook-docs.yaml`, `.gitbook/`, and asset links unless the requested edit explicitly requires changing them.

<!-- gitbook-agent-instructions:end -->

## Linear-tickets aanmaken

- Gebruik bij het aanmaken van issues voor nieuwe features altijd het template 'Nieuwe feature'. Behoud alle secties en vul ze op basis van de beschikbare context. Verzin geen ontbrekende informatie; vermeld onzekerheden onder 'Open vragen en beslissingen'.
- Maak nooit een Linear-ticket aan zonder dat Mark eerst gebriefd is over hoe het ticket eruitziet, wat erin staat en waarom het nodig is. Bestaat er al een passend ticket, werk dat dan bij in plaats van een nieuw aan te maken.
- Noem tickets altijd met hun beschrijvende titel, met het nummer tussen haakjes, bijvoorbeeld "Adresveld: 50-tekensgrens (SR-82)".
- Nieuwe tickets komen in Backlog met het label "Agent". Triage is niet mogelijk.
