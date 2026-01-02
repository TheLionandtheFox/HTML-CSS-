# HTML erklärt

> **Status:** Noch in Arbeit

## Schnelle übersicht über die wichtigsten Merkmale

### Struktur

HTML ist eine Baumstruktur mit einem `<html>`-Tag als **Wurzelelement (Root-Element)**. Innerhalb von `<html>` befinden sich immer genau zwei Bereiche: `<head>` (Metadaten) und `<body>` (sichtbare Inhalte).

Elemente werden durch Tags (`< >`) definiert, die oft Paare bilden (Start- und End-Tag wie zum Beispiel `<p>...</p>`).

#### Wichtige semantische Strukturelemente sind

- Überschriften (`<h1>` bis `<h6>`)
- Absätze (`<p>`)
- Listen (`<ul>`, `<ol>`)
- Abschnitte (`<section>`, `<div>`)
- Navigation (`<nav>`)

### Sprachfestlegung

Es ist Best Practice, das Attribut `lang` zu verwenden (`<html lang="de">`), um Suchmaschinen und Screenreadern die Sprache der Seite mitzuteilen.

### Pflicht-Elemente

Jedes gültige HTML5-Dokument **muss** die Elemente `html`, `head` und `body` enthalten. Wenn man sie vergisst, ergänzt sie der Browser automatisch (sie werden nicht automatisch in die Datei eingefügt, sondern nur im Browser intern ergänzt).

#### `<!DOCTYPE html>`

Die `<!DOCTYPE html>`-Deklaration muss ganz am Anfang der Datei stehen, um dem Browser mitzuteilen, dass es sich um HTML5 handelt, und um eine korrekte Darstellung sicherzustellen.

```html
<!DOCTYPE html>
```

#### `<html>`-Tag

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

Diese Tags bilden das Skelett jeder Webseite. Jedes HTML5-Dokument **sollte** die Basisstruktur enthalten:

- `<!DOCTYPE html>`
- `<html>`
- `<head>` (mit `<meta charset="UTF-8">` und `<title>`)
- `<body>`

Diese Elemente definieren das Dokument, stellen Metadaten bereit (wie den Titel für Browser-Tabs/Suchmaschinen) und umschließen den sichtbaren Inhalt. Auch semantische Tags wie `<header>`, `<nav>`, `<main>`, `<footer>` und Überschriften (`<h1>` bis `<h6>`) sind für Struktur und SEO entscheidend.

### Meta-Informationen & SEO

Diese Tags befinden sich im `<head>`-Bereich des HTML-Dokuments. Sie sind für den Besucher unsichtbar, aber essenziell für die Kommunikation mit Suchmaschinen und dem Browser. Sie geben Informationen über den Inhalt der Seite, damit diese besser verstanden, indexiert und in den Suchergebnissen (Snippet) korrekt angezeigt werden können.

#### `<title>`

Legt den Titel der Webseite fest, der im Browser-Tab und als Hauptüberschrift in den Suchergebnissen erscheint. Er ist das wichtigste HTML-Element, um Suchmaschinen das Thema der Seite zu signalisieren. Der `<title>` erscheint als Beschriftung oben im Browser-Tab (Registerkarte) und in der Titelleiste des Browserfensters. Er ist auch der Titel, der in Suchmaschinenergebnissen (SERPs) und bei Lesezeichen angezeigt wird, aber nicht direkt auf der Webseite selbst sichtbar ist.

```html
<title>HTML Glossar: SEO-Tags richtig nutzen</title>
```

#### `<meta name="description">`

Enthält eine kurze Zusammenfassung des Inhalts. Suchmaschinen nutzen diesen Text für das Snippet in den Suchergebnissen. Er dient als Werbetext, um die Klickrate (CTR) der Nutzer zu erhöhen.

```html
<meta name="description" content="Ein umfassendes Glossar über HTML-Tags, die Ihre Suchmaschinenoptimierung verbessern.">
```

#### `<meta name="viewport">`

Dieser Tag ist zwingend erforderlich für das responsive Design. Er sorgt dafür, dass die Webseite auf Mobilgeräten korrekt skaliert wird, was ein kritischer Rankingfaktor für Google ist.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### `<meta name="robots">`

Gibt Anweisungen an Suchmaschinen-Crawler, ob eine Seite indexiert werden soll oder ob Links auf der Seite verfolgt werden dürfen.

```html
<meta name="robots" content="index, follow">
```

#### `<link rel="stylesheet">`

Verknüpft das Dokument mit externen Ressourcen, meist CSS-Dateien. Wichtige Merkmale: Steht im `<head>`. Das Attribut rel="stylesheet" ist für CSS zwingend erforderlich.

```html
<link rel="stylesheet" href="style.css">
```

#### `<meta charset="UTF-8">`

Legt die Zeichenkodierung fest. Dies stellt sicher, dass Umlaute und Sonderzeichen weltweit in jedem Browser korrekt dargestellt werden und verhindert Darstellungsfehler.

```html
<meta charset="UTF-8">
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

### Video: `<video>`

Dient zum Einbetten von Videodateien ohne externe Player.

**Wichtige Merkmale**: Unterstützt Attribute wie `controls` (Play/Pause-Button), `autoplay` oder `loop`.

```html
<video src="film.mp4" controls width="400"></video>
```

### Audio: `<audio>`

Dient zum Einbetten von Tondateien oder Musik.

**Wichtige Merkmale**: Ähnlich wie `<video>`, benötigt meist das `controls`-Attribut, damit der Nutzer die Wiedergabe starten kann.

```html
<audio src="musik.mp3" controls></audio>
```

### iFrame: `<iframe>`

Bettet eine andere Webseite oder ein externes Medium (z.B. Google Maps) ein.

**Wichtige Merkmale**: Benötigt das `src`-Attribut. Sicherheitsmerkmale wie `sandbox` sind oft wichtig.

```html
<iframe src="https://www.wikipedia.org" width="500" height="300"></iframe>
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

Diese Tags verbessern Struktur, Barrierefreiheit und SEO (Suchmaschinenoptimierung).

### `<header>`

Definiert den Kopfbereich einer Seite oder eines Abschnitts.

**Wichtige Merkmale**: Enthält meist das Logo, den Seitentitel oder die Hauptnavigation. Er hilft Screenreadern, den Einstiegspunkt der Seite zu finden.

```html
<header>
    <h1>Unternehmensname</h1>
</header>
```

### `<nav>`

Markiert einen Bereich, der Navigationslinks enthält.

**Wichtige Merkmale**: Wird für Hauptmenüs, Inhaltsverzeichnisse oder Breadcrumbs verwendet. Nicht jeder Link muss in ein `<nav>`, nur größere Blöcke.

```html
<nav>
    <a href="/home">Home</a>
    <a href="/shop">Shop</a>
</nav>
```

### `<main>`

Kennzeichnet den einzigartigen Hauptinhalt des Dokuments.

**Wichtige Merkmale**: Darf nur einmal pro Seite vorkommen. Er schließt Header, Footer und Sidebar aus.

```html
<main>
    <h2>Aktuelle Nachrichten</h2>
    <p>Hier steht der wichtigste Text der Seite.</p>
</main>
```

### `<section>`

Definiert einen thematisch zusammengehörigen Abschnitt innerhalb eines Dokuments.

**Wichtige Merkmale**: Sollte in der Regel eine eigene Überschrift (`<h2>`-`<h6>`) haben.

```html
<section>
    <h2>Über uns</h2>
    <p>Wir sind ein Team aus Entwicklern.</p>
</section>
```

### `<article>`

Stellt einen eigenständigen, in sich geschlossenen Inhalt dar.

**Wichtige Merkmale**: Ideal für Blogbeiträge, Zeitungsartikel oder Forenposts, die theoretisch auch alleine auf einer Seite stehen könnten.

```html
<article>
    <h2>Rezept: Apfelkuchen</h2>
    <p>Zuerst die Äpfel schneiden...</p>
</article>
```

### `<aside>`

Markiert Inhalte, die nur indirekt mit dem Hauptinhalt zu tun haben.

**Wichtige Merkmale**: Wird oft für Seitenleisten (Sidebars), Werbebanner oder Glossar-Boxen verwendet.

```html
<aside>
    <h4>Wussten Sie schon?</h4>
    <p>HTML wurde 1989 erfunden.</p>
</aside>
```

### `<footer>`

Definiert den Fußbereich einer Seite oder eines Abschnitts.

**Wichtige Merkmale**: Enthält oft Copyright-Infos, Kontaktlinks oder rechtliche Hinweise (Impressum).

```html
<footer>
    <p>&copy; 2025 Mein Blog</p>
</footer>
```

---

## 6. Formulare & Benutzereingaben

### `<form>`

Erstellt einen Bereich für Benutzereingaben (Formulare).

**Wichtige Merkmale**: Nutzt Attribute wie `action` (Ziel des Formulars) und `method` (get/post), um Daten zu senden.

```html
<form action="/login" method="POST">
    <!-- Eingabefelder hier -->
</form>
```

### `<input>`

Das wichtigste Element für Dateneingaben innerhalb von Formularen.

**Wichtige Merkmale**: Ein leeres Tag. Der Typ (`type`) bestimmt die Funktion (z.B. text, password, checkbox, email).

```html
<input type="text" placeholder="Benutzername">
```

### `<label>`

Definiert eine Beschriftung für ein `<input>`-Element.

**Wichtige Merkmale**: Erhöht die Barrierefreiheit. Wenn man auf das Label klickt, wird das zugehörige Eingabefeld aktiviert.

```html
<label for="mail">E-Mail:</label>
<input type="email" id="mail">
```

### `<button>`

Erstellt eine anklickbare Schaltfläche.

**Wichtige Merkmale**: Kann Text oder Bilder enthalten. Innerhalb von Formularen sendet er diese standardmäßig ab.

```html
<button type="submit">Jetzt absenden</button>
```

### `<textarea>`

Ein mehrzeiliges Eingabefeld für längere Texte.

**Wichtige Merkmale**: Die Größe kann über die Attribute `rows` und `cols` oder per CSS gesteuert werden.

```html
<textarea rows="4">Geben Sie hier Ihre Nachricht ein.</textarea>
```

### `<select>` und `<option>`

Erstellt eine Dropdown-Auswahlliste.

**Wichtige Merkmale**: `<select>` ist der Container, `<option>` sind die einzelnen auswählbaren Punkte.

```html
<select name="autos">
    <option value="volvo">Volvo</option>
    <option value="bmw">BMW</option>
</select>
```

---

## 7. Tabellen

### `<table>`

Das Hauptelement zur Erstellung einer Datentabelle.

**Wichtige Merkmale**: Sollte nur für tabellarische Daten genutzt werden, nicht für das Layout der Webseite.

```html
<table>
    <!-- Zeilen und Zellen -->
</table>
```

### `<tr>` (Table Row)

Definiert eine Tabellenzeile.

**Wichtige Merkmale**: Enthält entweder Kopfzellen (`<th>`) oder Datenzellen (`<td>`).

```html
<tr>
    <td>Max</td>
    <td>Mustermann</td>
</tr>
```

### `<th>` (Table Header)

Definiert eine Kopfzelle in einer Tabelle.

**Wichtige Merkmale**: Der Text wird standardmäßig fett und zentriert dargestellt.

```html
<th>Vorname</th>
```

### `<td>` (Table Data)

Definiert eine Standard-Datenzelle in einer Tabelle.

**Wichtige Merkmale**: Enthält den eigentlichen Inhalt der Tabellenzelle.

```html
<td>Max</td>
```

---

## Vollständiges HTML-Beispiel

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Eine Beispielseite für HTML-Strukturen">
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
            <article>
                <h2>H2 Überschrift: Ein Bild sagt mehr als Worte</h2>
                <h3>H3 Überschrift</h3>
                <p>Hier drunter ist ein Bild mit img-Tag</p>
                <img src="beispiel.jpg" alt="Ein schönes Beispielbild" width="300">
            </article>
        </section>

        <aside>
            <h4>Wussten Sie schon?</h4>
            <p>HTML5 bietet viele neue semantische Elemente für bessere Strukturierung.</p>
        </aside>
    </main>

    <footer>
        <p>&copy; Im Footer: 2025 Mein Web-Nachschlagewerk</p>
    </footer>
</body>
</html>
```

---

## Weiterte Tags

## 8. Styling & Scripting

### `<style>`

Ermöglicht es, CSS-Regeln direkt innerhalb des HTML-Dokuments zu schreiben.

**Wichtige Merkmale**: Sollte sparsam verwendet werden; externe Dateien via `<link>` sind meist besser.

```html
<style>
    body { background-color: #f0f0f0; }
</style>
```

### `<script>`

Bindet JavaScript-Code ein, um die Seite interaktiv zu machen.

**Wichtige Merkmale**: Kann internen Code enthalten oder über `src` eine externe Datei laden.

```html
<script src="script.js" defer></script>
```

### `<noscript>`

Definiert einen Inhalt, der nur angezeigt wird, wenn JavaScript im Browser deaktiviert ist.

**Wichtige Merkmale**: Wichtig für die Barrierefreiheit und um Nutzer auf fehlende Funktionen hinzuweisen.

```html
<noscript>Bitte aktiviere JavaScript, um diese Seite zu nutzen.</noscript>
```

---

## 9. Interaktive Elemente

### `<details>`

Erstellt einen ausklappbaren Bereich, den der Nutzer öffnen und schließen kann.

**Wichtige Merkmale**: Funktioniert ohne JavaScript. Wird oft für FAQs verwendet.

```html
<details>
    <summary>Mehr Informationen klicken</summary>
    <p>Hier sind die versteckten Details.</p>
</details>
```

### `<summary>`

Definiert die sichtbare Beschriftung für ein `<details>`-Element.

**Wichtige Merkmale**: Muss das erste Kindelement innerhalb von `<details>` sein.

```html
<summary>Frage: Was ist HTML?</summary>
```

### `<dialog>`

Definiert ein Dialogfenster oder eine Overlay-Box (Modal).

**Wichtige Merkmale**: Kann mit JavaScript-Methoden wie `showModal()` oder `close()` gesteuert werden.

```html
<dialog open>
    <p>Dies ist ein wichtiges Fenster!</p>
    <button>Schließen</button>
</dialog>
```

### `<progress>`

Zeigt den Fortschritt einer Aufgabe an (Ladebalken).

**Wichtige Merkmale**: Benötigt die Attribute `value` (aktueller Stand) und `max` (Zielwert).

```html
<progress value="70" max="100"></progress>
```

### `<meter>`

Stellt einen skalaren Wert innerhalb eines bekannten Bereichs dar (z.B. Speicherplatzbelegung).

**Wichtige Merkmale**: Im Gegensatz zu `<progress>` geht es hier um statische Messwerte, nicht um einen Prozessfortschritt.

```html
Speicherauslastung: <meter value="0.6">60%</meter>
```

---

## 10. Erweiterte Medien & Inhalte

### `<figure>`

Umschließt eigenständige Inhalte wie Bilder, Grafiken oder Code-Beispiele, oft zusammen mit einer Bildunterschrift.

**Wichtige Merkmale**: Gruppiert den Inhalt semantisch als eine Einheit.

```html
<figure>
    <img src="diagramm.png" alt="Statistik">
    <figcaption>Abb 1: Nutzerwachstum 2025</figcaption>
</figure>
```

### `<figcaption>`

Definiert die Bildunterschrift oder Legende für ein `<figure>`-Element.

**Wichtige Merkmale**: Steht innerhalb von `<figure>`, entweder ganz oben oder ganz unten.

```html
<figcaption>Dies ist die Beschreibung der Grafik.</figcaption>
```

### `<canvas>`

Erstellt einen Bereich, in dem mithilfe von JavaScript Grafiken, Animationen oder Spiele gezeichnet werden können.

**Wichtige Merkmale**: Es ist nur ein Container; die eigentliche Grafikarbeit erfolgt per Skript.

```html
<canvas id="meinSpiel" width="200" height="200"></canvas>
```

### `<svg>`

Wird verwendet, um skalierbare Vektorgrafiken direkt in das HTML-Dokument einzubetten.

**Wichtige Merkmale**: SVG-Grafiken bleiben beim Zoomen scharf und können per CSS gestylt werden.

```html
<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" fill="red" />
</svg>
```

---

## 11. Semantische Text-Auszeichnung

### `<time>`

Markiert ein Datum oder eine Uhrzeit in einem maschinenlesbaren Format.

**Wichtige Merkmale**: Hilft Suchmaschinen, Termine oder Veröffentlichungsdaten korrekt zu erfassen (Attribut `datetime`).

```html
<time datetime="2025-12-24">Heiligabend 2025</time>
```

### `<mark>`

Hebt Textstellen gelb (standardmäßig) hervor, um eine Relevanz zu markieren.

**Wichtige Merkmale**: Verhält sich wie ein Textmarker.

```html
<p>Das ist ein <mark>wichtiger</mark> Hinweis.</p>
```

### `<code>`

Markiert Text als Computer-Code.

**Wichtige Merkmale**: Wird standardmäßig in einer Monospace-Schriftart (Dicktengleich) dargestellt.

```html
<p>Nutzen Sie den Befehl <code>git push</code>.</p>
```

### `<pre>`

Stellt vorformatierten Text exakt so dar, wie er im Quellcode geschrieben wurde (inklusive Leerzeichen und Umbrüchen).

**Wichtige Merkmale**: Häufig in Kombination mit `<code>` für mehrzeilige Code-Blöcke verwendet.

```html
<pre>
    Zeile 1
    Zeile 2 (eingerückt)
</pre>
```

### `<blockquote>`

Kennzeichnet einen längeren zitierten Abschnitt aus einer anderen Quelle.

**Wichtige Merkmale**: Browser rücken diesen Block meist standardmäßig ein.

```html
<blockquote cite="https://zitate.de">
    „Der Hunger kommt beim Essen."
</blockquote>
```

### `<cite>`

Gibt den Titel eines Werks an (z.B. Buch, Film, Lied), auf das verwiesen wird.

**Wichtige Merkmale**: Wird vom Browser meist kursiv dargestellt.

```html
<p>Ich lese gerade <cite>HTML für Profis</cite>.</p>
```

### `<abbr>`

Definiert eine Abkürzung oder ein Akronym.

**Wichtige Merkmale**: Mit dem `title`-Attribut wird die volle Bedeutung beim Drüberfahren mit der Maus (Hover) angezeigt.

```html
<p>Die <abbr title="World Wide Web">WWW</abbr>-Konferenz.</p>
```

### `<address>`

Enthält Kontaktinformationen für den Autor oder Besitzer eines Dokuments oder Artikels.

**Wichtige Merkmale**: Wird oft im `<footer>` verwendet.

```html
<address>
    Max Mustermann<br>
    Musterstraße 1, Berlin
</address>
```

### `<dfn>`

Markiert die definierende Instanz eines Begriffs.

**Wichtige Merkmale**: Zeigt an, dass der umschlossene Text hier im Kontext erklärt wird.

```html
<p><dfn>HTML</dfn> ist die Sprache des Webs.</p>
```

---

## 12. Technische Text-Auszeichnung

### `<kbd>`

Markiert Text als Tastatureingabe des Benutzers.

**Wichtige Merkmale**: Wird meist in einer Monospace-Schrift dargestellt.

```html
<p>Drücken Sie <kbd>F5</kbd> zum Aktualisieren.</p>
```

### `<samp>`

Markiert Text als Beispielausgabe eines Computerprogramms.

**Wichtige Merkmale**: Ähnlich wie `<code>` und `<kbd>`, dient der semantischen Unterscheidung.

```html
<p>Der Computer meldet: <samp>Datei nicht gefunden.</samp></p>
```

### `<var>`

Markiert eine Variable in einem mathematischen Ausdruck oder im Programmcode.

**Wichtige Merkmale**: Wird vom Browser meist kursiv dargestellt.

```html
<p><var>x</var> = <var>y</var> + 2</p>
```

### `<sub>`

Definiert tiefgestellten Text (Subscript).

**Wichtige Merkmale**: Wird oft für chemische Formeln verwendet.

```html
<p>H<sub>2</sub>O</p>
```

### `<sup>`

Definiert hochgestellten Text (Superscript).

**Wichtige Merkmale**: Wird oft für mathematische Exponenten oder Fußnotenverweise genutzt.

```html
<p>E = mc<sup>2</sup></p>
```

---

## 13. Erweiterte Formular-Elemente

### `<fieldset>`

Gruppiert verwandte Elemente innerhalb eines Formulars, um sie logisch (und meist visuell durch einen Rahmen) zusammenzufassen.

**Wichtige Merkmale**: Verbessert die Struktur und Barrierefreiheit komplexer Formulare.

```html
<fieldset>
    <legend>Kontaktdaten</legend>
    <input type="text" name="name">
</fieldset>
```

### `<legend>`

Definiert eine Überschrift für ein `<fieldset>`-Element.

**Wichtige Merkmale**: Muss das erste Element innerhalb eines `<fieldset>` sein.

```html
<legend>Zahlungsinformationen</legend>
```

### `<datalist>`

Enthält eine Liste von vordefinierten Optionen für ein `<input>`-Element (Auto-Vervollständigung).

**Wichtige Merkmale**: Der Nutzer kann aus der Liste wählen oder einen eigenen Text tippen. Verknüpfung erfolgt über die `id` des Datalist und das `list`-Attribut des Inputs.

```html
<input list="browser-liste">
<datalist id="browser-liste">
    <option value="Chrome">
    <option value="Firefox">
</datalist>
```

### `<optgroup>`

Gruppiert verwandte `<option>`-Elemente innerhalb eines `<select>`-Menüs.

**Wichtige Merkmale**: Hilft bei der Übersichtlichkeit langer Dropdown-Listen.

```html
<select>
    <optgroup label="Obst">
        <option>Apfel</option>
        <option>Banane</option>
    </optgroup>
</select>
```

---

## 14. Erweiterte Tabellen-Elemente

### `<caption>`

Definiert die Überschrift einer Tabelle.

**Wichtige Merkmale**: Muss unmittelbar nach dem öffnenden `<table>`-Tag stehen.

```html
<table>
    <caption>Monatsumsatz 2025</caption>
    <tr><td>...</td></tr>
</table>
```

### `<thead>`

Gruppiert die Kopfzeilen einer Tabelle.

**Wichtige Merkmale**: Hilfreich für das Styling und sorgt dafür, dass beim Drucken langer Tabellen der Kopf auf jeder Seite wiederholt wird.

```html
<thead>
    <tr><th>Name</th><th>Alter</th></tr>
</thead>
```

### `<tbody>`

Gruppiert den eigentlichen Datenbereich einer Tabelle.

**Wichtige Merkmale**: Trennt den Inhalt logisch vom Kopf (`<thead>`) und Fuß (`<tfoot>`).

```html
<tbody>
    <tr><td>Max</td><td>25</td></tr>
</tbody>
```

### `<tfoot>`

Gruppiert die Zusammenfassungs- oder Fußzeilen einer Tabelle.

**Wichtige Merkmale**: Wird oft für Summenzeilen am Ende einer Tabelle verwendet.

```html
<tfoot>
    <tr><td>Gesamt</td><td>100 €</td></tr>
</tfoot>
```

---

## 15. Spezielle Auszeichnungen

### `<ruby>`

Wird verwendet, um asiatische Schriftzeichen mit kleinen Aussprachehilfen (Annotationen) zu versehen.
**Hinweis**: Nicht zu verwechseln mit der Programmiersprache **Ruby**!!!  
In HTML bezeichnet `<ruby>` ein Typografie-Element, das zur Darstellung von Aussprachehilfen dient — insbesondere in Sprachen wie Japanisch oder Chinesisch.

**Wichtige Merkmale**: Container für `<rt>` und `<rp>`.

```html
<ruby>漢 <rt>kan</rt></ruby>
```

### `<rt>`

Gibt die Aussprache oder Erklärung der Zeichen innerhalb eines `<ruby>`-Elements an.

**Wichtige Merkmale:** Erscheint meist klein über oder neben dem Hauptzeichen (je nach Sprache und Layout).

```html
<ruby>漢 <rt>kan</rt></ruby>
```

### `<rp>`

Bietet Fallback-Klammern für Browser, die Ruby-Annotationen nicht unterstützen.
Wichtige Merkmale: Inhalt wird nur angezeigt, wenn der Browser `<ruby>` nicht versteht, z. B. Klammern um die Aussprache.

**Wichtige Merkmale**: Inhalt wird nur angezeigt, wenn der Browser `<ruby>` nicht versteht.

```html
<ruby>漢<rp>(</rp><rt>kan</rt><rp>)</rp></ruby>
```

---

## Vollständiges Beispiel mit erweiterten Tags

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Erweiterte HTML-Beispiele</title>
    <style>
        body { font-family: Arial, sans-serif; }
        mark { background-color: yellow; }
    </style>
</head>
<body>
    <header>
        <h1>Erweiterte HTML-Elemente</h1>
    </header>

    <main>
        <section>
            <h2>Interaktive FAQ</h2>
            <details>
                <summary>Was ist HTML5?</summary>
                <p>HTML5 ist die <mark>neueste Version</mark> der Hypertext Markup Language.</p>
            </details>
        </section>

        <section>
            <h2>Code-Beispiel</h2>
            <p>Verwenden Sie den Befehl <code>git commit</code> um Änderungen zu speichern.</p>
            <pre><code>function hallo() {
    console.log("Hallo Welt");
}</code></pre>
        </section>

        <section>
            <h2>Wissenschaftliche Formel</h2>
            <p>Die Formel für Wasser ist H<sub>2</sub>O.</p>
            <p>Einstein's Formel: E = mc<sup>2</sup></p>
        </section>

        <section>
            <h2>Statistik mit Beschriftung</h2>
            <figure>
                <img src="chart.png" alt="Verkaufszahlen">
                <figcaption>Abbildung 1: Verkaufsentwicklung 2025</figcaption>
            </figure>
        </section>

        <section>
            <h2>Fortschrittsanzeige</h2>
            <p>Download-Fortschritt:</p>
            <progress value="45" max="100">45%</progress>
            <p>Festplatte belegt:</p>
            <meter value="0.7" max="1">70%</meter>
        </section>

        <section>
            <h2>Formular mit Gruppierung</h2>
            <form>
                <fieldset>
                    <legend>Persönliche Daten</legend>
                    <label for="name">Name:</label>
                    <input type="text" id="name" list="namen">
                    <datalist id="namen">
                        <option value="Max">
                        <option value="Anna">
                    </datalist>
                </fieldset>
                <button type="submit">Absenden</button>
            </form>
        </section>

        <section>
            <h2>Tabelle mit Struktur</h2>
            <table>
                <caption>Quartalsergebnis 2025</caption>
                <thead>
                    <tr>
                        <th>Monat</th>
                        <th>Umsatz</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Januar</td>
                        <td>5.000 €</td>
                    </tr>
                    <tr>
                        <td>Februar</td>
                        <td>6.500 €</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr>
                        <td>Gesamt</td>
                        <td>11.500 €</td>
                    </tr>
                </tfoot>
            </table>
        </section>

        <section>
            <h2>Zitat</h2>
            <blockquote cite="https://example.com">
                „Wissen ist Macht."
            </blockquote>
            <p>Quelle: <cite>Philosophie für Anfänger</cite></p>
        </section>
    </main>

    <footer>
        <address>
            Kontakt: info@beispiel.de<br>
            Musterstraße 123, 12345 Musterstadt
        </address>
        <p>Veröffentlicht am <time datetime="2025-12-31">31. Dezember 2025</time></p>
    </footer>

    <script>
        console.log("Seite geladen");
    </script>
    <noscript>JavaScript ist deaktiviert.</noscript>
</body>
</html>
```
