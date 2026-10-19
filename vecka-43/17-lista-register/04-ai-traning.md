# 04 — AI-träning: lista i Main, `ArrayList` som typ och ägarskap

AI kan spotta ur sig “komplett register” på sekunder — med **`List` i `Main`**, **`ArrayList` som deklarerad fälttyp**, **`sökNamn`**, meny och factory. Det betyder inte att *du* äger listans hemvist eller kodstandarden. Här tränar du: **stryk spill**, **`List` i Register**, **`läggTill` + `listaAlla`**, **två medlemmar**.

Det är inte magi. Det är rätt rum + rätt deklarationstyp + två metoder.

---

## Scenario — problem först

Du ber AI: *“Lägg till lista av medlemmar i registret.”*  
Du får tillbaka något i stil med:

```java
// AI "hjälpte" — listan hamnade i Main
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Medlem> medlemmar = new ArrayList<>();  // fel rum + fel deklarationstyp
        medlemmar.add(new Medlem("Kim", 101));
        // ... loop i Main ...
    }
}
```

Eller i `Register`:

```java
public class Register {
    private ArrayList<Medlem> medlemmar = new ArrayList<>();  // ArrayList som typ
    // + sökNamn, createMedlem, Scanner-meny "bonus"
}
```

Svagheter:

- **Lista i `Main`** — fel rum; Exam 2 vill ha listan i `Register`.  
- **`ArrayList` som deklarerad typ** — bryter kursens mönster (`List` + `new ArrayList<>()`).  
- **`sökNamn` / meny / `Scanner`** — senare paket.  
- **Factory / `createMedlem`** — inte krav här.  
- **Publikt listfält** — muren borta; `Main` ska inte `.add` direkt.  
- Engelska metodnamn (`addMember`, `printAll`) om exam förväntar svenska (`läggTill`, `listaAlla`).

**Vad du tränar:** Feedback + en version *du* kan köra och förklara.  
**Varför:** Examination 2 — lista i `Register`, lägg till, lista alla.  
**Vad det INTE är:** “AI byggde hela registret” med sök och meny du inte bett om idag.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en **begränsad** prompt, t.ex.:

> Java. Register ska ha private List&lt;Medlem&gt; medlemmar = new ArrayList&lt;&gt;(). Metoder: läggTill(Medlem m) som gör add, listaAlla som loopar och skriver getNamn och getMedlemsnummer. Main: new Register, två hardkodade Medlem via läggTill (Kim 101, Moa 102), sedan listaAlla. Ingen lista i Main. Ingen sök. Ingen meny. Ingen Scanner. Ingen factory. Deklarera List, skapa med ArrayList.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Ligger `List` / `ArrayList` i **`Main`**?  
- [ ] Är fälttypen **`ArrayList<Medlem>`** i stället för `List<Medlem>`?  
- [ ] Saknas `import java.util.List`?  
- [ ] Finns `sökNamn` / meny / `Scanner` du **inte** bett om?  
- [ ] Factory / `createMedlem`?  
- [ ] Publikt fält eller `getMedlemmar()` som läcker listan?  
- [ ] Engelska metodnamn i stället för `läggTill` / `listaAlla`?  
- [ ] Kan du **peka** listfältet i `Register` och säga varför inte i `Main`?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — koppla till [03 — Övningar](./03-ovningar.md):

- `private List<Medlem> medlemmar = new ArrayList<>();` i `Register`  
- `läggTill` + `listaAlla`  
- `Main` utan egen lista — två `läggTill` + `listaAlla`  
- **ingen** sök, meny, factory

Testa kompilering och körning. Spara i ditt projekt.

### Steg 4 — Andra AI-felet (Main-lista eller ArrayList-typ)
Be AI “fixa” detta medvetet dåliga utkast — eller använd:

```java
// Fel A — lista i Main
List<Medlem> medlemmar = new ArrayList<>();
medlemmar.add(new Medlem("Kim", 101));

// Fel B — ArrayList som deklarerad typ i Register
private ArrayList<Medlem> medlemmar = new ArrayList<>();
```

Skriv **minst en** FEEDBACK-rad om **lista i Main** *eller* **ArrayList som typ**. Fixa till `List` i `Register` + metoder.

### Steg 5 — Reflektion (3 meningar)
1. Varför är listan i `Main` ett exam-problem även när programmet skriver ut rätt?  
2. Vad **strök** du som spill (sök, meny, factory, fel typ)?  
3. Vilket **exam-svar** ger du när någon frågar *var ligger listan?* — med pekning.

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade  
- [ ] Peka på **`private List<Medlem> medlemmar`** i `Register`  
- [ ] Peka på **`läggTill`** och **`listaAlla`**  
- [ ] Peka att **`Main` saknar** lista  
- [ ] **Ingen** sök / meny kvar  
- [ ] Konsolen visar Kim / Moa  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Kärna i `Register`:

```java
import java.util.ArrayList;
import java.util.List;

public class Register {
    private List<Medlem> medlemmar = new ArrayList<>();

    public void läggTill(Medlem m) {
        medlemmar.add(m);
    }

    public void listaAlla() {
        for (Medlem m : medlemmar) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
        }
    }
}
```

Typiska FEEDBACK-rader:

- `FEEDBACK: List i Main → flytta till private List i Register.`  
- `FEEDBACK: private ArrayList som typ → byt deklaration till List, behåll new ArrayList.`  
- `FEEDBACK: sökNamn + meny → stryk; paketet är läggTill + listaAlla.`  
- `FEEDBACK: Main gör medlemmar.add → private; använd läggTill.`  
- `FEEDBACK: addMember/printAll → byt till läggTill/listaAlla om exam använder svenska namn.`  
- `FEEDBACK: factory createMedlem → stryk; new Medlem + läggTill räcker här.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-utkast, stryker lista i Main och ArrayList som fälttyp, behåller List i Register med läggTill och listaAlla, och kan peka fältet inför Exam 2.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
