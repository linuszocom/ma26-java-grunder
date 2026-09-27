# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt* och skriva i README.

Sedan: öppna facit och rätta dig.

---

## Frågor — arv

1. Vad betyder `public class SavingsAccount extends Account` i **en** mening?  
2. Varför måste `super(owner, startBalance)` stå **först** i subklassens konstruktor?  
3. Varför får `SavingsAccount` **inte** skriva `this.balance = …` direkt?  
4. Vad gör `@Override` på `printInfo()` — och varför anropa `super.printInfo()` först?  
5. Varför räcker `ArrayList<Account>` för både vanliga konton och sparkonton?  
6. Vad saknas för **VG** om `SavingsAccount.java` finns men aldrig skapas från appen?  
7. Skillnad **G** och **VG** i Examination 1 (kort, två rader vardera).

---

## Frågor — README och examination

8. README Q1: nämn **`private`**, fil och **vad som händer om publikt** — i egna ord.  
9. README Q2: var ska **`new Account`** stå — och varför **inte** i `Main`?  
10. Skriv stegkedja för menyval **“sätt in pengar”** (fyra steg).  
11. Vad ska **AI-reflektion** innehålla (minst två saker)?  
12. Vad ska **inspelningen / muntlig redovisning** visa — och vad är **underkänt**?  
13. Hur många **delar** ska du förklara i IDE:n — och måste minst en vara?  
14. Varför ska exam-repo vara **eget publikt** repo — inte kurs-hubben?

---

## Frågor — felsökning

15. Vad är fel här?

```java
public SavingsAccount(String owner, double startBalance, double interestRate) {
    this.interestRate = interestRate;
    super(owner, startBalance);
}
```

16. Vad är fel här?

```java
public void applyInterest() {
    balance += balance * interestRate;
}
```

17. AI skrev README Q3: *“Programmet kör en loop tills avslut.”* Varför räcker inte det?

18. Peka i *din* exam-README eller kod: en rad för Q1, en för Q2, en stegkedja för Q3, en rad under **Muntligt — mina 2–3 delar**.

---

## Facit

<details>
<summary>Fråga 1 — extends</summary>

Subklassen **är** ett `Account` plus eget (t.ex. ränta). Den **ärver** fält och metoder från basklassen och lägger till det som skiljer sparkontot.

**Målsvar-nivå:** *“SavingsAccount är Account + tillbyggnad.”*

</details>

<details>
<summary>Fråga 2 — super först</summary>

`Account` fyller `private` fälten via sin konstruktor. `super(...)` **måste** vara första satsen — annars kompilerar det inte och fälten initieras inte rätt.

</details>

<details>
<summary>Fråga 3 — private i subklass</summary>

`balance` är `private` i `Account`. Subklassen står utanför muren — samma som `Main`. Använd `getBalance()` och `deposit()`.

</details>

<details>
<summary>Fråga 4 — Override</summary>

Samma metodnamn som i basklassen, specialiserat beteende. `super.printInfo()` kör basklassens utskrift först; sedan extra rad (räntesats).

</details>

<details>
<summary>Fråga 5 — ArrayList&lt;Account&gt;</summary>

Ett `SavingsAccount`-objekt **är** ett `Account`. Listan kan hålla båda; `printInfo` kan vara `@Override` per objekt.

</details>

<details>
<summary>Fråga 6 — VG saknas</summary>

Subklassen måste **användas** — skapas (t.ex. `createSavingsAccount`), läggas i listan, synas vid utskrift/meny. Fil utan `new` i appen = inte VG.

</details>

<details>
<summary>Fråga 7 — G vs VG</summary>

**G:** Account + register + meny + README + muntligt 2–3 delar (övergripande). **VG:** allt det + `SavingsAccount` i appen + djupare muntligt (private, factory, arv under huven).

</details>

<details>
<summary>Fråga 8 — README Q1</summary>

Inkapsling = fält dolda (`private`), åtkomst via metoder/getters. Publikt `balance` hade låtit extern kod hoppa förbi `withdraw`-regeln.

</details>

<details>
<summary>Fråga 9 — README Q2</summary>

`new Account(...)` i `createAccount` i `AccountRegister`, sedan `add`. Main anropar bara factory — så varje konto hamnar i listan på samma sätt.

</details>

<details>
<summary>Fråga 10 — stegkedja sätt in</summary>

Inmatning (ägare + belopp) → `findAccount` hittar objekt → `deposit(amount)` på objektet → utskrift (nytt saldo eller att kontot saknas).

</details>

<details>
<summary>Fråga 11 — AI-reflektion</summary>

Var du körde fast; om AI användes — **ett exempel** där du **ändrade** förslaget; vad som fungerade efteråt. Inte tom fras.

</details>

<details>
<summary>Fråga 12 — inspelning</summary>

**Visa:** samma repo, IDE öppen, kod synlig, din röst, markör pekar (4–8 min **inspelning** eller muntlig redovisning enligt Moodle). **Underkänt:** läsa README rakt av, webbdemo, bara meny utan klass, någon annan pratar.

</details>

<details>
<summary>Fråga 13 — 2–3 delar</summary>

**2–3 delar** valda i förväg. Minst **en OOP-del** (t.ex. private/konstruktor, factory/new, withdraw, VG arv) — inte bara `while`-loopen.

</details>

<details>
<summary>Fråga 14 — eget repo</summary>

Examination 1 är **individuell**. Bedömning på **din** commits, README och muntligt. Kurs-hubb/grupp = fel leverans.

</details>

<details>
<summary>Fråga 15 — super-ordning</summary>

`super` står **efter** `this.interestRate =` — måste vara **första** satsen i konstruktorn.

</details>

<details>
<summary>Fråga 16 — balance i subklass</summary>

Direkt `balance` — `private access`. Byt till `getBalance()` och `deposit(extra)`.

</details>

<details>
<summary>Fråga 17 — svag Q3</summary>

Stegkedja kräver **objekt** (`findAccount`) och **metod** (`deposit`/`withdraw`) + **utskrift**. “Loopen” beskriver styrning, inte dataflödet för ett val.

</details>

<details>
<summary>Fråga 18 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **Q1:** `private` på `owner`/`balance` i `Account.java`  
- **Q2:** `new Account` inuti `createAccount` i `AccountRegister.java`  
- **Q3:** fyra steg med `findAccount` + `deposit` eller `withdraw`  
- **Muntligt:** t.ex. “Account.java — private balance” och “AccountRegister — createAccount”

Fel: “README finns” utan pekning.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, exam-repo skapats, README-utkast skrivet, och (valfritt) VG-stretch testad:

- [ ] Målsvar **extends/super** — egna ord, högt  
- [ ] Målsvar **README Q1–Q3** — egna ord, högt  
- [ ] **Muntligt — mina 2–3 delar** i README  
- [ ] Exam-repo med skelett + minst en commit  
- [ ] AI-träning med minst tre FEEDBACK-rader (README + arv)  
- [ ] Vet vad inspelningen ska visa (IDE, 2–3 pekare)  

Då har du landat v4 Pass 3. Nästa: vecka 41 — färdigställa Kontoappen och lämna in (*publiceras i* `13-exam-1/`). Repetera [examination_1_kontoappen.md](../../examination_1_kontoappen.md).
