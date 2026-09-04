# 03 — Övningar

**Omfång den här delen:** Datalogiskt tänkande (utan kod) + första Java-projektet i IDE (konsol, `main` only). Ingen loop, ingen `Scanner`, inga extra metoder, inget Git, inga fler klasser än en.

AI får hjälpa dig skriva. Du måste kunna **peka och förklara** varje rad du behåller — och varför stegen i uppgift 1 är i rätt ordning.

---

## Uppgift 1 — Bibliotekslån utan kod (pizzeria-logik fast annat scenario)

**Mål:** Dela ett mini-problem i **data**, **handlingar** och **ordning** — utan Java-syntax.

**Problem först:** På stadsbiblioteket ska ett enkelt lånesystem (på papper) hantera **en** bok och **en** låntagare:

- Låntagaren heter **Alex**
- Boken heter **"Java för nybörjare"**
- Lånet gäller **14 dagar**
- Systemet ska **kontrollera** att boken inte redan är utlånad
- Om den är ledig: **registrera lånet** och **skriv ut** en lånekvitto-rad: *"Alex lånar Java för nybörjare i 14 dagar"*
- Om den är utlånad: **skriv ut** *"Boken är redan utlånad"* — registrera inget nytt lån

Många tänker: “Det här är ju inte kod — varför gör jag det?” Just därför. Datorn gör exakt dina steg — i ordning. Om du skriver ut kvittot innan du kollat status blir det fel i verkligheten och i Java senare.

**Krav:**
1. Öppna Docs/anteckningar (eller en textfil `ovning-bibliotek-steg.txt`).
2. Skriv **tre rubriker:** `Data`, `Handlingar`, `Ordning`.
3. Under **Data:** lista vad som måste finnas (namn, boktitel, dagar, status ledig/utlånad — du får välja hur du namnger status).
4. Under **Handlingar:** verb utan kod — t.ex. “kolla status”, “registrera lån”, “skriv ut meddelande”.
5. Under **Ordning:** numrerade steg 1–n som någon annan kan följa. **Minst sex steg.** Inkludera båda grenarna (ledig vs utlånad) — t.ex. med “om … annars …” i vanlig svenska.
6. **Felsök dig själv:** markera **ett** steg som skulle ge kaos om det flyttades **före** status-kollen. Skriv en mening varför.

**Klart-check (peka i DINA anteckningar):**
- [ ] Du kan peka på **datalistan** och säga vad varje post representerar  
- [ ] Du kan peka på **steg där utskrift sker** och bevisa att status redan är känd då  
- [ ] Du kan säga högt: *“Fel ordning här skulle betyda …”* (din markerade mening)  
- [ ] Inga Java-nyckelord krävs — men ordningen ska gå att översätta till `println` senare  

**Ägarskap:** AI får föreslå steg — du måste kunna försvara ordningen utan att läsa av chatten. Spara prompten om du använder AI; skriv en mening om vad du ändrade i ordningen efteråt.

---

## Uppgift 2 — Första Java-projektet: Hello + medvetet fel

**Mål:** Skapa projekt i IDE, köra `main`, läsa kompileringsfel, fixa och se output i **konsolen**.

**Problem först:** Du har aldrig kört Java i IDE — eller IDE:n visar rött direkt. Det är normalt. Målet är inte “perfekt kod på första försöket” — målet är att **kedjan** fungerar: projekt → Run → konsol (eller tydligt fel → fix → konsol).

**Krav:**

### Del A — Skapa och kör
1. Öppna **IntelliJ** eller **VS Code** (med Java-stöd).
2. Skapa ett **nytt Java-projekt** (tomt konsolprojekt räcker). Namn t.ex. `ovning-hello`.
3. Skapa klassen `HelloBibliotek` i filen **`HelloBibliotek.java`** (klassnamn = filnamn).
4. Skriv `main` som skriver **en rad** till konsolen — t.ex. hälsning kopplad till biblioteket:  
   `System.out.println("Bibliotekssystemet startar");`
5. Tryck **Run**. Bekräfta att texten syns i **konsolen** (inte bara i editorn).

### Del B — Medvetet fel och fix
6. **Inför ett fel med flit** — välj **ett** av:
   - saknad semikolon efter `println`
   - stavfel: `System.out.printlne(...)`
   - klass heter `HelloBibliotek` men filen sparades som `Hello.java`
7. Kör igen. **Läs** felmeddelandet — radnummer + första tydliga raden.
8. **Fixa** felet. Kör tills konsolen visar din rad igen.
9. I samma fil: lägg till **en rad till** i `main` som skriver ut lånekvitto-text från uppgift 1 (hårdkodad sträng räcker — t.ex. `"Alex lånar Java för nybörjare i 14 dagar"`). Kör och se **två rader** i konsolen.

**Referenskod (facit *efter* du testat själv — inte copy-paste före Run):**

```java
public class HelloBibliotek {
    public static void main(String[] args) {
        System.out.println("Bibliotekssystemet startar");
        System.out.println("Alex lånar Java för nybörjare i 14 dagar");
    }
}
```

**Klart-check (peka i DIN kod och IDE):**
- [ ] Projektnamn och filnamn `HelloBibliotek.java` matchar klassnamnet  
- [ ] Peka på `main` — varför måste programmet starta där?  
- [ ] Peka på en `println` — vad är skillnaden mot att bara skriva text i editorn?  
- [ ] Peka i **konsolen** på båda raderna efter lyckad körning  
- [ ] Peka på felraden du fixade — vad sa felet, och vad ändrade du?  

**Ägarskap:** AI får visa projektsteg — du ska kunna hitta **Run**, **konsol** och **felrad** i *din* IDE utan att AI sitter bredvid. Ta bort rader du inte förstår.

---

## Uppgift 3 — Stretch (valfritt)

Bygg pseudokod (numrerade steg) för **pizzeria-order hemleverans**: data (pizza, storlek, adress, pris), handlingar, ordning — minst åtta steg inklusive “om adress saknas → avbryt”. Jämför med biblioteks-uppgiften: vad är samma *mönster* (data före utskrift)?

**Klart-check:** En mening — vilket steg i pizzeria-flödet motsvarar “kolla om boken är utlånad”?

---

## När du kört fast

1. Kontrollera: JDK vald i IDE? (Project SDK / Java version)  
2. Filnamn = klassnamn?  
3. Kör [01-teoriguide](./01-teoriguide.md) — målsvar JDK/IDE/konsol.  
4. Gå vidare till [04 — AI-träning](./04-ai-traning.md) när uppgift 2 körs utan att du gissar varje klick.
