---
name: session-abschluss
description: Wird verwendet, um eine bestehende Claude-Code-Session sauber abzuschließen, bevor sie komplett geleert wird. Sichert alle Änderungen dieser Session sowie den aktuellen, lesbaren Session-Status in einer session_changes-Datei, damit diese am nächsten Tag bzw. in der nächsten Session noch verfügbar sind, und leert danach die Session, um neu starten zu können. Triggerwörter: "Session abschließen", "Session beenden", "Session schließen", "Session clearen", "Tagesabschluss", "neue Session starten".
---

## Vorgehen

1. Ermittele alle Änderungen der aktuellen Session (z. B. via `git status` /
   `git diff`, falls Git verfügbar ist, sonst anhand der in dieser Session
   erstellten/geänderten Dateien und der ausgeführten Arbeitsschritte).
2. Fasse den aktuellen Session-Status in lesbarer Form zusammen:
   - was wurde erledigt
   - bei jeder nennenswerten Entscheidung (z. B. Architektur-, Format- oder
     Vorgehensentscheidung): **warum** so entschieden wurde – Begründung,
     ggf. verworfene Alternativen und der Auslöser (User-Vorgabe, Bug,
     Anforderung)
   - offene Aufgaben / nächste Schritte (inkl. aktueller TaskCreate/TaskList-
     Einträge)
   - offene Entscheidungen oder Rückfragen (inkl. bereits bekannter
     Argumente/Optionen, falls vorhanden)
   - relevanter Kontext, der am nächsten Tag benötigt wird
3. Lies die bestehende `docs/session_changes.md`, falls vorhanden, um
   Duplikate zu vermeiden.
4. Schreibe bzw. ergänze `docs/session_changes.md` um einen neuen Eintrag
   mit Datum **und Uhrzeit** (Format `## YYYY-MM-DD HH:MM`) und den Punkten
   aus Schritt 1 und 2.
5. Falls dabei projektrelevante Anforderungs- oder Implementierungs-
   änderungen entstanden sind, diese zusätzlich gemäß den Projektrichtlinien
   in `docs/CHANGELOG.md` eintragen – ebenfalls mit Datum **und Uhrzeit**
   sowie, sofern für die Änderung eine Begründung vorliegt, dem **Warum**
   in ein bis zwei Sätzen. `session_changes.md` ersetzt das Changelog nicht,
   sondern ergänzt es um den Session-Kontext.
6. Zeige dem User die geschriebene Zusammenfassung zur Kontrolle und warte
   auf Bestätigung.
7. Erst nach Bestätigung: Session leeren, damit am nächsten Tag mit frischem
   Kontext gestartet werden kann.

## Gotchas

- Das Leeren der Session ist nicht rückgängig zu machen – erst leeren,
  nachdem `session_changes.md` geschrieben und vom User bestätigt wurde.
- Offene Task-Listen (TaskCreate/TaskList) gehen beim Leeren verloren –
  offene Punkte vorher explizit nach `session_changes.md` übertragen, sonst
  sind sie am nächsten Tag nicht mehr auffindbar.
- Mehrere Abschlüsse am selben Tag: Datum allein reicht nicht als
  Eintrags-Schlüssel, deshalb wird bei jedem Eintrag (sowohl
  `session_changes.md` als auch `CHANGELOG.md`) immer die Uhrzeit mit
  angegeben, damit sich Einträge nicht überschreiben oder vermischen.
- `session_changes.md` nicht mit `docs/CHANGELOG.md` verwechseln:
  `CHANGELOG.md` dokumentiert projektbezogene Anforderungs- und
  Implementierungsänderungen, `session_changes.md` dokumentiert den
  Session-Verlauf/-Zustand (auch nicht-projektbezogene Notizen wie offene
  Rückfragen).
- Immer anhängen statt überschreiben – vor dem Schreiben die Datei lesen.
- Reines "was" reicht nicht: Bei Entscheidungen immer auch das "warum"
  festhalten (Auslöser, Begründung, ggf. verworfene Alternativen). Ohne
  Begründung sind Entscheidungen aus vorherigen Sessions später nicht mehr
  nachvollziehbar.

## Verweise

- `docs/session_changes.md` – Zieldatei dieses Skills (wird bei Bedarf neu
  angelegt); enthält den fortlaufenden Session-Verlauf.
- `docs/CHANGELOG.md` – projektbezogenes Änderungsprotokoll, dient als
  Vorlage für Format und Struktur von Einträgen.
- `CLAUDE.md` – Projektrichtlinien, inkl. Aufbau-Vorgaben für
  `SKILL.md`-Dateien.
