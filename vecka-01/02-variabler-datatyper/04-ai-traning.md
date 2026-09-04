# 04 — AI-träning: Variabler, typer & ägarskap

AI kan spotta ur sig Java på sekunder. Det betyder inte att *du* äger etiketterna på lagret. Här tränar du: **se typfel, saknade citat och fel fack — ändra, förklara**.

Det är inte magi. Det är rätt hylltyp + deklaration före utskrift.

---

## Scenario — problem först

Du ber AI: *“Skriv Java som skriver ut en träningsprofil med namn, ålder, vikt och om personen är medlem.”*  
Du får tillbaka något i stil med:

```java
public class Main {
    public static void main(String[] args) {
        int namn = Erik;
        String alder = 28;
        double medlem = true;
        boolean viktKg = 72.5;
        String aktiv = ja;

        System.out.println(namn);
        System.out.println(alder);
        System.out.println(viktKg);
        System.out.println(medlem);
        System.out.println(puls);
    }
}
```

Det *ser ut* som fyra fält — men det kompilerar inte. Svagheter:

- **Text utan citat** (`Erik`) — Java tror det är variabelnamn.  
- **Tal i String** (`String alder = 28`) — fel hylltyp.  
- **Boolean i double** (`double medlem = true`) — helt fel fack.  
- **Decimal i boolean** (`boolean viktKg = 72.5`) — boolean är bara `true`/`false`.  
- **`ja` utan citat** — finns inte som Java-ord.  
- **`puls` odeklarerad** — *cannot find symbol*.  
- Namn som **inte matchar innehåll** (`medlem` som double) — förvirrar dig vid muntlig redovisning.

**Vad du tränar:** Feedback + en version *du* kan köra i IDE:n.  
**Varför:** Examination 1 kräver att du kan peka: typ, deklaration, tilldelning.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan förklara varje rad.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snutten ovan) där du ber om **fyra variabler i main** — `int`, `double`, `String`, `boolean` — och `System.out.println` för varje. Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Text utan `"..."`?  
- [ ] Tal lagda i `String`, eller text i `int`/`double`?  
- [ ] `boolean` med något annat än `true`/`false`?  
- [ ] Odeklarerade namn (`puls`, `enhet`, …)?  
- [ ] Komma i decimal (`19,90`)?  
- [ ] Egna metoder, `Scanner`, `if` som du **inte** bett om? (stryk — NOLL SPILL)  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — gärna kopplad till [03 — Uppgift 2](./03-ovningar.md) (väderstation) eller träningspass. Bara `main`, fyra typer, fyra println. Spara i ditt Java-projekt.

### Steg 4 — Reflektion (3 meningar)
1. Vilka typfel hade AI gjort?  
2. Vad ändrade du (med pekning på minst en rad)?  
3. Varför spelar rätt typ roll innan bankappens klasser kommer?

---

## Klart-check (peka i DIN fil)

- [ ] Tre FEEDBACK-rader sparade  
- [ ] Peka på varje datatyp och säg varför  
- [ ] Peka på något du *tog bort* (odeklarerad variabel, fel citat, `Scanner`/`if` om AI la till)  
- [ ] Programmet **kompilerar och kör** i IDE:n  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Exempel på ren träningsprofil:

```java
public class Main {
    public static void main(String[] args) {
        String namn = "Erik";
        int alder = 28;
        double viktKg = 72.5;
        boolean medlem = true;
        int puls = 118;

        System.out.println(namn);
        System.out.println(alder);
        System.out.println(viktKg);
        System.out.println(medlem);
        System.out.println(puls);
    }
}
```

Typiska FEEDBACK-rader:

- `FEEDBACK: int namn = Erik utan citat → String namn = "Erik";`  
- `FEEDBACK: String alder = 28 → int alder = 28;`  
- `FEEDBACK: double medlem = true → boolean medlem = true;`  
- `FEEDBACK: boolean viktKg = 72.5 → double viktKg = 72.5;`  
- `FEEDBACK: puls saknas → int puls = 118; deklarera före println.`  
- `FEEDBACK: String aktiv = ja → boolean aktiv = true; (eller String "ja" om du menade text — välj medvetet).`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-Java som utkast, fixar typer och deklarationer, och behåller bara kod jag kan förklara rad för rad.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
