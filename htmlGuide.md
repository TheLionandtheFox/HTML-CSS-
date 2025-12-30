# HTML Erklärt

> **Status:** Noch in Arbeit

## Wichtige Merkmale

### Struktur

HTML ist eine Baumstruktur mit einem `<html>`-Tag als **Wurzelelement (Root-Element)**. Innerhalb von `<html>` befinden sich immer genau zwei Bereiche: `<head>` (Metadaten) und `<body>` (sichtbare Inhalte).

Elemente werden durch Tags (`< >`) definiert, die oft Paare bilden (Start- und End-Tag wie `<p>...</p>`).

#### Wichtige semantische Strukturelemente sind

- Überschriften (`<h1>` bis `<h6>`)
- Absätze (`<p>`)
- Listen (`<ul>`, `<ol>`)
- Abschnitte (`<section>`)
- Navigation (`<nav>`)

### Sprachfestlegung

Es ist Best Practice, das Attribut `lang` zu verwenden (`<html lang="de">`), um Suchmaschinen und Screenreadern die Sprache der Seite mitzuteilen.

### Pflicht-Elemente

Jedes gültige HTML5-Dokument **muss** die Elemente `html`, `head` und `body` enthalten. Wenn man sie vergisst, ergänzt sie der Browser automatisch (sie werden nicht automatisch in die Datei eingefügt, sondern nur im Browser intern ergänzt).

Die `<!DOCTYPE html>`-Deklaration muss ganz am Anfang der Datei stehen, um dem Browser mitzuteilen, dass es sich um HTML5 handelt, und um eine korrekte Darstellung sicherzustellen.

#### Jedes HTML5-Dokument **sollte** die Basisstruktur enthalten

- `<!DOCTYPE html>`
- `<html>`
- `<head>` (mit `<meta charset="UTF-8">` und `<title>`)
- `<body>`

Diese Elemente definieren das Dokument, stellen Metadaten bereit (wie den Titel für Browser-Tabs/Suchmaschinen) und umschließen den sichtbaren Inhalt. Auch semantische Tags wie `<header>`, `<nav>`, `<main>`, `<footer>` und Überschriften (`<h1>` bis `<h6>`) sind für Struktur und SEO entscheidend.

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

## 1. Grundgerüst (Struktur-Tags)

Diese Tags bilden das Skelett jeder Webseite.

### `<!DOCTYPE html>`

```html
<!DOCTYPE html>
```

Die `<!DOCTYPE html>`-Deklaration ist **kein Tag** im eigentlichen Sinne, sondern eine notwendige Anweisung für den Browser. Sie teilt dem Browser mit, dass es sich um ein **HTML5-Dokument** handelt und stellt den korrekten Darstellungsmodus sicher.

### `<html>`-Tag

Das Wurzelelement umschließt das gesamte Dokument. Es signalisiert dem Browser, dass der gesamte darin enthaltene Code als HTML interpretiert werden soll. Es hat einen öffnenden und schließenden Tag und umschließt alle anderen Elemente einer Webseite (außer der `<!DOCTYPE html>`-Deklaration).

```html
<html> </html>
```

### `<head>`-Tag

Enthält Metainformationen (Titel, Scripte, CSS-Links), die nicht direkt auf der Seite erscheinen.

```html
<html>
    <head>
        <meta charset="UTF-8">
        <title>Seitentitel</title>
    </head>
</html>
```

### `<body>`-Tag

Umschließt den gesamten sichtbaren Inhalt der Webseite, wie Texte, Überschriften, Bilder, Links, Videos, Tabellen, Listen usw. Er fungiert als Container für alles, was der Besucher der Website sieht.

```html
<html>
    <head></head>
    <body>
        <h1>Willkommen</h1>
        <p>Dies ist der sichtbare Inhalt.</p>
    </body>
</html>
```

---

## 2. Text-Strukturierung & Semantik

Diese Tags geben dem Inhalt Bedeutung und helfen Suchmaschinen (SEO).

### Überschriften: `<h1>` bis `<h6>`

Für Überschriften. `<h1>` ist die wichtigste und sollte nur einmal pro Seite verwendet werden, da sie das Hauptthema darstellt.

#### Regeln für Überschriften h1-h6

- **h1 einmal pro Seite**: Die wichtigste Überschrift, der Titel der Seite, sollte nur einmal vorkommen, um das Hauptthema klar zu definieren.
- **Logische Hierarchie (h2-h6)**: Man muss der Reihenfolge folgen. Ein h2 ist unter h1, danach kommt h3 und so weiter. Vermeide Sprünge wie h2 → h4.
- **Häufigkeit**: h2, h3, h4 usw. können mehrmals verwendet werden, solange es der Struktur dient. Oft reichen h1-h3 für die meisten Seiten aus.
- Ein h2 nach einem z.B. h4 nur benutzen, wenn eine neue Section anfängt.

Die Reihenfolge h1-h6 muss logisch eingehalten werden, um die Struktur für Nutzer und Suchmaschinen zu wahren (z.B. h2 als Unterpunkt von h1, h3 als Unterpunkt von h2). Bei neuen Sektionen beginnt man einfach mit der nächsten logischen Ebene (wieder mit h2 und danach mit h3) und folgt dann wieder der Reihenfolge.

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

### Bilder: `<img>`

Bindet ein Bild ein (`src` und `alt` sind Pflicht).

```html
<img src="pfad/zum/bild.jpg" alt="Beschreibung des Bildes">
```

### Container: `<div>`

Der `<div>`-Tag ist ein universeller Container, um andere HTML-Elemente zu gruppieren und logische Abschnitte auf einer Webseite zu erstellen, die dann mittels CSS gestylt oder mit JavaScript manipuliert werden können.

Er hat keine eigene semantische Bedeutung, dient rein der Strukturierung und ist besonders nützlich für Layouts (z.B. mit Flexbox/Grid). Ohne Styling ist ein `<div>` unsichtbar (der `<div>`, nicht sein Inhalt!), wird aber als Block-Element behandelt, was einen Zeilenumbruch erzeugt und die volle Breite einnimmt.

```html
<div class="produkt-box">
    <h2>Produkt A</h2>
    <p>Beschreibung von Produkt A.</p>
</div>
```

### Inline-Container: `<span>`

Ist ein generischer (= es hat keine vordefinierte Bedeutung oder Darstellung) Inline-Container für Textabschnitte ohne visuelle Veränderung, um sie mit CSS zu stylen (Farbe, Schriftgröße) oder mit JavaScript zu manipulieren, ohne den Textfluss zu unterbrechen.

Im Gegensatz zu Block-Elementen wie `<div>`, bleibt der `<span>` in derselben Zeile, wo es platziert wird, und erzeugt keinen Zeilenumbruch. Sie funktionieren wie ein "Haken" (Hook) für gezielte Formatierungen innerhalb einer Zeile oder eines Absatzes. Wie dem `<div>` weist man dem `<span>` eine Klasse oder ID zu, um es mit CSS zu gestalten.

```html
<p>Dies ist ein normaler Satz. <span class="hervorhebung">Dieser Teil wird gelb hinterlegt</span> und hier geht der Satz normal weiter.</p>
```

---

## 5. Semantische HTML-Tags (Layout)

Diese Tags verbessern Struktur, Barrierefreiheit und SEO (Suchmaschinenoptimierung):

- **`<header>`**: Kopfbereich einer Seite oder eines Abschnitts.
- **`<nav>`**: Navigationsbereich.
- **`<main>`**: Hauptinhalt der Seite.
- **`<section>`**: Thematischer Abschnitt.
- **`<article>`**: Eigenständiger Inhalt (z.B. Blogpost).
- **`<footer>`**: Fußbereich der Seite.

---

## 6. Meta-Informationen & SEO

Diese Tags befinden sich im `<head>`-Bereich des HTML-Dokuments. Sie sind für den Besucher unsichtbar, aber essenziell für die Kommunikation mit Suchmaschinen und dem Browser.

### `<title>`

Legt den Titel der Webseite fest, der im Browser-Tab und als Hauptüberschrift in den Suchergebnissen erscheint. Er ist das wichtigste HTML-Element, um Suchmaschinen das Thema der Seite zu signalisieren.

```html
<title>HTML Glossar: SEO-Tags richtig nutzen</title>
```

### `<meta name="description">`

Enthält eine kurze Zusammenfassung des Inhalts. Suchmaschinen nutzen diesen Text für das Snippet in den Suchergebnissen. Er dient als Werbetext, um die Klickrate (CTR) der Nutzer zu erhöhen.

```html
<meta name="description" content="Ein umfassendes Glossar über HTML-Tags, die Ihre Suchmaschinenoptimierung verbessern.">
```

### `<meta name="viewport">`

Dieser Tag ist zwingend erforderlich für das responsive Design. Er sorgt dafür, dass die Webseite auf Mobilgeräten korrekt skaliert wird, was ein kritischer Rankingfaktor für Google ist.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### `<meta name="robots">`

Gibt Anweisungen an Suchmaschinen-Crawler, ob eine Seite indexiert werden soll oder ob Links auf der Seite verfolgt werden dürfen.

```html
<meta name="robots" content="index, follow">
```

### `<link rel="canonical">`

Verweist auf die Original-URL einer Webseite. Dies verhindert Probleme mit doppeltem Inhalt (Duplicate Content), indem es Google mitteilt, welche Version der Seite in den Suchindex gehört.

```html
<link rel="canonical" href="https://www.deineseite.de">
```

### `<meta charset="UTF-8">`

Legt die Zeichenkodierung fest. Dies stellt sicher, dass Umlaute und Sonderzeichen weltweit in jedem Browser korrekt dargestellt werden und verhindert Darstellungsfehler.

```html
<meta charset="UTF-8">
```

---

## Vollständiges HTML-Beispiel

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
