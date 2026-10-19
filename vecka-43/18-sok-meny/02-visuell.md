# 02 — Visuellt: sök och meny

Samma idéer som i teoriguiden — nu som flöde. `sökNamn` hit/miss, meny 1–4, Scanner-fälla. GitHub renderar diagrammen automatiskt.

---

## Tre filer — ansvar

```mermaid
flowchart TB
  main["Main.java<br/>Scanner · while · switch →"]
  reg["Register.java<br/>List · läggTill · listaAlla · sökNamn"]
  med["Medlem.java<br/>getNamn · getMedlemsnummer"]
  main -->|"läggTill / listaAlla / sökNamn"| reg
  reg -->|"for-each · getters"| med
  main -.->|"ALDRIG for-each över listan"| med
```

**Vad diagrammet visar:** Main frågar. Register söker och listar. Medlem ger namn/nummer via getters.  
**Kom ihåg / INTE:** Pil från Main till “loopa medlemmar” ska inte finnas.

---

## Anti: sök i Main → flytta till Register

```mermaid
flowchart LR
  subgraph daligt["Fel rum"]
    M1["for-each i Main"] --> M2["öppnar private lista"]
  end
  subgraph bra["Rätt rum"]
    R1["Main: sökNamn(sträng)"] --> R2["Register: loop + if"]
  end
  daligt -->|"flytta loop"| bra
```

**Målsvar (säg högt):** *“Main anropar. sökNamn i Register gör jobbet.”*

---

## `sökNamn` — hit vs miss

```mermaid
flowchart TD
  start["sökNamn(namn)"] --> loop["for-each Medlem m"]
  loop --> cmp["getNamn().equalsIgnoreCase(namn)?"]
  cmp -->|ja| hit["println namn + nummer · return"]
  cmp -->|nej| next["nästa m"]
  next --> loop
  loop -->|slut utan träff| miss["println Medlemmen saknas"]
```

**Kom ihåg / INTE:** Miss-raden hör **efter** loopen — inte i `else` varje varv. Hit utan `return` = loopen fortsätter i onödan.

---

## Konsol sida vid sida

```mermaid
flowchart LR
  h["sökNamn('Elsa')"] -->|hit| ok["Elsa 201"]
  m["sökNamn('Rune')"] -->|miss| no["Medlemmen saknas"]
```

**Vad diagrammet visar:** Samma metod. Olika sträng. Ett svar ut.

---

## Meny 1–4 — Exam-flöde

```mermaid
flowchart TD
  c1["1 ×2 läggTill Elsa + Nova"] --> c2["2 listaAlla → 2 rader"]
  c2 --> c3["3 sök Elsa → hit"]
  c3 --> c4["3 sök Rune → saknas"]
  c4 --> c5["4 kör = false"]
```

**Målsvar (säg högt):** *“Två medlemmar, lista, hit, miss, exit — sedan pekar jag på sökNamn.”*

---

## case 3 — Main frågar, Register svarar

```mermaid
flowchart LR
  s1["Val 3"] --> s2["nextLine namn"]
  s2 --> s3["register.sökNamn(…)"]
  s3 --> s4["konsol hit eller miss"]
```

**Kom ihåg / INTE:** case 3 ska **inte** innehålla for-each. Bara fråga + anrop.

---

## Scanner-fälla — `\n` efter `nextInt`

```mermaid
flowchart TD
  a["nextInt() läser 1"] --> b["buffert: \\n kvar"]
  b --> c{"nextLine() efter?"}
  c -->|nej| d["nästa nextLine äter \\n → namn = tom"]
  c -->|ja| e["ätare tar \\n → nästa nextLine = riktigt namn"]
```

**Kom ihåg / INTE:** Tomt namn är nästan alltid glömd `nextLine()` — inte “Scanner trasig”.

---

## Switch expression

```mermaid
flowchart LR
  v["int val"] --> sw["switch (val)"]
  sw --> c1["case 1 -> läggTill"]
  sw --> c2["case 2 -> listaAlla"]
  sw --> c3["case 3 -> sökNamn"]
  sw --> c4["case 4 -> kör = false"]
  sw --> d["default -> Ogiltigt val"]
```

**Kom ihåg / INTE:** `case n ->` (Java 21). Undvik klassisk `break`-switch när uttrycksformen räcker.

---

## Checkpoint (privat)

Säg högt: var sök bor, hit vs miss, varför meny i Main, varför `nextLine` efter `nextInt`. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
