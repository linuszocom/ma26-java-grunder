# 03 — Övningar

**Omfång det här paketet:** `sökNamn` i `Register` (for-each, `equalsIgnoreCase`, hit/`return`, miss efter loop). Full meny i `Main` 1–4 med `Scanner` + **switch expression** (`case n ->`). `List<Medlem>` deklarerad typ. Exam-körning: två medlemmar, lista, hit, miss, exit — peka på `sökNamn`. Ingen factory. Inget arv. Ingen README-uppsats.

AI får föreslå rader. Du måste kunna **peka och förklara** var sökloopen bor, hur hit/miss skiljs, och stegkedjan för menyval 3.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK 21. Filer: `Medlem.java`, `Register.java`, `Main.java`.

**Bygger på:** Lista + `läggTill` / `listaAlla` från [17-lista-register](../17-lista-register/). Saknar du det — använd minimala skelett nedan.

---

## Minimal skelett (start om du saknar lista-kod)

```java
// Medlem.java
public class Medlem {
    private String namn;
    private int medlemsnummer;

    public Medlem(String namn, int medlemsnummer) {
        this.namn = namn;
        this.medlemsnummer = medlemsnummer;
    }

    public String getNamn() { return namn; }
    public int getMedlemsnummer() { return medlemsnummer; }
}
```

```java
// Register.java — fyll på sökNamn i uppgifterna
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

---

## Uppgift 1 — Problem först: sök i Main → `sökNamn` i Register

**Mål:** Känna smärtan med sök i fel fil, implementera `sökNamn`, testa hit + miss **innan** full meny.

**Scenario (unikt — klätterklubb):** Klubben **“Vertikal”** har medlemmar Elsa (201) och Nova (202). Någon har börjat “söka” genom att speja — eller genom att försöka loopa i `Main`. Du ska äga metoden i `Register`.

**Trasig startidé** (kör/tänk först — skriv gärna om till kommentar så du ser felet):

```java
// Main.java — FEL mönster (gör ont)
// Tanken: "jag loopar här och letar Elsa"
// Problem: listan är private i Register — Main ska inte öppna pärmen.
// Om du har en getMedlemmar() / publik lista: ta bort den. Flytta loopen.
register.listaAlla();  // speja efter Elsa i konsolen — INTE Exam-sök
```

**Krav:**
1. Implementera `public void sökNamn(String namn)` i `Register`:
   - for-each över `medlemmar`
   - `m.getNamn().equalsIgnoreCase(namn)`
   - vid träff: skriv `namn + " " + nummer`, sedan `return`
   - efter loopen: `System.out.println("Medlemmen saknas");`
2. I `Main` (hardcoded, ingen meny än): två `läggTill` (Elsa 201, Nova 202), sedan `sökNamn("Elsa")` och `sökNamn("Rune")`.
3. **Ingen** for-each över medlemmar i `Main`. **Ingen** publik lista / `getMedlemmar` för sök.
4. Bekräfta konsol: `Elsa 201` respektive `Medlemmen saknas`.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public void sökNamn(String namn) {
    for (Medlem m : medlemmar) {
        if (m.getNamn().equalsIgnoreCase(namn)) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
            return;
        }
    }
    System.out.println("Medlemmen saknas");
}
```

```java
// Main — kort test
Register register = new Register();
register.läggTill(new Medlem("Elsa", 201));
register.läggTill(new Medlem("Nova", 202));
register.sökNamn("Elsa");
register.sökNamn("Rune");
```

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **for-each** — den står i `Register`, inte `Main`  
- [ ] Peka på **`return`** efter hit  
- [ ] Peka på **miss-raden** — efter `for`, inte i `else` varje varv  
- [ ] Förklara varför `listaAlla` + speja **inte** räcker som Exam-sök  

**Ägarskap:** Säg högt: *“När någon frågar vilken metod som söker pekar jag på sökNamn i Register.java.”*

---

## Uppgift 2 — Full meny: två medlemmar, lista, hit, miss, exit

**Mål:** Interaktiv meny 1–4. Köra samma kedja som Examination 2 kräver — via menyn.

**Scenario (unikt — samma klubb, nu reception):** Vertikals expedition tar emot medlemmar via textmeny tills någon väljer avsluta.

**Meny:**

| Val | Text | Handling |
|-----|------|----------|
| 1 | Lägg till | Läs namn + nummer → `läggTill(new Medlem(…))` |
| 2 | Lista | `listaAlla()` |
| 3 | Sök | Läs namn → `sökNamn(…)` |
| 4 | Avsluta | `kör = false` |

**Krav:**
1. `Scanner` **en** gång före loopen. `boolean kör = true;` + `while (kör)`.
2. Efter varje `nextInt()`: `scanner.nextLine()` som äter newline innan text läses.
3. `switch (val) { case 1 -> { … } … }` — **switch expression** (Java 21). `default` → `"Ogiltigt val"`.
4. case 3: **bara** fråga + `register.sökNamn(...)` — ingen sök-loop i `Main`.
5. case 1: efter `nextInt` för nummer — ät newline igen.
6. **Manuell testkörning** (skriv vilka val du tryckte):
   - 1 → Elsa, 201  
   - 1 → Nova, 202  
   - 2 → två rader  
   - 3 → `Elsa` → träff  
   - 3 → `Rune` → `Medlemmen saknas`  
   - 4 → avsluta utan krasch  
7. Peka i IDE:n på `sökNamn` när du är klar.

**Facit-riktning — utdrag `Main` (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Register register = new Register();
        boolean kör = true;

        while (kör) {
            System.out.println("1 Lägg till  2 Lista  3 Sök  4 Avsluta");
            int val = scanner.nextInt();
            scanner.nextLine();

            switch (val) {
                case 1 -> {
                    System.out.print("Namn: ");
                    String namn = scanner.nextLine();
                    System.out.print("Nummer: ");
                    int nr = scanner.nextInt();
                    scanner.nextLine();
                    register.läggTill(new Medlem(namn, nr));
                }
                case 2 -> register.listaAlla();
                case 3 -> {
                    System.out.print("Sök namn: ");
                    register.sökNamn(scanner.nextLine());
                }
                case 4 -> kör = false;
                default -> System.out.println("Ogiltigt val");
            }
        }
        scanner.close();
    }
}
```

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`scanner.nextLine()`** direkt efter meny-`nextInt`  
- [ ] Peka på **case 3** — anrop till `sökNamn`, ingen for-each  
- [ ] Peka på **case 4 → `kör = false`**  
- [ ] Bekräfta testkörning: två medlemmar, lista, hit, miss, exit  
- [ ] Säg högt var sökmetoden ligger  

**Ägarskap:** Du ska kunna köra demon utan facit och peka på `sökNamn` om någon frågar i IDE:n.

---

## Stretch (frivilligt — ingen VG på Exam 2)

- Sök `"elsa"` när medlemmen heter `"Elsa"` — dokumentera varför det funkar (`equalsIgnoreCase`).  
- Kör val 3 på **tom** lista — ska ge `Medlemmen saknas`, inte krasch.  
- Tryck `9` — `default` ska skriva ogiltigt val, loopen fortsätter.  
- Anteckna en mening: varför `nextLine()` efter `nextInt()` behövs.

**INTE i stretch här:** README-frågor (det är [19-exam2-start](../19-exam2-start/)), factory, arv, PR, VG-krav.

---

## När du kört fast

1. Alltid saknas → stavning, tom lista, saknar `equalsIgnoreCase`, eller jämför utan `getNamn()`.  
2. Saknas många gånger → flytta miss-raden **efter** `for`.  
3. Hit men flera rader / konstigt → saknar `return` efter träff.  
4. Tomt namn / hoppad fråga → `nextLine()` efter `nextInt()`.  
5. Loopen stannar aldrig → case 4 sätter inte `kör = false`.  
6. `cannot find symbol Scanner` → `import java.util.Scanner`.  
7. Sök-loop i `Main` → flytta till `Register.sökNamn`.  
8. Jämför [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
9. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
