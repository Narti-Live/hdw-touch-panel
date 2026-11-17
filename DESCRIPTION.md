# HdW-Labor Mediensteuerung – Bedienoberfläche (Prototyp v2)

Interaktiver Web-Prototyp der Touchpanel-Oberfläche für **Crestron VC-4 (2 Raumlizenzen)** auf dem **Crestron TS-770-B-S** (7", 1280 × 800).
Grundlage ist ausschließlich die LV-Anforderungsliste (LV 4.6.11, 4.7.12, 4.10, 4.10.1–4.10.3). Keine Dropdown-Menüs: jede Auswahl ist ein sichtbarer Button.

**Öffnen:** `index.html` im Browser (offline, eine Datei). Links außerhalb des Panels: Panel Seminarraum / Erfahrungsraum, „Timer 20 s“ (testet den 20-Minuten-Wechsel in 20 Sekunden), Vollbild. Diese Knöpfe gehören nicht zur Oberfläche.

## Aufbau
- **System aus → Systemstart-Symbol antippen → bestätigen →** Startablauf mit Schritten → direkt auf die erste Bedienebene (Start).
- **Kopfzeile:** Raum, Raumstatus, Benutzerebene **Einfach / Experte**, Sprache **DE / EN**, Uhrzeit, **Ausschalten** (nur von hier, mit Bestätigung; Ablauf: erst Ton stumm, dann Geräte nacheinander aus).
- **Symbolleiste links:** Funktionsgruppen. Im Expertenmodus kommen die Expertenseiten unter „Experte“ dazu.
- **Werte** (Lautstärke, Pegel, Laufzeit) als Balken mit −/+, Min/Max und Anzeigefeld. **Schaltzustände** über Farbe: blau = gewählt, grün = Ein/aktiv, rot = stumm/Aus-Befehl.
- **Kritische Befehle** (Start, Ausschalten, Raumtrennung) mit Bestätigung.

## Seiten und LV-Bezug
| Raum | Ebene | Seite | Funktion | LV |
|---|---|---|---|---|
| beide | – | Start/Aus | Systemstart mit Bestätigung, Shutdown (Audio zuerst stumm) | 4.10 S. 74 |
| beide | beide | Kopfzeile | DE/EN, Einfach/Experte | 4.10 S. 70, 72 |
| Seminar | Einfach | Start | Presets „Präsentation“, „Videokonferenz“ + aktueller Zustand | 4.10 S. 72 |
| Seminar | Einfach | Bild | Displayeingänge wählen (Display 1 + 2) | 4.10.2 |
| Seminar | Einfach | Ton | Lautstärke + Stumm (bei Trennung je Raumteil) | 4.10.2 |
| Seminar | Einfach | Videokonferenz | VK ein/aus, Mikrofone an/stumm, Kamerapositionen | 4.10.2 |
| Seminar | Experte | Mikrofone | Deckenmikrofone: Pegel einzeln + Gruppe (Stufen, Min/Max), Kanal-Stumm, VK-Aufschaltung, Zuordnung | 4.10 S. 74–75, 4.10.2 |
| Seminar | Experte | Kamera | PTZ, Zoom, Positionsspeicher, Bildsperre, Sichtschutz (Dowser) | 4.10 S. 75 |
| Seminar | Experte | Geräte | Displays Ein/Standby/Aus + Bildformat, Verstärker, Audio-DSP Ein/Aus | 4.10 S. 75 |
| Seminar | Experte | Raum | Raumtrennung per Button; Mikrofon-/VK-Zuordnung wird angezeigt | 4.10.2 |
| Erfahrung | Einfach | Start | Hauptpreset (Rendering → Projektor), Nebenpreset (Videoclip), 20-Min-Automatik mit Laufzeitbalken | 4.10.3 |
| Erfahrung | Einfach | Bild | Projektorquelle wählen (Rendering-Workstation / Steuer-PC) | 4.10.3 |
| Erfahrung | Einfach | Ton | Lautstärke + Stumm | 4.10.3 |
| Erfahrung | Experte | Geräte | Projektor Ein/Standby/Aus, Seitenverhältnis, Schwarzbild; Rendering läuft/pausiert; Verstärker | 4.10 S. 75, 4.10.3 |

Raumtrennung: zusammengelegt → alle Deckenmikrofone auf Display 1 / Videokonferenz; getrennt → Mikrofone wieder dem jeweiligen Display zugeordnet. 20 Minuten ohne Bedienung im Erfahrungsraum → Nebenpreset wird geladen, Rendering pausiert.

## Annahmen (bitte prüfen)
- Displayeingänge Seminarraum: **Raum-PC (Slot-in)** und **Drahtlos (Cynap)** je Display. Weitere Eingänge bei Bedarf ergänzen.
- Zuordnung bei Trennung: Deckenmikrofon 1 + 3 → Teil A (Display 1), Deckenmikrofon 2 → Teil B (Display 2).
- Projektorquellen: Rendering-Workstation, Steuer-PC (spielt den Videoclip).
- Pegelbereich Mikrofone −30 … +6 dB in 3-dB-Stufen; Lautstärke 0–100 % in 5-%-Stufen.
- Nicht enthalten, weil im LV für diese Räume keine Geräte dafür vorgesehen sind: Licht, Verschattung/Leinwand (Motoraktoren), Gebäudeleittechnik.
- Login/HTTPS des Browserzugangs ist Sache des VC-4-Servers und hier nicht nachgebildet. Die Symbol- und Begriffsbibliothek zur Freigabe wäre der nächste Schritt.

## Screenshots
Ordner `screenshots/`: `sem_*` = Seminarraum, `erf_*` = Erfahrungsraum, `en_*` = englische Oberfläche. Alle in Panelauflösung 1280 × 800.
