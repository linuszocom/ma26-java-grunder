# 02 — Visuellt: factory, sök och meny

Samma bilder som i teoriguiden — nu som flöde. `createAccount`, `findAccount`, meny 1–5. GitHub renderar diagrammen automatiskt.

---

## Tre filer — ansvar

```mermaid
flowchart TB
  main["Main.java<br/>Scanner · meny-loop"]
  reg["AccountRegister.java<br/>List · createAccount · findAccount · printAll"]
  acc["Account.java<br/>deposit · withdraw · getters"]
  main -->|"createAccount / findAccount / printAll"| reg
  reg -->|"get(i) · return pekare"| acc
  main -.->|"ALDRIG new Account"| acc
```

**Vad diagrammet visar:** Main anropar register. Register äger listan och skapandet. Main skapar inte konton direkt.  
**Kom ihåg / INTE:** Pil från Main till `new Account` ska inte finnas efter refaktorering.

---

## Factory — en dörr för `new`

```mermaid
flowchart LR
  subgraph daligt["new utspritt i Main"]
    M1["new Account"] --> M2["glöm add?"]
    M3["new Account"] --> M4["spökkonto"]
  end
  subgraph bra["createAccount"]
    C1["new Account"] --> C2["accounts.add"]
    C3["Main anropar bara createAccount"]
  end
  daligt -->|"flytta new"| bra
```

**Målsvar (säg högt / skriv i README):** *“new Account står i createAccount. Main beställer — fabriken bygger och lägger i listan.”*

---

## `findAccount` — linjär sökning

```mermaid
flowchart TD
  start["findAccount(owner)"] --> loop["i = 0 … size-1"]
  loop --> get["a = accounts.get(i)"]
  get --> cmp["getOwner().equalsIgnoreCase(owner)?"]
  cmp -->|ja| ret["return a"]
  cmp -->|nej| next["i++"]
  next --> loop
  loop -->|slut utan träff| null["return null"]
```

**Kom ihåg / INTE:** Sök skapar inte `new Account`. Miss = `null`, inte tomt objekt.

---

## Träff vs miss i Main

```mermaid
flowchart LR
  find["findAccount('Alva')"] -->|träff| dep["found.deposit(100)"]
  find2["findAccount('Zara')"] -->|null| msg["Skriv: kontot finns inte"]
  dep --> ok["Rätt saldo ändras"]
  msg --> safe["Ingen NPE"]
```

**Vad diagrammet visar:** Null-kollen **före** punkt-metod.  
**Kom ihåg / INTE:** `found.deposit` när `found` är `null` → krasch.

---

## Menyval 3 — stegkedja (Exam README Q3)

```mermaid
flowchart LR
  s1["1. Val 3 + owner + belopp"] --> s2["2. findAccount(owner)"]
  s2 --> s3["3. deposit på pekare"]
  s3 --> s4["4. Utskrift / lista visar nytt saldo"]
```

**Målsvar (säg högt / skriv i README):** *“Inmatning → hitta objekt → metod på objekt → synlig effekt i konsolen.”*

---

## Lista håller pekare

```mermaid
flowchart LR
  f0["fack 0 → @ Alva"] --> h0["Alva 200"]
  f1["fack 1 → @ Bo"] --> h1["Bo 80"]
```

**Kom ihåg / INTE:** `get(0)` är “första facket idag” — inte “alltid Alva” om ordningen ändras.

---

## Testkedja via meny

```mermaid
flowchart TD
  c1["1. Skapa Alva"] --> c2["2. Skapa Bo"]
  c2 --> c3["3. Lista → 2 rader"]
  c3 --> c4["4. Sätt in Alva"]
  c4 --> c5["5. Uttag för stort på Bo → stopp"]
```

**Kom ihåg / INTE:** Stoppat uttag = samma regel som [09-transaktioner](../../vecka-39/09-transaktioner/) — meddelande + oförändrat saldo.

---

## Checkpoint (privat)

Säg högt: factory-plats, sök returnerar pekare eller null, meny kopplar val till register. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
