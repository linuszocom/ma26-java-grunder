# 02 — Visuellt: kartoteklådan, skylt, två kort

Samma bilder som i teoriguiden — nu som flöde. Listan i `Register`, `List` vs `ArrayList`, `läggTill` / `listaAlla`, två medlemmar från `Main`. GitHub renderar diagrammen automatiskt.

---

## Problemet — lådan i expeditionsfickan

```mermaid
flowchart TB
  main["Main äger List av Medlem"]
  main --> fel["kompilerar — fel rum för Exam 2"]
```

**Kom ihåg / INTE:** Att det kör betyder **inte** att listan ligger rätt. Exam pekar i `Register`.

---

## Tre rum — lådan får innehåll

```mermaid
flowchart LR
  M["Medlem.java<br/>ett arkivkort"]
  R["Register.java<br/>kartoteklåda + lista"]
  S["Main.java<br/>expeditionsfönster"]
  S -->|"new Medlem + läggTill"| R
  R -->|"håller"| M
  S -->|"listaAlla"| R
```

**Vad diagrammet visar:** `Main` skapar kort och anropar. `Register` **äger** samlingen.  
**Målsvar (säg högt / skriv i README):** *“Listan bor i Register. Main har bara en Register-referens.”*

---

## Skylt vs innehåll — `List` / `ArrayList`

```mermaid
flowchart TB
  skylt["List&lt;Medlem&gt; — deklarerad typ"]
  innehall["new ArrayList&lt;&gt;() — skapas här"]
  falt["private medlemmar i Register"]
  skylt --> falt
  innehall --> falt
```

**Kom ihåg / INTE:** Skylten är `List`. Innehållet skapas med `ArrayList`. Deklarera **inte** fältet som `ArrayList` om du följer kursmönstret.

---

## Pipeline — från fönster till låda

```mermaid
flowchart LR
  n["new Register"] --> t1["läggTill Kim"]
  t1 --> t2["läggTill Moa"]
  t2 --> l["listaAlla"]
  l --> c["konsol: Kim 101 / Moa 102"]
```

**Vad du ska se:** Två rader. Bevis att `add` lagrat och loopen läst via getters.

---

## `läggTill` vs `listaAlla`

```mermaid
flowchart TB
  subgraph till["läggTill"]
    in["tar emot Medlem m"] --> add["medlemmar.add(m)"]
  end
  subgraph lista["listaAlla"]
    loop["for-each över medlemmar"] --> out["println getNamn + getMedlemsnummer"]
  end
```

**Kom ihåg / INTE:** `läggTill` **ändrar** listan. `listaAlla` **läser** och skriver. Ingen av dem är sök.

---

## Tom låda vs två kort

```mermaid
flowchart LR
  a["new Register"] --> z["size 0"]
  z --> b["2 × läggTill"]
  b --> s["size 2"]
  s --> p["listaAlla → 2 rader"]
```

**Kom ihåg / INTE:** Tom utskrift före `läggTill` = förväntat. Inte bevis att fältet saknas.

---

## Ansvarskarta — felsök rätt rum

```mermaid
flowchart TB
  q1["List i Main?"] --> a1["Flytta till Register"]
  q2["cannot find List?"] --> a2["import java.util.List"]
  q3["ArrayList som fälttyp?"] --> a3["Byt till List&lt;Medlem&gt;"]
  q4["medlemmar.add från Main?"] --> a4["private → läggTill"]
  q5["Inget i konsolen?"] --> a5["Anropa listaAlla efter läggTill"]
```

---

## Exam-peka

```mermaid
flowchart LR
  q["Var ligger listan?"] --> f["Register.java"]
  f --> field["private List&lt;Medlem&gt; medlemmar"]
```

**Målsvar (säg högt / skriv i README):** *“Jag öppnar Register och pekar på medlemmar — inte Main.”*

---

## Checkpoint (privat)

Säg högt: fel rum (lista i Main), skylt vs innehåll, `läggTill`/`listaAlla`, två rader i konsolen, exam-pekning. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
