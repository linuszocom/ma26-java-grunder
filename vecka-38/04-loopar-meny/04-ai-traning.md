# 04 — AI-träning: Loopar & ägarskap

AI kan skriva `while` och `for` på sekunder. Det betyder inte att *du* äger loopen. Här tränar du samma färdighet som examinationen kräver: **se vad som är svagt, ändra, förklara** — särskilt oändliga loopar, fel `<`/`<=`, och slarv kring `Scanner`.

Det är inte magi att “granska AI”. Det är samma metod som i teoriguiden — peka på villkoret, räkna varv, fråga om något gör att loopen kan sluta.

---

## Scenario — problem först

Du ber AI: *“Skriv en Java-klass med en meny för en kiosk. Scanner nextInt. While tills 0. Räkna också summa 1 till 10 med for.”*

Du får tillbaka något i stil med:

```java
import java.util.Scanner;

public class KioskAi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int val = 1;

        while (val != 0) {
            System.out.println("1. Kaffe");
            System.out.println("2. Visa summa 1-10");
            System.out.println("0. Stäng");
            val = scanner.nextInt();

            if (val == 2) {
                int sum = 0;
                for (int i = 1; i < 10; i++) {
                    sum += i;
                }
                System.out.println("Summa: " + sum);
            }
        }

        int count = 0;
        while (count < 3) {
            System.out.println("Räknar...");
        }
    }
}
```

Koden **kompilerar** men beter sig illa: fel summa (off-by-one i `for`), andra `while` **hänger** (glömt `count++`), menyn kanske inte visar sig första gången som du vill, och `scanner.close()` saknas (det sista är **ok i övningskod** — fokus är loop-logik, inte resursstängning).

**Vad du tränar:** Feedback på AI-kod + omskrivning du äger.  
**Varför:** Muntlig redovisning kräver att *du* kan säga hur många varv en loop kör och när meny avslutas.  
**Vad det INTE är:** “AI skrev det, alltså klart.” Inte `ArrayList`, inte egna metoder, inte `switch`, inte Git.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt till AI (eller jobba mot snutten ovan) med samma krav: meny med `Scanner.nextInt()`, `while` tills 0, minst en `for`-loop som summerar ett intervall. Spara prompten.

### Steg 2 — Granska (checklist)
Gå igenom koden och kryssa:

- [ ] Varje `while` — **vad i kroppen** gör att villkoret kan bli false? (ingen oändlig loop?)  
- [ ] Varje `for` — stämmer `<` / `<=` med **första och sista** tal du vill inkludera?  
- [ ] Meny: visas alternativ **före** `nextInt()`? Avslut vid val 0?  
- [ ] `Scanner` skapad **en gång** före meny-loopen (inte ny varje varv)?  
- [ ] Kan du för `i` 1…10 säga exakt vilken summa `for`-loopen **borde** ge — och vad AI-koden faktiskt ger?  
- [ ] Bara `main`, ingen `ArrayList`, ingen `switch`?

Skriv **minst tre** konkreta feedback-punkter:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Minst en** FEEDBACK ska handla om **oändlig loop** (glömt steg i `while`).  
**Minst en** ska handla om **off-by-one** i `for` (`<` vs `<=`).  
**Minst en** ska handla om **meny/Scanner** (ordning, avslut, eller ogiltigt val).

### Steg 3 — Anpassa
Skriv om till en klass **du äger** (t.ex. `KioskFixed.java`):

- Meny-loop med minst två val + 0 avsluta  
- `for` som summerar **1 till 10** korrekt (`sum` ska bli 55)  
- Ingen hängande `while` — ta bort eller fixa med `count++`  
- `if` / `else if` på val — ingen `switch`  
- Kör i IDE med minst två menyval + avslut  

*(Att inte anropa `scanner.close()` är acceptabelt här — notera gärna i reflektion att stängning blir viktigare senare.)*

### Steg 4 — Reflektion (3 meningar)
Skriv i anteckningar eller `REFLEKTION.md`:

1. Vad var fel eller svagt i AI-förslaget (oändlig loop, fel summa, meny)?  
2. Vad ändrade du — peka på villkor och steg-rader?  
3. Varför är det viktigt inför Exam 1 (meny-loop i `Main` som inte hänger)?

---

## Klart-check (peka i DIN omskrivna kod)

- [ ] Tre FEEDBACK-rader sparade  
- [ ] Peka på fixad `while` — vilken rad gör att villkoret blir false?  
- [ ] Peka på `for`-villkoret — varför ger det summa 55 för 1…10?  
- [ ] Peka på `while (val != 0)` och förklara flödet vid val 0  
- [ ] Reflektionens tre meningar klara  

---

## Facit-riktning (efter egen granskning)

<details>
<summary>Visa facit-riktning (inte full kod — bygg själv först)</summary>

**Typiska fel i snutten:**
- `for (int i = 1; i < 10; i++)` — summerar 1…9, summa 45, inte 55. Fix: `i <= 10` eller `i < 11` beroende på start.  
- Andra `while (count < 3)` utan `count++` — oändlig “Räknar…”. Fix: lägg `count++` i kroppen eller ta bort test-loopen.  
- `val = 1` före loop kan funka med `while (val != 0)` men menyn körs innan användaren “sett” 0 — ofta bättre start `val = -1` eller visa meny direkt; motivera ditt val.  
- Saknad hantering av ogiltigt val — lägg `else if (val != 0)` med meddelande.  
- `scanner.close()` saknas — **ok i det här paketet**; viktigare att `nextInt()` sitter efter `print` och att loopen avslutas.

**Efter fix:** Summa-loopen ger 55. Ingen hängande while. Meny avslutas vid 0 med tydlig avskedstext.

Bygg din egen variant; facit är **korrekt beteende + förklaring**, inte copy-paste av en enda lösning.

</details>

---

## Nästa steg

[05 — Självtest](./05-sjalvtest.md) — utan att titta på facit först.
