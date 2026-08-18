---
name: example-skill
description: Vorlage für neue Skills in diesem Marketplace. Wird benutzt, wenn ein neuer Team-Skill angelegt werden soll. Triggerwörter: "neuen Skill anlegen", "Skill-Vorlage".
---

## Vorgehen

1. Diesen Ordner (`plugins/example-plugin/skills/example-skill/`) als Vorlage
   kopieren und in `plugins/<plugin-name>/skills/<skill-name>/` umbenennen.
2. Frontmatter (`name`, `description`) auf den neuen Skill anpassen.
3. Die Abschnitte **Vorgehen**, **Gotchas** und **Verweise** mit den
   tatsächlichen Schritten, Stolperfallen und Referenzdateien des neuen
   Skills füllen.
4. Falls der Skill zu einem neuen Plugin gehört, das Plugin unter
   `.claude-plugin/marketplace.json` eintragen (siehe Repo-README).

## Gotchas

- Der Ordnername unter `skills/` wird zum Skill-Bezeichner
  (`/<plugin-name>:<skill-name>`) – auf Kleinschreibung und Bindestriche
  achten.
- `description` sollte klare Triggerwörter enthalten, damit der Skill
  zuverlässig automatisch erkannt wird.

## Verweise

- [`README.md`](../../../../README.md) – Gesamtstruktur des Marketplace
- [`.claude-plugin/marketplace.json`](../../../../.claude-plugin/marketplace.json) – Plugin-Registrierung
