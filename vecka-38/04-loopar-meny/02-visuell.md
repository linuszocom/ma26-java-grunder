# 02 — Visuellt: Loopar och meny-val

Samma hisstur-, löpband- och automat-metaforer som i teoriguiden — nu som flödeskartor. Ingen OOP i diagrammen: bara `main`, loopar och ett menyval.

GitHub renderar diagrammen nedan automatiskt.

---

## `while` — fråga, kropp, hopp tillbaka

```mermaid
flowchart TD
  START([vaning = 1]) --> Q{"vaning < 8?"}
  Q -->|true| BODY["Skriv ut våning\nvaning++"]
  BODY --> Q
  Q -->|false| SLUT(["Fortsätt efter loopen"])
```

**Vad diagrammet visar:** Villkoret testas **före** varje varv (entry-check). Kroppen ändrar `vaning` — annars fastnar pilen på `true` för evigt.  
**Varför det hjälper:** Du ser att “efter loopen” bara nås när frågan blir false.  
**Kom ihåg / INTE:** `if` har ingen tillbaka-pil — det frågar en gång.

**Målsvar (säg högt / skriv i README):**  
*“while testar villkoret, kör kroppen, hoppar tillbaka. Något i kroppen måste göra att villkoret så småningom blir false.”*

---

## Oändlig vs terminerande — löpbandet

```mermaid
flowchart TD
  subgraph term ["Terminerande — count++ finns"]
    T1["count = 0"] --> T2{"count < 5?"}
    T2 -->|true| T3["println\n count++"]
    T3 --> T2
    T2 -->|false| T4["Klar"]
  end
  subgraph oand ["Oändlig — count++ saknas"]
    O1["count = 0"] --> O2{"count < 5?"}
    O2 -->|true| O3["println\n (ingen count++)"]
    O3 --> O2
  end
  style oand fill:#fee,stroke:#c00
```

**Peka:** I höger gren blir `count` aldrig större — pilen till `true` loopar för evigt tills du stoppar programmet i IDE:n.

---

## `for` — start, villkor, steg

```mermaid
flowchart TD
  INIT["i = 1"] --> Q{"i <= 5?"}
  Q -->|true| BODY["Station i\nprintln"]
  BODY --> STEP["i++"]
  STEP --> Q
  Q -->|false| SLUT(["Loopen klar"])
```

**Vad diagrammet visar:** Init körs **en gång**. Sedan samma cykel som `while`, men `i++` sitter i for-huvudet.  
**Off-by-one:** Byt `i <= 5` till `i < 5` i huvudet — sista stationen (5) försvinner.

---

## `<` vs `<=` — sista stationen med eller utan

```mermaid
flowchart LR
  subgraph lt ["i < 5 — stoppar FÖRE 5"]
    A1["1"] --> A2["2"] --> A3["3"] --> A4["4"]
    A4 --> X["5 uteblir"]
  end
  subgraph lte ["i <= 5 — 5 ingår"]
    B1["1"] --> B2["2"] --> B3["3"] --> B4["4"] --> B5["5"]
  end
```

**Metod på papper:** Skriv första och sista tal du vill ha. Markera om sista ska ingå → `<=` eller justera gränsen.

---

## Meny-loop — automaten tills 0

```mermaid
flowchart TD
  START(["Scanner skapad\nval = -1"]) --> Q{"val != 0?"}
  Q -->|true| MENU["Visa meny\n1, 2, 0"]
  MENU --> READ["val = nextInt()"]
  READ --> HANDLE{"val?"}
  HANDLE -->|1| A["Köp biljett"]
  HANDLE -->|2| B["Visa pris"]
  HANDLE -->|0| C["(ingen action)"]
  HANDLE -->|annat| D["Ogiltigt val"]
  A --> Q
  B --> Q
  C --> Q
  D --> Q
  Q -->|false| BYE(["Hej då!"])
```

**Kom ihåg:** Efter val **hoppar** programmet tillbaka till `val != 0` — inte till `main`-slut. Först när `val == 0` blir villkoret false.

**Målsvar (säg högt / skriv i README):**  
*“Meny-loopen visar alternativ, läser val, hanterar, och frågar igen tills val är 0.”*

---

## `Scanner` i flödet

```mermaid
sequenceDiagram
  participant U as Användare
  participant K as Konsol
  participant P as Program
  P->>K: println meny
  P->>K: print "Val: "
  U->>K: skriver 2 + Enter
  K->>P: nextInt() → 2
  P->>K: println svar för val 2
  Note over P: while hoppar tillbaka
```

**INTE:** `nextInt()` skriver inte menyn — den **väntar** på input efter att du skrivit `print`.

---

## Metod som flöde — felsök loop

```mermaid
flowchart TD
  A["Programmet hänger eller fel antal varv?"] --> B{"Vet jag antal varv?"}
  B -->|Ja| C["Kolla for-villkor: < eller <=?"]
  B -->|Nej| D["Kolla while: ändras variabel i villkor?"]
  C --> E["Räkna första/sista på papper"]
  D --> E
  E --> F["Kör i IDE — stämmer utskrift?"]
  F --> G["Meny: når val == 0?"]
```

---

## Checkpoint (privat)

1. Rita en egen `while` med tre varv — markera var `count++` sitter och var loopen lämnar.  
2. Rita samma loop som `for` — var sitter start, villkor, steg?  
3. Rita meny-loopen med dina egna val (minst två + avsluta).  
4. Markera med rött var en oändlig loop skulle uppstå om du tar bort ett steg.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
