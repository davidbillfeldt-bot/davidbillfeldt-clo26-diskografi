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
CREATE TABLE albums (
                        id            INTEGER PRIMARY KEY,
                        title         TEXT NOT NULL,
                        release_year  INTEGER,
                        artist_id     INTEGER NOT NULL,
                        FOREIGN KEY (artist_id) REFERENCES artists(id)
);

CREATE TABLE songs (
                       id                INTEGER PRIMARY KEY,
                       title             TEXT NOT NULL,
                       duration_seconds  INTEGER,
                       track_number      INTEGER,
                       album_id          INTEGER NOT NULL,
                       FOREIGN KEY (album_id) REFERENCES albums(id)
);

```

---

## 3. Söka — SELECT

```sql
SELECT * FROM albums
ORDER BY release_year;


SELECT * FROM songs
WHERE album_id = 3
ORDER BY track_number;


SELECT album_id, COUNT(*)
FROM songs
GROUP BY album_id;


SELECT * FROM songs
ORDER BY duration_seconds DESC
    LIMIT 1;


SELECT * FROM songs
ORDER BY title;


```

---

## 4. Lägg till en ny rad — INSERT

```sql
INSERT INTO songs (title, duration_seconds, track_number, album_id)
VALUES ('Play Your Games', 195, 9, 1);

```

---

## 5. Ta bort en rad — DELETE

```sql
DELETE FROM songs WHERE id = 10;
```

---

## 6. Uppdatera en rad — UPDATE

```sql
UPDATE songs
SET album_id = 1
WHERE id IN (7, 8, 9);

```

---

## 7. VG-queries (om du siktar på VG)

```sql
SELECT album_id, ROUND(AVG(duration_seconds), 0) AS snittlangd
FROM songs
GROUP BY album_id;


--- query 7: Albumet med flest låtar ---
SELECT album_id, COUNT(*) AS antal
FROM songs
GROUP BY album_id
ORDER BY antal DESC
    LIMIT 1;

--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---
SELECT songs.title, songs.duration_seconds, albums.title AS album
FROM songs
         JOIN albums ON songs.album_id = albums.id
WHERE songs.duration_seconds > 240;
```
