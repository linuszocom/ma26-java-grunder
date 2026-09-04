# 03 — Övningar

**Omfång den här veckan:** `if` / `else` / `else if`, jämförelser, `&&` / `||` / `!`, död gren, `=` vs `==`. Värden **hårdkodas** i `main`. Ingen `while` / `for`. Ingen `Scanner`. Inga egna metoder utöver `main`. NOLL SPILL.

AI får hjälpa dig skriva. Du måste kunna **peka och förklara** varje villkor du behåller — och vilken gren som körs.

---

## Uppgift 1 — Spelpoäng med tyst bugg

**Mål:** Hitta och fixa logikfel (`=` vs `==`, död gren). Förklara vilken gren som *faktiskt* körs.

**Scenario:** Ett enkelt poängsystem ska skriva olika meddelanden beroende på `score`. Någon lämnade koden nedan — den kompilerar (med en varning om du råkar ha fel typ) eller beter sig konstigt. Din uppgift är att **inte** skriva om från noll utan **laga** logiken.

**Startkod (med buggar):**

```java
public class ScoreCheck {
    public static void main(String[] args) {
        int score = 750;
        int highScoreTarget = 800;

        if (score = highScoreTarget) {
            System.out.println("Nytt high score!");
        } else if (score > 0) {
            System.out.println("Poäng registrerade.");
        } else if (score > 500) {
            System.out.println("Halvvägs till bonus.");
        } else {
            System.out.println("Ingen poäng än.");
        }
    }
}
```

**Krav:**
1. Skapa klass `ScoreCheck` i ditt övningsprojekt (en fil `ScoreCheck.java`).
2. Fixa så programmet **kompilerar** och utskriften stämmer för `score = 750` och `highScoreTarget = 800`.
3. Ta bort eller ordna om så **ingen död gren** finns kvar — varje `else if` ska kunna nås för *något* rimligt värde.
4. Behåll hårdkodade värden (byt inte till `Scanner`).
5. Efter fix: kör med minst två värden på `score` (750 och t.ex. 850) — ändra talet, kör igen, notera utskriften.

**Klart-check (peka i DIN kod):**
- [ ] Peka på raden du ändrade från `=` till `==` (eller motsvarande fix) och säg *varför* `=` var fel i `if`  
- [ ] Peka på `else if`-grenen som var **död** i startkoden — förklara ordningen  
- [ ] För `score = 750`: vilken rad skrivs ut? Visa med körning i konsolen  
- [ ] Alla block har `{ }` kring flera rader om du lägger till fler  

**Ägarskap:** AI ok som bollplank — spara vad du frågade och **en mening** om vad du fixade själv. Du ska kunna förklara varje villkor muntligt.

---

## Uppgift 2 — Temperaturzoner (else if-stege + `&&` / `||`)

**Mål:** Bygga en `else if`-stege från brief; kombinera villkor med `&&` eller `||`.

**Brief (ingen färdig logik):**  
Du skriver ett väderprogram för en odling. Hårdkoda `double tempC` och `boolean windAlert`. Programmet ska skriva **en** zon per körning:

| Zon | Regel |
|-----|--------|
| **Extrem kyla** | `tempC <= -10` |
| **Frost** | `tempC <= 0` (men inte redan extrem kyla) |
| **Kyligt** | `tempC <= 12` |
| **Behagligt** | `tempC <= 22` |
| **Varmt** | `tempC > 22` |

**Extra regel:** Om `windAlert` är `true` **och** `tempC <= 12`, skriv **först** (eller direkt efter zonen) en extra rad: `"Varning: kyla + vind"`. Du får lösa det med nästlade `if` inuti en gren **eller** med `&&` i ett separat block efter zonutskriften — men **ingen loop**.

**Krav:**
1. Ny klass `TempZones.java` med `main`.
2. Minst fyra `else if`-grenar + `else` eller sista gren för “varmt”.
3. Minst **ett** ställe med `&&` (kyla + vind) och **ett** ställe där du motiverar varför du **inte** behövde `||`.
4. Testa med minst två värden: `(tempC = -3, windAlert = false)` och `(tempC = 8, windAlert = true)`.
5. Kommentera **inte** bort kod — fixa riktig logik.

**Klart-check (peka i DIN kod):**
- [ ] Peka på hela `else if`-kedjan och säg vilken gren som körs för `tempC = 8` och `windAlert = true`  
- [ ] Peka på raden med `&&` — vad måste båda sidor vara?  
- [ ] Finns **ingen** död gren om du byter `tempC` till -15, 5, 18 och 30? (kör eller räkna på papper)  
- [ ] Inga loopar, ingen `Scanner`  

**Ägarskap:** Skriv två meningar i anteckningar: varför ordningen på `else if` spelar roll för frost vs extrem kyla.

---

## Stretch (frivilligt, inom VAD)

- Lägg till en femte/zon-gren (t.ex. `tempC > 30` → `"Hetta"`) utan att skapa död gren.  
- Eller: nästlade `if` — inuti “Behagligt”, skriv olika text om `windAlert` är true/false.

---

## Nästa steg

När båda uppgifterna är klara och klart-checken sitter: [04 — AI-träning](./04-ai-traning.md).
