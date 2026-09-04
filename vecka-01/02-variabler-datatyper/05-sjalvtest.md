# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad är en **variabel** — med lagerhylla-bilden?  
2. Vad gör **deklaration** — och vad gör den **inte**?  
3. Vad gör **tilldelning** (`=`)? Kan samma variabel få ett nytt värde?  
4. När väljer du **`int`**, **`double`**, **`String`**, **`boolean`**? Ge ett exempel värde för varje.  
5. Varför måste **`String`**-text ha citattecken i Java-kod?  
6. Vad skriver **`System.out.println`** — och ändras variabeln efter utskrift?  
7. Vad betyder felmeddelandet **`cannot find symbol`**?  
8. Vad betyder **`variable might not have been initialized`**?  
9. Peka i *din* övningskod (uppgift 1 eller 2): en deklaration, en tilldelning, en utskrift — och **varför** ordningen spelar roll.  
10. *(Koppling Exam 1)* Varför behöver du kunna hålla isär `String` (ägare) och `double`/`int` (saldo) redan nu — även innan bankklasserna?

---

## Facit

<details>
<summary>Fråga 1 — variabel</summary>

En variabel är en **namngiven plats i minnet** för ett värde. Metafor: etikett på en lagerhylla — etiketten är namnet, innehållet är värdet. Du kan läsa och (med tilldelning) byta innehåll utan att skapa en ny plats varje gång.

**Målsvar-nivå:** *“En variabel är en namngiven plats för ett värde.”*

</details>

<details>
<summary>Fråga 2 — deklaration</summary>

**Deklaration** skapar variabeln och anger **typ** (vilket fack/hylltyp). Exempel: `int antal;` eller `String namn;`.

**INTE:** att fylla värdet (det är tilldelning), och inte samma sak som utskrift.

</details>

<details>
<summary>Fråga 3 — tilldelning</summary>

**Tilldelning** (`=`) stoppar in ett värde i variabeln. `antal = 5;` fyller hyllan. Samma namn kan tilldelas igen — `antal = 10;` **ersätter** innehållet, skapar inte automatiskt en ny variabel.

</details>

<details>
<summary>Fråga 4 — fyra typer</summary>

| Typ | När | Exempel |
|-----|-----|---------|
| `int` | heltal | `42`, `0`, `-1` |
| `double` | decimaltal | `18.5`, `19.90` |
| `String` | text | `"Stockholm"`, `"Hej"` |
| `boolean` | ja/nej | `true`, `false` |

**Målsvar-nivå:** *“Heltal → int. Decimal → double. Text → String. Ja/nej → boolean.”*

</details>

<details>
<summary>Fråga 5 — citattecken</summary>

Utan `"..."` tolkar Java ord som **variabelnamn** eller nyckelord — `Erik` ger fel, `"Erik"` är text. Citattecken markerar **String-literal**.

</details>

<details>
<summary>Fråga 6 — println</summary>

`System.out.println` skriver variabelns **värde** till konsolen. Variabeln **töms inte** — du kan skriva ut samma variabel flera gånger och få samma värde (tills du tilldelar om).

</details>

<details>
<summary>Fråga 7 — cannot find symbol</summary>

Java hittar inte namnet — variabeln är **inte deklarerad** (eller stavfel). Fix: deklarera med rätt typ före användning, t.ex. `int antal;` eller `int antal = 5;`.

</details>

<details>
<summary>Fråga 8 — might not have been initialized</summary>

Variabeln **finns** men har **inget värde** än. Du försökte läsa (t.ex. `println`) innan tilldelning. Fix: tilldela värde före utskrift.

</details>

<details>
<summary>Fråga 9 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **Deklaration:** rad med typ + namn (ev. `= värde` på samma rad)  
- **Tilldelning:** rad med `=` som sätter värde (kan vara samma rad som deklaration)  
- **Utskrift:** `System.out.println(...)`  
- **Varför ordning:** du kan inte skriva ut eller använda en variabel som inte skapats/fyllts

Fel svar: “AI skrev det” utan pekning, eller peka på rad utan förklara typ/ordning.

</details>

<details>
<summary>Fråga 10 — koppling Exam 1</summary>

I Kontoappen har konton **text** (`owner` som `String`) och **tal** (`balance` som `double` eller `int`). Blandar du typer tidigt — text i tal-fack, decimal i heltal utan att tänka — blir det kompileringsfel senare eller svårare att förklara vid muntlig redovisning. Grunden: **rätt typ för rätt data**, deklarera och tilldela medvetet.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar variabel — egna ord, högt  
- [ ] Målsvar fyra typer — egna ord, högt  
- [ ] Målsvar metod (deklarera → tilldela → skriv ut) — egna ord, högt  
- [ ] Uppgift 1 (lager) och/eller 2 (väder) körda  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat variabler och datatyper. Nästa paket: [03-villkor-logik](../03-villkor-logik/) — villkor och logik (*publiceras i nästa del*).
