# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför är **duplicerad kod** i `main` ett problem? Ge ett exempel (inte bara “det är dåligt”).  
2. Vad är en **metod** — och var i filen ska den ligga i det här paketet?  
3. Vad gör ett **anrop** (`metodnamn(...);`)?  
4. Skillnad **`void`** och metod med **returtyp** (t.ex. `double`)?  
5. Skillnad **parameter** vs **argument** — ge ett kort exempel.  
6. Vad gör **`return`** — och vad gör den **inte** ( jämför med `println` )?  
7. Varför kan du **inte** skriva `double x = skrivOrderRad(...);` om metoden är `void`?  
8. Vad betyder felmeddelandet **`missing return statement`**?  
9. Vad betyder det om javac klagar på **fel antal** argument vid anrop?  
10. Peka i *din* övningskod (uppgift 1, 2 eller 3): metodhuvud, en `return`-rad, ett anrop — och **varför** du valde parametrarna.  
11. *(Koppling Exam 1)* Hur liknar framtida `deposit(belopp)` och getters som returnerar saldo det du byggt idag — utan att du skrivit klassen `Account` än?

---

## Facit

<details>
<summary>Fråga 1 — duplicerad kod</summary>

Samma logik på flera ställen betyder att du måste **ändra varje kopia** när regeln ändras — lätt att missa en rad och få **inkonsistent** beteende. Exempel: fraktformel `varde * 0.15 + 29` kopierad tre gånger; ändras procenten till `0.18` glömmer du kanske order 102.

**Målsvar-nivå:** *“En kropp, flera anrop — ändring på ett ställe.”*

</details>

<details>
<summary>Fråga 2 — metod</summary>

En metod är ett **namngivet kodblock** med valfria parametrar och kropp. I det här paketet: **`public static`-metod utanför `main`**, fortfarande inuti klassen `Main`.

**INTE:** inuti `main`, inte en egen klass fil än.

</details>

<details>
<summary>Fråga 3 — anrop</summary>

Anropet **startar** metoden. Java hoppar till kroppen, kör den, och (om returtyp inte är `void`) **fortsätter i main med returvärdet** där anropet stod.

Parenteser **`()`** krävs även utan parametrar.

</details>

<details>
<summary>Fråga 4 — void vs retur</summary>

**`void`:** metoden gör sitt jobb (t.ex. skriver ut) men **lämnar inget värde** till anroparen.

**Returtyp (`double`, `int`, …):** metoden **`return`erar** ett värde som main kan spara i variabel eller skicka vidare.

</details>

<details>
<summary>Fråga 5 — parameter vs argument</summary>

**Parameter:** namn i **metoddeklarationen** — `beraknaFrakt(double varuvardet, ...)`.

**Argument:** **värde** i **anropet** — `beraknaFrakt(120.0, 0.15, 29.0)`.

Namn behöver inte matcha; **antal och typ** måste.

</details>

<details>
<summary>Fråga 6 — return vs println</summary>

**`return`:** skickar värde **tillbaka till Java-koden** som anropade — syns i konsol **först** om main skriver ut det.

**`println`:** skriver till **konsolen** — returnerar inget användbart värde till main.

</details>

<details>
<summary>Fråga 7 — void tilldelning</summary>

`void` betyder “ingen retur”. Det finns **inget tal** att stoppa i `double x`. javac: *void cannot be converted to double* (eller liknande).

</details>

<details>
<summary>Fråga 8 — missing return statement</summary>

Metoden lovar returtyp (t.ex. `double`) men ** alla kodvägar** når inte en **`return`**. Fix: `return uttryck;` med rätt typ.

</details>

<details>
<summary>Fråga 9 — fel antal argument</summary>

Anropet skickar **färre eller fler** värden än metodens parameterlista. Fix: räkna parametrar i deklaration vs argument i anrop — lägg till eller ta bort.

</details>

<details>
<summary>Fråga 10 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **Metodhuvud:** `public static double ... (...)`  
- **return:** rad som lämnar beräknat värde  
- **Anrop:** värden i parentes som matchar parametrar  
- **Varför parametrar:** formeln ska fungera för olika indata utan ny copy-paste

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 11 — koppling Exam 1</summary>

`deposit(belopp)` tar **belopp som parameter** — samma idé som `beraknaFrakt(varde, ...)`. Getters **returnerar** saldo/ägare så `main` (eller menyn) kan **läsa** utan att duplicera fältlogik. Idag tränar du mönstret i `Main`; senare flyttas kroppen till klassen `Account` — **parameter in, return ut, ingen triplicerad logik**.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar metod — egna ord, högt  
- [ ] Målsvar parameter/return — egna ord, högt  
- [ ] Målsvar varför metoder (återanvändning) — egna ord, högt  
- [ ] Uppgift 1 (frakt-refaktor) och minst uppgift 2 eller 3 körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat metoder i `Main`. Nästa paket: [06-arraylist-scanner](../06-arraylist-scanner/) — arrayer, listor och `Scanner` (*publiceras i nästa del*).
