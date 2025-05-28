# 🐳 Docker Cheatsheet - Inhaltsverzeichnis

## 1. Dateioperationen & Persistenz
- [Docker CP, Bind Mounts & Volumes](01_Copy-Bind_Mounts&Volumes.md)
  - Docker CP - Datei in Container kopieren
  - Bind Mounts - Live-Synchronisation mit Host
  - Volumes - Persistente Datenspeicherung
  - Vergleich der Methoden

## 2. Docker Volumes
- [Volumes mit Docker - Daten dauerhaft speichern](02_Volumes.md)
  - Benannte Volumes erstellen
  - Volumes verwalten
  - Praktisches Beispiel mit MariaDB

## 3. Netzwerke
- [Docker-Netzwerke - Container vernetzen](03_Network.md)
  - Netzwerkarten in Docker
  - Bridge-Netzwerk verstehen
  - Eigene Netzwerke erstellen
  - Kommunikation zwischen Containern
  - Debugging & Analyse
- [Container mit Docker-Netzwerken verbinden & trennen](04_NetworkBridge.md)
  - Container mit mehreren Netzwerken
  - Netzwerkverbindungen hinzufügen und entfernen
  - Prüfen der Netzwerkkonfiguration

## 4. Praktische Anwendungen
- [WordPress mit MariaDB & phpMyAdmin](05_WP&MariaDB&PhpMyAdmin.md)
  - Komplettes Setup mit Netzwerk
  - Datenbank konfigurieren
  - WordPress einrichten

---

## Übersicht der Hauptthemen

| Cheatsheet | Kernthemen | Praktische Anwendung |
|------------|------------|----------------------|
| CP, Mounts & Volumes | Datenaustausch, Synchronisation | Entwicklungsumgebungen |
| Volumes | Persistente Datenspeicherung | Datenbanken, Konfigurationsdateien |
| Netzwerke | Container-Kommunikation | Microservices, Multi-Container-Apps |
| WordPress-Setup | Komplettlösung | Webhosting, CMS-Deployment |