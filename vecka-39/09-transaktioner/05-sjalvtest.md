# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför ska `deposit` / `withdraw` ligga i `Account` som **instansmetoder** — inte som `static` i `Main`?  
2. Vad händer med `balance` när du anropar `nora.deposit(50.0)`?  
3. Vad betyder **`this.balance`** inuti `withdraw` när anropet var `nora.withdraw(20)`?  
4. Skillnad **`this.balance`** vs parametern **`amount`**?  
5. Vad är **uttagsregeln** vid belopp större än saldo? (Två saker.)  
6. Varför är den här `withdraw` fel mot regeln?

```java
public void withdraw(double amount) {
    this.balance = this.balance - amount;
    if (amount > this.balance) {
        System.out.println("Nej");
    }
}
```

7. Nora har `300`, Erik har `100`. Du kör `nora.withdraw(50)`. Vad händer med Eriks saldo — och varför?  
8. Räcker det att skriva ett meddelande om du **samtidigt** minskar saldot vid för stort uttag?  
9. *(Valfritt djup)* Vad ger `boolean withdraw` dig **utöver** meddelande + oförändrat saldo?  
10. Peka i *din* övningskod: `deposit`-huvud, `withdraw`-`if`, ett anrop i `Main` — och **varför** stoppgrenen inte tilldelar `balance`.  
11. *(Koppling Exam 1)* Vad ska du kunna säga muntligt om ett stoppat uttag i Kontoappen?

---

## Facit

<details>
<summary>Fråga 1 — instansmetod</summary>

Jobbet hör till **kontot**: samma regel för varje objekt. Du anropar `objekt.deposit(...)` så **rätt** `balance` ändras. `static` i `Main` duplicerar lätt logik och blandar ansvar.

**Målsvar-nivå:** *“Metoden bor på Account. Anropet objekt.metod väljer vilket saldo som påverkas.”*

</details>

<details>
<summary>Fråga 2 — deposit</summary>

`amount` läggs till på **Noras** `balance` (via `this.balance` i metoden). Andra objekts saldo ändras inte.

</details>

<details>
<summary>Fråga 3 — this</summary>

`this` är **nora** — objektet som fick anropet. `this.balance` är Noras saldo i den stunden.

</details>

<details>
<summary>Fråga 4 — this vs amount</summary>

**`this.balance`:** fältet på objektet.  
**`amount`:** beloppet som skickades in i parentesen vid anropet.

De är inte samma sak.

</details>

<details>
<summary>Fråga 5 — uttagsregeln</summary>

1. **`balance` oförändrat**  
2. **Tydligt meddelande** (t.ex. att uttaget medges ej)

**Målsvar:** *“För stort uttag: saldo orört + meddelande.”*

</details>

<details>
<summary>Fråga 6 — fel ordning</summary>

Minus körs **först**. Sedan jämför `if` mot ett **redan sänkt** saldo — meddelandet hjälper inte; pengarna (eller negativt saldo) är redan borta. Villkoret måste komma **före** mutation, och stoppgrenen får **inte** subtrahera.

</details>

<details>
<summary>Fråga 7 — två objekt</summary>

Eriks saldo **oförändrat**. Anropet stod på `nora` — `this` inne i metoden är Nora. Erik anropades aldrig.

</details>

<details>
<summary>Fråga 8 — meddelande + minus</summary>

**Nej.** Exam-kravet är meddelande **och** oförändrat saldo. Meddelande utan stoppad mutation bryter regeln.

</details>

<details>
<summary>Fråga 9 — boolean</summary>

`Main` får ett **`true`/`false`** att styra nästa steg med (`if (konto.withdraw(...))`). Det ersätter inte meddelande + oförändrat saldo — det kompletterar.

</details>

<details>
<summary>Fråga 10 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **deposit:** `public void deposit(double amount)` + ökning av `this.balance`  
- **withdraw if:** `amount > this.balance` **före** minus  
- **anrop:** `nora.deposit` / `nora.withdraw`  
- **varför ingen tilldelning i stopp:** saldot ska vara oförändrat

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 11 — Exam 1</summary>

Ungefär: *“När beloppet är större än saldot körs inte minskningen. Användaren får ett meddelande. balance är samma före och efter anropet. Jag pekar på if-grenen i withdraw.”*

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar metod på objekt — egna ord, högt  
- [ ] Målsvar uttagsregeln — egna ord, högt  
- [ ] Målsvar `this` (kort) — egna ord, högt  
- [ ] Uppgift 1 (`deposit`) och uppgift 2 (stoppat `withdraw`) körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat transaktioner på `Account`. Nästa steg: inkapsling och konstruktor i vecka 40 (*publiceras i nästa del*). Se även [08-klasser-objekt](../08-klasser-objekt/) om klass/objekt fortfarande känns lös.
