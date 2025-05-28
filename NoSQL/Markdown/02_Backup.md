## 💾 **MongoDB Backups & Wiederherstellung**

---

### 🔧 **Was brauchst du?**

📦 [MongoDB Database Tools](https://www.mongodb.com/try/download/database-tools)  
→ Enthält `mongodump` und `mongorestore` (für Backup & Restore)

---

### 📤 **Export (Backup) einer Datenbank**

```bash
mongodump --uri="<URI>" --db=<DBNAME> --username=<USER> --out=<OUTPUT>
```

🔑 **Parameter:**
- `<URI>` = Connection-String (z. B. aus MongoDB Atlas)
- `<DBNAME>` = Name der Datenbank
- `<USER>` = Benutzername (optional)
- `<OUTPUT>` = Zielordner für das Backup

📝 Erzeugt ein Ordner mit dem Namen `<OUTPUT>`, der `.bson`-Dateien enthält.

---

### 📥 **Import (Wiederherstellung)**

```bash
mongorestore --uri="<URI>" --db=<DBNAME> --username=<USER> <INPUT>
```

🔑 **Parameter:**
- `<INPUT>` = Pfad zum Dump-Ordner (z. B. `backup_folder/music/`)
- Andere Parameter wie oben

✅ Stellt die Datenbank aus dem angegebenen Verzeichnis wieder her.

---

### 🛠 **Beispiel – Lokale Instanz**

```bash
mongodump --db=music --out=db_backup
mongorestore --db=music_restored db_backup/music
```

---

## 🧪 **Automatisches Backup per Shell-Skript**

### 🔃 Backup erstellen und im Ordner `db_backup` speichern

```bash
#!/bin/bash

BACKUP_DIR=db_backup
DATE=$(date +%Y_%m_%d)
TARGET="$BACKUP_DIR/$DATE"

mongodump --db=music --out=$TARGET

# Maximal 10 Backups behalten
cd $BACKUP_DIR
ls -1tr | head -n -10 | xargs -d '\n' rm -rf --
```

---

### ⏰ **Tägliche Ausführung um 02:00 Uhr (via `cron`)**

```bash
crontab -e
```

🔽 Cron-Eintrag hinzufügen:

```
0 2 * * * /pfad/zum/skript/backup.sh
```

---

### ✅ **Best Practices:**

| Tipp | Warum |
|------|-------|
| Immer mit `--db` arbeiten | Nur gewünschte Datenbank sichern |
| Namen mit Datum versehen | Versionierung einfach halten |
| Backups regelmäßig prüfen | Korrupte Dumps nützen nichts |
| Altlasten löschen (z. B. nach 10 Tagen) | Speicherverbrauch minimieren |