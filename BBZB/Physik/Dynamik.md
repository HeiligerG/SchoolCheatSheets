# Physik Grundlagen - Bewegung und Kräfte

## 1. Geschwindigkeit

Geschwindigkeit beschreibt, wie viel Strecke in einer gewissen Zeit zurückgelegt wird. Sie ist eine vektorielle Größe mit Betrag und Richtung und kann gemessen werden.

### Einheiten:
- SI-Einheit: m/s (Meter pro Sekunde)
- Alltagseinheit: km/h (Kilometer pro Stunde)

### Umrechnungen:
- m/s zu km/h: Wert × 3,6
- km/h zu m/s: Wert ÷ 3,6

### Formeln:
- Formelzeichen: v
- Mittlere Geschwindigkeit: v = Δs / Δt
  - Δs = Streckenänderung [m]
  - Δt = Zeitänderung [s]
- Momentane Geschwindigkeit: v(t) = ds/dt

### Weg-Zeit-Gesetz:
- s(t) = 0,5 · a · t² + v₀ · t + s₀
  - s₀ = Anfangsposition [m]
  - v₀ = Anfangsgeschwindigkeit [m/s]
  - a = Beschleunigung [m/s²]
  - t = Zeit [s]

## 2. Gleichförmige Bewegung

Bei gleichförmiger Bewegung ist die Geschwindigkeit konstant (a = 0).

### Formeln:
- s(t) = v · t + s₀
- v = konstant
- a = 0

## 3. Gleichmäßig beschleunigte Bewegung

Die Beschleunigung a beschreibt die Änderung der Geschwindigkeit über einen Zeitraum. Sie ist ebenfalls eine vektorielle Größe mit Betrag und Richtung.

### Einheit:
- m/s² (Meter pro Sekunde zum Quadrat)

### Formeln:
- Beschleunigung: a = Δv / Δt
- Geschwindigkeits-Zeit-Gesetz: v(t) = a · t + v₀
- Weg-Zeit-Gesetz: s(t) = 0,5 · a · t² + v₀ · t + s₀

### Wichtig:
- Die Richtung der Beschleunigung sollte immer in Diagrammen eingezeichnet werden
- Eine negative Beschleunigung bedeutet Verzögerung (Bremsung)

## 4. Schiefe Ebene

Bei der schiefen Ebene wirkt ein Teil der Gewichtskraft in Richtung der Ebene.

### Szenarien:
- Die Masse ruht (Kräftegleichgewicht)
- Die Masse bewegt sich mit konstanter Geschwindigkeit (Kräftegleichgewicht)
- Die Masse beschleunigt (resultierende Kraft wirkt hangabwärts)

### Formeln:
- Hangabtriebskraft: FH = FG · sin(α) = m · g · sin(α)
  - FG = Gewichtskraft [N]
  - m = Masse [kg]
  - g = Erdbeschleunigung (≈ 9,81 m/s²)
  - α = Neigungswinkel der Ebene [°]
- Normalkraft: FN = FG · cos(α) = m · g · cos(α)

## 5. Reibungskräfte

Reibungskräfte wirken der Bewegung entgegen oder verhindern das Einsetzen einer Bewegung.

### Arten von Reibung:
1. **Haftreibung** - verhindert das Einsetzen einer Bewegung
2. **Gleitreibung** - behindert eine bereits bestehende Bewegung
3. **Rollreibung** - tritt bei rollenden Körpern auf

### Allgemeine Formel:
- R = μ · FN
  - R = Reibungskraft [N]
  - μ = Reibungskoeffizient (dimensionslos)
  - FN = Normalkraft [N]

### Haftreibung:
- RH = μH · FN
- An der schiefen Ebene: RH = FN · tan(α)
- Wichtig: Haftreibung ist unabhängig von der Auflagefläche
- Haftreibung ist abhängig von der Rauheit der Oberflächen und der Normalkraft

### Gleitreibung:
- RG = μG · FN
- In der Regel gilt: μG < μH
- Gleitreibung ist ein dynamisches Phänomen

### Rollreibung:
- RR = μR · FN
- In der Regel gilt: μR < μG < μH
- Daher ist Rollen energetisch günstiger als Gleiten

### Prinzip zur Reibung ohne Masse

**Herleitung**

Wenn du eine Reibungskraft wie $R = \mu \cdot F_N$ hast und sie in die Bewegungsgleichung $F = m \cdot a$ einsetzt, passiert Folgendes:

$$a = \frac{R}{m} = \frac{\mu \cdot F_N}{m}$$

Und da auf einer horizontalen Fläche die Normalkraft ist:  

$$F_N = m \cdot g$$

Dann ergibt sich:

$$a = \frac{\mu \cdot m \cdot g}{m} = \mu \cdot g$$

**Die Masse kürzt sich raus!**

---

 **Merksatz:**

> **„Bei Reibungsverzögerung auf horizontaler Fläche hängt die Bremswirkung nur von $\mu$ und $g$ ab – nicht von der Masse!"**

Dadurch kannst du auch **ohne Masse** den Weg, die Beschleunigung oder die Zeit berechnen, wenn ein Körper durch Reibung abbremst.

### Anwendungsformeln

**Beschleunigung durch Reibung:**
$$a = -\mu \cdot g$$

**Bremsweg:**
$$s = \frac{v_0^2}{2 \cdot \mu \cdot g}$$

**Bremszeit:**
$$t = \frac{v_0}{\mu \cdot g}$$

**Geschwindigkeit nach einer bestimmten Zeit:**
$$v(t) = v_0 - \mu \cdot g \cdot t$$

**Geschwindigkeit nach einer bestimmten Strecke:**
$$v(s) = \sqrt{v_0^2 - 2 \cdot \mu \cdot g \cdot s}$$

**Beispiel**

Ein Auto fährt mit 50 km/h (≈ 13,9 m/s) auf einer horizontalen Straße. Der Reibungskoeffizient zwischen Reifen und Straße beträgt $\mu = 0,7$.

**Bremsweg:**
$$s = \frac{v_0^2}{2 \cdot \mu \cdot g} = \frac{13,9^2}{2 \cdot 0,7 \cdot 9,81} ≈ \frac{193,2}{13,7} ≈ 14,1 \text{ m}$$

**Bremszeit:**
$$t = \frac{v_0}{\mu \cdot g} = \frac{13,9}{0,7 \cdot 9,81} ≈ \frac{13,9}{6,87} ≈ 2,0 \text{ s}$$

**Verzögerung:**
$$a = -\mu \cdot g = -0,7 \cdot 9,81 ≈ -6,9 \text{ m/s}^2$$

**Besonderheiten**

- Diese Vereinfachung gilt nur für die Gleitreibung auf horizontalen Flächen
- Bei geneigten Flächen kommt der Einfluss des Winkels hinzu
- Die Formel zeigt, warum bei gleichem Reibungskoeffizienten alle Körper gleich schnell fallen oder gleich stark bremsen, unabhängig von ihrer Masse
- Dies erklärt auch, warum ein leichter und ein schwerer LKW den gleichen Bremsweg haben (bei identischen Reifen und Straßenbedingungen)

## 6. Kräfte allgemein

### Einheit:
- Newton [N] = kg·m/s²

### Newtonsche Gesetze:
1. **Trägheitsgesetz**: Ein Körper verharrt im Zustand der Ruhe oder der gleichförmigen Bewegung, solange keine Kraft auf ihn einwirkt.
2. **Grundgesetz der Dynamik**: F = m · a
3. **Wechselwirkungsgesetz**: Actio = Reactio

### Wichtige Kräfte:
- Gewichtskraft: FG = m · g
- Federkraft: FF = D · s (mit Federkonstante D)
- Zentripetalkraft: FZ = m · v² / r

## 7. Impuls und Energie

### Impuls:
- p = m · v [kg·m/s]
- Impulserhaltungssatz: In einem abgeschlossenen System bleibt der Gesamtimpuls konstant

### Kinetische Energie:
- Ekin = 0,5 · m · v² [J]

### Potentielle Energie:
- Lageenergie: Epot = m · g · h [J]
- Spannenergie: Espann = 0,5 · D · s² [J]

### Energieerhaltungssatz:
- In einem abgeschlossenen System bleibt die Gesamtenergie konstant
- Eges = Ekin + Epot = konstant
