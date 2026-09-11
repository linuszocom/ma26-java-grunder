# 03 — Övningar

**Omfång det här paketet:** `public static`-metoder i `Main.java`. Parametrar, `return`, `void`. Anrop från `main` (och loop om du vill). Primitiva typer och `String`. Ingen egen klass. Ingen `ArrayList` krävs. Loopar från föregående paket är OK.

AI får föreslå rader. Du måste kunna **peka och förklara** metodhuvud, parametrar, `return`, anrop och varför du refaktorerade.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK. Kör `Main` och läs **konsolen** i IDE:n.

---

## Uppgift 1 — Refaktorera duplicerad fraktkod (problem-först)

**Mål:** Hitta upprepad logik, bryt ut till en `return`-metod med parametrar, och anropa den i stället för copy-paste.

**Scenario / startläge:** E-handeln “NordPost” ska skriva ut fraktkostnad för tre ordrar. Formeln är densamma överallt: `varuvärde * procent + fastAvgift`. Någon har kopierat formeln rakt av — din jobb: **en metod, tre anrop**.

**Trasig / duplicerad startkod** (kopiera till `Main.java`):

```java
public class Main {
    public static void main(String[] args) {
        double varde1 = 120.0;
        double varde2 = 85.0;
        double varde3 = 200.0;

        double frakt1 = varde1 * 0.15 + 29.0;
        double frakt2 = varde2 * 0.15 + 29.0;
        double frakt3 = varde3 * 0.15 + 29.0;

        System.out.println("Order 101: " + frakt1 + " kr");
        System.out.println("Order 102: " + frakt2 + " kr");
        System.out.println("Order 103: " + frakt3 + " kr");
    }
}
```

**Krav:**
1. Skapa metoden `public static double beraknaFrakt(double varuvardet, double procent, double fastAvgift)` med **`return`** — samma matematik som idag.
2. Ersätt de tre duplicerade raderna med **tre anrop** till `beraknaFrakt(...)`.
3. Behåll utskrifterna (order 101–103) — samma slutvärden som före refaktorering.
4. Metoden ska ligga **utanför** `main`, i samma klass.
5. *(Valfritt)* Byt till en `for`-loop som anropar `beraknaFrakt` tre gånger (t.ex. `orderNr` 101–103 med olika `varde`) — metoden ska fortfarande anropas inuti loopen.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public class Main {
    public static void main(String[] args) {
        double varde1 = 120.0;
        double varde2 = 85.0;
        double varde3 = 200.0;

        double frakt1 = beraknaFrakt(varde1, 0.15, 29.0);
        double frakt2 = beraknaFrakt(varde2, 0.15, 29.0);
        double frakt3 = beraknaFrakt(varde3, 0.15, 29.0);

        System.out.println("Order 101: " + frakt1 + " kr");
        System.out.println("Order 102: " + frakt2 + " kr");
        System.out.println("Order 103: " + frakt3 + " kr");
    }

    public static double beraknaFrakt(double varuvardet, double procent, double fastAvgift) {
        return varuvardet * procent + fastAvgift;
    }
}
```

Förväntade fraktbelopp: `47.0`, `41.75`, `59.0`. Om du ändrar `0.15` till `0.18` ska **en rad** i metoden räcka.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **metodhuvudet** — returtyp, namn, tre parametrar  
- [ ] Peka på **`return`** — vad skickas tillbaka till anropet?  
- [ ] Peka på **ett anrop** — vilka **argument** skickas till vilka **parametrar**?  
- [ ] Förklara **varför** du inte längre har tre identiska formler i `main`  
- [ ] Konsolen visar tre fraktbelopp — programmet kompilerar

**Ägarskap:** AI ok som bollplank — du ska kunna förklara refaktoreringen muntligt: “samma beteende, en kropp”.

---

## Uppgift 2 — Enhetsomvandling med parameter och return

**Mål:** Skriva en metod som tar indata, returnerar omräknat värde, och anropa den från `main` med minst två olika argument.

**Brief:** Reseappen “MilKoll” ska visa sträckor i **mil** när användaren matat in **km**. Bygg metoden själv — inga duplicerade formler i `main`.

**Krav:**
1. Metod `public static double kmTillMil(double km)` med formeln `km * 0.621371` och **`return`**.
2. I `main`: minst **två** olika km-värden (t.ex. `10.0` och `42.195` — maraton).
3. Spara varje returvärde i en **egen variabel** i `main`.
4. Skriv ut båda med `System.out.println` — tydlig etikett i texten (t.ex. `"10 km = … mil"`).
5. **Ingen** formel `* 0.621371` kvar direkt i `main` — bara i metoden.

**Exempel på rimlig konsol** (avrundning kan skilja):

```
10 km = 6.21371 mil
42.195 km = 26.218 mil
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på **parametern** `km` — var får den sitt värde?  
- [ ] Peka på **`return`** — varför räcker inte `println` inuti metoden om `main` ska spara talet?  
- [ ] Peka på **två anrop** — samma metod, olika argument  
- [ ] Bekräfta: ingen egen klass, bara `static` i `Main`

**Ägarskap:** Skriv själv först. Med AI: spara prompten + en mening om vad du ändrade.

---

## Uppgift 3 — BMI-liknande beräkning (return, två parametrar)

**Mål:** Metod med två parametrar som returnerar ett beräknat `double`-värde — utan person-klass eller objekt.

**Brief:** Hälsokiosken vill visa BMI från vikt (kg) och längd (meter). Formeln: `vikt / (längd * längd)`.

**Krav:**
1. Metod `public static double beraknaBmi(double viktKg, double langdMeter)` med **`return`** enligt formeln.
2. I `main`: testa minst **två** personer (olika vikt/längd) — spara varje BMI i variabel.
3. Skriv ut båda BMI-värden (en rad per person räcker).
4. Lägg till en **`void`**-metod `skrivBmiEtikett(String namn, double bmi)` som skriver en rad: `"Namn: … BMI: …"`. Anropa den **efter** du räknat BMI — så du tränar **både** `return` och `void` i samma program.
5. Allt i `Main.java` — inga extra klasser.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public class Main {
    public static void main(String[] args) {
        double bmiAnna = beraknaBmi(65.0, 1.70);
        skrivBmiEtikett("Anna", bmiAnna);

        double bmiErik = beraknaBmi(82.0, 1.85);
        skrivBmiEtikett("Erik", bmiErik);
    }

    public static double beraknaBmi(double viktKg, double langdMeter) {
        return viktKg / (langdMeter * langdMeter);
    }

    public static void skrivBmiEtikett(String namn, double bmi) {
        System.out.println("Namn: " + namn + " BMI: " + bmi);
    }
}
```

Ungefärliga BMI: Anna ~22.5, Erik ~24.0.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **`beraknaBmi`** — två parametrar, ett returvärde  
- [ ] Peka på **`skrivBmiEtikett`** — `void`, varför ingen `return`?  
- [ ] Förklara ordningen: **räkna först** (return), **skriv sedan** (void-anrop)  
- [ ] Koppla muntligt till Exam 1: “deposit tar belopp som parameter — här tar BMI metoden vikt och längd”

**Ägarskap:** Du ska kunna byta formeln till t.ex. rabatt eller celsius→fahrenheit med **samma metod-mönster**.

---

## Uppgift 4 — Stretch (valfritt)

Byt enhetsomvandling till **celsius → fahrenheit**: `return celsius * 9.0 / 5.0 + 32;`. Tre testvärden i en `for`-loop (`-18`, `0`, `37`). Samma krav: formeln **bara** i metoden.

**Klart-check:** Peka på loopen och metoden — vem styr **antal**, vem styr **formel**?

---

## När du kört fast

1. *missing return statement* → lägg till `return` i alla grenar (här: en rak kropp räcker).  
2. *void cannot be converted to …* → du försöker spara retur från `void` — anropa utan tilldelning eller byt returtyp.  
3. *cannot find symbol* på metodnamn → stavning, eller metod ligger inuti `main`.  
4. Fel antal parametrar → räkna argument i anrop vs parentes i deklaration.  
5. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
6. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
