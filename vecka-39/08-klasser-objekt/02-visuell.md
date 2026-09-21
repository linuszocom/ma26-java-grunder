# 02 — Visuellt: mall, instans och fält

Samma bilder som i teoriguiden — nu som flöde. Klass `Account`, objekt via `new`, fält `owner` / `balance`. Ingen `deposit`. GitHub renderar diagrammen automatiskt.

---

## Lösa variabler vs klass

```mermaid
flowchart TB
  subgraph daligt["main med lösa namn"]
    O1["owner1 / balance1"]
    O2["owner2 / balance2"]
  end
  subgraph bra["klass + objekt"]
    C["Account.java<br/>owner, balance"]
    A["new → objekt A"]
    B["new → objekt B"]
    C --> A
    C --> B
  end
```

**Vad diagrammet visar:** Klassen beskriver fälten en gång. Varje `new` ger en egen instans.  
**Kom ihåg / INTE:** Två konton ≠ två klassfiler.

---

## Klass (mall) vs objekt (instans)

```mermaid
flowchart LR
  mall["Account.java<br/>mall / typ"]
  new1["new Account()"]
  obj["Objekt i minnet<br/>egna fält"]
  mall -->|"skapar"| new1 --> obj
```

**Målsvar (säg högt / skriv i README):** *“Klassen är mallen. new bygger instansen. Fälten lever på objektet.”*

---

## new innan punkt

```mermaid
flowchart LR
  deklarera["Account card"]
  skapa["card = new Account()"]
  satt["card.owner = …"]
  deklarera --> skapa --> satt
```

**Kom ihåg / INTE:** Punkt utan `new` → ofta `NullPointerException`. Först skapa, sen fylla.

---

## Punktnotation — öppna luckorna

```mermaid
flowchart TB
  obj["Objekt card"]
  owner["card.owner"]
  balance["card.balance"]
  obj --> owner
  obj --> balance
```

**Vad diagrammet visar:** Variabeln `card` pekar på objektet. Fälten nås med `card.fält`.  
**Kom ihåg / INTE:** `println(card)` ≠ innehållet i luckorna.

---

## Två objekt — egna saldon

```mermaid
flowchart TB
  klass["Klass Account"]
  a["Objekt a<br/>Alex / 500"]
  b["Objekt b<br/>Sam / 1200"]
  klass --> a
  klass --> b
  change["a.balance = 800"]
  change --> a
  note["b oförändrad"]
  b -.-> note
```

**Målsvar (säg högt / skriv i README):** *“Två new, två adresser. Ändrar jag a rör jag inte b.”*

---

## Filträd — Main och Account

```mermaid
flowchart TB
  src["src/"]
  main["Main.java<br/>new + utskrift"]
  acc["Account.java<br/>class + fält"]
  src --> main
  src --> acc
```

**Kom ihåg / INTE:** `public class Account` måste heta `Account.java`. Inte `Konto.java`.

---

## Checkpoint (privat)

Säg högt: klass vs objekt, varför `new` först, varför utskrift av fält, varför filnamn matchar. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
