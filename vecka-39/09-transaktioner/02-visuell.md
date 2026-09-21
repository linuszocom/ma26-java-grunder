# 02 — Visuellt: objektet gör jobbet

Samma bilder som i teoriguiden — nu som flöde. `deposit` / `withdraw` på `Account`. GitHub renderar diagrammen automatiskt.

---

## Anrop väljer objekt

```mermaid
flowchart LR
  main["Main"] --> nora["nora.deposit(50)"]
  main --> erik["erik.deposit(50)"]
  nora --> nBal["Noras balance +50"]
  erik --> eBal["Eriks balance +50"]
```

**Vad diagrammet visar:** Punkten väljer **vilket** konto som ändras. Samma metodkod — olika objekt i minnet.  
**Kom ihåg / INTE:** En `static`-metod i `Main` som “råkar” ändra ett fält — här bor knappen på kontot.

---

## `deposit` — före och efter

```mermaid
flowchart LR
  fore["balance = 300"] --> dep["deposit(50)"]
  dep --> efter["balance = 350"]
```

**Målsvar (säg högt / skriv i README):** *“deposit lägger till amount på this.balance. Inget stoppvillkor krävs för vanlig insättning.”*

---

## `withdraw` — två vägar

```mermaid
flowchart TD
  start["withdraw(amount)"] --> frag["amount > this.balance?"]
  frag -->|ja| stop["Meddelande<br/>balance orörd"]
  frag -->|nej| ok["balance = balance - amount"]
```

**Vad diagrammet visar:** Frågan kommer **före** minus. Stoppvägen lämnar saldot som det var.  
**Kom ihåg / INTE:** Meddelande *och* minus = regeln är trasig.

---

## Problem först vs regel

```mermaid
flowchart TB
  subgraph daligt["Alltid minus"]
    A1["balance = balance - amount"]
    A2["Kan bli negativt"]
  end
  subgraph bra["Med if"]
    B1["if amount > balance"]
    B2["annars: minus"]
    B1 --> B2
  end
  daligt -->|"lägg till villkor"| bra
```

**Kom ihåg / INTE:** “Det kompilerar” ≠ “regeln håller”. Exam 1 bryr sig om **beteendet** vid för stort belopp.

---

## `this` vs `amount`

```mermaid
flowchart LR
  obj["Objektet nora"] --> th["this.balance"]
  anrop["Anropet withdraw(100)"] --> am["amount = 100"]
  th --- am
  am -->|"används i if / minus"| th
```

**Målsvar (säg högt / skriv i README) — this:** *“this pekar på objektet som fick anropet. amount är bara parametern.”*

---

## Valfritt — boolean tillbaka till Main

```mermaid
flowchart LR
  w["withdraw(...)"] -->|true| ok["Main: uttag beviljat"]
  w -->|false| stop["Main: uttag stoppat"]
```

**Kom ihåg / INTE:** `boolean` ersätter inte meddelandet + oförändrat saldo — det **kompletterar** så Main kan styra nästa steg.

---

## Checkpoint (privat)

Säg högt: objekt före punkt, deposit ökar, withdraw har två vägar, this vs amount. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
