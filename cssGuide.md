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

```css
/* Erster Buchstabe */
p::first-letter {
    font-size: 2em;
    color: red;
}

/* Erste Zeile */
p::first-line {
    font-weight: bold;
}

/* Inhalt vor/nach Element einfügen */
p::before {
    content: "→ ";
}

p::after {
    content: " ←";
}
```

---
