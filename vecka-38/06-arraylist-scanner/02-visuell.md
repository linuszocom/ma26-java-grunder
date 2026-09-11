# 02 — Visuellt: array, lista och Scanner

Samma packnings- och spellistetänk som i teoriguiden — nu som kartor du kan peka på. GitHub renderar Mermaid automatiskt.

---

## Array — fasta fack, index 0

```mermaid
flowchart LR
  subgraph arr ["int[5] packVikt"]
    F0["[0] 800 g"]
    F1["[1] 1200 g"]
    F2["[2] 450 g"]
    F3["[3] 300 g"]
    F4["[4] 950 g"]
  end
  L["length = 5"]
  S["sista index = 4"]
  L --> S
```

**Vad diagrammet visar:** Fem fack, numrerade 0–4. `length` är 5 — men index 5 finns inte.  
**Varför det hjälper:** Off-by-one: loop ska stanna **före** `length`, inte **på** `length`.  
**Kom ihåg / INTE:** Array växer inte. Ett sjätte föremål kräver ny array eller annan struktur.

**Målsvar (säg högt / skriv i README):** *“length är antal fack; sista index är length minus 1; loop: i från 0, i mindre än length.”*

---

## Index utanför — krasch

```mermaid
flowchart TD
  A["packVikt.length == 5"]
  B["Lagligt: index 0 … 4"]
  C["packVikt[5] eller packVikt[99]"]
  D["ArrayIndexOutOfBoundsException"]

  A --> B
  C --> D
```

**Problem först:** Du räknar som människa (“femte facket = 5”). Java säger nej.

---

## ArrayList — växer vid add

```mermaid
flowchart LR
  E["[] tom · size 0"]
  A1["add Midnight Run"]
  A2["add Static Echo"]
  A3["add Low Tide"]
  E --> A1 --> A2 --> A3
```

```mermaid
flowchart TB
  subgraph efter ["Efter tre add"]
    I0["get(0) → Midnight Run"]
    I1["get(1) → Static Echo"]
    I2["get(2) → Low Tide"]
  end
  SZ["size() → 3"]
```

**Vad diagrammet visar:** Du bestämmer inte storlek i förväg. Varje `add` tar ett fack till.  
**Kom ihåg / INTE:** `get(3)` när `size()` är 3 → `IndexOutOfBoundsException` (samma idé som array, annat namn).

---

## Array vs List — samma loop, olika ord

```mermaid
flowchart LR
  subgraph arrayLoop ["Array"]
    AL1["i = 0"]
    AL2["i < arr.length"]
    AL3["arr[i]"]
  end
  subgraph listLoop ["List"]
    LL1["i = 0"]
    LL2["i < lista.size()"]
    LL3["lista.get(i)"]
  end
```

**Målsvar (säg högt / skriv i README):** *“Samma for-mönster — byt length mot size() och hakparentes mot get.”*

---

## Scanner — två läsare, samma kassa

```mermaid
flowchart TD
  KB["Tangentbord System.in"]
  SC["Scanner"]
  NL["nextLine() → String hel rad"]
  NI["nextInt() → int"]
  KB --> SC
  SC --> NL
  SC --> NI
```

**Vad diagrammet visar:** En Scanner, två metoder — olika **typ** tillbaka.  
**Kom ihåg / INTE:** `nextInt` läser **inte** resten av raden som text.

---

## Fällan: nextInt lämnar Enter

```mermaid
sequenceDiagram
  participant U as Användare
  participant S as Scanner
  U->>S: skriver 3 + Enter
  S->>S: nextInt() tar 3
  Note over S: Enter ligger kvar i kön
  U->>S: skriver Mjölk + Enter
  S->>S: nextLine() läser TOM rad
  Note over S: Mjölk ligger kvar till nästa nextLine
```

**Fix i diagram:**

```mermaid
flowchart LR
  N1["nextInt()"]
  SL["nextLine() släng"]
  N2["nextLine() spara"]
  N1 --> SL --> N2
```

**Målsvar (säg högt / skriv i README):** *“Efter nextInt: en nextLine som jag inte sparar — sen den riktiga nextLine för text.”*

---

## Inköpslista — data genom kedjan

```mermaid
flowchart TD
  P["println fråga produkt"]
  R1["nextLine → String"]
  Q["println fråga antal"]
  R2["nextInt → int"]
  SW["nextLine släng"]
  ADD["lista.add(produkt)"]
  OUT["println produkt × antal"]

  P --> R1 --> Q --> R2 --> SW --> ADD --> OUT
```

**Ordning spelar roll:** Fråga → läs → fråga → läs → **släng Enter** → spara i lista.

---

## Felsökningskarta

```mermaid
flowchart TD
  X{Krasch eller konstigt?}
  A{ArrayIndexOutOfBounds?}
  B{IndexOutOfBounds på get?}
  C{TOM String efter tal?}
  FIX1["Index ≥ length — räkna om 0 … length−1"]
  FIX2["Index ≥ size() — samma räkning"]
  FIX3["Extra nextLine efter nextInt"]

  X --> A
  X --> B
  X --> C
  A --> FIX1
  B --> FIX2
  C --> FIX3
```

---

## Checkpoint (privat)

Rita på papper: array med 3 fack + en lista efter två `add`. Markera index 0 och sista lagliga index för båda. Lägg till pil: vad händer vid `get(3)` när size är 3?

När kartan sitter: [03 — Övningar](./03-ovningar.md).
