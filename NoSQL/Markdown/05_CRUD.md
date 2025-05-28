## 🧾 **MongoDB CRUD – Schnellstart, einfach erklärt**

---

### 🧠 Was ist CRUD?

| Buchstabe | Bedeutung | Was es macht       |
|-----------|-----------|--------------------|
| C         | Create    | Daten einfügen     |
| R         | Read      | Daten auslesen     |
| U         | Update    | Daten verändern    |
| D         | Delete    | Daten löschen      |

---

## 🔧 Vorbereitung

### Starte die MongoDB Shell:
```bash
mongosh
```

Oder verbinde dich zu deiner DB:
```bash
mongosh "mongodb://localhost:27017"
```

---

### 1️⃣ Wähle oder erstelle deine Datenbank:
```js
use meine_datenbank
```

### 2️⃣ Wähle oder erstelle eine Collection (Tabelle):
```js
db.createCollection("produkte")
```

---

## ✅ **C – Create: Neue Daten einfügen**

### Ein einzelnes Produkt:
```js
db.produkte.insertOne({ name: "Tastatur", preis: 30 })
```

### Mehrere Produkte auf einmal:
```js
db.produkte.insertMany([
  { name: "Monitor", preis: 120 },
  { name: "Maus", preis: 15 }
])
```

💡 MongoDB erstellt automatisch ein `_id`-Feld für jedes Dokument (wie eine eindeutige ID).

---

## 🔎 **R – Read: Daten finden**

### Alle Daten anzeigen:
```js
db.produkte.find()
```

### Nur ein Ergebnis:
```js
db.produkte.findOne()
```

### Filtern: Nur Produkte mit preis = 15
```js
db.produkte.find({ preis: 15 })
```

### Größer als 20:
```js
db.produkte.find({ preis: { $gt: 20 } })
```

---

## ✏️ **U – Update: Daten ändern**

### Einen Eintrag ändern:

```js
db.produkte.updateOne(
  { name: "Tastatur" },
  { $set: { preis: 35 } }
)
```

➡️ Ändert nur **einen** passenden Eintrag.

### Alle mit preis = 15 auf preis = 20 ändern:

```js
db.produkte.updateMany(
  { preis: 15 },
  { $set: { preis: 20 } }
)
```

---

## ❌ **D – Delete: Daten löschen**

### Einen Eintrag löschen:

```js
db.produkte.deleteOne({ name: "Maus" })
```

### Mehrere löschen:

```js
db.produkte.deleteMany({ preis: { $lt: 25 } })
```

---

## 🪄 **Bonus: Nur bestimmte Felder anzeigen (Projektion)**

```js
db.produkte.find({}, { name: true, _id: false })
```

➡️ Zeigt **nur den Namen** aller Produkte, ohne `_id`.

---

## 📌 Tipp: Schnell alles zurücksetzen

```js
db.produkte.drop()
```

➡️ Löscht die ganze Collection `produkte`.

---

### 🧠 Merken:

- `insertOne`, `insertMany` = Einfügen
- `find`, `findOne` = Lesen
- `updateOne`, `updateMany` + `$set` = Ändern
- `deleteOne`, `deleteMany` = Löschen