# 02 — Visuellt: arv, lista och examination

Samma bilder som i teoriguiden — nu som flöde. GitHub renderar diagrammen automatiskt.

---

## Arv — basklass och subklass

```mermaid
flowchart TB
  Account["Account<br/>owner, balance<br/>deposit, withdraw, getters"]
  Savings["SavingsAccount extends Account<br/>+ interestRate<br/>+ applyInterest"]
  Account --> Savings
```

**Vad diagrammet visar:** Subklassen **är** ett konto plus eget. Basklassen försvinner inte.  
**Kom ihåg / INTE:** INTE `implements`. INTE två orelaterade klasser.

**Målsvar (säg högt / skriv i README):** *“extends = samma Account-dörrar + tillbyggnad.”*

---

## Konstruktor — super först

```mermaid
flowchart LR
  new["new SavingsAccount(...)"] --> super["super(owner, startBalance)<br/>Account fyller private fält"]
  super --> own["this.interestRate = ..."]
```

**Kom ihåg / INTE:** `this.interestRate` **före** `super` → javac-fel.

---

## Private mur — dörr, inte lucka

```mermaid
flowchart LR
  subgraph fel["Fel i subklass"]
    F1["this.balance = ..."]
    F2["javac: private access"]
  end
  subgraph ratt["Rätt"]
    R1["getBalance()"]
    R2["deposit(extra)"]
  end
  fel -->|"använd dörrar"| ratt
```

**Målsvar (säg högt / skriv i README):** *“Arv öppnar inte private. applyInterest via getBalance + deposit.”*

---

## `@Override` — två konton, samma anrop

```mermaid
flowchart TD
  loop["printAll: get(i).printInfo()"] --> a1["Account → en rad"]
  loop --> a2["SavingsAccount → super + ränta"]
```

**Kom ihåg / INTE:** Loopen behöver inte veta vilken typ — objektet vet sin klass.

---

## Polymorfism — en lista

```mermaid
flowchart TB
  list["ArrayList&lt;Account&gt;"]
  list --> i0["fack 0: Account Kim"]
  list --> i1["fack 1: SavingsAccount Moa"]
```

**Kom ihåg / INTE:** INTE bara `ArrayList<SavingsAccount>` om vanliga konton också ska in.

---

## Factory VG — syskon-dörr

```mermaid
flowchart LR
  main["Main / test"] --> ca["createAccount → new Account"]
  main --> cs["createSavingsAccount → new SavingsAccount"]
  ca --> list["accounts.add"]
  cs --> list
```

**Vad diagrammet visar:** Båda `new` i `AccountRegister` — inte utspritt i `Main`.

---

## G vs VG

```mermaid
flowchart LR
  G["G: Account + register + meny + README + muntligt"]
  VG["VG: + SavingsAccount i lista + under huven"]
  G --> VG
```

**Kom ihåg / INTE:** G = full OOP på inkapsling/factory — VG lägger **arv i appen**.

---

## README Q3 — stegkedja (meny “sätt in”)

```mermaid
flowchart LR
  in["inmatning<br/>ägare + belopp"] --> obj["findAccount"]
  obj --> met["deposit(amount)"]
  met --> ut["utskrift<br/>saldo / saknas"]
```

**Målsvar (säg högt / skriv i README):** *“Ett menyval = in → objekt → metod → ut.”*

**Kom ihåg / INTE:** INTE “while-loopen” utan objekt och metodnamn.

---

## Examination — två leveranser samma vecka

```mermaid
flowchart TB
  repo["Publikt GitHub-repo<br/>kod + README + ≥5 commits"]
  oral["Muntligt / inspelning<br/>IDE 2–3 delar 4–8 min"]
  repo --- oral
  moodle["Moodle samma examinationsvecka"]
  repo --> moodle
  oral --> moodle
```

**Vad diagrammet visar:** Repo och röst hör ihop — samma projekt, samma vecka.  
**Kom ihåg / INTE:** INTE webbdemo. INTE bara README utan IDE.

---

## Exam-repo start (struktur)

```mermaid
flowchart LR
  gh["Nytt GitHub-repo"] --> ide["IDE-projekt"]
  ide --> readme["README-utkast Q1–Q3"]
  readme --> c1["första commit"]
```

**Kom ihåg / INTE:** Det här paketet = utkast — färdig app = examinationsveckan.

---

## Checkpoint (privat)

Säg högt: extends, super, private via dörrar, en lista, README stegkedja, två exam-leveranser. Jämför med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
