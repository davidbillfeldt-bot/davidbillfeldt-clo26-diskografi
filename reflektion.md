# Reflektion — Inlämning 1

**Namn:** [David Billfeldt]  
**Datum:** [18-10-2026]

---

## Vad var svårast?

I början var det svårt att förstå skillnaden mellan en tabell och en kolumn,
till exempel skrev jag `FROM album_id` i stället för `FROM songs`. Jag råkade
också lägga in dubletter av albumen och några låtar fick fel album_id, vilket
jag fick rätta med DELETE och UPDATE. Det tog också en stund att få ordning på
Git, Rider och ER-diagrammet.
Använde mig även av AI för att förstå och felsöka syntax 
---

## Vad lärde du dig?

Jag lärde mig skapa tabeller med primary keys och foreign keys, fylla dem med min
data med INSERT och hitta rätt data med SELECT, WHERE, ORDER BY, GROUP BY, COUNT,
AVG och LIMIT. Jag lärde mig också hur en JOIN fungerar (tillslut) och hur man bygger ett
many-to-many-förhållande med en kopplingstabell.
OBS GLÖM EJ WHERE NÄR DU KÖR DELETE...
---

## Hur använde du SQL i praktiken — vad kändes naturligt och vad var förvirrande?

Enkla queries som att sortera album efter år eller låtar i bokstavsordning
kändes naturliga, eftersom SQL nästan läses som vanlig engelska. GROUP BY var
mer förvirrande i början, men det klarnade när jag tänkte på det som att lägga
låtarna i högar per album och sedan räkna varje hög. JOIN var också förvirrande
tills jag förstod att den matchar album_id i songs med id i albums.

---

## Om du hade mer tid — vad hade du lagt till eller gjort annorlunda?

Jag hade lagt till fler album och låtar, och kanske tabeller för turnéer eller
samarbeten med andra artister. Jag hade också planerat datan noggrannare från
början, så att jag inte hade behövt rätta dubletter och fel album_id i efterhand.

---

## (VG) Varför valde du just den här tabellstrukturen?

Resonera kring ditt designval: Vad hade hänt om du löst det på ett annat sätt? Vilka för- och nackdelar ser du med din lösning jämfört med ett alternativ?

Jag delade upp artister, album och låtar i egna tabeller så att varje uppgift
bara lagras på ett ställe (3NF). Om jag till exempel hade skrivit albumtiteln
direkt på varje låt hade samma titel upprepats många gånger, och om den behövde
ändras skulle jag behöva uppdatera flera rader och riskera att missa någon. Nu
räcker det att ändra den på ett ställe i albums.
Foreign keys ligger på "många"-sidan: ett album har många låtar, därför har
songs ett album_id och inte tvärtom.
För genrer valde jag en kopplingstabell (song_genres) eftersom en låt kan ha
flera genrer och en genre kan finnas på flera låtar. Ett alternativ hade varit
en genre-kolumn i songs, men då kan varje låt bara ha en genre. Ett annat hade
varit att skriva flera genrer i samma fält, som "Hard Rock, Blues Rock", men det
bryter mot normaliseringen och gör det svårt att söka. Nackdelen med min lösning
är att den kräver fler tabeller och JOINs för att visa datan, men den är mer
flexibel och undviker dubbel information.
