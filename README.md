# AT7 Media — Email Signaturen

Assets fuer animierte Email-Signaturen mit AT7 Banner.

## Dateien

| Datei | Zweck | Groesse |
|-------|-------|---------|
| `at7-banner.gif` | Animierter Banner (400x72, transparenter Hintergrund). **Frame 0 = AT7 Logo** | ~790 KB |
| `at7-banner-fallback.png` | Statisches AT7 Logo (fuer manuelle Verwendung) | ~4 KB |
| `signatur.html` | Fertige Signatur-Vorlage zum Einfuegen | — |

## Hosting-URL

Die Banner-GIF wird direkt von GitHub Raw gehostet:

```
https://raw.githubusercontent.com/AT7-Media-GmbH/email-signaturen/main/at7-banner.gif
```

Diese URL ist oeffentlich, HTTPS, permanent. Nie umbenennen — alte Mails wuerden das Bild verlieren. Bei Updates: neue Datei mit Versions-Suffix (`at7-banner-v2.gif`) und HTML anpassen.

## Outlook-Verhalten (wichtig)

Outlook Desktop (2007–2021, neue Outlook App) spielt **keine GIF-Animationen**, sondern zeigt ausschliesslich den ersten Frame eingefroren an.

Darum wurde das GIF so umsortiert, dass **Frame 0 das AT7 Logo** zeigt. Ergebnis:

| Client | Verhalten |
|--------|-----------|
| Gmail (Web + App) | Volle Animation |
| Apple Mail | Volle Animation |
| Outlook Web (OWA) | Volle Animation |
| Outlook Desktop | Zeigt Logo-Frame statisch (sauber lesbar) |
| Outlook Mobile | Volle Animation |
| Thunderbird | Volle Animation |

Kein VML-Hack noetig — ein einziges `<img>` reicht.

## Signatur einbinden

### Gmail

1. `signatur.html` lokal im Browser oeffnen
2. Die gerenderte Signatur markieren und kopieren (Cmd/Ctrl+A, Cmd/Ctrl+C)
3. Gmail → Einstellungen → Alle Einstellungen → Allgemein → Signatur → neue erstellen oder bestehende editieren → einfuegen

Erster Abruf laedt das Bild einmal durch Gmail's Image Proxy (googleusercontent.com); danach gecached.

### Outlook Desktop

1. Signatur via Signatur-Editor anlegen → `signatur.html` Inhalt reinkopieren
2. Outlook zeigt nur Frame 0 (Logo) — das ist gewollt
3. Alternativ: Template-Datei direkt im Outlook Signatur-Ordner ablegen:
   `%AppData%\Microsoft\Signatures\AT7.htm`

### Apple Mail

1. Mail → Einstellungen → Signaturen → neue anlegen
2. `signatur.html` im Safari oeffnen, kopieren, in Signatur-Feld einfuegen
3. Apple Mail laedt externe Bilder nach (manchmal Einstellung aktivieren: "Entfernte Inhalte in Nachrichten laden")

## Technische Details

- **Format:** GIF 89a, 400×72 px
- **Frames:** 185 (nach Optimierung), 20 ms pro Frame, Loop = infinit
- **Hintergrund:** Transparent (Palette-Index)
- **Farben:** 128er Palette, Bayer-Dither
- **Frame 0:** AT7 Logo + "AT7 MEDIA" Text (frontal, ungedreht)

## Aenderungen / Neues GIF

Wenn das Banner aktualisiert werden soll:

1. Neues animiertes GIF erzeugen (Quelle: Ops-Render-Pipeline)
2. Unbedingt darauf achten, dass **Frame 0 das AT7 Logo** zeigt — sonst zerstoert es Outlook-Anzeige
3. Als `at7-banner-vN.gif` im Repo ablegen (niemals bestehende Datei ueberschreiben falls Signaturen schon in Umlauf sind)
4. `signatur.html` auf neue Version zeigen lassen
