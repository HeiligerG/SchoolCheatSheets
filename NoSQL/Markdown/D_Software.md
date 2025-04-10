## 🐍 **MongoDB mit Python – `pymongo` praktisch einsetzen**

---

### 🔌 **1. Verbindung herstellen**

```python
from pymongo import MongoClient

client = MongoClient("mongodb://localhost:27017/")
print(client.server_info())
```

---

### 📂 **2. Datenbankzugriff**

```python
db = client["inf"]
```

- Erst beim Speichern eines Dokuments wird die DB wirklich angelegt

---

### 📁 **3. Collection-Zugriff**

```python
col = db["module"]
```

---

## ✍️ **CRUD in Python mit `pymongo`**

---

### ➕ **Create**

```python
col.insert_one({ "number": 165, "description": "NoSQL-Datenbanken einsetzen" })
```

---

### 🔍 **Read**

```python
print(col.find_one())  # Erstes Dokument

# Mit Filter
for m in col.find({ "number": { "$gt": 100 } }):
    print(m)
```

---

### 🔄 **Update**

```python
col.update_one(
    { "number": 165 },
    { "$set": { "description": "NoSQL verstehen" } }
)
```

---

### ❌ **Delete**

```python
col.delete_one({ "number": 165 })
```

---

### 🆔 **Suche mit ID**

```python
import bson

_id = bson.ObjectId("644a6d1c6ad2ed9113095057")
doc = col.find_one({ "_id": _id })
```

---

## 🔗 **Existenz prüfen**

```python
if "admin" in client.list_database_names():
    print("DB exists")

if "module" in db.list_collection_names():
    print("Collection exists")
```

---

## 🧰 **Objekte als Dokumente speichern**

```python
class Room():
    def __init__(self, name, seats, is_reservable, _id=None):
        if _id: self._id = _id
        self.name = name
        self.seats = seats
        self.is_reservable = is_reservable

room = Room("Pilatus", 12, True)
col.insert_one(room.__dict__)
```

---

### 🔄 **Objekt aus DB lesen**

```python
room = Room(**col.find_one())
```

---

## 🧱 **Data Access Object (DAO)**

```python
class DaoRoom():
    def __init__(self, conn):
        self.col = MongoClient(conn)["buildings"]["rooms"]

    def create(self, room):
        self.col.insert_one(room.__dict__)

    def read(self):
        return Room(**self.col.find_one())
```