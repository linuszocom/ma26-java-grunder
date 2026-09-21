# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad är skillnaden mellan **klass** och **objekt**?  
2. Varför räcker det inte med lösa variabler `owner1` / `balance1` i `main` när målet är Exam 1?  
3. Vilka **fält** ska `Account` ha i det här paketet — namn och ungefärlig typ?  
4. Vad gör **`new Account()`**?  
5. Vad betyder **`card.owner = "Alex"`** — punktnotation?  
6. Varför måste filen heta **`Account.java`** när klassen heter `Account`?  
7. Vad syns oftast om du skriver **`System.out.println(card)`** — och vad ska du skriva ut i stället?  
8. Du har två objekt `a` och `b`. Du sätter `a.balance = 800`. Vad händer med `b.balance`?  
9. Vad betyder **`NullPointerException`** när du tar `.owner` på en `Account`-variabel?  
10. Peka i *din* övningskod: klassen, ett `new`, två fält-tilldelningar — och **varför** du skapade en separat fil.  
11. *(Koppling Exam 1)* Hur är dagens `Account.java` första byggstenen mot Kontoappen — och vad kommer **senare** (utan att du kodar det nu)?

---

## Facit

<details>
<summary>Fråga 1 — klass vs objekt</summary>

**Klass:** mallen / typen i `Account.java` — beskriver vilka fält ett konto har.

**Objekt:** en **instans** i minnet efter `new Account()` — en konkret sak med egna fältvärden.

**Målsvar-nivå:** *“Klassen är mallen. Objektet är instansen efter new.”*

</details>

<details>
<summary>Fråga 2 — lösa variabler</summary>

Lösa namn hör inte ihop som en typ. Exam 1 kräver klassen **`Account`** (senare med metoder, inkapsling, register). Redan nu tränar du att **ägarskap + saldo** bor på ett objekt.

</details>

<details>
<summary>Fråga 3 — fält</summary>

Minst **`owner`** (`String`) och **`balance`** (`double` eller `int`) — engelska namn.

</details>

<details>
<summary>Fråga 4 — new</summary>

Skapar ett **nytt objekt** (instans) av typen `Account` i minnet och ger dig en referens du kan spara i en variabel.

</details>

<details>
<summary>Fråga 5 — punktnotation</summary>

Gå in i objektet som `card` pekar på och sätt (eller läs) fältet `owner`. Fältet hör till **objektet**, inte till klassen som “ett gemensamt saldo”.

</details>

<details>
<summary>Fråga 6 — filnamn</summary>

En `public class Account` **måste** ligga i filen `Account.java`. Annars: kompileringsfel. Fel stavning / svenska namn räknas inte.

</details>

<details>
<summary>Fråga 7 — println objekt</summary>

Oftast typ + intern adress (`Account@…`), **inte** ägare/saldo. Skriv ut `card.owner` och `card.balance`.

</details>

<details>
<summary>Fråga 8 — två objekt</summary>

`b.balance` **ändras inte** (så länge `a` och `b` pekar på **olika** objekt från två `new`). Varje instans har egna fält.

</details>

<details>
<summary>Fråga 9 — NPE</summary>

Variabeln pekar **ingenstans** (`null`) — du glömde `new` (eller tilldelade aldrig objektet). Fix: `card = new Account();` innan punkten.

</details>

<details>
<summary>Fråga 10 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **Klassfil:** `Account.java` / `public class Account`  
- **new:** raden som skapar instansen  
- **Fält:** `….owner = …` och `….balance = …`  
- **Varför egen fil:** Exam 1 / Java-krav — `public` klass i egen fil med matchande namn

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 11 — koppling Exam 1</summary>

Idag: filen `Account.java`, fält `owner` / `balance`, skapa med `new`, visa data. **Senare:** `private` + konstruktor, `deposit` / `withdraw`, lista/register, factory — men **samma** kärna: klassen är mallen, varje konto är ett objekt.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar klass vs objekt — egna ord, högt  
- [ ] Målsvar fält + `new` — egna ord, högt  
- [ ] Målsvar filnamn `Account.java` — egna ord, högt  
- [ ] Uppgift 1 och uppgift 2 körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat klass + objekt + fält. Nästa paket: [09-transaktioner](../09-transaktioner/) — `deposit` / `withdraw` (*publiceras i nästa del*).
