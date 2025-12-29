# HTML Erklärt

**Status:** Noch in Arbeit

## Wichtige Merkmale

- **Struktur**:
Ist ein Baumstruktur mit einem `<html>`-Tag als **Wurzelelement (Root-Element)**. Innerhalb von `<html>` befinden sich immer genau zwei Bereiche:  
`<head>` (Metadaten) und `<body>` (sichtbare Inhalte).
Elemente werden durch Tags () definiert, die oft Paare bilden (Start- und End-Tag wie `<p>...</p>`).
Wichtige semantische Strukturelemente sind Überschriften (`<h1>–<h6>`), Absätze (`<p>`), Listen (`<ul>, <ol>`), Abschnitte (`<section>`) und Navigation (`<nav>`), um Inhalte logisch zu gliedern.

- **Sprachfestlegung**:  
Es ist Best Practice, das Attribut `lang` zu verwenden  
(`<html lang="de">`), um Suchmaschinen und Screenreadern  
die Sprache der Seite mitzuteilen.

- **Pflicht-Elemente**:  
Jedes gültige HTML5-Dokument **muss** die Elemente `html`, `head` und `body` enthalten. Wenn man es vergisst, ergänzt es der Browser automatisch (si werden nicht automatisch in die Datei eingefügt, sondern nur im Browser intern ergänzt).
`<!DOCTYPE html>`-Deklaration, die ganz am Anfang der Datei stehen muss, um dem Browser mitzuteilen, dass es sich um HTML5 handelt, und um eine korrekte Darstellung sicherzustellen.
Jedes HTML5-Dokument **sollte** die Basisstruktur enthalten:
`<!DOCTYPE html>`, `<html>`, `<head>` (mit `<meta charset="UTF-8">` und `<title>`), `<body>`, da diese das Dokument definieren, Metadaten (wie den Titel für Browser-Tabs/Suchmaschinen) bereitstellen und den sichtbaren Inhalt umschließen, wobei auch semantische Tags wie `<header>`, `<nav>`, `<main>`, `<footer>` und Überschriften (`<h1>` bis `<h6>`) für Struktur und SEO entscheidend sind.

## Übersicht Aufbau

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <title>Titel der Seite</title>
</head>
<body>
    <h1>Hallo Welt!</h1>
</body>
</html>
```

---

1. Grundgerüst (Struktur-Tags)

Diese Tags bilden das Skelett jeder Webseite:

## <!DOCTYPE html>

    `<!DOCTYPE html>`

Die `<!DOCTYPE html>`- Keine Tag im eigentlichen Sinne, sondern die Deklaration für HTML5. Deklaration teilt dem Browser mit, dass es sich um ein **HTML5-Dokument** handelt.  
Sie ist **kein HTML-Tag**, sondern eine notwendige Anweisung für den korrekten Darstellungsmodus.

## **`<html>`** Tag

Das Wurzelelement, umschließt das gesamte Dokument. Es signalisiert dem Browser, dass der gesamte darin enthaltene Code als HTML interpretiert werden soll. Es hat einen offenen und geschlossenen Tag.
Es umschließt alle anderen Elemente einer Webseite (außer der `<!DOCTYPE html>`-Deklaration).  

    <html> </html>

- **`<head>`**: Enthält Metainformationen (Titel, Scripte, CSS-Links), die nicht direkt auf der Seite erscheinen.

    ``` <html>
        <head>
            <meta charset="UTF-8">
            <title>Seitentitel</title>
        </head>
    </html>
    ```

- **`<body>`**: Umschließt den gesamten sichtbaren Inhalt der Webseite, wie Texte, Überschriften, Bilder, Links, Videos, Tabellen, Listen usw. Er fungiert als Container für alles, was der Besucher der Website sieht.

        ```<html>
        <head></head>
        <body>
            <h1>Willkommen</h1>
            <p>Dies ist der sichtbare Inhalt.</p>
        </body>
    </html>```

## 2. Text-Strukturierung & Semantik

Diese Tags geben dem Inhalt Bedeutung und helfen Suchmaschinen (SEO):

- **`<h1>` bis `<h6>`**: Für Überschriften. h1 ist die wichtigste und sollte nur einmal pro Seite verwendet werden, da sie das Hauptthema darstellt. Die Reihenfolge h1-h6 muss logisch eingehalten werden, um die Struktur für Nutzer und Suchmaschinen zu wahren (z. B. H2 als Unterpunkt von H1, H3 als Unterpunkt von H2) – man darf nicht überspringen oder rückwärts springen (h2 und danach h4 geht nicht). Bei neuen Sektionen beginnt man einfach mit der nächsten logischen Ebene (wieder mit h2 und danach mit h3) und folgt dann wieder der Reihenfolge.
Regeln für Überschriften h1-h6:
**h1 Einmal pro Seite**: Die wichtigste Überschrift, der Titel der Seite, sollte nur einmal vorkommen, um das Hauptthema klar zu definieren.
**Logische Hierarchie (h2-h6)**: Muss man der Reihenfolge folgen. Ein h2 ist unter h2, danach kommt h3 und so weiter. Vermeide Sprünge wie h2 -> h4.
**Häufigkeit**: h2, h3, h4 usw. können mehrmals verwendet werden, solange es der Struktur dient. Oft reichen h1-h3 für die meisten Seiten aus. Ein h2 nach einem zB. h4 nur benutzen, wenn es neue Section anfängt.

```html
<html>
    <head></head>
    <body>
        <h1>Hauptthema</h1>
        <h2>Unterthema</h2>
        <h3>Unterthema</h3>
        <h4>Unterthema</h4>
        <h5>Unterthema</h5>
        <h6>Unterthema</h6>
    </body>
</html>
```

### Weitere Text-Tags

- **`<p>`**: Definiert einen Textabsatz (Paragraph).
- **`<strong>`**: Hebt Text fett hervor (starke semantische Betonung).
- **`<em>`**: Hebt Text kursiv hervor (Akzentuierung). Screenreader erkennen es und können die Betonung auch hörbar machen.
- **`<br>`**: Erzwingt einen Zeilenumbruch (selbstschließendes Tag).
- **`<hr>`**: Zeichnet eine horizontale Linie zur Trennung.

---

## 3. Listen & Verweise

### Links: `<a>`

Erstellt einen Hyperlink (Attribut `href` erforderlich).

```html
<p>Diese Seite <a href="https://www.seite.de">Link Name</a> ist verlinkt.</p>
```

### Ungeordnete Liste: `<ul>`

```html
<ul>
    <li>Apfel</li>
    <li>Hundefutter</li>
    <li>Batterien</li>
</ul>
```

### Geordnete Liste: `<ol>`

```html
<ol>
    <li>Erster Schritt</li>
    <li>Zweiter Schritt</li>
    <li>Dritter Schritt</li>
</ol>
```

### Listenelement: `<li>`

Einzelnes Listenelement. `<li>`-Elemente werden innerhalb von `<ul>` oder `<ol>` verwendet.

---

## 4. Medien & Container

- `<img>`: Bindet ein Bild ein (`src` und `alt` sind Pflicht).

    `<img src="pfad/zum/bild.jpg" alt="Beschreibung des Bildes">`

- `<div>`:  Der `<div>` Tag ist ein universeller Container, um andere HTML-Elemente zu gruppieren und logische Abschnitte auf einer Webseite zu erstellen, die dann mittels CSS gestylt oder mit JavaScript manipuliert werden können. Er hat keine eigene semantische Bedeutung, dient rein der Strukturierung und ist besonders nützlich für Layouts (z. B. mit Flexbox/Grid). Ohne Styling ist ein `<div>` unsichtbar (der `<div>`, nicht sein Inhalt!), wird aber als Block-Element behandelt, was einen Zeilenumbruch erzeugt und die volle Breite einnimmt

```html
<div class="produkt-box">
    <h2>Produkt A</h2>
    <p>Beschreibung von Produkt A.</p>
</div>
```

- `<span>`: Ist dafür da um generischer (= es hat keine vordefinierte Bedeutung oder Darstellung. Es ist nur ein Werkzeug) Inline-Container für Textabschnitte ohne visuelle Veränderung zu markieren, damit sie mit CSS gestylt (Farbe, Schriftgröße) oder mit JavaScript manipuliert werden können, ohne den Textfluss zu unterbrechen. Das heißt: Im Gegensatz zu Block-Elementen wie `<div>`, bleibt der `<span>` in derselben Zeile, wo es platziert wird, und erzeugt keinen Zeilenumbruch. Sie funktionieren wie ein "Haken" (Hook) für gezielte Formatierungen innerhalb einer Zeile oder eines Absatzes. Wie dem `<div>` weist man dem `<span>` eine Klasse oder ID zu, um es mit CSS zu gestalten.

```html
<p>Dies ist ein normaler Satz. <span class="hervorhebung">Dieser Teil wird gelb hinterlegt</span> und hier geht der Satz normal weiter.</p>
```

---

## 5. Semantische HTML-Tags (Layout)

Diese Tags verbessern Struktur, Barrierefreiheit und SEO (=Suchmaschinenoptimierung):

- `<header>`: Kopfbereich einer Seite oder eines Abschnitts.

Diese Tags befinden sich im <head>-Bereich des HTML-Dokuments. Sie sind für den Besucher unsichtbar, aber essenziell für die Kommunikation mit Suchmaschinen und dem Browser:
<title>: Dies ist das wichtigste On-Page-SEO-Element. Er legt den Titel der Seite fest, der oben im Browser-Tab und als klickbare Überschrift in den Suchergebnissen (SERPs) angezeigt wird. Ein prägnanter Titel verbessert das Ranking und die Klickrate.

- `<meta>`: Zusammenfassung, beeinflusst Klicks, obwohl Google oft eigene Beschreibungen generiert.

    `<meta name=”name” content=”content”>`

## Meta-Informationen & SEO

- `<title>`: Legt den Titel der Webseite fest, der im Browser-Tab und als Hauptüberschrift in den Suchergebnissen erscheint. Er ist das wichtigste HTML-Element, um Suchmaschinen das Thema der Seite zu signalisieren.

```html
<title>HTML Glossar: SEO-Tags richtig nutzen</title>
```

- `<meta name="description">`: Enthält eine kurze Zusammenfassung des Inhalts. Suchmaschinen nutzen diesen Text für das Snippet in den Suchergebnissen. Er dient als Werbetext, um die Klickrate (CTR) der Nutzer zu erhöhen.

    `<meta name="description" content="Ein umfassendes Glossar über HTML-Tags, die Ihre Suchmaschinenoptimierung verbessern.">`

- `<meta name="viewport">`: Dieser Tag ist zwingend erforderlich für das responsive Design. Er sorgt dafür, dass die Webseite auf Mobilgeräten korrekt skaliert wird, was ein kritischer Rankingfaktor für Google ist.

    `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

- `<meta name="robots">`: Gibt Anweisungen an Suchmaschinen-Crawler, ob eine Seite indexiert werden soll oder ob Links auf der Seite verfolgt werden dürfen.

    `<meta name="robots" content="index, follow">`

- `<link rel="canonical">`: Verweist auf die Original-URL einer Webseite. Dies verhindert Probleme mit doppeltem Inhalt (Duplicate Content), indem es Google mitteilt, welche Version der Seite in den Suchindex gehört.

    `<link rel="canonical" href="www.deineseite.de">`

- `<meta charset="UTF-8">`: Legt die Zeichenkodierung fest. Dies stellt sicher, dass Umlaute und Sonderzeichen weltweit in jedem Browser korrekt dargestellt werden und verhindert Darstellungsfehler.

    `<meta charset="UTF-8">`

- `<nav>`: Navigationsbereich.
- `<main>`: Hauptinhalt der Seite.
- `<section>`: Thematischer Abschnitt.
- `<article>`: Eigenständiger Inhalt (z. B. Blogpost).
- `<footer>`: Fußbereich der Seite.

## Vollständiges html

```html
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
                <li><a href="https://dasisteinlink.de" target="_blank">Verlinkung zu</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="info">
            <h2>Über HTML</h2>
            <p>HTML ist die <strong>Standard-Markupsprache</strong> für Webseiten. 
            Mit HTML5 stehen uns viele <em>semantische Elemente</em> zur Verfügung.</p>
            <p>Das ist ein Absatz mit p Tag. <strong>Das ist dick mit Strong-Tag gemacht.</strong> für Webseiten. 
            <em>Kursiver Text mit em Tag.</em></p>
            
            <hr>
            
            <h3>Das ist eine Liste:</h3>
            <ul>
                <li>Einzelne Listen-Elemente</li>
                <li>Ein Texteditor (z.B. VS Code)</li>
                <li>Ein moderner Webbrowser</li>
                <li>Gute Dokumentationen</li>
            </ul>
        </section>

        <section>
            <div>
                <h2>H2 Überschrift: Ein Bild sagt mehr als Worte</h2>
                <h3>H3 Überschrift</h3>
                <p>Hier drunter ist ein Bild mit img-Tag</p>
                <img src="beispiel.jpg" alt="Ein schönes Beispielbild" width="300">
            </div>
        </section>
    </main>

    <footer>
        <p>&copy; Im Footer: 2025 Mein Web-Nachschlagewerk</p>
    </footer>
</body>
</html>
```
