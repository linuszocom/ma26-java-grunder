# 04 — AI-träning: Villkor & ägarskap

AI kan skriva `if`-satser på sekunder. Det betyder inte att *du* äger logiken. Här tränar du samma färdighet som examinationen kräver: **se vad som är svagt, ändra, förklara** — särskilt `=`, saknade klamrar och fel operator.

Det är inte magi att “granska AI”. Det är samma metod som i teoriguiden — peka på frågan, räkna true/false, hitta död gren.

---

## Scenario — problem först

Du ber AI: *“Skriv en Java-klass som kollar om en spelare får gå in i en zon. Hårdkoda level och hasKey. Skriv ut om dörren öppnas eller stängd.”*

Du får tillbaka något i stil med:

```java
public class ZoneGate {
    public static void main(String[] args) {
        int level = 12;
        boolean hasKey = true;

        if (level = 10)
            System.out.println("Boss zone — turn back.");
        else if (level >= 5 || hasKey = false) {
            System.out.println("Side area — proceed with caution.");
        } else if (level > 0) {
            System.out.println("Starter zone.");
        }

        if (level >= 10 && !hasKey)
            System.out.println("Door locked.");
        else
            System.out.println("Door open.");
    }
}
```

Koden **kompilerar inte** som den står (tilldelning där boolean krävs) — eller om AI “fixat” det slarvigt beter den sig fel. Dessutom: saknade klamrar, `hasKey = false` i stället för `== false` eller `!hasKey`, och `else if`-ordning som kan ge oväntad utskrift.

**Vad du tränar:** Feedback på AI-kod + omskrivning du äger.  
**Varför:** Muntlig redovisning kräver att *du* kan säga vilken gren som körs och varför.  
**Vad det INTE är:** “AI skrev det, alltså är det klart.” Inte loop. Inte `Scanner`.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt till AI (eller jobba bara mot snutten ovan) med samma krav: hårdkodade `level` och `hasKey`, minst två grenar, svenska eller engelska utskrifter. Spara prompten.

### Steg 2 — Granska (checklist)
Gå igenom koden (AI:ns eller snutten) och kryssa:

- [ ] Används `==` i jämförelser — inte `=` i `if`-parentesen (utom booleans där du *medvetet* frågar)?  
- [ ] Har varje `if` / `else` **klammer `{ }`** om fler än en rad ska hänga ihop?  
- [ ] Är `&&` / `||` rätt för kravet (båda vs minst en)?  
- [ ] Finns **död gren** i `else if`-kedjan?  
- [ ] Kan du för `level = 12, hasKey = true` säga exakt vilka rader som skrivs ut?  
- [ ] Inga loopar, ingen `Scanner`, bara `main`?

Skriv **minst tre** konkreta feedback-punkter i formen:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Minst en** FEEDBACK ska handla om `=` vs `==` eller tilldelning i villkor.  
**Minst en** ska handla om saknade klamrar eller fel `&&`/`||`.

### Steg 3 — Anpassa
Skriv om till en klass **du äger** (t.ex. `ZoneGateFixed.java`):

- Kompilerar och kör i IDE  
- Tydlig logik: t.ex. bosszon om `level >= 10`, sidozon om `level >= 5 && hasKey`, annars starter  
- En extra rad som kombinerar `&&` och en som använder `!` (t.ex. `!hasKey`)  
- Hårdkodade värden — byt `level` / `hasKey`, kör igen, dokumentera utskriften  

### Steg 4 — Reflektion (3 meningar)
Skriv i anteckningar eller `REFLEKTION.md`:

1. Vad var fel eller svagt i AI-förslaget (eller snutten)?  
2. Vad ändrade du?  
3. Varför är det viktigt inför Exam 1 (t.ex. uttagsregel: “bara om saldo räcker”)?

---

## Klart-check (peka i DIN omskrivna kod)

- [ ] Tre FEEDBACK-rader sparade  
- [ ] Peka på ett villkor med `==` och förklara skillnaden mot `=`  
- [ ] Peka på `{ }` du lade till — vad hade hänt utan dem?  
- [ ] Peka på `&&` eller `||` — vad krävs för att grenen ska bli true?  
- [ ] Reflektionens tre meningar klara  

---

## Facit-riktning (efter egen granskning)

<details>
<summary>Visa facit-riktning (inte full kod — bygg själv först)</summary>

**Typiska fel i snutten:**
- `if (level = 10)` — tilldelning, inte jämförelse; ska vara `level == 10` eller `level >= 10` beroende på krav.  
- `hasKey = false` inuti `||` — tilldelar och förstör variabeln; använd `!hasKey` eller `hasKey == false`.  
- Saknade klamrar efter första `if` — bara första `println` hänger på villkoret; resten körs alltid.  
- Sista `if/else` utan klammer — samma risk.  
- `else if (level > 0)` efter grenar som redan täcker de flesta positiva level — kan bli död eller redundant; ordna smalast/specifikast först eller använd tydlig stege.

**Efter fix för `level = 12, hasKey = true` (exempellogik du kan välja):**  
Boss/meddelande om `level >= 10`, annars sidozon om `level >= 5 && hasKey`, annars starter. Dörr: låst om `level >= 10 && !hasKey`, annars öppen — *om* du separerar boss-regeln så.

Bygg din egen variant; facit är **korrekt beteende + förklaring**, inte copy-paste av en enda lösning.

</details>

---

## Nästa steg

[05 — Självtest](./05-sjalvtest.md) — utan att titta på facit först.
