# HTML Erklärt

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

1. Grundgerüst (Struktur-Tags)

Diese Tags bilden das Skelett jeder Webseite:

## Übersicht Aufbau

    <!DOCTYPE html>
    <html lang="de">
    <head>
        <title>Titel der Seite</title>
    </head>
    <body>
        <h1>Hallo Welt!</h1>
    </body>
    </html>

## < html > Tag

Das `<html>`-Tag ist das **Wurzelelement (Root-Element)** eines HTML-Dokuments.  
Es signalisiert dem Browser, dass der gesamte darin enthaltene Code als HTML interpretiert werden soll.



    <!DOCTYPE html>: Keine Tag im eigentlichen Sinne, sondern die Deklaration für HTML5.
    <html>: Das Wurzelelement, umschließt das gesamte Dokument.
    <head>: Enthält Metainformationen (Titel, Scripte, CSS-Links), die nicht direkt auf der Seite erscheinen.
    <body>: Umschließt den gesamten sichtbaren Inhalt der Webseite.

2. Text-Strukturierung & Semantik
Diese Tags geben dem Inhalt Bedeutung und helfen Suchmaschinen (SEO).

    <h1> bis <h6>: Überschriften (h1 ist die wichtigste).
    <p>: Definiert einen Textabsatz (Paragraph).
    <strong>: Hebt Text fett hervor (starke semantische Betonung).
    <em>: Hebt Text kursiv hervor (Akzentuierung).
    <br>: Erzwingt einen Zeilenumbruch (selbstschließendes Tag).
    <hr>: Zeichnet eine horizontale Linie zur thematischen Trennung.

3. Listen & Verweise

    <a>: Erstellt einen Hyperlink (Attribut href erforderlich).
    <ul>: Ungeordnete Liste (Aufzählungszeichen).
    <ol>: Geordnete Liste (Nummerierung).
    <li>: Einzelnes Listenelement innerhalb von <ul> oder <ol>.

4. Medien & Container

    <img>: Bindet ein Bild ein (Attribute src und alt sind Pflicht).
    <div>: Ein allgemeiner Block-Container zur Gruppierung von Elementen (für CSS-Styling).
    <span>: Ein Inline-Container für Textabschnitte.

5. Semantische HTML5-Tags (Layout)
Verbessern die Struktur für Barrierefreiheit und SEO.

    <header>: Kopfbereich einer Seite oder eines Abschnitts.
    <nav>: Enthält Navigationslinks.
    <main>: Markiert den Hauptinhalt der Seite.
    <section>: Definiert einen thematischen Abschnitt.
    <article>: Für eigenständige Inhalte (z. B. Blogposts).
    <footer>: Fußbereich einer Seite.

## Ausführliches Beispiel

<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Meine Beispielseite 2025</title>
</head>
<body>
    <header>
        <h1>Willkommen auf meiner Website</h1>
        <nav>
            <ul>
                <li><a href="#info">Informationen</a></li>
                <li><a href="https://developer.mozilla.org" target="_blank">MDN Web Docs</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="info">
            <h2>Über HTML</h2>
            <p>HTML ist die <strong>Standard-Markupsprache</strong> für Webseiten. 
            Mit HTML5 stehen uns viele <em>semantische Elemente</em> zur Verfügung.</p>
            
            <hr>
            
            <h3>Wichtige Werkzeuge:</h3>
            <ul>
                <li>Ein Texteditor (z. B. VS Code)</li>
                <li>Ein moderner Webbrowser</li>
                <li>Gute Dokumentationen</li>
            </ul>
        </section>

        <section>
            <h2>Ein Bild sagt mehr als Worte</h2>
            <img src="beispiel.jpg" alt="Ein schönes Beispielbild" width="300">
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Mein Web-Nachschlagewerk</p>
    </footer>
</body>
</html>
