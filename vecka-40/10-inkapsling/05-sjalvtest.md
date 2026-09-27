# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad är **inkapsling** i dina ord — och varför bryr sig Exam 1?  
2. Peka mentalt i kod: var är **`private balance`** — och vad får `Main` göra istället för `kim.balance = …`?  
3. Vad betyder felet **`balance has private access in Account`**?  
4. Vad gör **`getOwner()`** och **`getBalance()`** — och vad gör de **inte**?  
5. Varför är **`setBalance`** en dålig idé i Kontoappen?  
6. Vad händer när du skriver **`new Account("Kim", 1000)`** — vilken metod körs, och vem får sätta fälten?  
7. Förklara **`this.owner = owner`** i konstruktorn.  
8. Varför fungerar **`withdraw`** fortfarande med `this.balance` inuti `Account` trots `private`?  
9. Skillnad **`List<Account>`** som typ och **`new ArrayList<>()`** vid skapande?  
10. Vad lagrar **`accounts.get(0)`** — och varför räcker inte `println(accounts.get(0))` för att visa saldo?  
11. *(Exam README Q1)* Skriv **två meningar**: inkapsling + peka `private balance` + bakdörren om publikt fält.  
12. Peka i *din* övningskod: `private`, konstruktor, en getter, `List` i register, loop i `printAll`.  
13. Vad tillhör **Pass 2** (`11-factory-lista`) som **inte** ska finnas i det här paketet?

---

## Facit

<details>
<summary>Fråga 1 — inkapsling</summary>

Objektets data är **dold** (`private`) och nås utifrån via **kontrollerade metoder** (getters, deposit, withdraw). Exam 1 vill se att du förstår **varför** — inte bara att ordet finns.

**Målsvar-nivå:** *“State sitter inne i Account. Main går via getters och affärsmetoder — inte direkt på fälten.”*

</details>

<details>
<summary>Fråga 2 — private balance</summary>

Fältet är låst för `Main`. Läsa: `getBalance()`. Ändra saldo: `deposit` / `withdraw` — inte tilldelning med `=`.

</details>

<details>
<summary>Fråga 3 — has private access</summary>

Du försöker nå `balance` (eller `owner`) **från en annan klass** (`Main`). javac stoppar **före körning**. Fix: getter eller flytta logik till `Account` — **ta inte bort** `private`.

</details>

<details>
<summary>Fråga 4 — getters</summary>

Returnerar ägare/saldo för utskrift. De **ändrar inte** saldo och är **inte** setters.

</details>

<details>
<summary>Fråga 5 — setBalance</summary>

Ger `Main` en **skriv-dörr** till saldo — samma risk som publikt fält (`-99999`). Exam kräver getters, inte setters på balance.

</details>

<details>
<summary>Fråga 6 — new Account</summary>

**Konstruktorn** körs. Den sätter `this.owner` och `this.balance` **inuti** `Account`. `Main` får inte fylla private-fält direkt efteråt.

</details>

<details>
<summary>Fråga 7 — this i konstruktor</summary>

`this` = objektet som skapas. Vänster `owner` = fältet i valvet. Höger `owner` = parametern från `new`.

</details>

<details>
<summary>Fråga 8 — withdraw inuti</summary>

`private` gäller **åtkomst mellan klasser**. Kod **inuti samma klass** (`Account`) får läsa/skriva `balance` direkt.

</details>

<details>
<summary>Fråga 9 — List vs ArrayList</summary>

**Deklarera** mot interface `List` (flexibelt, kodstandard). **Skapa** konkret `ArrayList` med `new ArrayList<>()`.

</details>

<details>
<summary>Fråga 10 — get(0)</summary>

En **referens** till ett `Account`-objekt. `println` på objektet skriver **adress** (`Account@…`). Visa ägare/saldo med getters eller metod på kontot.

</details>

<details>
<summary>Fråga 11 — Exam README Q1</summary>

Ungefär: *“Inkapsling betyder att balance är private så Main inte kan skriva godtyckliga värden. Jag pekar på private balance i Account.java. Hade fältet varit publikt kunde Main sätta balance = -99999 utan att withdraw-regeln används.”*

</details>

<details>
<summary>Fråga 12 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **private** framför fält  
- **konstruktor** med `this.owner = owner`  
- **getOwner** eller **getBalance**  
- **`List<Account> accounts`** + **`new ArrayList<>()`**  
- **for-loop** med `get(i)` i `printAll`

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 13 — Pass 2</summary>

`createAccount` (factory), hitta konto på `owner`, ev. sökning — **inte** i slug 10. Inte heller full Exam-meny eller arv här.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar inkapsling + Exam Q1 — egna ord, högt  
- [ ] Målsvar konstruktor + getters — egna ord, högt  
- [ ] Målsvar registerlista — egna ord, högt  
- [ ] Uppgift 1 (private/konstruktor/getters) och uppgift 2 (register, ≥2 konton) körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat inkapsling och registergrund. Nästa steg: [11-factory-lista](../11-factory-lista/) — factory och sökning (*publiceras i nästa del*). Saknar du `deposit` / `withdraw`: [09-transaktioner](../../vecka-39/09-transaktioner/).
