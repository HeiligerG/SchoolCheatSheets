## 🔹 **Volumes mit Docker – Daten dauerhaft speichern**

---

### 🧱 **Benanntes Volume erstellen und mit einem Container verknüpfen**

Mit einem Volume kannst du sicherstellen, dass Daten erhalten bleiben, selbst wenn der Container gelöscht wird.

```powershell
docker run -d -v my_mariadb_data:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=sml12345 mariadb
```

- `-v my_mariadb_data:/var/lib/mysql`: Mountet das Volume `my_mariadb_data` auf das Standard-Datenverzeichnis von MariaDB.
- `-e MARIADB_ROOT_PASSWORD=...`: Setzt das Root-Passwort für MariaDB.

---

### 🔍 **Mount überprüfen**

```powershell
docker ps       # Container-ID kopieren
docker inspect -f "{{.Mounts}}" <CONTAINER_ID>
```

Du solltest etwas Ähnliches sehen wie:

```
[{volume my_mariadb_data ... /var/lib/mysql ...}]
```

---

### 📦 **Alle Volumes anzeigen**

```powershell
docker volume ls
```

Das benannte Volume `my_mariadb_data` wird hier gelistet und bleibt erhalten – auch wenn du den Container stoppst oder löschst.

---

### 🧹 **Volumes löschen (Vorsicht!)**

Wenn du versuchst, ein Volume zu löschen, das noch mit einem (auch gestoppten) Container verknüpft ist:

```powershell
docker volume rm <VOLUME_NAME>
```

… bekommst du **eine Fehlermeldung**, z. B.:

```
volume is in use - [<CONTAINER_ID>]
```

🔧 Lösung:

```powershell
docker rm <CONTAINER_ID>
docker volume rm <VOLUME_NAME>
```

Nur wenn **kein Container mehr das Volume benutzt**, kannst du es entfernen.

---

### 🧪 **Beispiel: Automatisch generiertes Volume**

Wenn du **kein Volume angibst**, erstellt Docker automatisch eins:

```powershell
docker run -d -e MARIADB_ROOT_PASSWORD=sml12345 mariadb
```

Mit `docker volume ls` siehst du ein kryptisch benanntes Volume, das mit dem Container verknüpft wurde.

⚠️ Auch hier: Erst den Container löschen, **dann** das Volume entfernen.

---

### 🧰 **Persistente Datenbank mit MariaDB & Volume**

MariaDB mit Volume + echte Daten rein:

```powershell
docker run -d -v maria_db:/var/lib/mysql --name old_db -e MARIADB_ROOT_PASSWORD=sml12345 mariadb:10.5
```

Dann rein in die DB:
```powershell
docker exec -it old_db mysql -u root -psml12345
```

In der SQL-Shell:

```sql
CREATE DATABASE docker_containers_db;
USE docker_containers_db;

CREATE TABLE docker_containers_table (
  CONTAINER_ID VARCHAR(13),
  IMAGE VARCHAR(20),
  NAME VARCHAR(20)
);

INSERT INTO docker_containers_table VALUES
('605adf483577', 'mariadb', 'mariadb-test'),
('582c5cdbe015', 'mysql', 'mysql-test'),
('e09e0b567f53', 'postgres', 'postgres-test');

SELECT * FROM docker_containers_table;
```

Erwartete Ausgabe:

```
+--------------+----------+---------------+
| CONTAINER_ID | IMAGE    | NAME          |
+--------------+----------+---------------+
| 605adf483577 | mariadb  | mariadb-test  |
| 582c5cdbe015 | mysql    | mysql-test    |
| e09e0b567f53 | postgres | postgres-test |
+--------------+----------+---------------+
```

Beende die MySQL-Shell mit:
```sql
exit;
```

Dann den Container stoppen:
```powershell
docker stop old_db
```

Das Volume `maria_db` bleibt erhalten und enthält die komplette Datenbank – **persistente Speicherung funktioniert** ✅