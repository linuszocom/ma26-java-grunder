# 03 — Övningar

**Omfång den här veckan:** `while`, `for`, `count++` / `count--`, loop-villkor, oändlig vs avslutande loop, off-by-one (`<` vs `<=`), `Scanner` + `nextInt()`, meny-loop tills avsluta (`0`). All kod i **`main`**. Inga egna metoder utöver `main`. Ingen `ArrayList`. Ingen OOP. Ingen Git. Ingen `switch`. NOLL SPILL.

AI får hjälpa dig skriva. Du måste kunna **peka och förklara** varje loop-villkor och var loopen avslutas.

---

## Uppgift 1 — Löpbandet som aldrig stannar (fixa oändlig `while`)

**Mål:** Hitta varför loopen aldrig slutar. Laga så exakt **fem** rader “Knäböj {n}” skrivs (n = 1 … 5) och programmet avslutas normalt.

**Scenario:** Ett träningspass ska räknas med `while`. Någon lämnade koden nedan — den skriver samma rad om och om igen (eller hänger). Du ska **inte** skriva om från noll utan **fixa** logiken.

**Startkod (med bugg):**

```java
public class RepFix {
    public static void main(String[] args) {
        int rep = 1;
        while (rep <= 5) {
            System.out.println("Knäböj " + rep);
            // rep++;  ← av misstag bortkommenterad i originalet
        }
        System.out.println("Pass klart!");
    }
}
```

**Krav:**
1. Skapa klass `RepFix` i ditt övningsprojekt.
2. Fixa loopen så **exakt fem** rader skrivs och `"Pass klart!"` syns efteråt.
3. Använd `while` (byt inte till `for` i den här uppgiften).
4. Kör i IDE — bevisa att programmet **inte** behöver stoppas manuellt.

**Klart-check (peka i DIN kod):**
- [ ] Peka på raden som gjorde att villkoret aldrig blev false — vad saknades?  
- [ ] Peka på `while`-villkoret och säg vilket värde `rep` har när loopen **lämnas**  
- [ ] Visa konsolutskrift: fem knäböj-rader + “Pass klart!”  
- [ ] Inga metoder utöver `main`, ingen `Scanner` här  

**Ägarskap:** AI ok som bollplank — spara **en mening** om vad som orsakade oändlig loop. Du ska kunna förklara muntligt utan att läsa koden ordagrant.

---

## Uppgift 2 — Hisstur off-by-one (fixa `for`-intervall)

**Mål:** Förstå `<` vs `<=`. Skriv om eller fixa en `for`-loop så utskriften matchar briefen exakt.

**Brief:** Ett hotell har våningar **1 till 8** inklusive. Programmet ska skriva en rad per våning: `"Hiss anländer våning X"`. Efter loopen: `"Destination nådd."`

**Startkod (skriver fel antal våningar):**

```java
public class HissTur {
    public static void main(String[] args) {
        for (int vaning = 1; vaning < 8; vaning++) {
            System.out.println("Hiss anländer våning " + vaning);
        }
        System.out.println("Destination nådd.");
    }
}
```

**Krav:**
1. Ny klass `HissTur.java`.
2. Fixa loopen så våning **8** ingår — inte bara 1–7.
3. Motivera skriftligt (två meningar i anteckningar): varför originalet var off-by-one och vilken operator/gräns du valde.
4. Alternativ lösning tillåten: behåll `<` men ändra start/gräns så 8 ändå skrivs — **motivera** i klart-check.

**Klart-check (peka i DIN kod):**
- [ ] Peka på for-villkoret (`<` eller `<=`) och säg vilket **sista** våningsnummer som skrivs ut  
- [ ] Kör programmet — räkna rader: ska vara **åtta** våningsrader  
- [ ] Förklara off-by-one med egna ord (inte “AI fixade”)  
- [ ] Ingen `while`, ingen `Scanner` i den här filen  

**Ägarskap:** Byt `vaning < 8` till `vaning <= 8` **eller** `vaning < 9` — båda kan funka; du ska veta **varför** ditt val ger 1…8.

---

## Uppgift 3 — P-automat med meny-loop (`Scanner` + `nextInt()`)

**Mål:** Bygga en textmeny som loopar tills användaren väljer avsluta. Läsa val med `Scanner`.

**Scenario (unikt — parkering, inte bank):** Du kodar en enkel **P-automat** för ett litet garage. Användaren ska kunna köpa tid, se pris och avsluta. All state kan vara hårdkodad eller en enkel `int`-räknare i `main` (t.ex. antal sålda biljetter) — **ingen lista**, ingen factory.

**Meny (minst):**

| Val | Handling |
|-----|----------|
| 1 | Skriv ut att 1 timme köpts (t.ex. `"Biljett: 1 timme, 25 kr"`) |
| 2 | Visa timpris (hårdkodat `"25 kr/tim"`) |
| 3 | (valfritt) Visa antal sålda biljetter om du räknar med `int biljetter` |
| 0 | Avsluta — skriv `"Garage stängt."` och **lämna** loopen |

**Krav:**
1. Klass `PAutomat.java` med `main`.
2. `import java.util.Scanner;` — **en** `Scanner` skapas före loopen.
3. `while (val != 0)` (eller motsvarande tydlig avslutslogik).
4. `if` / `else if` för val — **ingen** `switch`.
5. Ogiltigt val (t.ex. 9) ska ge tydligt meddelande men **inte** avsluta programmet.
6. Testa manuellt: minst ett köp, visa pris, ogiltigt val, avsluta med 0.

**Klart-check (peka i DIN kod):**
- [ ] Peka på `while`-raden — vad måste `val` vara för att loopen ska fortsätta?  
- [ ] Peka var `nextInt()` anropas — vad händer om användaren skriver bokstäver? (kort: programmet kan krascha — ok att notera; robust inmatning kommer senare)  
- [ ] Peka på grenen för val 0 — varför avslutas loopen **efter** att val lästs?  
- [ ] Kör och beskriv i en mening vad som händer vid val 1 och vid val 0  
- [ ] Inga egna metoder, ingen `ArrayList`, ingen Git  

**Ägarskap:** Spara en kort **datalogisk stegkedja** (3–5 steg) för val 1: visa meny → läs val → … → tillbaka till meny. Samma tänk som Exam 1 README senare.

---

## Stretch (frivilligt, inom VAD)

- Lägg till val 3: räkna `biljetter++` vid varje köp och skriv ut totalt sålda.  
- Skriv en **nedräknande** `while` (t.ex. nedstängning “Stänger om 5 … 1 min”) med `count--`.  
- Summera 1–100 med `for` och `sum += i` i en fjärde klass `SumHundred.java`.

---

## Nästa steg

När alla tre uppgifterna är klara och klart-checken sitter: [04 — AI-träning](./04-ai-traning.md).
