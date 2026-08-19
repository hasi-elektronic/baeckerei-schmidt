# AGENTS.md

## Cursor Cloud specific instructions

### Was ist dieses Projekt?

Eine einzelne statische Landingpage für die „Bäckerei Schmidt" (Vaihingen/Enz).
Das gesamte Projekt besteht aus genau einer Datei: `index.html`. CSS und
JavaScript sind inline in dieser Datei enthalten. Es gibt **kein** Build-System,
**keine** Paketverwaltung (`package.json` o.ä.), **keine** Abhängigkeiten,
**keine** Tests und **keine** Lint-Konfiguration.

### Entwicklungsserver starten

Die Seite ist rein statisch und braucht nur einen statischen Dateiserver. Am
einfachsten mit dem im Basis-Image vorhandenen Python:

```
python3 -m http.server 8000 --bind 0.0.0.0
```

Danach ist die Seite unter `http://localhost:8000/` erreichbar. Ein Öffnen der
Datei über `file://` funktioniert grundsätzlich auch, aber der HTTP-Server ist
für Browser-Tests (computerUse) zuverlässiger.

### Lint / Test / Build

Es existieren keine Lint-, Test- oder Build-Schritte, weil es keine
Toolchain-Konfiguration gibt. „Bauen" = die `index.html` unverändert ausliefern.
Änderungen werden verifiziert, indem der Server läuft und die Seite im Browser
geladen wird (Hot Reload gibt es nicht – nach Bearbeiten von `index.html` einfach
die Browserseite neu laden).

### Kernfunktionalität / manueller Smoke-Test

Die einzige interaktive Kernfunktion ist das Kontaktformular im Abschnitt
„Kontakt & Bestellung": Nach dem Absenden zeigt ein Inline-`<script>` ein
JavaScript-`alert()` mit „Danke für Ihre Nachricht! …" (Demo, kein echtes
Backend). Ein sinnvoller Hello-World-Test ist daher: Formular ausfüllen und
absenden, den Bestätigungsdialog prüfen.

### Hinweise

- Der Footer verlinkt `impressum.html` und `datenschutz.html`, die (noch) nicht
  existieren – das ist kein Setup-Fehler.
- Externe Ressourcen (Google Fonts) werden per CDN geladen; ohne Netzwerkzugriff
  fällt die Seite auf System-Schriftarten zurück, bleibt aber voll funktionsfähig.
