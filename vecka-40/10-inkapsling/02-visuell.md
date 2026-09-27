# 02 — Visuellt: bankvalv, konstruktor och valvbok

Samma bilder som i teoriguiden — nu som flöde. `private`, getters, konstruktor och `AccountRegister`. GitHub renderar diagrammen automatiskt.

---

## Inkapsling — foajé vs valv

```mermaid
flowchart TB
  subgraph main["Main — foajé"]
    Mread["getOwner / getBalance"]
    Mwrite["deposit / withdraw"]
  end
  subgraph account["Account — bankvalv"]
    pf["private owner, balance"]
    dep["deposit / withdraw inuti"]
  end
  Mread -->|"läsa"| pf
  Mwrite -->|"regler"| dep
  dep --> pf
```

**Vad diagrammet visar:** `Main` når state via **dörrar** — inte direkt på facket.  
**Kom ihåg / INTE:** `private` gömmer fält **för Main**, inte för metoder **inuti** `Account`.

---

## Bakdörren — publikt vs private

```mermaid
flowchart LR
  pub["Publikt fält"] --> bad["Main: balance = -99999"]
  priv["private + getters"] --> ok["Main: getBalance + deposit"]
```

**Målsvar (säg högt / skriv i README — Exam Q1):** *“Publikt fält = Main kan skriva vad som helst. private stoppar det — jag pekar på private balance i README.”*

---

## Getters — läs genom luckan

```mermaid
flowchart LR
  main["Main: kim.getBalance()"] --> acc["Account: return balance"]
  acc --> main2["Main får 1000.0 att skriva ut"]
```

**Kom ihåg / INTE:** Getter **returnerar** — den ändrar inte saldo. `setBalance` vore skriv-dörr (stryk).

---

## Konstruktor — ett `new`, ett fyllt valv

```mermaid
flowchart LR
  n["new Account('Kim', 1000)"] --> k["konstruktor"]
  k --> th["this.owner / this.balance"]
  th --> kim["kim pekar på färdigt konto"]
```

**Vad diagrammet visar:** Fälten fylls **inuti** klassen vid födelse — Main sätter inte `kim.owner = ...` efter `private`.

---

## `this` i konstruktorn

```mermaid
flowchart LR
  arg["parameter owner = 'Kim'"] --> this["this.owner = owner"]
  this --> fack["fältet i detta objekt"]
```

**Målsvar (säg högt / skriv i README):** *“this = kontot som new bygger. Vänster = fält, höger = argument.”*

---

## Valvbok — lista håller pekare

```mermaid
flowchart TB
  reg["AccountRegister"]
  f0["fack 0 → Account Kim"]
  f1["fack 1 → Account Moa"]
  reg --> f0
  reg --> f1
```

**Vad diagrammet visar:** Listan lagrar **referenser** till konton — inte kopior av hela klassen.  
**Kom ihåg / INTE:** `println(accounts.get(0))` = adress — inte ägare/saldo.

---

## `add` och `printAll`

```mermaid
flowchart LR
  add1["add(new Account(...))"] --> size["size() växer"]
  size --> loop["for i: get(i).getOwner()"]
  loop --> out["konsol: Kim: 500.0"]
```

**Kom ihåg / INTE:** `List<Account>` som typ, `new ArrayList<>()` vid skapande — inte `ArrayList` som deklarerad typ.

---

## Tre filer

```mermaid
flowchart TB
  A["Account.java<br/>private + konstruktor + getters + transaktioner"]
  R["AccountRegister.java<br/>List + add + printAll"]
  M["Main.java<br/>register + add + printAll"]
  M --> R
  R --> A
```

---

## Checkpoint (privat)

Säg högt: valv/private, getter vs fält, konstruktor vid `new`, lista i register, Exam Q1-pekning. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
