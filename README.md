# team-skills

Plugin-Marketplace für gemeinsam genutzte Claude-Code-Skills im Team.

## Struktur

```
team-skills/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace-Manifest, listet alle Plugins
└── plugins/
    └── <plugin-name>/
        ├── .claude-plugin/
        │   └── plugin.json    # Plugin-Manifest
        └── skills/
            └── <skill-name>/
                └── SKILL.md    # Der eigentliche Skill
```

## Neuen Skill hinzufügen

1. Neues (oder bestehendes) Plugin unter `plugins/<plugin-name>/` anlegen.
2. Darin `skills/<skill-name>/SKILL.md` erstellen.
3. Plugin in `.claude-plugin/marketplace.json` unter `plugins` eintragen:

```json
{
  "name": "<plugin-name>",
  "source": "./plugins/<plugin-name>",
  "description": "Kurzbeschreibung"
}
```

## SKILL.md-Aufbau

- **Frontmatter:** `name` (kurzer eindeutiger Bezeichner) und `description`
  (Trigger-Situation, Kurzfassung, konkrete Triggerwörter).
- **Body:**
  1. **Vorgehen** – Schritt-für-Schritt-Beschreibung
  2. **Gotchas** – bekannte Stolperfallen und Lösungen
  3. **Verweise** – relevante Referenzdateien/Templates/Beispiele

Siehe `plugins/example-plugin/skills/example-skill/SKILL.md` als Vorlage.

## Nutzung in Claude Code

```
/plugin marketplace add OC-Phelan/team-skills
/plugin install <plugin-name>@team-skills
```
