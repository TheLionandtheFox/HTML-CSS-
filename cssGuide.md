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

**Nachteile**: Nicht wiederverwendbar, schlechte Wartbarkeit

### 2. Internes CSS (im `<style>`-Tag)

```html
<head>
    <style>
        p { color: blue; }
    </style>
</head>
```

**Verwendung**: Für einzelne Seiten mit spezifischem Styling
