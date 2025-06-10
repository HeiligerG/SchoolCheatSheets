# Docker Compose CheatSheet - Modul 347

## 📚 Inhaltsverzeichnis

- [Docker Compose CheatSheet - Modul 347](#docker-compose-cheatsheet---modul-347)
  - [📚 Inhaltsverzeichnis](#-inhaltsverzeichnis)
  - [📋 YAML Grundlagen](#-yaml-grundlagen)
    - [YAML vs JSON](#yaml-vs-json)
    - [Arrays und Objekte](#arrays-und-objekte)
    - [Variablen und Referenzen](#variablen-und-referenzen)
  - [🐳 Docker Compose Struktur](#-docker-compose-struktur)
    - [Grundlegende compose.yaml](#grundlegende-composeyaml)
    - [Services Definition](#services-definition)
  - [⚙️ Service-Konfiguration](#️-service-konfiguration)
    - [Basis-Optionen](#basis-optionen)
    - [Umgebungsvariablen](#umgebungsvariablen)
    - [Volumes](#volumes)
    - [Netzwerk \& Ports](#netzwerk--ports)
    - [Abhängigkeiten](#abhängigkeiten)
  - [🔨 Docker Compose Befehle](#-docker-compose-befehle)
    - [Starten \& Stoppen](#starten--stoppen)
    - [Build \& Management](#build--management)
    - [Debugging](#debugging)
  - [🏗️ Praktische Beispiele](#️-praktische-beispiele)
    - [Einfacher Web-Stack](#einfacher-web-stack)
    - [Datenbank mit phpMyAdmin](#datenbank-mit-phpmyadmin)
    - [WordPress Stack](#wordpress-stack)
    - [Flask + Redis + Nginx](#flask--redis--nginx)
    - [PostgreSQL + pgAdmin](#postgresql--pgadmin)
  - [🎯 Profile \& Skalierung](#-profile--skalierung)
    - [Service-Profile](#service-profile)
    - [Skalierung](#skalierung)
  - [🔐 Sicherheit \& Best Practices](#-sicherheit--best-practices)
    - [.env Dateien](#env-dateien)
    - [Secrets](#secrets)
    - [Best Practices](#best-practices)
  - [🔄 Typische Workflows](#-typische-workflows)
    - [Entwicklung](#entwicklung)
    - [Produktion](#produktion)
    - [Debugging](#debugging-1)
  - [⚠️ Wichtige Hinweise](#️-wichtige-hinweise)
    - [Volume-Management](#volume-management)
    - [Netzwerk](#netzwerk)
    - [Restart-Policies](#restart-policies)

<div style="page-break-before: always;"></div>

## 📋 YAML Grundlagen

### YAML vs JSON

**JSON:**
```json
{
  "key": "Wert",
  "key2": "asdfgg\nTest"
}
```

**YAML:**
```yaml
key: Wert
key2: "asdfgg\nTest"
```

### Arrays und Objekte

**Einfaches Array:**
```yaml
themen:
  - Syntax
  - Listen
  - Objekte
  - Referenzen
```

**Array mit Objekten:**
```yaml
personen:
  - name: Anna
    rolle: Lehrerin
  - name: Tom
    rolle: Lernender
```

### Variablen und Referenzen

```yaml
name: &lernender Max Mustermann
best_lernender: *lernender

hauptperson: &haupt Max Mustermann
beste_person: *haupt
```

<div style="page-break-before: always;"></div>


## 🐳 Docker Compose Struktur

### Grundlegende compose.yaml

```yaml
services:
  service-name:
    image: image-name
    # oder
    build: ./path
    
volumes:
  volume-name:
    
networks:
  network-name:
```

**Wichtig:** `version: '3'` ist veraltet und nicht mehr erforderlich!

### Services Definition

```yaml
services:
  web:
    image: nginx
    build: ./app
    container_name: my_web
    ports:
      - "8080:80"
    volumes:
      - ./data:/app/data
    environment:
      - ENV_VAR=value
    depends_on:
      - db
    restart: always
```

## ⚙️ Service-Konfiguration

### Basis-Optionen

```yaml
services:
  app:
    image: nginx                    # Verwende Image
    build: ./path                   # Baue aus Dockerfile
    container_name: my_container    # Container-Name setzen
    command: ["nginx", "-g", "daemon off;"]  # Command überschreiben
```

### Umgebungsvariablen

```yaml
services:
  app:
    environment:
      - MYSQL_ROOT_PASSWORD=password
      - MYSQL_DATABASE=mydb
      - DEBUG=true
    # oder
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: mydb
```

<div style="page-break-before: always;"></div>

**Mit .env-Datei:**
```yaml
services:
  db:
    environment:
      - MYSQL_ROOT_PASSWORD=${DB_PASSWORD}
```

### Volumes

**Named Volumes:**
```yaml
services:
  db:
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
    name: custom_db_name
```

**Bind Mounts:**
```yaml
services:
  web:
    volumes:
      - ./website:/usr/share/nginx/html:ro
      - ./config:/etc/nginx/conf.d
```

### Netzwerk & Ports

```yaml
services:
  web:
    ports:
      - "8080:80"        # Host:Container
      - "443:443"
      - "80"             # Nur Container-Port (auto-assign Host)
    expose:
      - "3000"           # Nur für andere Container
```

### Abhängigkeiten

```yaml
services:
  web:
    depends_on:
      - db
      - redis
    restart: always              # always, no, on-failure, unless-stopped
    restart: on-failure:10       # Max 10 Versuche
```

<div style="page-break-before: always;"></div>

## 🔨 Docker Compose Befehle

### Starten & Stoppen

```bash
# Standard starten
docker compose up

# Im Hintergrund starten
docker compose up -d

# Mit bestimmten Profilen
docker compose --profile frontend up

# Stoppen
docker compose down

# Stoppen mit Volume-Löschung
docker compose down -v

# Pause/Unpause
docker compose pause
docker compose unpause
```

### Build & Management

```bash
# Bauen (bei Dockerfile-Änderungen)
docker compose up --build

# Nur bauen ohne starten
docker compose build

# Einzelnen Service bauen
docker compose build web

# Services skalieren
docker compose up --scale web=3

# Logs anzeigen
docker compose logs
docker compose logs web
```

### Debugging

```bash
# Laufende Services anzeigen
docker compose ps

# In Container einsteigen
docker compose exec web bash

# Kommando in Service ausführen
docker compose run web ls -la

# Container neu starten
docker compose restart web
```

<div style="page-break-before: always;"></div>

## 🏗️ Praktische Beispiele

### Einfacher Web-Stack

```yaml
services:
  web:
    image: nginx
    ports:
      - "7080:80"
  
  web2:
    build: ./httpd
    ports:
      - "7081:80"
```

### Datenbank mit phpMyAdmin

```yaml
services:
  db:
    image: mariadb
    environment:
      - MARIADB_ROOT_PASSWORD=sml12345
      - MARIADB_DATABASE=blog
      - MARIADB_USER=blog
      - MARIADB_PASSWORD=sml12345
    restart: always
    volumes:
      - db_data:/var/lib/mysql

  pma:
    image: phpmyadmin
    environment:
      - PMA_HOST=db
    ports:
      - "6080:80"
    restart: always
    depends_on:
      - db

volumes:
  db_data:
    name: db_data_wordpress
```

<div style="page-break-before: always;"></div>

### WordPress Stack

```yaml
services:
  db:
    image: mariadb
    environment:
      - MYSQL_ROOT_PASSWORD=sml12345
      - MARIADB_DATABASE=blog
      - MARIADB_USER=blog
      - MARIADB_PASSWORD=sml12345
    restart: on-failure:10
    volumes:
      - db_data:/var/lib/mysql
    profiles:
      - backend

  wp:
    image: wordpress
    environment:
      - WORDPRESS_DB_HOST=db
      - WORDPRESS_DB_USER=blog
      - WORDPRESS_DB_PASSWORD=sml12345
      - WORDPRESS_DB_NAME=blog
    ports:
      - "6081:80"
    restart: on-failure:10
    depends_on:
      - db
    volumes:
      - wp_data:/var/www/html
    profiles:
      - frontend

  pma:
    image: phpmyadmin
    environment:
      - PMA_HOST=db
    ports:
      - "6080:80"
    restart: on-failure:10
    depends_on:
      - db
    profiles:
      - debug

volumes:
  db_data:
    name: db_data_wordpress
  wp_data:
    name: wp_data_wordpress
```

<div style="page-break-before: always;"></div>

### Flask + Redis + Nginx

```yaml
services:
  flask:
    build: .
    container_name: flask_app
    depends_on:
      - redis
    environment:
      - REDIS_HOST=redis

  redis:
    image: redis:alpine
    container_name: redis_cache

  nginx:
    image: nginx
    ports:
      - "3333:80"
    depends_on:
      - flask
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
```

### PostgreSQL + pgAdmin

```yaml
services:
  postgres:
    image: postgres
    environment:
      - POSTGRES_DB=uebungsdatenbank
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./init:/docker-entrypoint-initdb.d

  pgadmin:
    image: dpage/pgadmin4
    environment:
      - PGADMIN_DEFAULT_EMAIL=admin@example.com
      - PGADMIN_DEFAULT_PASSWORD=admin
    ports:
      - "5050:80"
    volumes:
      - pgadmin_data:/var/lib/pgadmin
    depends_on:
      - postgres

volumes:
  postgres_data:
  pgadmin_data:
```

<div style="page-break-before: always;"></div>

## 🎯 Profile & Skalierung

### Service-Profile

```yaml
services:
  db:
    image: mariadb
    profiles:
      - backend
      
  web:
    image: nginx
    profiles:
      - frontend
      
  debug:
    image: phpmyadmin
    profiles:
      - debug
```

**Verwendung:**
```bash
# Nur Frontend
docker compose --profile frontend up

# Mehrere Profile
docker compose --profile frontend --profile debug up

# Alle Services ohne Profile + bestimmte Profile
docker compose --profile debug up
```

### Skalierung

```yaml
services:
  web:
    image: nginx
    ports:
      - "80"  # Automatische Port-Zuweisung
    deploy:
      replicas: 3
```

**Manuell skalieren:**
```bash
docker compose up --scale web=5
```

## 🔐 Sicherheit & Best Practices

### .env Dateien

**.env:**
```env
DB_PASSWORD=sml12345
MYSQL_ROOT_PASSWORD=supersecret
API_KEY=your-secret-key
```

<div style="page-break-before: always;"></div>

**compose.yaml:**
```yaml
services:
  db:
    environment:
      - MYSQL_ROOT_PASSWORD=${DB_PASSWORD}
      - API_KEY=${API_KEY}
```

### Secrets

```yaml
services:
  app:
    secrets:
      - db_password
      - api_key

secrets:
  db_password:
    file: ./secrets/db_password.txt
  api_key:
    external: true
```

### Best Practices

1. **Verwenden Sie .env für sensible Daten**
2. **Named Volumes für Datenpersistenz**
3. **depends_on für Service-Reihenfolge**
4. **restart: on-failure für Produktionsumgebungen**
5. **Profile für verschiedene Umgebungen**
6. **Bind Mounts nur für Entwicklung**
7. **Spezifische Image-Tags (nicht latest)**

## 🔄 Typische Workflows

### Entwicklung
```bash
# Mit Build starten
docker compose up --build

# Logs verfolgen
docker compose logs -f

# Service neu starten
docker compose restart web
```

### Produktion
```bash
# Im Hintergrund starten
docker compose up -d

# Status prüfen
docker compose ps

# Updates
docker compose pull
docker compose up -d
```

<div style="page-break-before: always;"></div>

### Debugging
```bash
# Container-Details
docker compose ps
docker compose logs service-name

# In Container einsteigen
docker compose exec service-name bash

# Neue Container-Instanz für Debugging
docker compose run service-name bash
```

## ⚠️ Wichtige Hinweise

### Volume-Management
- **Named Volumes** überleben `docker compose down`
- **Bind Mounts** spiegeln lokale Dateien direkt
- Bei DB-Passwort-Änderungen: Volume neu erstellen!

### Netzwerk
- Services können sich über Service-Namen erreichen
- `depends_on` garantiert nur Start-Reihenfolge, nicht Verfügbarkeit
- `links` ist deprecated, verwenden Sie Service-Namen

### Restart-Policies
- `no`: Niemals neu starten
- `always`: Immer neu starten
- `on-failure`: Nur bei Fehlern
- `unless-stopped`: Außer manuell gestoppt

---
*Erstellt für Modul 347 - Docker Compose Prüfungsvorbereitung*