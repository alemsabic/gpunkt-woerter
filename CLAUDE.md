# WÖRTER - gpunkt.org Content

**Repository:** Content-Quelle für gpunkt.org (Reizwörterbuch)
**Site-Repo:** `/Users/alemsabic/Desktop/gpunkt.org`
**Sync:** Auto-sync via GitHub Actions → `gpunkt-site/content/`

**Ziel:** Politische Reizwörter dokumentieren - mit verifizierten Quellen, wissenschaftlicher Mechanismus-Analyse.

---

## 🔥 NÄCHSTER SCHRITT

**Trigger:** *"Claude, vieux copain, what's on the plate"*

### ZIEL: 30-MINUTEN-WORKFLOW

Die Fabrik ist fertig. Jetzt testen wir sie an "Sozialtourismus" — erster vollständiger Durchlauf.

**Warum 30 Minuten realistisch ist:**

| Schritt | Zeit | Wer |
|---|---|---|
| 1-SCAN läuft im Hintergrund | ~10 min | passiv |
| 2-SICHTEN → KONTEXT-MATERIAL | ~3 min | AI |
| 3-DRAFT-THIS → Draft | ~4 min | AI |
| Belege manuell einsetzen | ~5-8 min | Mensch |
| Zotero Import | ~3 min | Mensch |
| 5-VERIFY + git push | ~2 min | Mensch |

**Aktive Zeit: ~15-20 min. Mit Scan im Hintergrund: unter 30 min.**
(Mit Edit-Schritt: +10-15 min → ~40-45 min, für Goldstandard-Qualität.)

**Trick:** Scan starten → sofort mit 2-SICHTEN beginnen (Scan läuft parallel).

---

**Status Sozialtourismus:**
- ✅ DIP-Scan abgeschlossen: `Recherche/Sozialtourismus/DIP-Sozialtourismus.md` (23 Zitate, 2014–2025)
- ⬜ KONTEXT-MATERIAL (2-SICHTEN.md)
- ⬜ Draft (3-DRAFT-THIS.md)
- ⬜ Belege einsetzen + Zotero
- ⬜ 5-VERIFY + git push

**Nächste Aktion:** `2-SICHTEN.md` öffnen, `DIP-Sozialtourismus.md` einfügen, KONTEXT-MATERIAL generieren.

---

## 📋 DER WORKFLOW (4 Schritte)

**Vollständige Dokumentation:** `wort-fabrik/HANDBUCH.md`

### Schritt 1: SCAN
```bash
python3 wort-fabrik/1-SCAN.py "Begriff"
```
→ Scannt alle ~4600 BT-Protokolle, Output: `Recherche/[Begriff]/DIP-[Begriff].md`

### Schritt 2: SICHTEN
- `2-SICHTEN.md` + DIP-Datei → KI wählt 8-10 beste Zitate
- Output: KONTEXT-MATERIAL Block → in `3-DRAFT-THIS.md` einfügen

### Schritt 3: DRAFT
- `3-DRAFT-THIS.md` mit KONTEXT-MATERIAL an KI → vollständiger Draft
- Belege-Sektion bleibt Placeholder

### Schritt 4: EDIT (optional)
- `4-EDIT-THIS.md` → Polishing bis Goldstandard

**Danach:** BibTeX → Zotero → `5-VERIFY.py` → `git push`

---

## ⚠️ CRITICAL RULES

### BibTeX Format für Bundestag-Zitate

**Citekey:** `autor_jahr` (lowercase, Unterstrich)
- ✅ `merkel_2010`, `höcke_2018`, `weidel_2025`
- ❌ `Merkel2010`, `merkel-2010`

**Note-Field:** `Plenarprotokoll XX/YY` (KEINE Seitenzahlen!)
- ✅ `note = {Plenarprotokoll 20/73}`
- ❌ `note = {Seite 8537A}`
- **Grund:** XML-Struktur änderte sich 2022

### Keine Sekundärquellen
- ✅ Bundestag-Protokolle, Original-Videos, Qualitätsmedien mit wörtlicher Rede
- ❌ "Correctiv berichtet, dass X sagte...", indirekte Rede

### Belege = Placeholder im Draft
- KI füllt Belege NICHT aus
- Belege kommen aus KONTEXT-MATERIAL, manuell ausgewählt
- Dann per Zotero in `bibliography.bib`

---

## 📁 WICHTIGE DATEIEN

**Pipeline (in Reihenfolge):**
- `wort-fabrik/1-SCAN.py` — Bundestag-Scan
- `wort-fabrik/2-SICHTEN.md` — DIP-Sichtung → KONTEXT-MATERIAL
- `wort-fabrik/3-DRAFT-THIS.md` — Recherche + Draft (Phasen A→E)
- `wort-fabrik/4-EDIT-THIS.md` — 3-Phasen-Editor
- `wort-fabrik/5-VERIFY.py` — Citekey-Prüfung

**Referenz:**
- `wort-fabrik/REF-Kriterien.md` — Zitat-Auswahlkriterien
- `wort-fabrik/REF-Werkzeugkasten.md` — 14 Mechanismen

**Ordner:**
- `wort-fabrik/Recherche/[Begriff]/` — DIP-Outputs
- `wort-fabrik/Drafts/` — Entwürfe
- `wort-fabrik/imports/to_zotero.bib` — BibTeX-Sammler (temporär)
- `wort-fabrik/Queue.md` — 100 Begriffe in der Pipeline

---

## 📚 ZUSÄTZLICHE QUELLEN (SPÄTER)

### Priorität A: Sofort nutzbar

**1. Landtage**
- **Bayern:** [PARLDOK](https://www.bayern.landtag.de/parlamentsdokumente/) — CSU-Hochburg
- **NRW:** [Landtag NRW Doku](https://www.landtag.nrw.de/portal/WWW/dokumentenarchiv/)
- **Sachsen:** [EDAS](https://edas.landtag.sachsen.de/)

**2. Europaparlament**
- [Europarl Plenarprotokolle](https://www.europarl.europa.eu/plenary/de/debates-video.html)

**3. Bundesrat**
- [Plenarprotokolle](https://www.bundesrat.de/DE/plenum/plenum-kompakt/plenum-kompakt-node.html)

---

## 📝 SESSION-LOG

### Session 2026-02-08

**Pipeline fertiggestellt:**
- ✅ `bundestag_recherche.py` → v3 (vollständiger Ein-Scan, alle Jahrgänge)
- ✅ KONTEXT-MATERIAL-Block in `3-DRAFT-THIS.md` eingebaut
- ✅ `2-SICHTEN.md` auf KONTEXT-MATERIAL-Output-Format umgestellt
- ✅ `HANDBUCH.md` wiederhergestellt + auf v3 aktualisiert
- ✅ Dateien umbenannt: 1-SCAN, 2-SICHTEN, 3-DRAFT-THIS, 4-EDIT-THIS, REF-*
- ✅ VORLAGE.md → _archiv (vollständig in 3-DRAFT-THIS eingebettet)

### Session 2026-02-07

- ✅ Script verbessert — längere Zitate, BibTeX-Fix
- ✅ BibTeX-Problem gelöst: `note = {Plenarprotokoll XX/YY}` einheitlich
- ✅ Test: "Sozialtourismus" — 23 Zitate aus 4600 Protokollen

---

*Letzte Aktualisierung: 2026-02-08*
*Nächster Trigger: "Claude, vieux copain, what's on the plate"*
