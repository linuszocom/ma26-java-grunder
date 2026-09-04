# 02 — Visuellt: lagerhyllor och etiketter

Samma bilder som i teoriguiden — nu som flöde. Bara `main`. Ingen `if`, ingen loop, ingen `Scanner`. GitHub renderar diagrammen automatiskt.

---

## Värdet måste ligga någonstans

```mermaid
flowchart LR
  etikett["Etikett<br/>temperaturC"]
  hylla["Lagerhylla<br/>18.5"]
  konsol["System.out.println<br/>du SER 18.5"]

  etikett --> hylla
  hylla --> konsol
```

**Vad diagrammet visar:** Etiketten är variabelnamnet. Hyllan är platsen i minnet. Konsolen visar en kopia av innehållet.  
**Kom ihåg / INTE:** Utskriften tömmer inte hyllan. Du kan `println` samma variabel flera gånger.

---

## Deklaration → tilldelning → utskrift

```mermaid
flowchart TD
  D["Deklaration<br/>int antalPaHylla;"] --> T["Tilldelning<br/>antalPaHylla = 5;"]
  T --> P["Utskrift<br/>System.out.println(antalPaHylla);"]
  P --> K["Konsolen: 5"]
```

**Målsvar (säg högt / skriv i README):** *“Skapa platsen, fyll den, titta i den. Ordning spelar roll.”*

---

## Fyra hylltyper — rätt fack

```mermaid
flowchart TB
  subgraph intFack["int — heltal"]
    i1["42"]
  end
  subgraph doubleFack["double — decimal"]
    d1["18.5"]
  end
  subgraph stringFack["String — text"]
    s1["&quot;Göteborg&quot;"]
  end
  subgraph boolFack["boolean — ja/nej"]
    b1["true / false"]
  end
```

**Kom ihåg / INTE:** `3.5` i `int`-facket → javac stoppar. `"true"` är text (String), inte boolean.

---

## Fel sortering = kompileringskrasch

```mermaid
flowchart LR
  fel["Text i int-fack<br/>int namn = &quot;Anna&quot;;"]
  javac["javac vägrar<br/>incompatible types"]
  fix["Byt typ eller innehåll<br/>String namn = &quot;Anna&quot;;"]

  fel --> javac
  javac --> fix
```

**Vad diagrammet visar:** Felet är oftast *fel hylltyp*, inte “trasig dator”. Läs *cannot be converted to*.

---

## Samma etikett, nytt innehåll

```mermaid
flowchart LR
  A["antalPaHylla = 3"] --> B["println → 3"]
  B --> C["antalPaHylla = 10"]
  C --> D["println → 10"]
```

**Kom ihåg / INTE:** Samma variabelnamn, uppdaterat värde — inte automatiskt en ny variabel.

---

## Checkpoint (privat)

Säg högt: etikett, deklaration, tilldelning, fyra typer, varför `println` inte tömmer. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
