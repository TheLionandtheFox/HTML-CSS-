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

### Pseudo-Klassen

Wählen Elemente in einem bestimmten Zustand aus.

```css
/* Link-Zustände */
a:link { color: blue; }        /* Unbesuchter Link */
a:visited { color: purple; }   /* Besuchter Link */
a:hover { color: red; }        /* Maus darüber */
a:active { color: orange; }    /* Beim Klicken */

/* Andere häufige Pseudo-Klassen */
input:focus { border-color: blue; }  /* Element hat Fokus */
li:first-child { font-weight: bold; } /* Erstes Kind */
li:last-child { border: none; }       /* Letztes Kind */
p:nth-child(2) { color: red; }        /* Zweites Kind */
```

### Pseudo-Elemente

Wählen einen bestimmten Teil eines Elements aus.

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
