# HTML Erklärt !! noch nicht fertig !!

## Wichtige Merkmale

- **Struktur**:  
Es umschließt alle anderen Elemente einer Webseite (außer der `<!DOCTYPE html>`-Deklaration).  
Innerhalb von `<html>` befinden sich immer genau zwei Bereiche:  
`<head>` (Metadaten) und `<body>` (sichtbare Inhalte).

- **Sprachfestlegung**:  
Es ist Best Practice, das Attribut `lang` zu verwenden  
(z. B. `<html lang="de">`), um Suchmaschinen und Screenreadern  
die Sprache der Seite mitzuteilen.

- **Pflicht-Tag**:  
Jedes gültige HTML5-Dokument **muss** dieses Tag enthalten.

## Übersicht Aufbau

<!DOCTYPE html>: Keine Tag im eigentlichen Sinne, sondern die Deklaration für HTML5.
- **`<html>`**: Das Wurzelelement, umschließt das gesamte Dokument.
- **`<head>`**: Enthält Metainformationen (Titel, Scripte, CSS-Links), die nicht direkt auf der Seite erscheinen.
- **`<body>`**: Umschließt den gesamten sichtbaren Inhalt der Webseite.

    <!DOCTYPE html>
    <html lang="de">
    <head>
        <title>Titel der Seite</title>
    </head>
    <body>
        <h1>Hallo Welt!</h1>
    </body>
    </html>

1. Grundgerüst (Struktur-Tags)

Diese Tags bilden das Skelett jeder Webseite:

## <!DOCTYPE html>

    <!DOCTYPE html>

Die `<!DOCTYPE html>`-Deklaration teilt dem Browser mit, dass es sich um ein **HTML5-Dokument** handelt.  
Sie ist **kein HTML-Tag**, sondern eine notwendige Anweisung für den korrekten Darstellungsmodus.

## `<html>` Tag

Das `<html>`-Tag ist das **Wurzelelement (Root-Element)** eines HTML-Dokuments.  
Es signalisiert dem Browser, dass der gesamte darin enthaltene Code als HTML interpretiert werden soll. Es hat einen offenen und geschlossenen Tag.

    <html></html>

## 2. Text-Strukturierung & Semantik

Diese Tags geben dem Inhalt Bedeutung und helfen Suchmaschinen (SEO):

- `<h1>` bis `<h6>`: Überschriften (h1 ist die wichtigste).
- `<p>`: Definiert einen Textabsatz (Paragraph).
- `<strong>`: Hebt Text fett hervor (starke semantische Betonung).
- `<em>`: Hebt Text kursiv hervor (Akzentuierung).
- `<br>`: Erzwingt einen Zeilenumbruch (selbstschließendes Tag).
- `<hr>`: Zeichnet eine horizontale Linie zur thematischen Trennung.
