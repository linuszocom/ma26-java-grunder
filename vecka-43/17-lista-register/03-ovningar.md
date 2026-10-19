# 03 — Övningar

**Omfång det här paketet:** `private List<Medlem> medlemmar = new ArrayList<>()` i `Register`. Metoder `läggTill` och `listaAlla` (skriv ut namn + nummer via getters). `Main`: två hardkodade medlemmar, anropa registret — **ingen** egen lista. **Ingen** `sökNamn`, **ingen** meny/`Scanner`, **ingen** factory, **inget** arv. **Inte** Git-fokus.

AI får föreslå rader. Du måste kunna **peka** listfältet i `Register` och förklara varför det **inte** ligger i `Main`.

**Var du kör:** Java-projekt med `Medlem.java`, `Register.java`, `Main.java` (från [15-tre-klasser](../../vecka-42/15-tre-klasser/) eller skelettet nedan).

**Bygger på:** `Medlem`-mur + tre filer. Här: **fyller** den tomma `Register`.

---

## Minimal skelett (start om du saknar treklass-kod)

```java
// Medlem.java
public class Medlem {
    private String namn;
    private int medlemsnummer;

    public Medlem(String namn, int medlemsnummer) {
        this.namn = namn;
        this.medlemsnummer = medlemsnummer;
    }

    public String getNamn() {
        return namn;
    }

    public int getMedlemsnummer() {
        return medlemsnummer;
    }
}
```

```java
// Register.java — fylls i uppgifterna
public class Register {
    // lista kommer här
}
```

---

## Uppgift 1 — Problem först: lista i `Main` (gör ont)

**Mål:** Känna att “det kör” **inte** betyder rätt rum — innan du flyttar listan till `Register`.

**Scenario:** Föreningen **“Nordljus”** ska arkivera medlemmar. Någon har börjat så här — listan ligger i expeditionsfönstret:

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Medlem> medlemmar = new ArrayList<>();
        medlemmar.add(new Medlem("Kim", 101));
        medlemmar.add(new Medlem("Moa", 102));
        for (Medlem m : medlemmar) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
        }
    }
}
```

**Krav:**
1. Lägg in koden (eller motsvarande) och **kör** — du ska se två rader.
2. Skriv **tre meningar** (Docs eller kommentar): Var ligger listan *nu*? Var *ska* den ligga enligt Exam 2? Vad är `Register` till för om listan bor i `Main`?
3. **Rör inte** den färdiga lösningen än — uppgift 2–3 flyttar och bygger metoder.

**Klart-check:**
- [ ] Programmet kör och skriver Kim / Moa  
- [ ] Du har skrivit varför detta **inte** är rätt ägare  
- [ ] Du kan säga högt: *listan ska peka i Register.java*

**Ägarskap:** Smärtan är poängen — inte “AI sa att Register är bättre”.

---

## Uppgift 2 — Flytta listan till `Register` (`List` som typ)

**Mål:** `private List<Medlem>` i `Register`. `Main` utan egen lista.

**Scenario:** Kartoteklådan får sin skylt. Expeditionsfönstret lämnar tillbaka lådan.

**Krav:**
1. I `Register.java`:
   - `import java.util.ArrayList;`
   - `import java.util.List;`
   - `private List<Medlem> medlemmar = new ArrayList<>();`
2. **Ta bort** all `List` / `ArrayList` / `.add` från `Main` (kan lämna en tom `main` eller `new Register()` tills vidare).
3. Deklarera **inte** fältet som `ArrayList<Medlem>` — typen ska vara `List<Medlem>`.
4. **Ingen** `läggTill` / `listaAlla` ännu (uppgift 3). **Ingen** sök. **Ingen** meny.
5. Projektet ska kompilera.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
import java.util.ArrayList;
import java.util.List;

public class Register {
    private List<Medlem> medlemmar = new ArrayList<>();
    // läggTill + listaAlla = nästa uppgift
}
```

```java
public class Main {
    public static void main(String[] args) {
        Register register = new Register();
        // metoder kommer i uppgift 3
    }
}
```

Peka: fältet finns **bara** i `Register`.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`private List<Medlem> medlemmar`** i `Register`  
- [ ] Peka på **`new ArrayList<>()`** — skapandet  
- [ ] Peka att **`Main` saknar** egen lista  
- [ ] Imports för både `List` och `ArrayList`  
- [ ] Projektet kompilerar

**Ägarskap:** Muntligt: “Skylten är List. Innehållet är ArrayList. Lådan är Register.”

---

## Uppgift 3 — `läggTill` + `listaAlla` + två medlemmar

**Mål:** Stoppa in två arkivkort och skriv ut listan. Bevisa ägarskap med konsolen.

**Scenario:** Nordljus registrerar **Kim 101** och **Moa 102**. Receptionen anropar lådan — gräver inte i den själv.

**Krav:**
1. I `Register`:
   - `public void läggTill(Medlem m) { medlemmar.add(m); }`
   - `public void listaAlla()` — for-each över `medlemmar`, skriv `getNamn()` + mellanslag + `getMedlemsnummer()`
2. I `Main`:
   - `Register register = new Register();`
   - två anrop: `register.läggTill(new Medlem("Kim", 101));` och samma för `"Moa", 102`
   - `register.listaAlla();`
3. **Ingen** `List` i `Main`. **Ingen** `register.medlemmar.add`. **Ingen** `sökNamn` / meny / `Scanner`.
4. Kör — konsolen ska visa två rader (Kim / Moa med nummer).

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

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

```java
public class Main {
    public static void main(String[] args) {
        Register register = new Register();
        register.läggTill(new Medlem("Kim", 101));
        register.läggTill(new Medlem("Moa", 102));
        register.listaAlla();
    }
}
```

Konsol (ungefär):

```text
Kim 101
Moa 102
```

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`läggTill`** — var sker `add`?  
- [ ] Peka på **`listaAlla`** — var används getters?  
- [ ] Peka på **två `läggTill`** i `Main`  
- [ ] Peka på **listfältet i `Register`** — Exam-svar: *här*  
- [ ] Konsolen visar namn + nummer för **två** medlemmar  
- [ ] **Ingen** lista i `Main`

**Ägarskap:** Du ska kunna säga: “Jag pekar listan i Register — Main anropar bara.”

---

## Uppgift 4 — Stretch (valfritt)

Välj **en** (inom paketet — ingen sök/meny):

### A) Tredje kortet
`läggTill` en tredje `Medlem` (t.ex. `"Noa", 103`). Kör `listaAlla`. Peka: tre rader — fortfarande **en** lista i `Register`.

### B) Exam-mening
Skriv **en mening** i Docs/README: *Var ligger listan, och vilken typ har fältet?* (förebåd Exam 2-lista).

**Klart-check:** Peka fältet i `Register` efter stretch.

---

## När du kört fast

1. *cannot find symbol: class List* → `import java.util.List;` (och `ArrayList`).  
2. *medlemmar has private access* → du står i `Main` — använd `läggTill`, inte `.add` på fältet.  
3. Tom konsol → anropa `listaAlla` **efter** `läggTill`.  
4. AI ger `ArrayList` som fälttyp eller lista i `Main` → byt till `List` i `Register`.  
5. AI ger `sökNamn` / meny → stryk (nästa paket).  
6. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
7. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
