## 🧠 **Allgemeine Struktur beim Googeln**
```
[Problem] [Programmiersprache] [Framework/Tool] [Fehlercode (wenn vorhanden)] [Kontext]
```
> Beispiel: `TypeError map is not a function JavaScript React array`

### Inhaltsverzeichnis: Google-Suchtipps für Programmierer

1. [Allgemeine Struktur beim Googeln](#allgemeine-struktur-beim-googeln)
2. [Effektive Suchbegriffe & Operatoren](#effektive-suchbegriffe--operatoren)
3. [Programmier-spezifische Begriffe](#programmier-spezifische-begriffe-die-du-kombinieren-kannst)
4. [Fehlermeldungen richtig googeln](#fehlermeldungen-richtig-googeln)
5. [Tipps nach Programmiersprache](#tipps-nach-programmiersprache)
   - [Python](#python)
   - [JavaScript / React / Node](#javascript--react--node)
   - [C/C++/Java](#ccjava)
6. [Spezielle Google-Tricks für Entwickler](#spezielle-google-tricks-für-entwickler)
7. [Top-Websites für Programmierer](#top-websites-für-programmierer)
8. [Beispiel-Suchanfragen](#beispiel-suchanfragen)
9. [Docker-Suchbegriffe & -Beispiele](#docker-suchbegriffe---beispiele)
10. [Spezifische Beispiel-Suchanfragen für Docker](#spezifische-beispiel-suchanfragen-für-docker)
11. [Bonus: Docker-Spezifische Seiten zum Googeln](#bonus-docker-spezifische-seiten-zum-googeln-mit-site)
12. [Power-Search-Tipp für Docker](#power-search-tipp-für-docker)
---

## 🔍 **Effektive Suchbegriffe & Operatoren**

| Operator | Bedeutung | Beispiel |
|----------|-----------|----------|
| `"`      | **Genauer Wortlaut** | `"TypeError: undefined is not a function"` |
| `site:`  | **Nur auf einer bestimmten Website suchen** | `site:stackoverflow.com react router redirect` |
| `filetype:` | **Bestimmte Dateitypen suchen** | `python tutorial filetype:pdf` |
| `OR`     | **Entweder das oder das** | `python OR javascript web scraping` |
| `-`      | **Ausschließen** | `javascript map -site:w3schools.com` |
| `*`      | **Platzhalter (Wildcard)** | `how to * in javascript` |

---

## 🔧 **Programmier-spezifische Begriffe, die du kombinieren kannst**

| Kategorie | Suchbegriffe |
|----------|--------------|
| Fehlersuche | `error`, `exception`, `traceback`, `stack trace`, `debug`, `crash`, `not working` |
| Hilfe bei Syntax | `syntax`, `syntax error`, `invalid`, `expected` |
| Wie etwas geht | `how to`, `example`, `tutorial`, `best practice`, `sample code`, `implementation` |
| Erklärung | `what is`, `why`, `difference between`, `vs`, `explanation`, `docs` |
| Performance | `optimize`, `performance`, `slow`, `benchmark`, `fastest` |
| Tools & Frameworks | `React`, `Django`, `Pandas`, `Tailwind`, etc. |

---

## 🧩 **Fehlermeldungen richtig googeln**

1. **Original lassen**, aber überflüssige Pfade/IDs entfernen:  
   Statt:  
   `File "/home/user/project/main.py", line 34, in <module>`  
   → Nutze:  
   `main.py line 34 in module`

2. **Wichtige Teile isolieren:**  
   Nur den Fehler:  
   `IndexError: list index out of range Python`

3. **Auf Englisch übersetzen, wenn du eine deutsche Meldung bekommst**

---

## ⚙️ **Tipps nach Programmiersprache**

- **Python**  
  - `python [modul] example`  
  - `python pandas iterate over dataframe`  
  - `python [fehler] stackoverflow`

- **JavaScript / React / Node**  
  - `javascript async await example`  
  - `react useEffect fetch data`  
  - `nodejs fs readfile async`

- **C/C++/Java**  
  - `c segmentation fault`  
  - `java nullpointerexception fix`  
  - `c++ vector vs array performance`

---

## 💎 **Spezielle Google-Tricks für Entwickler**

- `inurl:` – Nur Ergebnisse mit bestimmten Wörtern in der URL  
  → `inurl:docs.python.org requests`

- `intitle:` – Nur Ergebnisse mit bestimmten Wörtern im Titel  
  → `intitle:"react hooks"`

- `define:` – Für Definitionen  
  → `define:closure in javascript`

---

## 📚 **Top-Websites für Programmierer**

| Website | Inhalt |
|--------|--------|
| [stackoverflow.com](https://stackoverflow.com) | Fehlerbehebung, Beispiele |
| [dev.to](https://dev.to) | Blogposts, Tipps, Community |
| [github.com](https://github.com) | Repos, echte Beispiele |
| [mdn web docs](https://developer.mozilla.org) | JavaScript, HTML, CSS Doku |
| [geeksforgeeks.org](https://geeksforgeeks.org) | Theorie & Praxis |
| [w3schools.com](https://w3schools.com) | Grundsyntax (vorsichtig geniessen 😄) |

---

## 🛠️ Beispiel-Suchanfragen

- ✅ `how to filter a list in python`
- ✅ `TypeError: cannot read property 'map' of undefined react`
- ✅ `css center div horizontally and vertically flexbox`
- ✅ `best way to validate email in javascript`

---

## 🐳 **Docker-Suchbegriffe & -Beispiele**

Docker kann tricky sein – hier sind Begriffe, die du mit anderen Keywords kombinieren solltest:

| Thema | Suchbegriffe / Beispiele |
|-------|---------------------------|
| Container starten / stoppen | `docker start`, `docker stop`, `docker restart`, `docker run example` |
| Container-Logs | `docker logs container_name`, `docker container log error` |
| Fehlerbehebung | `docker build failed`, `docker image not found`, `dockerfile permission denied` |
| Netzwerk / Ports | `docker port mapping`, `docker expose port not working`, `docker network bridge` |
| Volumes & Daten | `docker volume mount`, `docker bind mount vs volume`, `docker volume not updating` |
| Dockerfile | `dockerfile copy not working`, `dockerfile install python`, `multi-stage docker build` |
| Images | `docker image size too big`, `docker pull from private registry`, `docker image tag latest` |
| Compose | `docker-compose up`, `docker-compose env file`, `docker-compose restart service` |
| Debug | `docker exec -it container /bin/bash`, `docker inspect`, `docker ps -a` |

---

## 🔍 **Spezifische Beispiel-Suchanfragen für Docker**

- ✅ `dockerfile nodejs app example`
- ✅ `docker build permission denied`
- ✅ `docker-compose postgres persistent data`
- ✅ `docker container exited with code 137`
- ✅ `how to share volume between docker containers`
- ✅ `docker run -p explained`
- ✅ `docker nginx reverse proxy example`

---

## 🛠️ Bonus: Docker-Spezifische Seiten zum Googeln mit `site:`

| Website | Warum es hilft |
|--------|----------------|
| `site:docs.docker.com` | Offizielle Dokumentation, immer aktuell |
| `site:stackoverflow.com docker` | Konkrete Probleme & Lösungen |
| `site:github.com` | Beispiele für Dockerfiles, docker-compose.yml |
| `site:medium.com docker` | Artikel & Tutorials |
| `site:dev.to docker` | Dev-Perspektive, moderne Best Practices |

---

## 🔥 Power-Search-Tipp für Docker:

Wenn du nach einem **Fehler in einem Container** suchst:
```
[Fehlermeldung] docker container logs OR docker build error
```

Oder wenn du ein **Problem beim Build hast:**
```
failed to solve with frontend dockerfile.v0 site:stackoverflow.com
```
