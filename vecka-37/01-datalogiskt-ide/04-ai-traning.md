# 04 — AI-träning: Java-start & ägarskap

AI kan skriva Java på sekunder. Det betyder inte att *du* äger den. Här tränar du samma färdighet som examinationen kräver: **se vad som är svagt, ändra, förklara** — innan du trycker Run och tror att du är klar.

Det är inte magi att “granska AI”. Det är samma metod som i teoriguiden — data, ordning, och att veta **var** saker ska ligga.

---

## Scenario — problem först

Du ber AI: *“Skapa ett enkelt Java HelloWorld-projekt som skriver Hej till konsolen.”*

Du får tillbaka något i stil med:

**Fil 1 — sparad som `Main.java`:**

```java
class HelloWorld {
    static void main() {
        System.out.print("Hej")
        System.out.println("Konsolen funkar");
    }
}
```

**AI:s kommentar:** “Lägg båda filerna i samma mapp och kör i webbläsaren. `print` och `println` är samma sak.”

Det *låter* nästan rimligt. Men flera saker stoppar dig från att **äga** koden — och från att klara muntligt eller Exam 1 där du ska köra i **IDE med JDK**.

**Vad du tränar:** Feedback på AI-kod + omskrivning du äger.  
**Varför:** Du ska kunna peka på `main`, filnamn och konsol — och veta varför felmeddelanden uppstår.  
**Vad det INTE är:** “AI skrev det, alltså är det klart.”

---

## Din uppgift (ca 45–60 min)

### Steg 1 — Prompt
Skriv en egen prompt till AI (eller jobba bara mot snutten ovan utan ny AI) där du ber om ett minimalt konsolprogram. Spara prompten.

### Steg 2 — Granska (checklist)
Gå igenom koden och kryssa:

- [ ] `public` på klass och `main`?  
- [ ] `main` har signaturen `public static void main(String[] args)`?  
- [ ] **Klassnamn** matchar **filnamn** (och stor bokstav)?  
- [ ] Semikolon efter varje statement?  
- [ ] `System.out.println` vs `print` — vet du skillnaden (radbryt eller inte)?  
- [ ] Körs det i **konsol via IDE/JDK** — inte “webbläsare”?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** konkreta feedback-punkter i formen:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Ledtrådar (titta själv först):** filnamn vs klassnamn; `main`-signaturen; saknad `public`; semikolon; AI:ns råd om webbläsare.

### Steg 3 — Anpassa
Skriv om till kod **du äger** — i ditt eget projekt (ny mapp `ovning-ai-granskning/` eller utöka `ovning-hello`):

- Klass t.ex. `AiGranskning` i `AiGranskning.java`
- Korrekt `main`
- Minst två `println` som visar att du förstår radbryt (t.ex. en rad med `print` + en med `println` — **medvetet**, så du kan förklara output)

Kör. Fixa tills konsolen visar det du förväntar dig.

### Steg 4 — Reflektion (3 meningar)
Skriv i anteckningar eller `REFLEKTION.txt` i projektmappen:

1. Vad var fel eller vilseledande i AI-förslaget (eller snutten)?  
2. Vad ändrade du?  
3. Varför spelar filnamn + `main` + JDK/IDE roll inför Exam 1?

---

## Klart-check (peka i DIN omskrivna kod)

- [ ] Tre FEEDBACK-rader sparade  
- [ ] Peka på `main`-signaturen och säg *varför* varje del (`public`, `static`, `void`, `String[] args`) finns — om du är osäker på en del: slå upp och skriv en mening  
- [ ] Peka på något du **tog bort eller ändrade** från AI — varför dög det inte?  
- [ ] Kör programmet — peka i **konsolen** och förklara varje rad output  
- [ ] Reflektionens tre meningar klara  

---

## Facit-riktning (titta efter du granskat själv)

Exempel på giltig feedback (dina egna ord får skilja sig):

- `FEEDBACK: Klassen heter HelloWorld i kod men filen Main.java → filnamn måste matcha public class.`  
- `FEEDBACK: main saknar public static och String[] args → JVM hittar inte startpunkten.`  
- `FEEDBACK: Saknad semikolon efter print → kompileringsfel.`  
- `FEEDBACK: AI säger webbläsare → kursen kör Java i IDE/konsol med JDK, inte i browser.`  
- `FEEDBACK: print vs println — print avslutar inte raden; jag behöver förstå output innan jag blandar dem.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-förslag som utkast, granskar rad för rad och filstruktur, och behåller bara det jag kan förklara och köra i IDE.”*

---

## Ägarskaps-checklista (spara)

Innan du räknar Java-kod som “klar”:

- [ ] Jag kan hitta **Run** och **konsolen** i min IDE  
- [ ] Jag vet var **JDK** är inställt om Run klagar på Java  
- [ ] Jag kan läsa **ett** kompileringsfel och peka på radnumret  
- [ ] Jag kan säga JDK vs IDE utan att blanda ihop dem  
- [ ] Jag har kört programmet själv — inte bara sett kod i chatten  

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
