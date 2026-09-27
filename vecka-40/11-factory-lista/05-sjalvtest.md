# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför ska `new Account` stå i `createAccount` och **inte** i `Main`? (Två skäl.)  
2. Vad gör `createAccount` som två separata steg (`new` + `add`) som Main lätt kan glömma om de skiljs?  
3. Vad returnerar `findAccount("Leo")` om Leo finns i listan? Om `"Zara"` saknas?  
4. Varför `getOwner().equalsIgnoreCase(owner)` — inte `a == owner`?  
5. Vad händer om du kör `register.findAccount("X").deposit(100)` utan null-koll när X saknas?  
6. Varför är `accounts.get(0).deposit(100)` ett dåligt mönster jämfört med sök på ägare?  
7. Nämn **fyra** steg i stegkedjan för menyval 3 (sätt in) — från användarens val till synlig effekt.  
8. Vilka menyval (1–5) ska finnas i Exam 1 — och vilket val avslutar loopen?  
9. Varför deklareras listan som `List<Account>` men skapas med `new ArrayList<>()`?  
10. Peka i *din* övningskod: `createAccount`, en rad i `findAccount`, null-koll i meny — och **var** `new Account` får stå.  
11. *(Koppling Exam 1)* Vad ska README Q2 ungefär svara om factory — var skapas objekten och varför inte i `Main`?  
12. *(Koppling Exam 1)* Efter testkörning: vad ska du **se** i konsolen efter stoppat uttag på för lågt saldo?

---

## Facit

<details>
<summary>Fråga 1 — varför inte new i Main</summary>

1. **Exam / README Q2:** Ett tydligt skapande-ställe — factory.  
2. **Listan:** `createAccount` kan alltid `add` efter `new`. Main kan skapa **spökkonton** utanför listan.

**Målsvar-nivå:** *“Main beställer. Registret skapar och lägger i listan. new Account ska inte vara utspritt i Main.”*

</details>

<details>
<summary>Fråga 2 — new + add</summary>

`new` bygger objektet i minnet. `add` lägger pekaren i registrets lista. Utan båda i samma metod kan Main `new`:a utan `add` — `printAll` visar inte kontot.

</details>

<details>
<summary>Fråga 3 — retur findAccount</summary>

Leo → **pekare** (`Account`) till Leos objekt (samma som i listan). Zara saknas → **`null`** (ingen pekare).

</details>

<details>
<summary>Fråga 4 — equalsIgnoreCase</summary>

`==` jämför referenser, inte textinnehåll. `getOwner()` ger en `String`. `equalsIgnoreCase` matchar `"leo"` och `"Leo"`. Utan getter når du inte `private owner`.

</details>

<details>
<summary>Fråga 5 — NPE</summary>

`findAccount` returnerar `null`. Anropet `.deposit(100)` på `null` ger **`NullPointerException`**. Lösning: spara i variabel, `if (found != null)`.

</details>

<details>
<summary>Fråga 6 — get(0)</summary>

Fack 0 är **ordning**, inte identitet. Nytt konto först i listan → fel person får pengar. Sök på **ägare** hittar rätt objekt oavsett index.

</details>

<details>
<summary>Fråga 7 — stegkedja val 3</summary>

Rimlig kedja (4+ steg):  
(1) Användaren väljer 3 och anger ägare + belopp.  
(2) `Main` anropar `findAccount(owner)`.  
(3) Träff → `deposit(amount)` på det objektet.  
(4) Ev. bekräftelse eller lista visar höjt saldo.

</details>

<details>
<summary>Fråga 8 — menyval Exam</summary>

1 Skapa · 2 Lista · 3 Sätt in · 4 Ta ut · **5 Avsluta** (lämnar loopen).

</details>

<details>
<summary>Fråga 9 — List vs ArrayList</summary>

**`List`** = deklarationstyp (gränssnitt) — flexibelt och kursstandard. **`ArrayList`** = konkret implementation som faktiskt skapas. Samma mönster som `List<String>` i vecka 38.

</details>

<details>
<summary>Fråga 10 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **`createAccount`:** rad med `new Account` **och** `accounts.add`  
- **`findAccount`:** loop + `equalsIgnoreCase` + `return null` sist  
- **Meny:** `if (found != null)` före `deposit`/`withdraw`  
- **`new Account`:** bara i `createAccount` (sök i projektet)

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 11 — README Q2</summary>

Ungefär: *“Account-objekt skapas i createAccount i AccountRegister. Där står new Account. Main anropar bara createAccount så varje konto hamnar i listan och skapandet inte är utspritt.”*

</details>

<details>
<summary>Fråga 12 — stoppat uttag</summary>

**Meddelande** att uttaget medges ej (eller liknande). **Saldo oförändrat** före/efter — samma regel som v3 transaktioner. Lista efteråt ska visa samma belopp på kontot.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar factory — egna ord, högt  
- [ ] Målsvar sök + null — egna ord, högt  
- [ ] Målsvar meny/stegkedja — egna ord, högt  
- [ ] Uppgift 1 (refaktorera `new`) och uppgift 2 (mini-meny) körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat factory, sök och meny. Nästa steg: [12-arv-exam1-start](../12-arv-exam1-start/) — eller fortsätt Exam 1-repo om du redan startat. Saknar du inkapsling/lista: [10-inkapsling](../10-inkapsling/).
