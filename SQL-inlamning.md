# SQL-inlämning — Diskografi

**Namn:** [David Billfeldt]  
**Artist:** [Greta Van Fleet]  
**Datum:** [18-10-2026]

---

> Lägg länk till eller bild på ditt ER-diagram här:
> `[ER-diagram](er_diagram.png)`

---

## 1. Skapa databasen — CREATE TABLE

```sql
PRAGMA foreign_keys = ON;

CREATE TABLE artists (
                         id           INTEGER PRIMARY KEY,
                         name         TEXT NOT NULL,
                         formed_year  INTEGER,
                         country      TEXT
);

```

---

## 2. Seeda med data — INSERT

```sql
--- skriv din SQL-kod här ---

```

---

## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---


--- query 2: Lista alla låtar på ett specifikt album ---


--- query 3: Antal låtar per album ---


--- query 4: Längsta låten ---


--- query 5: Alla låtar sorterade alfabetiskt ---

```

---

## 4. Lägg till en ny rad — INSERT

```sql
--- lägg till ett nytt album eller en ny låt ---

```

---

## 5. Ta bort en rad — DELETE

```sql
--- ta bort en rad ur valfri tabell ---

```

---

## 6. Uppdatera en rad — UPDATE

```sql
--- uppdatera minst en rad i valfri tabell ---

```

---

## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---


--- query 7: Albumet med flest låtar ---


--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---

```
