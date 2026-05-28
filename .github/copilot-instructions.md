# Copilot Instructions — common-ground

> See root `.github/copilot-instructions.md` for global conventions.

Claude Code plugin voor **Common Ground compliance** in gemeentelijke IT. Toetst implementaties aan Common Ground principes: data bij de bron, API-first architectuur, open standaarden, gescheiden applicatie- en datalaag.

## Structure

```
.claude-plugin/plugin.json    # Plugin metadata (name, description, version, keywords)
skills/common-ground/
  SKILL.md                    # Skill definition — triggers, model config, scope
```

## Installation

```bash
claude install djimit/common-ground
```

## Typical Usage

- **Architectuurreview** — Toets gemeentelijke IT op de 5 Common Ground principes
- **API-first analyse** — Beoordeel of systemen data ontsluiten via gestandaardiseerde API's
- **Data bij de bron** — Check of data bij de bron blijft en niet gekopieerd wordt
- **Laagscheiding** — Valideer scheiding tussen applicatie-, proces- en infrastructuurlaag
- **GEMMA-koppeling** — Toets op GEMMA-architectuurprincipes en referentiecomponenten
- **Migratie-advies** — Adviseer over transitie van zaakgericht naar informatiekundig werken

## Domain Context

- Common Ground — informatiekundige visie van Nederlandse gemeenten ([commonground.nl](https://commonground.nl/))
- GEMMA — Gemeentelijke Model Architectuur ([gemmaonline.nl](https://www.gemmaonline.nl))
- VNG Realisatie — ontwikkelaar en beheerder van Common Ground
- Voorbeeldimplementaties: Haven, NL Design System (NLDS), SensRNet

## License

MIT (see `plugin.json`)
