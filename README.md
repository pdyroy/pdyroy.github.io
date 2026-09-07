# pdyroy.github.io

Persönliche Website mit dem Jekyll-Theme **Minimal Mistakes** (_remote_theme @ 4.28.1), gehostet auf GitHub Pages.

## Struktur des Repos

```
pdyroy.github.io/
├── _config.yml          # Globale Einstellungen (Titel, Autor, Menü-Basics, Theme)
├── index.html           # Startseite (Home-Layout, zeigt neueste Posts)
├── _pages/              # "Normale" Seiten
│   ├── about.md         #   z.B. die About-Seite (zu /about/)
│   └── 404.md           #   Fehlerseite
├── _data/
│   └── navigation.yml   # das obere Menü
├── assets/images/       # Bilder (Avatar bio-photo.jpg, …)
├── _posts/              # Blog-Posts (legt man bei Bedarf an)
├── Gemfile              # Ruby-Pakete (i.d.R. nicht anfassen)
└── _site/               # lokale Build-Ausgabe (niemals committen)
```

Ganz grob: Alles mit `_` davor ist Jekyll-spezifisch (Posts, Pages, Daten, Config). Bilder und statische Dateien nach `assets/`. Zum Veröffentlichen: Dateien ändern → commiten → pushen; GitHub baut dann neu.

## 1. Normale Seite hinzufügen (z.B. /projekte/)

Neue Datei anlegen, z.B. `_pages/projekte.md`:

```markdown
---
permalink: /projekte/
title: "Projekte"
---

Hier beschreibe ich meine Projekte.
```

Der **Front Matter** (Block zwischen den `---`) bestimmt die URL (`permalink`) und den Titel. Inhalt einfach als Markdown darunter.

Damit die Seite im Menü auftaucht, in `_data/navigation.yml` eintragen:

```yaml
main:
  - title: "About"
    url: /about/
  - title: "Projekte"
    url: /projekte/
```

Hinweis: Diese Seiten nutzen automatisch das `single`-Layout mit Author-Profil (steht in `_config.yml` unter `defaults`). Abweichendes Layout, z.B. `layout: splash`, setzt man im Front Matter.

## 2. Blog-Post schreiben

Ordner `_posts/` anlegen, Dateiname **zwingend** mit Datum + Titel:
`_posts/2026-09-07-mein-erster-post.md`

```markdown
---
title: "Mein erster Post"
date: 2026-09-07
---

Hier steht der Inhalt des Posts.
```

- **Dateiname** bestimmt Datum und Slug-URL.
- Posts erscheinen automatisch auf der Startseite (`index.html` → Home) und im Feed.
- URL-Struktur (`permalink: /:categories/:title/`) erzeugt Pfade wie `/posts-name/`.

## 3. Einstellungen ändern (_config.yml)

Dort stehen z.B. `title`, `author` (Name/Bio/Avatar/Links, aktuell Platzhalter), `minimal_mistakes_skin` (Farbschema: `default`, `dark`, `mint`, `sunrise`, …), `footer.links`.

## 4. Veröffentlichen (live)

```bash
git add -A
git commit -m "add projekte page"
git push origin main
```

GitHub baut automatisch neu — nach ~1–2 Min ist der Stand auf <https://pdyroy.github.io>.

---

## Strukturreferenz (Detail)

- `_config.yml` – globale Site-Einstellungen
- `_data/navigation.yml` – oberes Menü
- `_pages/*.md` – statische Seiten (URL via `permalink`)
- `_posts/*.md` – Blog-Posts (Dateiname = Datum + Slug)
- `assets/images/` – Bilder (Avatar, Teaser, Header)
- `Gemfile` – Ruby-Abhängigkeiten (nicht anfassen)
- `_site/` – Build-Ausgabe (gitignored, nie committen)

## Links

- Theme-Doku: <https://mmistakes.github.io/minimal-mistakes/docs/>
- Live-Site: <https://pdyroy.github.io>
