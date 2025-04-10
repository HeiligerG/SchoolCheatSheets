## 💻 **MongoDB Shell – Arbeiten mit Datenbanken**

---

### 🚀 **Starten der Shell**

```bash
mongosh
```

Mit Verbindung zu Remote-Datenbank (Cloud, Docker, Port etc.):

```bash
mongosh "mongodb://localhost:27017"
```

---

## 📂 **Datenbank-Basics**

| Befehl                       | Funktion                                      |
|-----------------------------|-----------------------------------------------|
| `show dbs`                  | Alle vorhandenen Datenbanken anzeigen         |
| `use <dbName>`              | Zu Datenbank wechseln / neu erstellen         |
| `db`                        | Aktuelle Datenbank anzeigen                   |

> Datenbank wird **erst gespeichert**, wenn Dokumente vorhanden sind.

---

## 📁 **Collections verwalten**

| Befehl                              | Funktion                         |
|-------------------------------------|----------------------------------|
| `db.getCollectionNames()`           | Zeigt alle Collections           |
| `db.createCollection("name")`       | Neue Collection erstellen        |
| `db.<alt>.renameCollection("neu")`  | Collection umbenennen            |
| `db.<name>.drop()`                  | Collection löschen               |

---

## ✍️ **CREATE – Daten einfügen**

### Einzelnes Dokument

```js
db.item.insertOne({ name: "Tastatur", price: 15 })
```

### Mehrere Dokumente

```js
db.item.insertMany([
  { name: "Monitor", price: 150 },
  { name: "Maus", price: 10 },
  { name: "Lautsprecher", price: 40 }
])
```

---

## 🔍 **READ – Daten abfragen**

### Alles anzeigen

```js
db.item.find()
```

### Nach Attributwert filtern

```js
db.item.find({ name: "Tastatur" })
```

### Vergleichsoperatoren

| Operator | Bedeutung                 | Beispiel                          |
|----------|---------------------------|-----------------------------------|
| `$eq`    | gleich                    | `{ price: { $eq: 40 } }`          |
| `$ne`    | ungleich                 | `{ price: { $ne: 40 } }`          |
| `$gt`    | größer                   | `{ price: { $gt: 40 } }`          |
| `$gte`   | größer oder gleich       | `{ price: { $gte: 40 } }`         |
| `$lt`    | kleiner                  | `{ price: { $lt: 40 } }`          |
| `$lte`   | kleiner oder gleich      | `{ price: { $lte: 40 } }`         |

---

### Logische Operatoren

```js
db.item.find({
  $and: [
    { price: { $gt: 10 } },
    { price: { $lt: 100 } }
  ]
})
```

---

### Ausgabe einschränken (Projektion)

```js
db.item.find({}, { name: true, _id: false })
```

> Nur `name` wird angezeigt, `_id` wird ausgeblendet.