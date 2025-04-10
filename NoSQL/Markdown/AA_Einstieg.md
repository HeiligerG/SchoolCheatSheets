## 🍃 **NoSQL mit MongoDB – lokal & in der Cloud**

---

### 📦 **Was ist MongoDB?**

MongoDB ist eine **NoSQL-Datenbank**, die Daten im **JSON-ähnlichen Format (BSON)** speichert. Sie ist flexibel, schemalos und ideal für moderne Webanwendungen.

---

### 🧱 **Grundaufbau MongoDB (Konzept)**

```
Cluster > Server > Datenbank > Collection > Document
```

- **Document**: Datensatz im JSON-Format
- **Collection**: Gruppe von Documents
- **Database**: Sammlung von Collections
- **Cluster**: Sammlung von MongoDB-Servern

---

### ⚙️ **Lokale Installation (nur nötig, wenn ohne Docker)**

- MongoDB Server: [mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
- Mongo Shell (mongosh): [mongodb.com/try/download/shell](https://www.mongodb.com/try/download/shell)

**Service prüfen:**

```bash
# Linux
sudo systemctl status mongod

# Windows
get-service mongodb
```

**Shell starten:**

```bash
mongosh
```

---

### 🧪 **Testverbindung lokal**

```bash
mongosh
```

Danach kannst du direkt mit Befehlen wie `show dbs` oder `use test` arbeiten.

---

### ☁️ **MongoDB Atlas – Cloud-Datenbank**

1. Registrieren unter [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Cluster erstellen (Free Tier reicht)
3. Neuen **Datenbankbenutzer** anlegen unter *Security > Database Access*
4. **IP-Zugriff** konfigurieren unter *Security > Network Access*

---

### 🔑 **Zugriff über die Shell (Cloud)**

1. In Atlas → **Database** → „Connect“
2. **„Connect with MongoDB Shell“** auswählen
3. Connection-String kopieren & einfügen

```bash
mongosh "mongodb+srv://<CLUSTER>.mongodb.net/myFirstDatabase" --username <username>
```

Dann Passwort eingeben.

---

### 📁 **Datenbank & Collections anlegen**

```js
use music

db.createCollection("songs")
db.createCollection("gigs")

db.songs.insertOne({ title: "Rainy Day", artist: "Nova", duration: 215 })
db.gigs.insertOne({ location: "Zurich", date: "2025-06-12", band: "Nova" })
```

---

### 🔒 **Benutzer mit eingeschränkten Rechten anlegen (nur Cloud GUI)**

- Benutzer `readonly_songs` → Zugriff **nur auf Collection `songs`**
- Login testen → `show dbs` darf nur `music` anzeigen

---

### 🌍 **Netzwerkzugriff prüfen**

- IP blockieren: Zugriff schlägt fehl
- Zugriff für **alle IPs erlauben**: Wiederherstellung der Verbindung

---

### 🐳 **MongoDB im Docker-Container betreiben**

**Standard-Start (Port 27017):**
```bash
docker run -d --name mongo -p 27017:27017 mongo
```

**Custom-Port (z. B. 55555):**
```bash
docker run -d --name mongo_custom -p 55555:27017 mongo
```

---

### 🧬 **Verbindung via Shell zum Container**

```bash
mongosh "mongodb://localhost:55555"
```

Ab da funktioniert die Shell wie gewohnt.

---

### 🔎 **JSON Basics (MongoDB-Datenstruktur)**

```json
{
  "vorname": "Lena",
  "name": "Müller",
  "alter": 24,
  "adresse": {
    "strasse": "Bahnhofstrasse 12",
    "plz": 8001,
    "ort": "Zürich"
  },
  "kinder": ["Max", "Anna"]
}
```

- **Key** = Attributname
- **Value** = Wert (String, Number, Array, Object, etc.)