# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad gör en `while`-loop — och hur skiljer den sig från ett `if`?  
2. Vad händer om du glömmer `count++` i `while (count < 5)`?  
3. Skriv strukturen för en `for`-loop (tre delar i huvudet) och ge ett exempel som skriver ut 1, 2, 3, 4, 5.  
4. Skillnad mellan `i < 5` och `i <= 5` när `i` startar på 1 — vilket värde är **sista** som skrivs ut i varje fall?  
5. Vad är off-by-one — ge ett eget kort exempel (inte bara facit).  
6. Vad gör `Scanner` och `nextInt()` i en meny? Var i koden brukar du skapa `Scanner`?  
7. Varför `while (val != 0)` för en textmeny — vad betyder val 0?  
8. När väljer du `while` framför `for` — och tvärtom?  
9. Peka i *din* kod från [03 — Övningar](./03-ovningar.md): visa `while`-villkoret i P-automaten och förklara när loopen slutar.  
10. Koppling till Exam 1: varför behöver `Main` en meny-loop — vad ska hända när användaren väljer avsluta?

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. **`while`** testar villkoret; om true körs kroppen och kontrollen **upprepas**. **`if`** testar en gång. Loopen **hoppar tillbaka**; `if` gör det inte.  
2. **`count`** förblir samma — villkoret förblir true → **oändlig loop** (programmet hänger tills du stoppar det).  
3. **`for (start; villkor; steg)`** — t.ex. `for (int i = 1; i <= 5; i++) { System.out.println(i); }`.  
4. **`i < 5`** med start 1 → sista utskrift **4**. **`i <= 5`** → sista **5**.  
5. **Off-by-one** = ett varv för mycket eller för lite. Eget exempel: loop `i < 10` när du ville 1…10 — 10 saknas.  
6. **`Scanner`** läser från konsol; **`nextInt()`** läser nästa heltal. Skapa **en** `Scanner` före meny-loopen, inte ny varje varv.  
7. **`val != 0`** = fortsätt tills användaren väljer **0 (avsluta)**. Då blir villkoret false och programmet lämnar loopen.  
8. **`while`:** okänt antal varv, användaren styr stopp (meny). **`for`:** känt antal (summa, fast antal rader).  
9. Subjektivt — rimligt om du pekar på `while (val != 0)` och säger att loopen slutar när `val == 0` efter `nextInt()`. Fel om “den stannar av sig själv”.  
10. **Exam 1 `Main`** ska låta användaren göra flera bankval (skapa, lista, sätt in, ta ut) i **samma körning** och **avsluta medvetet** med val 5/0 — utan loop slutar programmet efter ett val.

</details>

---

## Facit — övningar (kort)

<details>
<summary>Visa facit för Uppgift 1–3 (efter eget försök)</summary>

### Uppgift 1 — RepFix

- Avkommentera eller lägg till `rep++;` i kroppen.  
- Efter fix: `rep` går 1→5, vid `rep == 6` är `rep <= 5` false.  
- Fem rader “Knäböj 1” … “Knäböj 5”, sedan “Pass klart!”.

### Uppgift 2 — HissTur

- Byt till `vaning <= 8` **eller** `vaning < 9` (med start 1).  
- Originalet `vaning < 8` ger våning 1–7 — **off-by-one** (8 saknas).  
- Åtta rader + “Destination nådd.”

### Uppgift 3 — PAutomat

- `while (val != 0)` med meny före `nextInt()`.  
- Val 1: köp-meddelande; val 0: `"Garage stängt."` och loop exit.  
- Ogiltigt val: meddelande, loop fortsätter.  
- Datalogisk kedja val 1: visa meny → läs `val` → `if (val == 1)` → utskrift biljett → tillbaka till while-test.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i egen kod:

- [ ] Målsvar **while** — egna ord, högt  
- [ ] Målsvar **meny-loop** — egna ord, högt  
- [ ] Målsvar **for / off-by-one** — egna ord, högt  
- [ ] P-automat kör i IDE utan manuell stopp  
- [ ] Summa 1–10 (AI-uppgiften) korrekt om du gjort steg 3  

Då har du landat loop- och meny-målet för v2 T1. Nästa paket: metoder (`05-metoder`, publiceras separat).
