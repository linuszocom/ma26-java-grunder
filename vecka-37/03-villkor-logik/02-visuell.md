# 02 — Visuellt: Villkor och logik

Samma trafikljus-metafor som i teoriguiden — nu som bild. Ingen loop i diagrammen: ett hårdkodat värde, en väg genom grenarna.

GitHub renderar diagrammen nedan automatiskt.

---

## `if` / `else` — två vägar

```mermaid
flowchart TD
  START([Programmet når if]) --> Q{"score >= 800?"}
  Q -->|true| A["Kör if-blocket\nBonus unlocked!"]
  Q -->|false| B["Hoppar över if\neller kör else"]
  A --> SLUT([Fortsätter efter blocket])
  B --> SLUT
```

**Vad diagrammet visar:** En fråga, högst två huvudvägar (plus att koden efter blocket alltid körs).  
**Varför det hjälper:** Du ser att false inte “stannar programmet” — det väljer annan gren eller inget.  
**Kom ihåg / INTE:** `if` upprepar inte. Det frågar **en gång** per körning.

---

## `else if`-stege — första sanna vinner

```mermaid
flowchart TD
  START([tempC = 22]) --> Q1{"tempC <= 0?"}
  Q1 -->|true| G1["Frost"]
  Q1 -->|false| Q2{"tempC <= 15?"}
  Q2 -->|true| G2["Kyligt"]
  Q2 -->|false| Q3{"tempC <= 25?"}
  Q3 -->|true| G3["Behagligt"]
  Q3 -->|false| G4["Varmt"]
```

För `tempC = 22`: första false, andra false, tredje **true** → “Behagligt”. Grenarna under testas inte längre.

**Målsvar (säg högt / skriv i README):**  
*“I en else if-kedja testas frågorna uppifrån. Första true kör sitt block — resten hoppas över.”*

---

## Död gren — gren som aldrig nås

```mermaid
flowchart TD
  START([points = 50]) --> Q1{"points > 0?"}
  Q1 -->|true| OK["Poäng kvar"]
  Q1 -->|false| Q2{"points > 100?"}
  Q2 -->|???| DEAD["Hög poäng\nDÖD GREN"]
  style DEAD fill:#fee,stroke:#c00
```

Om `points = 50`: första frågan true → “Poäng kvar”. Grenen `points > 100` **kan inte** nås när `points` redan var > 0 men ≤ 100 — och när `points > 100` hade första grenen redan varit true. (I det här exemplet är andra grenen meningslös.)

**Peka på papper:** Rita samma stege med ditt värde. Markera vilken ruta som aldrig kan nås.

---

## `&&` och `||` — kombinera frågor

```mermaid
flowchart LR
  subgraph och ["&& — båda måste vara true"]
    A1["score >= 800"] --> R1{&&}
    A2["dailyQuestDone"] --> R1
    R1 -->|båda true| WIN["Dubbel bonus"]
    R1 -->|annars| LOSE["Ingen dubbel bonus"]
  end
```

```mermaid
flowchart LR
  subgraph eller ["|| — minst en true"]
    B1["isMember"] --> R2{||}
    B2["orderTotal >= 500"] --> R2
    R2 -->|minst en true| SHIP["Fri frakt"]
    R2 -->|båda false| PAY["Betala frakt"]
  end
```

**Kom ihåg:** `&&` = strängare (allt måste stämma). `||` = mildare (ett räcker).

---

## `=` vs `==` — tilldela vs jämför

```mermaid
flowchart TD
  subgraph fel ["Fel i if — tilldelning"]
    F1["if (level = 5)"] --> F2["Sätter level till 5\nInte en jämförelse"]
  end
  subgraph ratt ["Rätt — jämförelse"]
    R1["if (level == 5)"] --> R2["Frågar: är level lika med 5?\ntrue eller false"]
  end
```

**Om du blandar ihop dem:** programmet ändrar data när du trodde du bara frågade.

---

## Metod som flöde — felsök logik

När du tvekar — följ pilarna. Det är samma metod som i teoriguiden.

```mermaid
flowchart TD
  A["Vilket hårdkodat värde har variabeln?"] --> B["Skriv frågan — == inte ="]
  B --> C["Beräkna true/false på papper"]
  C --> D{"else if-kedja?"}
  D -->|Ja| E["Testa uppifrån — första true vinner"]
  D -->|Nej| F["Kör if eller hoppa över"]
  E --> G["Finns död gren? Saknas klammer?"]
  F --> G
  G --> H["Kör i IDE — stämmer utskriften?"]
```

---

## Checkpoint (privat)

1. Rita en egen `else if`-stege (tre grenar) för **spelpoäng** eller **temperatur**.  
2. Markera med rött vilken gren som vore död om du byter ordning på två frågor.  
3. Skriv en kombination med `&&` och en med `||` — vilken är strängast?

När kartan sitter: [03 — Övningar](./03-ovningar.md).
