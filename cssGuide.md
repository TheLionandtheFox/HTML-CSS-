# CSS Erklärt

> **Status:** Noch in Arbeit

## Was ist CSS?

**CSS (Cascading Style Sheets)** ist eine Stylesheet-Sprache, die das Aussehen und Layout von HTML-Elementen steuert. Während HTML die Struktur einer Webseite definiert, bestimmt CSS deren visuelle Gestaltung.

### Wichtige Merkmale

- **Trennung von Inhalt und Design**: während HTML für Struktur ist, ist CSS für Styling.
- **Wiederverwendbarkeit**: Eine CSS-Regel kann auf viele Elemente angewendet werden.
- **Kaskadierung**: Spätere Regeln überschreiben frühere Regeln
- **Spezifität**: Genauere Selektoren haben Vorrang vor allgemeinen.

---

## Grundlegende CSS-Syntax

```css
selektor {
    eigenschaft: wert;
    eigenschaft: wert;
}
```

**Beispiel:**

```css
p {
    color: blue;
    font-size: 16px;
}
```

---

## CSS in HTML einbinden

### 1. Inline-CSS (direkt im HTML-Element)

```html
<p style="color: red; font-size: 20px;">Text</p>
```

**Nachteile**: Nicht wiederverwendbar, schlechte Wartbarkeit, unübersichtlich, zu viel unnötige Arbeit = nicht effizient

### 2. Internes CSS (im `<style>`-Tag)

```html
<head>
    <style>
        p { color: blue; }
    </style>
</head>
```

**Verwendung**: Für einzelne Seiten mit spezifischem Styling, wenn der Code kurz und übersichtlich ist. Gut für einen One-Pager.

### 3. Externes CSS (separate .css-Datei) **EMPFOHLEN**

```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

**Vorteile**: Beste Wartbarkeit, Wiederverwendbarkeit, Browser-Caching, man kann mehrere seiten mit demselben oder für jede Seite eigene style erstellen, effiziente und schnellere Arbeit, flexibel

---

## Wichtigste CSS-Regeln und Konzepte

### 1. Das Box-Modell

Jedes HTML-Element ist eine rechteckige Box mit folgenden Bereichen (von innen nach außen):

1. **Content** (Inhalt): Der eigentliche Text/Bild
2. **Padding** (Innenabstand): Raum zwischen Inhalt und Rahmen
3. **Border** (Rahmen): Umrandung des Elements
4. **Margin** (Außenabstand): Raum zwischen Element und anderen Elementen

```css
.box {
    width: 200px;           /* Breite des Inhalts */
    padding: 20px;          /* Innenabstand */
    border: 2px solid black; /* Rahmen */
    margin: 10px;           /* Außenabstand */
}
```

### 2. Spezifität (Wichtigkeit von Selektoren)

CSS-Regeln werden nach ihrer Spezifität angewendet. Je spezifischer, desto höher die Priorität:

1. **Inline-Styles** (höchste Priorität): `style="color: red"`
2. **IDs**: `#header { color: red }`
3. **Klassen, Attribute, Pseudo-Klassen**: `.button { color: red}`, `[type="text"]`, `:hover`
4. **Elemente**: `p { color: red }`, `div { color: red }`

```css
/* Niedrige Spezifität */
p { color: black; }

/* Höhere Spezifität */
.text { color: blue; }

/* Noch höhere Spezifität */
#wichtig { color: red; }
```

### 3. Die Kaskade

Wenn mehrere Regeln auf dasselbe Element zutreffen, gewinnt:

1. Die Regel mit höherer Spezifität
2. Bei gleicher Spezifität: die zuletzt definierte Regel

```css
p { color: blue; }
p { color: red; }  /* Diese Regel gewinnt */
```

---

## 1. Selektoren

Selektoren bestimmen, welche HTML-Elemente gestylt werden. Größstenteils können die Namen für die Selektoren frei vergeben werden.
Man muss darauf achten, dass der Name der Selektoren deutlich und klar ist. Am besten keine kryptischen zahlen oder Buchstabenfolge.
Es sind keine Umlaute (ä, ö, ü) und keine Sonderzeichen (wie ß, !, ?, #, %, &) erlaubt (außer Bindestrich und Unterstrich), sie müssen case-sensitiv sein (Groß-/Kleinschreibung zählt), sollten funktionsbasiert benannt werden und können über Logische Pseudoklassen (:is(), :not()) kombiniert werden, wobei spezielle Regeln für Komplexität und Verschachtelung gelten. Wichtig ist auch die Spezifität bei Konflikten.
Die grundlegenden HTML-Elemente und einige spezielle Selektoren (wie Pseudo-Elemente) sind festgelegt.

### Universal-Selektor `*`

Wählt **alle** Elemente aus.

```css
* {
    margin: 0;
    padding: 0;
}
```

### Element-Selektor

Wählt alle Elemente eines bestimmten Typs aus. Sie sind vordefiniert.

```css
p {
    color: blue;
}

h1 {
    font-size: 32px;
}
```

### Klassen-Selektor `.klassenname`

Wählt alle Elemente mit einer bestimmten Klasse aus. Klassen können mehrfach verwendet werden.

```html
<p class="highlight">Dieser Text ist hervorgehoben</p>
<button class="buttonred">Klick mich</button>
```

```css
.highlight {
    background-color: yellow;
    color: blue;
}

.buttonred {
    background-color: red;
    padding: 10px;
    border-radius: 5px;
}
```

### ID-Selektor `#idname`

Wählt ein Element mit einer bestimmten ID aus. IDs sollten **einmalig** pro Seite sein.

```css
#header {
    background-color: navy;
    color: white;
}
```

```html
<div id="header">Kopfbereich</div>
```

### Nachfahren-Selektor (Descendant)

Wählt Elemente aus, die **innerhalb** eines anderen Elements liegen (auf beliebiger Ebene).

```css
div p {
    color: green;
}
```

Wählt alle `<p>` innerhalb von `<div>`.

### Kind-Selektor (Child) `>`

Wählt nur **direkte** Kinder eines Elements aus.

```css
div > p {
    font-weight: bold;
}
```

Wählt nur `<p>`, die direkte Kinder von `<div>` sind.

### Geschwister-Selektor `+`

Wählt **genau das erste** Element aus, das **direkt** nach einem anderen Element steht — also den **unmittelbaren Nachbarn** im gleichen Elternelement.

```css
h2 + p {
    margin-top: 0;
}
```

Wählt das erste `<p>` nach einem `<h2>`.

```html
<h2>Überschrift</h2>
<p>Absatz 1</p>
<p>Absatz 2</p>
```

Nur „Absatz 1“ wird ausgewählt, weil er direkt nach dem `<h2>` folgt.
„Absatz 2“ wird nicht angesprochen, da er nicht unmittelbar auf `<h2>` folgt.

### Allgemeiner Geschwister-Selektor `~`

Wählt **alle** Geschwister-Elemente aus, die nach einem Element kommen. Unabhängig davon, ob sie direkt oder erst später im Dokument stehen.

```css
h2 ~ p {
    color: gray;
}
```

```html
<h2>Überschrift</h2>
<p>Absatz 1</p>
<p>Absatz 2</p>
```

Hier werden „Absatz 1“ und „Absatz 2“ beide ausgewählt,
weil sie beide nach dem `<h2>` im selben Elternelement vorkommen.
Nochmal zum verdeutlichen:

`+` → nur den direkt folgenden Nachbarn;

`~` → alle nachfolgenden Geschwister

### Attribut-Selektor

Wählt Elemente basierend auf ihren Attributen aus. Das heißt **je nachdem, ob sie ein bestimmtes Attribut (und ggf. einen bestimmten Attributwert)** besitzen.  
Attribut-Selektoren sind sehr nützlich, um Elemente gezielt nach Eigenschaften zu stylen – etwa `type`, `href`, `title`, `lang`, usw.

```html
<input type="text">
<input type="password"> <!-- wird NICHT ausgewählt -->
```

```css
/* Element mit bestimmtem Attribut */
input[type="text"] {
    border: 1px solid gray;
}
```

Wählt nur `<input>`-Elemente aus, deren Attribut type genau den Wert text hat, also z. B.:

```html
<a href="https://www.google.com">Google</a>
<a href="https://news.google.de">Google News</a>
<a href="https://example.com">Beispiel</a> <!-- wird NICHT ausgewählt -->

```

```css
/* Element mit Attribut, das einen Wert enthält */
a[href*="google"] {
    color: red;
}
```

Wählt alle `<a>` -Elemente aus, deren Attribut href irgendwo „google“ enthält

**Übersicht:**

| Syntax | Bedeutung | Beispiel | Beschreibung |
| --------- | ------------ | ----------- | --------------- |
| `[attr]` | Hat dieses Attribut | `[disabled]` | Wählt alle Elemente mit dem Attribut `disabled` aus |
| `[attr="wert"]` | Exakter Wertvergleich | `[type="text"]` | Wählt nur Elemente, deren Attribut exakt `text` ist |
| `[attr*="teil"]` | Enthält Teilzeichenkette | `[href*="google"]` | Wählt alle Elemente, deren Attribut den Text „google“ enthält |
| `[attr^="anfang"]` | Beginnt mit | `[class^="btn-"]` | Wählt alle Elemente, deren Attributwert mit „btn-“ beginnt |
| `[attr$="ende"]` | Endet mit | `[src$=".jpg"]` | Wählt alle Elemente, deren Attributwert auf „.jpg“ endet |

## Pseudo-Klassen und Pseudo-Elemente

### Der Unterschied zwischen Pseudo-Klassen und Pseudo-Elementen

**Einfach gesagt:**

- **Pseudo-Klassen** (`:`) sprechen **ganze Elemente** in einem bestimmten **Zustand** an
- **Pseudo-Elemente** (`::`) sprechen **Teile** von Elementen an oder fügen **virtuellen Inhalt** hinzu

**Merkhilfe:**

- Pseudo-Klassen haben **einen** Doppelpunkt: `:hover`
- Pseudo-Elemente haben **zwei** Doppelpunkte: `::before`

---

### 1. Pseudo-Klassen (`:`)

Pseudo-Klassen werden verwendet, um Elemente abhängig von ihrem **Zustand** oder ihrer **Position** anzusprechen, ohne dass man dafür extra Klassen im HTML schreiben musst. Sie eignen sich besonders gut, um auf Benutzerinteraktionen zu reagieren (z. B. Maus darüber, Klick, Fokus) oder bestimmte Elemente innerhalb von Listen, Formularen oder Textbereichen gezielt zu gestalten.

### Link-Zustände

Diese Pseudo-Klassen funktionieren speziell bei Links (`<a>`-Elementen).

#### `:link` - Unbesuchter Link

Spricht Links an, die der Benutzer **noch nicht** besucht hat.

```css
/* Link-Zustände */
a:link { color: blue; }        /* Unbesuchter Link */
```

```html
<a href="https://example.com">Dieser Link ist noch unbesucht</a>
```

**Wann wird es verwendet?** Für Links, die noch nicht im Browser-Verlauf sind.

#### `:visited` - Besuchter Link

Spricht Links an, die der Benutzer **bereits besucht** hat.

```css
a:visited { color: purple; }   /* Besuchter Link */
```

**Wichtig:** Aus Sicherheitsgründen können nur wenige Eigenschaften geändert werden (color, background-color, border-color).

**Beispiel-Szenario:** Du möchtest, dass besuchte Links eine andere Farbe haben, damit Nutzer sehen, welche Seiten sie schon kennen.

---

#### `:hover` - Maus darüber

Wird aktiv, wenn der Benutzer mit der Maus **über** das Element fährt.

```css
a:hover { color: red; }        /* Wird aktiv, wenn der Benutzer mit der Maus über das Element fährt. */
```

**Funktioniert nicht nur bei Links!** Du kannst `:hover` auf fast alle Elemente anwenden:

```css
button:hover {
    background-color: lightblue;
    transform: scale(1.1);
}

div:hover {
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

img:hover {
    opacity: 0.7;
}
```

**Praxis-Beispiel:** Ein Button, der beim Drüberfahren größer wird

```css
.button {
    padding: 10px 20px;
    background-color: blue;
    color: white;
    transition: all 0.3s;
}

.button:hover {
    background-color: darkblue;
    transform: scale(1.05);
}

---

#### `:active` - Beim Klicken

Wird aktiv im **Moment des Klicks**.

```css
a:active { color: orange; }    /*im Moment des Klicks (während die Maustaste gedrückt ist)*/

button:active {
    transform: scale(0.95);
}
```

**Wichtig:** Die Reihenfolge bei Links muss sein: **L**o**V**e **HA**te

- `:link`
- `:visited`
- `:hover`
- `:active`

Anders funktioniert es nicht richtig wegen der CSS-Kaskade!

### Andere häufige Pseudo-Klassen

#### `:focus` - Element hat Fokus

Wird aktiv, wenn ein Element ausgewählt ist (z.B. wenn du in ein Eingabefeld klickst).

```css
input:focus {
    border-color: blue;
    outline: 2px solid blue;
    background-color: lightyellow;
}

textarea:focus {
    border-color: green;
}
```

```html
<input type="text" placeholder="Klick mich an!">
```

**Wenn du ins Eingabefeld klickst**, wird es blau umrandet.

**Praxis-Beispiel:** Bessere Sichtbarkeit für Barrierefreiheit

```css
button:focus {
    outline: 3px solid orange;
    outline-offset: 2px;
}
```

---

#### `:checked` - Angekreuzt

Für Checkboxen und Radio-Buttons, die aktiviert sind.

```css
input[type="checkbox"]:checked {
    background-color: green;
}

input[type="radio"]:checked + label {
    font-weight: bold;
    color: blue;
}
```

```html
<input type="checkbox" id="agree">
<label for="agree">Ich stimme zu</label>
```

**Praxis-Beispiel:** Custom Checkbox-Design

```css
input[type="checkbox"]:checked::before {
    content: "✓";
    color: white;
}
```

---

#### `:disabled` - Deaktiviert

Für Formularelemente, die nicht benutzt werden können.

```css
input:disabled {
    background-color: #e0e0e0;
    cursor: not-allowed;
    opacity: 0.5;
}
```

```html
<input type="text" disabled placeholder="Nicht editierbar">
```

---

#### `:enabled` - Aktiviert

Das Gegenteil von `:disabled`.

```css
input:enabled {
    background-color: white;
}
```

---

### Positions-basierte Pseudo-Klassen (Kinder)

Diese Pseudo-Klassen wählen Elemente basierend auf ihrer **Position** innerhalb des Elternelements aus.

#### `:first-child` - Erstes Kind

Wählt ein Element aus, wenn es das **erste Kind** seines Elternelements ist.

```css
li:first-child {
    font-weight: bold;
    color: red;
}
```

```html
<ul>
    <li>Erstes Element (wird rot und fett)</li>
    <li>Zweites Element</li>
    <li>Drittes Element</li>
</ul>
```

**Wichtig:** Das Element muss wirklich das erste Kind sein!

```html
<!-- Funktioniert NICHT -->
<ul>
    <h3>Überschrift</h3>  <!-- h3 ist das erste Kind -->
    <li>Erstes li</li>     <!-- Wird NICHT gestylt -->
</ul>
```

---

#### `:last-child` - Letztes Kind

Wählt das letzte Kind aus.

```css
li:last-child {
    border-bottom: none;
}
```

**Praktisches Beispiel:** Bei einer Liste soll das letzte Element keinen unteren Rahmen haben

```css
.item {
    border-bottom: 1px solid gray;
}

.item:last-child {
    border-bottom: none;
}
```

---

#### `:nth-child(n)` - N-tes Kind

Wählt das n-te Kind aus. **Sehr mächtig!**

```css
/* Zweites Element */
li:nth-child(2) {
    color: red;
}

/* Jedes ungerade Element (1, 3, 5, 7...) */
li:nth-child(odd) {
    background-color: lightgray;
}

/* Jedes gerade Element (2, 4, 6, 8...) */
li:nth-child(even) {
    background-color: white;
}

/* Jedes dritte Element (3, 6, 9, 12...) */
li:nth-child(3n) {
    font-weight: bold;
}

/* Jedes dritte Element ab dem zweiten (2, 5, 8, 11...) */
li:nth-child(3n+2) {
    color: blue;
}

/* Die ersten 3 Elemente */
li:nth-child(-n+3) {
    border: 2px solid red;
}
```

**Zebra-Streifen für Tabellen:**

```css
tr:nth-child(odd) {
    background-color: #f9f9f9;
}

tr:nth-child(even) {
    background-color: white;
}
```

---

#### `:nth-last-child(n)` - N-tes Kind von hinten

Zählt von hinten!

```css
/* Vorletztes Element */
li:nth-last-child(2) {
    color: orange;
}

/* Die letzten 3 Elemente */
li:nth-last-child(-n+3) {
    font-style: italic;
}
```

---

#### `:only-child` - Einziges Kind

Wählt ein Element aus, wenn es das **einzige** Kind seines Elternelements ist.

```css
p:only-child {
    text-align: center;
}
```

```html
<!-- Wird zentriert -->
<div>
    <p>Ich bin das einzige Kind</p>
</div>

<!-- Wird NICHT zentriert -->
<div>
    <p>Ich habe Geschwister</p>
    <p>Ich auch</p>
</div>
```

---

### Typ-basierte Pseudo-Klassen

Ähnlich wie die obigen, aber nur für **gleiche Element-Typen**.

#### `:first-of-type` - Erster seines Typs

Wählt das erste Element eines bestimmten Typs innerhalb des Elternelements.

```css
p:first-of-type {
    font-size: 1.2em;
}
```

```html
<div>
    <h2>Überschrift</h2>
    <p>Erster Absatz (wird größer)</p>
    <p>Zweiter Absatz</p>
</div>
```

**Unterschied zu `:first-child`:** `:first-of-type` ignoriert andere Element-Typen!

---

#### `:last-of-type` - Letzter seines Typs

```css
p:last-of-type {
    margin-bottom: 0;
}
```

---

#### `:nth-of-type(n)` - N-ter seines Typs

```css
/* Jeder zweite Absatz */
p:nth-of-type(2n) {
    background-color: yellow;
}
```

---

#### `:only-of-type` - Einziger seines Typs

```css
p:only-of-type {
    font-weight: bold;
}
```

---

### Negation und andere

#### `:not()` - Negation

Wählt alle Elemente aus, die **nicht** dem Selektor entsprechen.

```css
/* Alle Absätze außer die mit Klasse "special" */
p:not(.special) {
    color: gray;
}

/* Alle Links außer die zu eigener Domain */
a:not([href*="meine-domain.de"]) {
    color: red;
}

/* Alle Inputs außer Checkboxen */
input:not([type="checkbox"]) {
    border: 1px solid gray;
}
```

**Praxis-Beispiel:** Alle Buttons außer der mit Klasse "primary"

```css
button:not(.primary) {
    background-color: gray;
}
```

---

#### `:empty` - Leeres Element

Wählt Elemente aus, die **keinen** Inhalt haben.

```css
div:empty {
    display: none;
}

p:empty::before {
    content: "Dieser Absatz ist leer";
    color: red;
}
```

```html
<div></div>  <!-- Wird ausgeblendet -->
<div> </div> <!-- NICHT leer (Leerzeichen zählt!) -->
```

---

#### `:root` - Wurzelelement

Wählt das Wurzelelement aus (bei HTML ist das `<html>`). Wird oft für CSS-Variablen verwendet.

```css
:root {
    --primary-color: blue;
    --spacing: 20px;
}
```

---

### 2. Pseudo-Elemente (`::`)

Pseudo-Elemente sprechen **Teile** von Elementen an oder fügen **virtuellen Inhalt** hinzu, der im HTML nicht existiert. Sie werden verwendet, um bestimmte Teile eines Elements oder künstlich eingefügten Inhalt zu stylen, der im HTML nicht als eigenes Tag vorhanden ist. Typische Beispiele sind der erste Buchstabe, die erste Zeile eines Textes oder zusätzlicher Inhalt vor bzw. nach einem Element.

### `::before` - Inhalt vor Element

Fügt Inhalt **vor** dem eigentlichen Element-Inhalt ein.

```css
p::before {
    content: "→ ";
    color: blue;
    font-weight: bold;
}
```

```html
<p>Dies ist ein Absatz</p>
```

**Ergebnis:** → Dies ist ein Absatz

**Das `content`-Property ist PFLICHT!** Ohne `content` erscheint nichts.

```css
/* Funktioniert NICHT */
p::before {
    color: red;
}

/* Funktioniert */
p::before {
    content: "";  /* Auch leerer String ist okay */
    color: red;
}
```

Ein Praxis-Beispiel: **Icons vor Links**

```css
a.external::before {
    content: "🔗 ";
}

a.pdf::before {
    content: "📄 ";
}
```

Ein Praxis-Beispiel: **Dekorative Elemente**

```css
.quote::before {
    content: """;
    font-size: 3em;
    color: lightgray;
    position: absolute;
    left: -20px;
    top: -10px;
}
```

Ein Praxis-Beispiel: **Nummerierung**

```css
.chapter {
    counter-increment: chapter;
}

.chapter::before {
    content: "Kapitel " counter(chapter) ": ";
    font-weight: bold;
    color: blue;
}
```

---

### `::after` - Inhalt nach Element

Fügt Inhalt **nach** dem eigentlichen Element-Inhalt ein.

```css
p::after {
    content: " ←";
    color: red;
}
```

```html
<p>Dies ist ein Absatz</p>
```

**Ergebnis:** Dies ist ein Absatz ←

Praxis-Beispiel: **Clearfix für Floats**

```css
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```

Praxis-Beispiel: **Button mit Pfeil**

```css
.button::after {
    content: " →";
    transition: transform 0.3s;
}

.button:hover::after {
    transform: translateX(5px);
}
```

Praxis-Beispiel: **Pflichtfelder markieren**

```css
.required::after {
    content: " *";
    color: red;
}
```

```html
<label class="required">Name</label>
```

Ergebnis: **Name**

---

### `::first-letter` - Erster Buchstabe

Stylt den **ersten Buchstaben** eines Elements.

```css
p::first-letter {
    font-size: 3em;
    font-weight: bold;
    color: red;
    float: left;
    margin-right: 5px;
}
```

**Ergebnis:** Klassischer "Drop Cap"-Effekt wie in Büchern

```html
<p>Dies ist ein langer Text, und der erste Buchstabe ist sehr groß.</p>
```

**Nur bei Block-Elementen!** Funktioniert nicht bei `display: inline`.

**Erlaubte Eigenschaften:** Schrift, Farbe, Hintergrund, Margins, Padding, Border, Text-Decoration

---

### `::first-line` - Erste Zeile

Stylt die **erste Zeile** eines Elements.

```css
p::first-line {
    font-weight: bold;
    color: blue;
    text-transform: uppercase;
}
```

**Wichtig:** Die erste Zeile ändert sich, wenn das Browserfenster verkleinert wird!

**Erlaubte Eigenschaften:** Schrift, Farbe, Hintergrund, Text-Decoration, line-height

---

### `::selection` - Markierter Text

Stylt Text, den der Benutzer **markiert** (mit der Maus).

```css
::selection {
    background-color: yellow;
    color: black;
}

/* Für Firefox */
::-moz-selection {
    background-color: yellow;
    color: black;
}
```

**Praxis-Beispiel:** Corporate Identity

```css
::selection {
    background-color: #3498db;
    color: white;
}
```

---

### `::placeholder` - Platzhalter-Text

Stylt den Platzhalter-Text in Eingabefeldern.

```css
input::placeholder {
    color: lightgray;
    font-style: italic;
    opacity: 0.7;
}

input:focus::placeholder {
    opacity: 0.3;
}
```

```html
<input type="text" placeholder="Gib deinen Namen ein">
```

---

## Kombination von Pseudo-Klassen und Pseudo-Elementen

Du kannst beides kombinieren.

```css
/* ::before nur beim Hovern anzeigen */
a:hover::before {
    content: " →";
}

/* Erster Buchstabe des ersten Absatzes */
p:first-of-type::first-letter {
    font-size: 4em;
    color: red;
}

/* ::after nur für besuchte Links */
a:visited::after {
    content: " ✓";
    color: green;
}
```

---

## Vollständiges Praxis-Beispiel

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <style>
        /* Liste mit Nummerierung per ::before */
        .custom-list {
            counter-reset: item;
            list-style: none;
        }
        
        .custom-list li {
            counter-increment: item;
            margin-bottom: 10px;
        }
        
        .custom-list li::before {
            content: counter(item) ". ";
            font-weight: bold;
            color: blue;
            margin-right: 5px;
        }
        
        /* Zebra-Streifen mit :nth-child */
        .custom-list li:nth-child(odd) {
            background-color: #f0f0f0;
            padding: 5px;
        }
        
        /* Letztes Element ohne unteren Rand */
        .custom-list li:last-child {
            border-bottom: none;
        }
        
        /* Hover-Effekt */
        .custom-list li:hover {
            background-color: #e0e0e0;
            transform: translateX(5px);
            transition: all 0.3s;
        }
        
        /* Links mit Icons */
        a[href^="http"]::before {
            content: "🔗 ";
        }
        
        a[href$=".pdf"]::before {
            content: "📄 ";
        }
        
        /* Textmarkierung */
        ::selection {
            background-color: yellow;
            color: black;
        }
        
        /* Erster Absatz besonders */
        p:first-of-type::first-letter {
            font-size: 2em;
            font-weight: bold;
            color: red;
        }
    </style>
</head>
<body>
    <p>Dies ist der erste Absatz mit großem Anfangsbuchstaben.</p>
    <p>Dies ist der zweite Absatz.</p>
    
    <ul class="custom-list">
        <li>Erster Punkt</li>
        <li>Zweiter Punkt</li>
        <li>Dritter Punkt</li>
        <li>Vierter Punkt</li>
    </ul>
    
    <a href="https://example.com">Externer Link</a>
    <a href="dokument.pdf">PDF-Datei</a>
</body>
</html>
```

---

## Zusammenfassung: Wann was verwenden?

| Situation | Verwende |
| ----------- | ---------- |
| Hover-Effekt | `:hover` |
| Fokus in Formular | `:focus` |
| Erstes/Letztes Element | `:first-child` / `:last-child` |
| Jedes zweite Element | `:nth-child(even)` |
| Icon vor Text einfügen | `::before` |
| Dekorative Elemente | `::before` / `::after` |
| Erster Buchstabe groß | `::first-letter` |
| Markierten Text stylen | `::selection` |
| Platzhalter in Input | `::placeholder` |

---

## 2. Farben & Hintergründe

Farben sind eines der wichtigsten Gestaltungsmittel im Webdesign. Sie beeinflussen die Stimmung, Lesbarkeit und Markenidentität einer Website. CSS bietet verschiedene Möglichkeiten, Farben zu definieren – von einfachen Farbnamen bis zu komplexen Farbräumen mit Transparenz. Ob über Namen, Hexa Zahlen, RGB usw. Es gibt viele Möglichkeiten Farben zu wählen.

```css
p {
    color: red; /* Farbe rot */
    color: #ff0000;          /* Hexadezimal */
    color: rgb(255, 0, 0);   /* RGB */
    color: rgba(255, 0, 0, 0.5); /* RGB mit Transparenz */
}
```

### `color`

Die `color`-Eigenschaft in CSS bestimmt die Farbe des Textes innerhalb eines Elements. Sie ist eine der am häufigsten verwendeten CSS-Eigenschaften und bildet die Grundlage für lesbare und ansprechende Typografie.

### Grundlegende Syntax

```css
p {
    color: red; /* rote Farbe */
}
```

Diese einfache Regel färbt den Text aller `<p>`-Elemente rot. Die `color`-Eigenschaft wird vererbt – das bedeutet, wenn man sie auf ein Elternelement setzt, erben alle Kindelemente diese Farbe, sofern sie nicht explizit überschrieben wird.

### `background-color`

Setzt die Hintergrundfarbe.

```css
div {
    background-color: lightblue;
}
```

### Farbdefinition: Verschiedene Formate

CSS unterstützt mehrere Formate zur Farbangabe, jedes mit seinen eigenen Vor- und Nachteilen.

### 1. Farbnamen (Named Colors)

CSS kennt 147 vordefinierte Farbnamen wie `red`, `blue`, `green`, `white`, `black` usw. Diese sind intuitiv und leicht zu merken.

```css
h1 {
    color: crimson;
}

p {
    color: navy;
}

.highlight {
    color: gold;
}
```

**Vorteile:**

- Einfach zu schreiben und zu merken
- Gut für schnelles Prototyping
- Selbstdokumentierend (man sieht sofort, welche Farbe gemeint ist)

**Nachteile:**

- Begrenzte Auswahl (nur 147 Farben)
- Nicht präzise genug für professionelles Design
- Verschiedene Browser können Farbnamen minimal unterschiedlich interpretieren

**Häufige Farbnamen:**

- `white` (#FFFFFF) – Weiß
- `black` (#000000) – Schwarz
- `red` (#FF0000) – Rot
- `blue` (#0000FF) – Blau
- `green` (#008000) – Grün
- `gray` / `grey` (#808080) – Grau
- `darkgray` (#A9A9A9) – Dunkelgrau
- `lightgray` (#D3D3D3) – Hellgrau
- `silver` (#C0C0C0) – Silber

**Anwendungsfall:** Farbnamen eignen sich hauptsächlich für Entwicklungsumgebungen, schnelles Testen oder wenn man sehr gebräuchliche Farben benötigt. Für professionelle Projekte sollte man präzisere Formate verwenden.

---

### 2. Hexadezimal (Hex-Codes)

Hexadezimale Farbcodes sind das am häufigsten verwendete Format in professionellem Webdesign. Sie bestehen aus einem Hash-Symbol (#) gefolgt von 6 Zeichen (0-9 und A-F), die die Rot-, Grün- und Blau-Anteile der Farbe repräsentieren.

```css
p {
    color: #ff0000;  /* Rot */
}

h2 {
    color: #0000ff;  /* Blau */
}

.text {
    color: #3498db;  /* Ein helles Blau */
}
```

**Aufbau eines Hex-Codes:**

`#RRGGBB` – wobei:

- **RR** = Rot (00 bis FF)
- **GG** = Grün (00 bis FF)
- **BB** = Blau (00 bis FF)

Jedes Paar kann Werte von 00 (keine Farbe) bis FF (maximale Farbe) annehmen. FF in Hexadezimal entspricht 255 in Dezimal.

**Beispiele mit Erklärung:**

```css
#000000  /* Schwarz (kein Rot, kein Grün, kein Blau) */
#FFFFFF  /* Weiß (maximales Rot, Grün und Blau) */
#FF0000  /* Reines Rot (nur Rot-Kanal voll) */
#00FF00  /* Reines Grün */
#0000FF  /* Reines Blau */
#808080  /* Mittleres Grau (alle Kanäle bei 50%) */
#FF00FF  /* Magenta (Rot + Blau) */
#00FFFF  /* Cyan (Grün + Blau) */
#FFFF00  /* Gelb (Rot + Grün) */
```

**Kurzform (3-stellig):**

Wenn beide Zeichen eines Farbkanals identisch sind, kann man die Kurzform verwenden:

```css
#f00  /* Gleich wie #ff0000 (Rot) */
#0f0  /* Gleich wie #00ff00 (Grün) */
#00f  /* Gleich wie #0000ff (Blau) */
#fff  /* Gleich wie #ffffff (Weiß) */
#000  /* Gleich wie #000000 (Schwarz) */
#369  /* Gleich wie #336699 */
```

Der Browser erweitert automatisch: `#f00` wird zu `#ff0000`.

**Hex mit Transparenz (8-stellig):**

Moderne Browser unterstützen auch 8-stellige Hex-Codes für Transparenz:

```css
#ff000080  /* Rot mit 50% Transparenz */
#3498dbff  /* Volles Blau (FF = 100% opak) */
#00000000  /* Komplett transparent */
```

Die letzten zwei Zeichen (00-FF) bestimmen den Alpha-Kanal (Transparenz):

- `00` = komplett transparent
- `80` = 50% transparent
- `FF` = komplett deckend

**Vorteile:**

- Präzise Farbdefinition (16,7 Millionen Farben möglich)
- Kompakte Schreibweise
- Weit verbreitet und von allen Design-Tools unterstützt
- Gut lesbar, wenn man das System versteht

**Nachteile:**

- Nicht intuitiv für Anfänger
- Schwer, Farben "im Kopf" zu mischen
- Transparenz erfordert 8-stellige Codes (nicht alle Tools unterstützen das)

**Praxis-Tipp:** Man kann Hex-Codes aus Design-Tools (Figma, Photoshop, etc.) kopieren oder Online-Farbwähler nutzen. Moderne Code-Editoren zeigen oft eine Farbvorschau neben dem Code an.

---

### 3. RGB (Red Green Blue)

RGB definiert Farben durch Mischung von Rot, Grün und Blau. Jeder Kanal kann Werte von 0 bis 255 annehmen (insgesamt 256 Stufen pro Kanal).

```css
p {
    color: rgb(255, 0, 0);    /* Rot */
    color: rgb(0, 255, 0);    /* Grün */
    color: rgb(0, 0, 255);    /* Blau */
    color: rgb(128, 128, 128); /* Mittleres Grau */
}
```

**Syntax:**

```css
rgb(rot, grün, blau)
```

Jeder Wert ist eine Zahl von 0 bis 255.

**Wie RGB funktioniert:**

RGB ist ein additives Farbmodell – man startet mit Schwarz (keine Farbe) und addiert Licht:

- `rgb(0, 0, 0)` = Schwarz (kein Licht)
- `rgb(255, 255, 255)` = Weiß (alle Lichter voll)
- `rgb(255, 0, 0)` = Rot (nur roter Kanal)
- `rgb(255, 255, 0)` = Gelb (Rot + Grün = Gelb)
- `rgb(0, 255, 255)` = Cyan (Grün + Blau = Cyan)

**Vorteile von RGB:**

- Intuitiver als Hex, da man mit Dezimalzahlen arbeitet
- Einfacher zu verstehen, welche Farbe entsteht
- Leichter programmatisch zu manipulieren (z.B. mit JavaScript)

**Nachteile:**

- Längere Schreibweise als Hex
- Keine Transparenz (dafür gibt es RGBA)

**Umrechnung Hex zu RGB:**

Um einen Hex-Code zu RGB umzurechnen:

1. Teile den Hex-Code in drei Paare: RR GG BB
2. Rechne jedes Paar von Hexadezimal zu Dezimal um

Beispiel: `#3498db`

- `34` (hex) = 52 (dezimal)
- `98` (hex) = 152 (dezimal)
- `db` (hex) = 219 (dezimal)
- Ergebnis: `rgb(52, 152, 219)`

**Praxis-Beispiel:**

```css
.button-primary {
    background-color: rgb(52, 152, 219);  /* Ein helles Blau */
    color: rgb(255, 255, 255);            /* Weißer Text */
}

.button-primary:hover {
    background-color: rgb(41, 128, 185);  /* Dunkleres Blau beim Hover */
}
```

---

### 4. RGBA (RGB mit Alpha/Transparenz)

RGBA erweitert RGB um einen vierten Wert: den Alpha-Kanal für Transparenz. Alpha reicht von 0 (komplett transparent) bis 1 (komplett deckend).

```css
p {
    color: rgba(255, 0, 0, 0.5);   /* Rotes Halbtransparent */
    color: rgba(0, 0, 0, 0.8);     /* Fast deckend Schwarz */
    color: rgba(255, 255, 255, 0.1); /* Fast transparent Weiß */
}
```

**Syntax:**

```css
rgba(rot, grün, blau, alpha)
```

- **rot, grün, blau**: 0-255
- **alpha**: 0.0 bis 1.0 (oder 0% bis 100%)

**Alpha-Werte verstehen:**

- `0` oder `0.0` = komplett transparent (unsichtbar)
- `0.5` = 50% transparent (halbtransparent)
- `1` oder `1.0` = komplett deckend (keine Transparenz)

**Wichtiger Unterschied zu `opacity`:**

`rgba()` macht nur die Farbe transparent, während `opacity` das gesamte Element samt Inhalt transparent macht:

```css
/* Nur der Hintergrund ist transparent */
.box {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;  /* Text bleibt voll deckend */
}

/* Das GESAMTE Element wird transparent (inkl. Text!) */
.box {
    background-color: black;
    opacity: 0.5;  /* Text wird auch transparent */
}
```

**Praxis-Beispiele:**

Beispiel 1: **Overlay über Bild**

```css
.image-overlay {
    position: relative;
}

.image-overlay::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);  /* Dunkles Overlay */
}
```

Beispiel 2: **Glasmorphismus-Effekt**

```css
.glass-card {
    background-color: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
}
```

Beispiel 3: **Sanfter Schatten mit Transparenz**

```css
.card {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1),
                0 2px 4px rgba(0, 0, 0, 0.06);
}
```

Die Transparenz ermöglicht es, dass Schatten natürlicher aussehen und sich an den Hintergrund anpassen.

Beispiel 4: **Hover-Effekt mit Transparenz**

```css
.button {
    background-color: rgb(52, 152, 219);
    transition: background-color 0.3s;
}

.button:hover {
    background-color: rgba(52, 152, 219, 0.8);
}
```

---

### 5. HSL (Hue, Saturation, Lightness)

HSL ist ein alternatives Farbmodell, das für Menschen intuitiver ist als RGB. Es definiert Farben durch Farbton, Sättigung und Helligkeit.

```css
p {
    color: hsl(0, 100%, 50%);     /* Rot */
    color: hsl(120, 100%, 50%);   /* Grün */
    color: hsl(240, 100%, 50%);   /* Blau */
    color: hsl(0, 0%, 50%);       /* Grau */
}
```

**Syntax:**

```css
hsl(hue, saturation, lightness)
```

**Die drei Komponenten erklärt:**

1. **Hue (Farbton)**: 0-360 Grad auf dem Farbkreis
   - 0° / 360° = Rot
   - 60° = Gelb
   - 120° = Grün
   - 180° = Cyan
   - 240° = Blau
   - 300° = Magenta

2. **Saturation (Sättigung)**: 0% bis 100%
   - 0% = Graustufe (keine Farbe)
   - 50% = Mäßig gesättigt
   - 100% = Voll gesättigt (kräftige Farbe)

3. **Lightness (Helligkeit)**: 0% bis 100%
   - 0% = Schwarz
   - 50% = Normale Farbe
   - 100% = Weiß

**Visualisierung:**

```css
/* Gleicher Farbton (Rot), unterschiedliche Sättigung */
hsl(0, 100%, 50%)  /* Kräftiges Rot */
hsl(0, 75%, 50%)   /* Weniger gesättigtes Rot */
hsl(0, 50%, 50%)   /* Noch weniger gesättigt */
hsl(0, 0%, 50%)    /* Grau (keine Sättigung) */

/* Gleicher Farbton (Blau), unterschiedliche Helligkeit */
hsl(240, 100%, 10%)  /* Sehr dunkles Blau */
hsl(240, 100%, 30%)  /* Dunkles Blau */
hsl(240, 100%, 50%)  /* Normal Blau */
hsl(240, 100%, 70%)  /* Helles Blau */
hsl(240, 100%, 90%)  /* Sehr helles Blau */
```

**Vorteile** von HSL:

- Intuitiver für Menschen (man denkt eher in "Farbton" als in RGB-Werten)
- Einfach, Farbvariationen zu erstellen (z.B. hellere/dunklere Versionen)
- Perfekt für programmatische Farbgenerierung
- Großartig für konsistente Farbpaletten

Praxis-Beispiel: **Farbpalette generieren**

```css
:root {
    --hue: 210;  /* Blau-Farbton */
}

.color-primary {
    background-color: hsl(var(--hue), 80%, 50%);
}

.color-primary-light {
    background-color: hsl(var(--hue), 80%, 70%);  /* Hellere Version */
}

.color-primary-dark {
    background-color: hsl(var(--hue), 80%, 30%);  /* Dunklere Version */
}

.color-primary-pale {
    background-color: hsl(var(--hue), 30%, 90%);  /* Sehr blass */
}
```

Durch Änderung nur der `--hue`-Variable kann man die gesamte Farbpalette auf einen anderen Farbton umstellen!

---

### 6. HSLA (HSL mit Alpha)

Wie RGBA erweitert HSLA das HSL-Format um Transparenz.

```css
p {
    color: hsla(0, 100%, 50%, 0.5);    /* Halbtransparentes Rot */
    color: hsla(120, 100%, 50%, 0.3);  /* 30% deckend Grün */
}
```

**Syntax:**

```css
hsla(hue, saturation, lightness, alpha)
```

Praxis-Beispiel: **Dynamisches Theme mit Transparenz**

```css
:root {
    --theme-hue: 210;
}

.overlay {
    background-color: hsla(var(--theme-hue), 50%, 30%, 0.9);
}

.highlight {
    background-color: hsla(var(--theme-hue), 80%, 60%, 0.2);
}
```

---

## Moderne Farbformate (Bonus)

### HWB (Hue, Whiteness, Blackness)

Ein neueres, noch intuitiveres Format (seit 2021 in allen modernen Browsern):

```css
p {
    color: hwb(0 0% 0%);      /* Reines Rot */
    color: hwb(0 50% 0%);     /* Rot mit 50% Weiß gemischt */
    color: hwb(0 0% 50%);     /* Rot mit 50% Schwarz gemischt */
}
```

---

## Teil 2: Hintergründe

Hintergründe sind eines der vielseitigsten Gestaltungsmittel in CSS. Sie können weit mehr als nur einfarbig oder mit einem Bild sein – von komplexen Verläufen über mehrschichtige Designs bis hin zu Mischmodi und Animationen. Dieser Guide deckt alle Aspekte von CSS-Hintergründen ab.

---

## Grundlegende Background-Eigenschaften

### `background-color` - Hintergrundfarbe

Die `background-color`-Eigenschaft setzt eine solide Hintergrundfarbe für ein Element. Sie akzeptiert alle CSS-Farbformate (Named Colors, Hex, RGB, HSL, etc.).

```css
div {
    background-color: lightblue;
}

.header {
    background-color: #3498db;
}

.overlay {
    background-color: rgba(0, 0, 0, 0.5);
}
```

**Box-Model und Hintergrundfarbe:**

Die Hintergrundfarbe füllt standardmäßig den gesamten Bereich des Elements, einschließlich Padding, aber **nicht** das Margin. Sie erstreckt sich bis zum äußeren Rand des Borders.

```
┌─────────── Margin (transparent) ───────────┐
│ ┌─────── Border ──────┐                    │
│ │ ┌─── Padding ────┐  │ ← background-color │
│ │ │   Content      │  │ ← füllt bis hier   │
│ │ └────────────────┘  │                    │
│ └─────────────────────┘                    │
└────────────────────────────────────────────┘
```

**Wichtig:** Wenn man auch ein `background-image` setzt, liegt die Farbe **unter** dem Bild. Sie wird sichtbar, wenn das Bild transparent ist oder nicht den gesamten Bereich abdeckt.

---

### `background-image` - Hintergrundbild

Setzt ein oder mehrere Hintergrundbilder für ein Element.

```css
body {
    background-image: url('bild.jpg');
}

.hero {
    background-image: url('header-bg.png');
}

/* Relativer Pfad */
.section {
    background-image: url('../images/pattern.svg');
}

/* Absoluter Pfad */
.banner {
    background-image: url('https://example.com/image.jpg');
}
```

**Wichtige Hinweise:**

1. **Pfade müssen in Anführungszeichen** stehen (einfach oder doppelt)
2. **Relative Pfade** beziehen sich auf die CSS-Datei, nicht auf die HTML-Datei
3. Das Bild wird **standardmäßig wiederholt** (gekachelt), wenn es kleiner als der Container ist
4. Wenn das Bild nicht geladen werden kann, wird die `background-color` sichtbar (falls gesetzt)

**Mehrere Bilder übereinander:**

```css
.element {
    background-image: url('overlay.png'), url('main-bg.jpg');
    /* Das erste Bild liegt oben, das zweite darunter */
}
```

**SVG als Hintergrund:**

```css
.icon {
    background-image: url('data:image/svg+xml,<svg>...</svg>');
}

/* Oder als Datei */
.pattern {
    background-image: url('pattern.svg');
}
```

---

### `background-size` - Größe des Hintergrundbilds

Steuert die Darstellungsgröße des Hintergrundbilds.

```css
div {
    background-size: cover;      /* Füllt Container aus, beschneidet ggf. */
    background-size: contain;    /* Bild komplett sichtbar, ggf. Leerraum */
    background-size: 100px 50px; /* Feste Breite × Höhe */
    background-size: 50%;        /* 50% der Container-Breite */
    background-size: auto;       /* Original-Größe (Standard) */
}
```

**Die verschiedenen Werte im Detail:**

#### `cover` - Füllt den Container vollständig

```css
.hero {
    background-image: url('landscape.jpg');
    background-size: cover;
}
```

**Verhalten:**

- Das Bild wird so skaliert, dass es den **gesamten Container ausfüllt**
- Das Seitenverhältnis bleibt erhalten
- Teile des Bildes können **abgeschnitten** werden
- Kein Leerraum im Container

**Anwendungsfall:** Hero-Sections, Full-Screen-Backgrounds, wenn der Container immer gefüllt sein soll.

#### `contain` - Bild vollständig sichtbar

```css
.gallery-item {
    background-image: url('photo.jpg');
    background-size: contain;
    background-repeat: no-repeat;
}
```

**Verhalten:**

- Das Bild wird so skaliert, dass es **vollständig sichtbar** ist
- Das Seitenverhältnis bleibt erhalten
- Es kann **Leerraum** entstehen
- Das Bild wird nicht abgeschnitten

**Anwendungsfall:** Produkt-Bilder, Logos, wenn das gesamte Bild sichtbar sein muss.

#### Feste Größen

```css
.icon {
    background-image: url('icon.png');
    background-size: 50px 50px;  /* Breite × Höhe */
}

.banner {
    background-size: 100% auto;  /* Volle Breite, Höhe automatisch */
}

.sidebar {
    background-size: auto 200px;  /* Breite automatisch, feste Höhe */
}
```

**Prozentuale Angaben:**

```css
.element {
    background-size: 50% 50%;  /* 50% der Container-Breite und -Höhe */
}
```

**Wichtig:** Bei zwei Werten gilt: `Breite Höhe`. Bei einem Wert wird die Höhe automatisch berechnet (Seitenverhältnis bleibt erhalten).

---

### `background-position` - Position des Hintergrundbilds

Bestimmt, wo das Hintergrundbild innerhalb des Elements positioniert wird.

```css
div {
    background-position: center;        /* Zentriert (horizontal und vertikal) */
    background-position: top right;     /* Oben rechts */
    background-position: bottom left;   /* Unten links */
    background-position: 50% 50%;       /* Prozentual zentriert */
    background-position: 20px 30px;     /* 20px von links, 30px von oben */
}
```

**Schlüsselwörter:**

Horizontal: `left`, `center`, `right`  
Vertikal: `top`, `center`, `bottom`

```css
/* Ein Wert = horizontal, vertikal wird auf center gesetzt */
background-position: right;  /* = right center */

/* Zwei Werte */
background-position: top right;     /* Oben rechts */
background-position: center bottom; /* Horizontal zentriert, unten */
```

**Prozentuale Angaben:**

```css
background-position: 0% 0%;      /* Oben links (Standard) */
background-position: 100% 100%;  /* Unten rechts */
background-position: 50% 50%;    /* Zentriert */
background-position: 25% 75%;    /* 25% von links, 75% von oben */
```

**Wichtig:** Bei Prozentangaben wird der entsprechende Punkt des Bildes mit dem entsprechenden Punkt des Containers ausgerichtet. `50% 50%` bedeutet: Der Mittelpunkt des Bildes liegt am Mittelpunkt des Containers.

**Pixel/Em-Angaben:**

```css
background-position: 10px 20px;   /* 10px von links, 20px von oben */
background-position: 2em 1em;     /* Relativ zur Schriftgröße */
background-position: -10px 0;     /* Negativ = aus dem Container heraus */
```

**Vier-Wert-Syntax (präzise Positionierung):**

```css
/* 10px vom rechten Rand, 20px vom unteren Rand */
background-position: right 10px bottom 20px;

/* 5% vom linken Rand, 10% vom oberen Rand */
background-position: left 5% top 10%;
```

**Praxis-Beispiele:**

```css
/* Logo oben links mit Abstand */
.header {
    background-image: url('logo.png');
    background-position: left 20px top 20px;
    background-repeat: no-repeat;
}

/* Dekoratives Bild unten rechts */
.section {
    background-image: url('decoration.svg');
    background-position: right bottom;
    background-repeat: no-repeat;
}
```

---

### `background-repeat` - Wiederholung des Hintergrundbilds

Steuert die Wiederholung des Hintergrundbilds.

```css
div {
    background-repeat: no-repeat;  /* Keine Wiederholung */
    background-repeat: repeat;     /* In beide Richtungen (Standard) */
    background-repeat: repeat-x;   /* Nur horizontal */
    background-repeat: repeat-y;   /* Nur vertikal */
    background-repeat: space;      /* Mit Abständen, ohne Abschneiden */
    background-repeat: round;      /* Strecken, um ohne Abschneiden zu kacheln */
}
```

**Die verschiedenen Werte im Detail:**

#### `no-repeat` - Keine Wiederholung

```css
.hero {
    background-image: url('background.jpg');
    background-repeat: no-repeat;
    background-size: cover;
}
```

Das Bild wird nur einmal angezeigt, unabhängig von der Größe des Containers.

#### `repeat` - Standardverhalten

```css
.pattern {
    background-image: url('tile.png');
    background-repeat: repeat;  /* Standard, kann weggelassen werden */
}
```

Das Bild wird horizontal und vertikal wiederholt, um den gesamten Container zu füllen. Am Rand kann das Bild abgeschnitten werden.

#### `repeat-x` - Nur horizontal

```css
.stripe {
    background-image: url('stripe.png');
    background-repeat: repeat-x;
}
```

**Anwendungsfall:** Horizontale Muster, Trennlinien, dekorative Streifen.

#### `repeat-y` - Nur vertikal

```css
.sidebar {
    background-image: url('vertical-pattern.png');
    background-repeat: repeat-y;
}
```

**Anwendungsfall:** Vertikale Muster, Seitenleisten-Dekorationen.

#### `space` - Mit gleichmäßigen Abständen

```css
.grid {
    background-image: url('dot.png');
    background-repeat: space;
}
```

**Verhalten:**

- Bilder werden wiederholt, aber **nicht abgeschnitten**
- Zwischen den Bildern entstehen **gleichmäßige Abstände**
- Wenn nur ein Bild passt, wird es zentriert

#### `round` - Strecken für perfekte Kachelung

```css
.tiles {
    background-image: url('tile.png');
    background-repeat: round;
}
```

**Verhalten:**

- Bilder werden leicht **gestreckt oder gestaucht**
- So dass sie **ohne Abschneiden** perfekt kacheln
- Das Seitenverhältnis kann sich ändern

**Zwei-Wert-Syntax:**

```css
/* Horizontal und vertikal unterschiedlich */
background-repeat: repeat-x no-repeat;  /* Nur horizontal */
background-repeat: no-repeat repeat-y;  /* Nur vertikal */
background-repeat: space round;         /* Horizontal space, vertikal round */
```

---

### `background-attachment` - Scroll-Verhalten

Bestimmt, ob der Hintergrund mit dem Inhalt scrollt oder fixiert bleibt.

```css
div {
    background-attachment: scroll;  /* Scrollt mit (Standard) */
    background-attachment: fixed;   /* Fixiert relativ zum Viewport */
    background-attachment: local;   /* Scrollt mit dem Element-Inhalt */
}
```

**Die verschiedenen Werte:**

#### `scroll` - Standard-Verhalten

```css
.section {
    background-image: url('pattern.png');
    background-attachment: scroll;
}
```

Der Hintergrund ist fest mit dem Element verbunden. Wenn man die Seite scrollt, scrollt der Hintergrund mit.

#### `fixed` - Parallax-Effekt

```css
.parallax {
    background-image: url('mountains.jpg');
    background-attachment: fixed;
    background-size: cover;
    background-position: center;
}
```

**Verhalten:**

- Der Hintergrund bleibt **relativ zum Viewport fixiert**

- Beim Scrollen scheint der Inhalt über

**Box-Model und Hintergrundfarbe:**

```
┌─────────── Margin (transparent) ───────────┐
│ ┌─────── Border ──────┐                    │
│ │ ┌─── Padding ────┐  │ ← background-color │
│ │ │   Content      │  │ ← füllt bis hier   │
│ │ └────────────────┘  │                    │
│ └─────────────────────┘                    │
└────────────────────────────────────────────┘
```

---

## 3. Text & Schrift

## Einführung

Typografie ist eines der wichtigsten Elemente im Webdesign. Gut gestalteter Text verbessert die Lesbarkeit, vermittelt Persönlichkeit und beeinflusst die Benutzererfahrung maßgeblich. CSS bietet umfangreiche Möglichkeiten zur Textgestaltung – von grundlegenden Schriftarten bis zu modernen typografischen Features.

---

## Teil 1: Schriftarten (Font Properties)

### `font-family` - Schriftart festlegen

Die `font-family`-Eigenschaft bestimmt, welche Schriftart für Text verwendet wird. Sie ist eine der fundamentalsten typografischen Eigenschaften.

```css
p {
    font-family: Arial, sans-serif;
}

h1 {
    font-family: 'Times New Roman', serif;
}

code {
    font-family: 'Courier New', monospace;
}
```

Grundprinzip: **Font Stack (Fallback-Kette)**

Man definiert mehrere Schriftarten in einer Prioritätsliste. Der Browser verwendet die erste verfügbare Schrift:

```css
body {
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

**Reihenfolge:**

1. `'Helvetica Neue'` – Präferierte Schrift
2. `Helvetica` – Fallback 1
3. `Arial` – Fallback 2
4. `sans-serif` – Generischer Fallback (Browser wählt)

**Wichtig:** Schriftnamen mit Leerzeichen müssen in Anführungszeichen stehen:

```css
/* Richtig */
font-family: 'Times New Roman', serif;
font-family: "Courier New", monospace;

/* Falsch */
font-family: Times New Roman, serif;  /* Syntax-Fehler! */
```

**Die fünf generischen Schriftfamilien:**

Diese sollten immer am Ende des Font Stack stehen:

#### 1. `serif` - Serifenschriften

Schriften mit kleinen "Füßchen" an den Buchstabenenden. Wirken traditionell, seriös, elegant.

```css
.article {
    font-family: Georgia, 'Times New Roman', Times, serif;
}
```

**Typische Serif-Schriften:**

- Georgia
- Times New Roman
- Garamond
- Palatino

**Anwendungsfall:** Lange Texte, Artikel, formelle Dokumente, Print-Design-Ästhetik

#### 2. `sans-serif` - Serifenlose Schriften

Schriften ohne Verzierungen. Wirken modern, klar, sachlich.

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
}
```

**Typische Sans-Serif-Schriften:**

- Arial
- Helvetica
- Verdana
- Roboto
- Open Sans

**Anwendungsfall:** Moderne Websites, UI-Elemente, Bildschirm-Lesbarkeit

#### 3. `monospace` - Dicktengleiche Schriften

Jeder Buchstabe hat die gleiche Breite. Typisch für Code und technische Texte.

```css
code, pre {
    font-family: 'Fira Code', 'Consolas', 'Monaco', 'Courier New', monospace;
}
```

**Typische Monospace-Schriften:**

- Courier New
- Consolas
- Monaco
- Fira Code (mit Ligaturen)

**Anwendungsfall:** Code-Blöcke, Terminal-Output, Tabellen mit Zahlen

#### 4. `cursive` - Schreibschriften

Schriften, die Handschrift imitieren.

```css
.signature {
    font-family: 'Brush Script MT', cursive;
}
```

**Anwendungsfall:** Unterschriften, dekorative Überschriften (sparsam einsetzen!)

#### 5. `fantasy` - Dekorative Schriften

Stark stilisierte, künstlerische Schriften.

```css
.logo {
    font-family: 'Impact', fantasy;
}
```

**Anwendungsfall:** Logos, Überschriften (sehr sparsam!)

**System Font Stack (moderne Best Practice):**

Verwendet die Standard-UI-Schriften des jeweiligen Betriebssystems:

```css
body {
    font-family: 
        -apple-system,        /* macOS/iOS Safari */
        BlinkMacSystemFont,   /* macOS Chrome */
        'Segoe UI',           /* Windows */
        Roboto,               /* Android */
        'Helvetica Neue',     /* macOS älter */
        Arial,                /* Universal Fallback */
        sans-serif;           /* Generischer Fallback */
}
```

**Vorteile:**

- Keine Ladezeit (Schriften bereits im System)
- Native Darstellung auf jedem Gerät
- Optimale Lesbarkeit
- Konsistent mit OS-UI

**Web Fonts einbinden:**

Methode 1: **Google Fonts**

```html
<!-- Im HTML <head> -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
```

```css
body {
    font-family: 'Roboto', sans-serif;
}
```

Methode 2: **@font-face (eigene Fonts)**

```css
@font-face {
    font-family: 'MeineSchrift';
    src: url('fonts/meineschrift.woff2') format('woff2'),
         url('fonts/meineschrift.woff') format('woff');
    font-weight: normal;
    font-style: normal;
    font-display: swap;  /* Wichtig für Performance */
}

body {
    font-family: 'MeineSchrift', sans-serif;
}
```

**`font-display` Werte:**

- `swap` – Text sofort mit Fallback anzeigen, dann Font tauschen (empfohlen)
- `block` – Kurz warten, dann Fallback, dann Font
- `fallback` – Sehr kurz warten, dann Fallback (Font wird ggf. gar nicht geladen)
- `optional` – Browser entscheidet basierend auf Verbindungsgeschwindigkeit

---

### `font-size` - Schriftgröße

Die `font-size`-Eigenschaft bestimmt die Größe des Textes. Die Wahl der richtigen Einheit ist entscheidend für Responsive Design und Barrierefreiheit.

```css
p {
    font-size: 16px;      /* Pixel (absolut) */
    font-size: 1.5em;     /* Relativ zum Elternelement */
    font-size: 1.5rem;    /* Relativ zum Root-Element */
    font-size: 100%;      /* Prozent (relativ zum Elternelement) */
    font-size: 1.2vw;     /* Relativ zur Viewport-Breite */
}
```

**Die verschiedenen Einheiten im Detail:**

#### Pixel (px) - Absolute Einheit

```css
p {
    font-size: 16px;
}

h1 {
    font-size: 32px;
}
```

**Eigenschaften:**
- Feste Größe, ändert sich nicht
- Einfach zu verstehen und zu berechnen
- Ignoriert Browser-Einstellungen (problematisch für Barrierefreiheit!)

**Wann verwenden:** Nur wenn präzise Pixel-Größen erforderlich sind (selten!)

**Problem:** Nutzer, die die Browser-Schriftgröße ändern (z.B. sehbehinderte Menschen), werden ignoriert.

#### Em (em) - Relativ zum Elternelement

```css
body {
    font-size: 16px;  /* Basis */
}

.container {
    font-size: 1.2em;  /* 1.2 × 16px = 19.2px */
}

.container p {
    font-size: 0.875em;  /* 0.875 × 19.2px = 16.8px */
}
```

**Eigenschaften:**
- Relativ zur Schriftgröße des **Elternelements**
- Kaskadiert (kann zu unerwarteten Ergebnissen führen)
- Gut für komponentenbasiertes Scaling

**Kaskadierungs-Problem:**

```css
.outer {
    font-size: 1.2em;  /* 19.2px wenn Basis 16px */
}

.outer .inner {
    font-size: 1.2em;  /* 1.2 × 19.2px = 23.04px (!) */
}

.outer .inner .deep {
    font-size: 1.2em;  /* 1.2 × 23.04px = 27.65px (!!) */
}
```

Die Schriftgröße wird bei jeder Verschachtelungsebene multipliziert!

**Wann verwenden:** Für relative Größen innerhalb einer Komponente (z.B. Buttons)

#### Rem (rem) - Relativ zum Root-Element

```css
html {
    font-size: 16px;  /* Root-Schriftgröße */
}

p {
    font-size: 1rem;      /* = 16px */
}

h1 {
    font-size: 2.5rem;    /* = 40px */
}

small {
    font-size: 0.875rem;  /* = 14px */
}
```

**Eigenschaften:**
- Relativ zur Schriftgröße des `<html>`-Elements
- Kaskadiert **nicht** (konsistenter als em)
- Respektiert Browser-Einstellungen (barrierefreundlich)

**Vorteile:**
- Vorhersehbar und einfach zu berechnen
- Ein zentraler Ort (`:root` / `html`) für Schriftgrößen-Anpassungen
- Barrierefreiheit wird unterstützt

**Best Practice: 62.5% Trick**

```css
html {
    font-size: 62.5%;  /* = 10px bei Standard-Browser (16px × 0.625) */
}

body {
    font-size: 1.6rem;  /* = 16px */
}

h1 {
    font-size: 3.2rem;  /* = 32px */
}

small {
    font-size: 1.4rem;  /* = 14px */
}
```

**Vorteil:** Einfache Umrechnung: `1rem = 10px`, `1.6rem = 16px`, etc.

**Wann verwenden:** Standard für moderne Websites (empfohlen!)

#### Prozent (%) - Relativ zum Elternelement

```css
body {
    font-size: 16px;
}

p {
    font-size: 100%;   /* = 16px */
}

h1 {
    font-size: 200%;   /* = 32px */
}
```

Verhält sich ähnlich wie `em`, aber mit Prozent-Notation.

**Wann verwenden:** Selten, `em` oder `rem` sind meist besser.



---

#### `font-weight`

Steuert die Schriftstärke (Fettdruck).

```css
p {
    font-weight: normal;   /* 400 */
    font-weight: bold;     /* 700 */
    font-weight: 600;      /* Zahlenwert */
}
```

#### `font-style`

Setzt den Schriftstil.

```css
p {
    font-style: normal;
    font-style: italic;
    font-style: oblique;
}
```

#### `text-align`

Richtet Text horizontal aus.

```css
p {
    text-align: left;
    text-align: center;
    text-align: right;
    text-align: justify;  /* Blocksatz */
}
```

#### `text-decoration`

Fügt Textdekorationen hinzu oder entfernt sie.

```css
a {
    text-decoration: none;        /* Unterstreichung entfernen */
    text-decoration: underline;
    text-decoration: line-through; /* Durchgestrichen */
}
```

#### `text-transform`

Ändert die Groß-/Kleinschreibung.

```css
p {
    text-transform: uppercase;   /* GROSSBUCHSTABEN */
    text-transform: lowercase;   /* kleinbuchstaben */
    text-transform: capitalize;  /* Erster Buchstabe Groß */
}
```

#### `line-height`

Bestimmt die Zeilenhöhe.

```css
p {
    line-height: 1.5;      /* Faktor (empfohlen) */
    line-height: 24px;     /* Feste Höhe */
}
```

#### `letter-spacing`

Steuert den Abstand zwischen Buchstaben.

```css
h1 {
    letter-spacing: 2px;
    letter-spacing: -1px;  /* Engerer Abstand */
}
```

#### `word-spacing`

Steuert den Abstand zwischen Wörtern.

```css
p {
    word-spacing: 5px;
}
```

#### `text-shadow`

Fügt einen Schatten zum Text hinzu.

```css
h1 {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    /* horizontal vertikal unschärfe farbe */
}
```

---
