# PH-fun

Kleine Werkzeuge für Seminarlektionen an der PHSG, ausgeliefert über GitHub Pages.

## Bali: «Wo stehst du?» (Seminarlektion 30.11.2026)

Die Mitstudierenden stimmen mit dem Handy zum Antrag ab («Ja», «Ja unter Bedingungen», «Nein»), einmal vor und einmal nach der Wasserkonferenz. Der Beamer zeigt das Ergebnis live und im Vergleich, wie viele gewechselt haben.

| Seite | Adresse |
|---|---|
| Handy, Runde 1 (Folie 14) | https://kingofwar1918.github.io/PH-fun/bali/?r=v |
| Handy, Runde 2 (Folie 19) | https://kingofwar1918.github.io/PH-fun/bali/?r=n |
| Beamer | https://kingofwar1918.github.io/PH-fun/bali/beamer.html |
| Probelauf (eigene Zählung) | `?r=v&s=probe`, `?r=n&s=probe`, `beamer.html?s=probe` |

Beamer bedienen: Klicker oder Pfeiltasten wechseln zwischen «1 Vorher», «2 Nachher», «3 Vergleich»; Tasten 1 bis 3 springen direkt. «Neu zählen ab jetzt» blendet ältere Stimmen auf diesem Gerät aus (z. B. nach einem Test mit der echten Adresse). `beamer.html?a=x` öffnet direkt den Vergleich.

QR-Codes: `bali/qr-seminar-vorher.png`, `bali/qr-seminar-nachher.png` (Probe: `qr-probe-*.png`).

### Datenschutz

Gespeichert wird pro Handy nur eine zufällige Kennung, die Wahl und die Uhrzeit, kein Name und kein Login. Die Stimmen sind öffentlich lesbar (sonst könnte der Beamer sie ohne Anmeldung nicht zählen). Fällt das Netz aus, läuft die Abstimmung im Raum mit den Schildern weiter.

### Einrichtung (einmalig)

1. Firebase-Projekt nur für dieses Tool, Realtime Database in europe-west1, gesperrter Modus.
2. In der Firebase-Konsole unter «Realtime Database → Regeln» den Inhalt von `firebase/regeln.json` einfügen und veröffentlichen.
3. Die Datenbank-Adresse steht in `bali/index.html` und `bali/beamer.html` bei `CONFIG.datenbank` (ph-fun-bali, europe-west1).
4. Nach der Lektion die Daten in der Konsole unter `bali-wasser` löschen.

Die Regeln sind am Firebase-Emulator geprüft: Schreiben nur gültiger Stimmen (`ja`, `bed`, `nein`, Serverzeit) unter `bali-wasser/oeffentlich/{sitzung}/{vorher|nachher}/{kennung}`, kein Löschen, kein Schreiben oder Lesen ausserhalb.
