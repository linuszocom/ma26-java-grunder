# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad gör ett `if`-statement — och vad händer om villkoret är `false` och det **inte** finns `else`?  
2. Skillnad mellan `=` och `==` i Java — när använder du vilket i ett villkor?  
3. När väljer du `else if` i stället för ett nytt, fristående `if`?  
4. Vad betyder `&&` respektive `||`? Ge ett kort vardagsexempel vardera (inte från minnet av facit — ditt eget).  
5. Vad är en **död gren**? Hur hittar du en i en `else if`-kedja?  
6. Varför rekommenderas `{ }` även runt en enda rad i `if`?  
7. Givet: `int score = 650;` och kedjan `if (score >= 800) … else if (score >= 400) … else …` — vilken gren körs?  
8. Givet: `boolean frostWarning = true;` — vad är värdet av `!frostWarning`?  
9. Peka i *din* kod från [03 — Övningar](./03-ovningar.md): nämn ett villkor och **varför** du valde `>`, `>=`, eller `==` där.  
10. Koppling till Exam 1: varför behöver `withdraw` ett villkor — vad ska hända när beloppet är större än saldot?

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. **`if`** testar om uttrycket i parentesen blir `true`. Om ja — körs blocket. Om `false` **utan** `else` — hoppas blocket över; programmet fortsätter efter `if`.  
2. **`=`** tilldelar (stoppar värde i variabel). **`==`** jämför om två värden är lika och ger `boolean`. I `if`-parentes ska du **jämföra** (`==`, `<`, `>=`, …), inte tilldela med `=` (utom medveten boolean-tilldelning — undvik).  
3. **`else if`** när grenarna är **ömsesidigt uteslutande** — bara en ska vinna (t.ex. temperaturzoner). Fristående `if` när flera villkor oberoende kan vara true samtidigt.  
4. **`&&`:** båda måste vara true (t.ex. “bonus om poäng hög **och** daglig quest klar”). **`||`:** minst en true (t.ex. “fri frakt om medlem **eller** order över 500 kr”).  
5. **Död gren** = kod som aldrig kan köras p.g.a. ordning/täckning i tidigare villkor. **Hitta:** rita stege, sätt in testvärde, följ uppifrån — markera grenar som omöjliga att nå.  
6. Utan klammer gäller bara **nästa rad** för villkoret; fler rader körs oavsett. `{ }` gör blocket tydligt och säkrar vid ändringar.  
7. **`score >= 800`** false. **`score >= 400`** true → **mitten-grenen** (400–799) körs.  
8. **`!frostWarning`** → `false` (not true).  
9. Subjektivt — rimligt om du kopplar operator till frågan (“>= 800 för att inkludera exakt 800”). Fel om “AI skrev det” eller “såg bra ut”.  
10. **`withdraw`** ska **inte** minska saldo om beloppet > saldo — villkor stoppar uttaget och skriver meddelande. Samma tänk som `if (amount <= balance)` i framtida kod (metod kommer senare i kursen).

</details>

---

## Facit — övningar (kort)

<details>
<summary>Visa facit för Uppgift 1–2 (efter eget försök)</summary>

### Uppgift 1 — ScoreCheck (riktning)

- Byt `if (score = highScoreTarget)` till `if (score == highScoreTarget)` (eller `>=` om du vill fira “minst high score” — motivera).  
- Ordna om stege, t.ex.:  
  - `if (score == highScoreTarget)` → “Nytt high score!”  
  - `else if (score > 500)` → “Halvvägs till bonus.”  
  - `else if (score > 0)` → “Poäng registrerade.”  
  - `else` → “Ingen poäng än.”  
  (Smalare/trösklar först om du vill undvika död gren.)  
- För `score = 750`, `highScoreTarget = 800`: första false, andra true → **“Halvvägs till bonus.”**  
- Död gren i originalet: `else if (score > 500)` efter `else if (score > 0)` — alla score > 500 träffar redan `score > 0`.

### Uppgift 2 — TempZones (riktning)

- Stege uppifrån: extrem kyla (`<= -10`), frost (`<= 0`), kyligt (`<= 12`), behagligt (`<= 22`), else varmt.  
- `(tempC = -3, windAlert = false)` → **Frost** (inte extrem).  
- `(tempC = 8, windAlert = true)` → **Kyligt** + extra rad med `if (tempC <= 12 && windAlert)` → “Varning: kyla + vind”.  
- `&&` för vindvarning: både kyla **och** vindflagga.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i egen kod:

- [ ] Målsvar `if` / logik — egna ord, högt  
- [ ] Målsvar `=` vs `==` — egna ord, högt  
- [ ] En död gren förklarad med ordning i kedjan  
- [ ] Minst ett villkor med `&&` eller `||` förklarat i din kod  

Då har du landat villkor-målet för vecka 1. Nästa: loopar och meny-val (vecka 2).
