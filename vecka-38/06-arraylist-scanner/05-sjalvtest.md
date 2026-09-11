# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför använder du en **array** i stället för fem separata `int`-variabler för en packlista med fem föremål?  
2. Array med `length == 4` — vilket är **första** och **sista lagliga** index? Vad händer vid `arr[4]`?  
3. Skillnad **`arr.length`** och **`lista.size()`** — parenteser och när du använder vardera?  
4. Varför deklarerar du **`List<String>`** men skriver **`new ArrayList<>()`**? (Två roller.)  
5. Hur skriver du ut **alla** element i en `List<String>` med en `for`-loop? Nämn `get` och `size`.  
6. Vad gör **`Scanner.nextLine()`** — och hur skiljer det sig från **`nextInt()`**?  
7. Användaren skriver `5` + Enter, sedan `Kaffe` + Enter. Koden kör `nextInt()` och direkt `nextLine()` för produktnamn. Vad blir produktsträngen troligen — och **varför**?  
8. **Fix:** Skriv två kodrader (inte hela program) som löser problem i fråga 7 efter `int antal = scanner.nextInt();`  
9. Peka i *din* kod från [03 — Övningar](./03-ovningar.md): nämn **en array-indexering** och **ett `get`-anrop** — förklara skillnad syntax.  
10. **Exam-koppling:** Examination 1 ska hålla konton i en lista; Examination 2 ska hålla medlemmar i en lista. Nämn **två** saker du tränade i den här mappen som överförs dit (ännu utan egna klasser i listan här).

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. **Ett namn, många fack** — en loop kan gå igenom alla; lättare att ändra antal fack på ett ställe; samma mönster som senare listor. Fem variabler skalar inte och går inte att loopa utan duplication.  
2. **Första index 0, sista 3.** `arr[4]` → `ArrayIndexOutOfBoundsException` (index 4 finns inte; length är 4 ⇒ index 0–3).  
3. **Array:** `.length` **utan** parentes — antal fack. **Lista:** `.size()` **med** parentes — antal element. Loop: `i < arr.length` respektive `i < lista.size()`.  
4. **`List`** = kontrakt/typ du jobbar mot (flexibelt, kodstandard). **`ArrayList`** = konkret implementation du **skapar** med `new`. Variabeln ska inte låsa vid implementation i deklarationen.  
5. `for (int i = 0; i < lista.size(); i++) { System.out.println(lista.get(i)); }` — eller formaterad variant. `get(i)` läser index `i`; loopen stannar före `size()`.  
6. **`nextLine()`** läser hela raden som `String` (text till Enter). **`nextInt()`** läser ett heltal — lämnar ofta **Enter kvar** i kön. Olika returtyper och olika beteende kvar i bufferten.  
7. Produkt blir troligen **tom sträng `""`** (eller bara whitespace). **`nextInt()`** tog `5` men lämnade radbrytningen; **`nextLine()`** läste den tomma raden — `"Kaffe"` ligger kvar till **nästa** `nextLine()`.  
8. T.ex. `scanner.nextLine();` (släng Enter) följt av `String produkt = scanner.nextLine();` — eller motsvarande där andra raden är den som sparar namnet.  
9. Subjektivt — rimligt: array `packVikt[i]` med hakparentes, ingen metod; lista `spellista.get(i)` med metodanrop. Båda 0-baserade. Fel om de beskrivs som identiska syntax.  
10. T.ex. **(a)** samla flera rader i en **lista** med `add` och loopa ut med `get`/`size`; **(b)** **Scanner** för inmatning i meny/register; **(c)** indextänk 0 … size−1; **(d)** undvika IndexOutOfBounds vid fel `get`. (Två räcker.)

</details>

---

## Klart för Pass 3?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i egen kod:

- [ ] Målsvar array (index 0, length, loop) — egna ord, högt  
- [ ] Målsvar List/add/get/size — egna ord, högt  
- [ ] Målsvar nextInt + nextLine-fällan — egna ord, högt  
- [ ] Packlista, spellista och inköpslista körda i IDE  
- [ ] Minst fyra FEEDBACK-rader från AI-träningen sparade  

Då har du landat vecka 38 pass 3. Nästa i kursen: klasser och objekt (vecka 39).

---

## Nästa steg

Fortsätt till vecka 39-material när det publiceras — eller repetera [04-loopar-meny](../04-loopar-meny/) och [05-metoder](../05-metoder/) om något känns svagt.
