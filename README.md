# Website von Lukas P. Huber

Persönliche Website, gehostet auf [GitHub Pages](https://huber.church/).

## Wie funktioniert die Website?

Die Website wird mit [Hugo](https://gohugo.io/) gebaut – einem Programm, das aus einfachen Textdateien eine Website erstellt. Du musst Hugo **nicht** installieren: Bei jedem Push auf den `main`-Branch baut GitHub die Website automatisch und veröffentlicht sie.

## Inhalte ändern

Alle Texte der Website stehen in einer einzigen Datei:

**[`content/_index.md`](content/_index.md)**

### So geht's (direkt auf GitHub):

1. Öffne [`content/_index.md`](content/_index.md) auf GitHub.
2. Klicke auf den **Stift** (Edit-Symbol) oben rechts.
3. Ändere den gewünschten Text.
4. Klicke unten auf **«Commit changes»**.
5. Fertig – die Website wird automatisch in ca. 1–2 Minuten aktualisiert.

### Was steht in der Datei?

Die Datei ist in Abschnitte gegliedert:

| Abschnitt       | Was er enthält                              |
|-----------------|---------------------------------------------|
| `ueber_mich`    | Biografie / Über mich                       |
| `taetigkeiten`  | Liste der aktuellen Tätigkeiten und Rollen  |
| `podcasts`      | Podcast-Beschreibungen und Links            |
| `kontakt`       | Kontaktinformationen                        |

### Einen Text ändern

Suche den Abschnitt (z. B. `ueber_mich`) und ändere den Text nach `text: >`. Beispiel:

```yaml
ueber_mich:
  titel: "Über mich"
  text: >
    Hier steht der neue Text...
```

### Eine Tätigkeit hinzufügen

Füge unter `taetigkeiten` → `eintraege` einen neuen Eintrag hinzu:

```yaml
    - rolle: "Neue Rolle"
      beschreibung: >
        Beschreibung der neuen Tätigkeit.
```

Achte darauf, dass die Einrückung (Leerzeichen am Anfang) genau gleich ist wie bei den bestehenden Einträgen.

### Einen Link einfügen

Links werden so geschrieben:

```
[Angezeigter Text](https://www.beispiel.ch)
```

## Bilder hinzufügen

1. Lade ein Bild in den Ordner `static/images/` hoch (auf GitHub: «Add file» → «Upload files»).
2. Im Text kann das Bild dann so referenziert werden: `![Beschreibung](images/mein-bild.jpg)`

## Dateistruktur

```
├── content/
│   └── _index.md          ← Alle Texte der Website
├── layouts/
│   ├── index.html          ← Haupttemplate (HTML-Struktur)
│   ├── _default/
│   │   └── baseof.html     ← Basis-Layout
│   └── partials/
│       ├── head.html        ← Meta-Tags
│       └── footer.html      ← Fusszeile
├── static/
│   ├── css/
│   │   └── style.css       ← Design / Aussehen
│   └── images/              ← Bilder
├── .github/
│   └── workflows/
│       └── deploy.yml       ← Automatisches Deployment
├── hugo.toml                ← Hugo-Konfiguration
└── README.md                ← Diese Datei
```

## GitHub Pages einrichten

Falls GitHub Pages noch nicht eingerichtet ist:

1. Gehe zu **Settings** → **Pages** im GitHub-Repository.
2. Unter **Source** wähle **GitHub Actions**.
3. Unter **Custom domain** trage `huber.church` ein und aktiviere **Enforce HTTPS**.
4. Speichern – ab jetzt wird die Website bei jedem Push automatisch gebaut und veröffentlicht.

### DNS-Konfiguration für huber.church

Beim Domain-Registrar müssen folgende DNS-Einträge gesetzt sein:

| Typ   | Name | Wert                         |
|-------|------|------------------------------|
| A     | @    | 185.199.108.153              |
| A     | @    | 185.199.109.153              |
| A     | @    | 185.199.110.153              |
| A     | @    | 185.199.111.153              |
| CNAME | www  | riesentoaster.github.io      |

## Lokal testen (optional)

Falls du die Website lokal anschauen möchtest:

```bash
# Hugo installieren (macOS)
brew install hugo

# Website lokal starten
hugo server
```

Dann öffne http://localhost:1313/ im Browser.
