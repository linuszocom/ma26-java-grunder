# 03 — Övningar

**Omfång den här delen:** Array (skapa, fylla, loopa ut), `List` / `ArrayList` (`add`, `get`, skriv ut), `Scanner` (`nextLine`, blanda text och `nextInt`). Bara `Main.java`. Loopar och `static`-metoder OK. **Ingen** objektlista, **ingen** Git, **inga** klasser utöver den du kör i.

AI får hjälpa dig skriva. Du måste kunna **peka och förklara** varje rad — särskilt index, `size()` vs `length`, och varför du har en extra `nextLine()`.

---

## Uppgift 1 — Packlista: array med vikt i gram

**Mål:** Skapa en **fast** packlista med array, fylla fack, loopa ut med index och `length`.

**Problem först:** Du ska packa för en dags vandring. Fem föremål — vikten i gram är känd. Du *kan* ha fem `int`-variabler, men uppgiften tränar **ett namn, fem fack** så Examination senare kan loopa konton/medlemmar på samma sätt.

**Brief:**
| Fack | Föremål (för dig) | Vikt (g) |
|------|-------------------|----------|
| 0 | Vattenflaska | 800 |
| 1 | Matlåda | 1200 |
| 2 | Regnjacka | 450 |
| 3 | Powerbank | 300 |
| 4 | Första hjälpen | 950 |

**Krav:**
1. Ny klass `Packlista.java` med `main`.
2. `int[] packVikt = new int[5];` — fyll alla fem index **0–4** (inte 1–5).
3. `for`-loop: skriv ut varje rad som `Fack i: XXX g` (t.ex. `Fack 0: 800 g`).
4. Efter loopen: räkna **total vikt** i en variabel `totalGram` (loop eller manuell summering i loop — **en** loop räcker).
5. Skriv ut en rad: `Total packvikt: … g`.
6. **Medvetet test:** kommentera inte bort — lägg till **en** rad `System.out.println(packVikt[5]);`, kör, läs Exception, **ta bort** raden. Skriv en mening i anteckningar: vad betydde felet?

**Referenskod (facit *efter* du testat — inte copy-paste före Run):**

```java
public class Packlista {
    public static void main(String[] args) {
        int[] packVikt = new int[5];
        packVikt[0] = 800;
        packVikt[1] = 1200;
        packVikt[2] = 450;
        packVikt[3] = 300;
        packVikt[4] = 950;

        int totalGram = 0;
        for (int i = 0; i < packVikt.length; i++) {
            System.out.println("Fack " + i + ": " + packVikt[i] + " g");
            totalGram = totalGram + packVikt[i];
        }
        System.out.println("Total packvikt: " + totalGram + " g");
    }
}
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på `new int[5]` — varför fem, inte sex?  
- [ ] Peka på loop-villkoret `i < packVikt.length` — varför inte `<=`?  
- [ ] Peka på `packVikt[0]` — varför börjar första föremålet på 0?  
- [ ] Peka på Exception-raden du testade — vilket index var illegal?  
- [ ] Peka i **konsolen** på totalen (3700 g om vikterna matchar tabellen)  

**Ägarskap:** AI ok — spara prompten. Du ska kunna rita fem fack med index 0–4 utan att titta.

---

## Uppgift 2 — Spellista: växande List med add

**Mål:** Bygga en spellista som **växer** med `add`, läsa med `get`, skriv ut numrerad lista med `for` + `size()`.

**Problem först:** Tre låtar idag, kanske sju imorgon. En array med `new String[3]` stoppar dig vid låt fyra — samma krasch som i teoriguiden.

**Krav:**
1. Ny klass `Spellista.java` med `main`.
2. Importera `java.util.List` och `java.util.ArrayList`.
3. Deklarera `List<String> spellista = new ArrayList<>();` — **inte** `ArrayList<String>` som variabeltyp.
4. `add` minst **fyra** låttitlar (egna eller exempel: `"Northern Lights"`, `"Paper Moon"`, `"Dockside"`, `"Quiet Hour"`).
5. `for`-loop: skriv ut `1. Titel` (människonummer = `i + 1`, index = `i`).
6. Skriv ut sista raden: `Antal låtar: X` med `size()`.

**Referenskod (facit efter eget försök):**

```java
import java.util.List;
import java.util.ArrayList;

public class Spellista {
    public static void main(String[] args) {
        List<String> spellista = new ArrayList<>();
        spellista.add("Northern Lights");
        spellista.add("Paper Moon");
        spellista.add("Dockside");
        spellista.add("Quiet Hour");

        for (int i = 0; i < spellista.size(); i++) {
            System.out.println((i + 1) + ". " + spellista.get(i));
        }
        System.out.println("Antal låtar: " + spellista.size());
    }
}
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på deklarationen — varför `List` vänster och `ArrayList` höger?  
- [ ] Peka på `get(i)` — vad händer om du skriver `spellista[i]`?  
- [ ] Peka på `size()` — varför parentes, inte som `length`?  
- [ ] Peka på `(i + 1)` i utskriften — skillnad mot index `i`?  
- [ ] **Konsolen** visar fyra numrerade rader + antal  

**Ägarskap:** Byt minst två låttitlar till egna. Förklara muntligt: array vs lista för den här uppgiften.

---

## Uppgift 3 — Inköpslista: Scanner med text + tal

**Mål:** Läsa **produktnamn** (`nextLine`) och **antal** (`nextInt`) från konsolen, hantera Enter-fällan, spara produkter i `List<String>`, skriv ut sammanfattning.

**Problem först:** Handlingslistan ska fyllas i kassan — inte i koden. Användaren skriver namn och antal. Glömmer du Enter efter `nextInt()` blir nästa produkt tom (se [04 — AI-träning](./04-ai-traning.md)).

**Krav:**
1. Ny klass `Inkopslista.java` med `main`.
2. `Scanner scanner = new Scanner(System.in);`
3. `List<String> produkter = new ArrayList<>();`
4. Läs in **två** produkter i följd. För varje produkt:
   - Skriv `"Produkt:"` (eller tydligare prompt)
   - `String namn = scanner.nextLine();`
   - Skriv `"Antal:"`
   - `int antal = scanner.nextInt();`
   - **`scanner.nextLine();`** — släng Enter (obligatorisk rad, ingen variabel)
   - `produkter.add(namn);`
   - Skriv ut direkt: `→ namn × antal` (eller liknande)
5. Efter båda: loopa `produkter` och skriv `"Inköpt: …"` för varje sparat namn.
6. Sista rad: `"Rader i listan: " + produkter.size()`

**Exempel körning (inmatning fetstilt):**

```
Produkt:
Mjölk
Antal:
2
→ Mjölk × 2
Produkt:
Bröd
Antal:
1
→ Bröd × 1
Inköpt: Mjölk
Inköpt: Bröd
Rader i listan: 2
```

**Referenskod (facit efter eget försök):**

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Scanner;

public class Inkopslista {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<String> produkter = new ArrayList<>();

        for (int r = 0; r < 2; r++) {
            System.out.println("Produkt:");
            String namn = scanner.nextLine();
            System.out.println("Antal:");
            int antal = scanner.nextInt();
            scanner.nextLine();

            produkter.add(namn);
            System.out.println("→ " + namn + " × " + antal);
        }

        for (int i = 0; i < produkter.size(); i++) {
            System.out.println("Inköpt: " + produkter.get(i));
        }
        System.out.println("Rader i listan: " + produkter.size());
    }
}
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på `scanner.nextLine()` **efter** `nextInt()` — vad händer om du tar bort den? (testa en gång)  
- [ ] Peka på `produkter.add(namn)` — varför spara bara namn, inte antal i listan? (antal skrivs ut direkt — OK i G-nivå; parallel array är stretch)  
- [ ] Peka på båda looparna — en för inläsning, en för utskrift — varför två steg?  
- [ ] Kör med **egna** produkter — konsolen matchar din inmatning  

**Ägarskap:** Spara skärmdump eller kopiera konsolutskrift i anteckningar. Du ska kunna simulera inmatning utan att gissa ordningen.

---

## Stretch (valfritt, inom VAD)

- **Metod:** `static void skrivNumreradLista(List<String> rader)` — anrop från `Spellista` eller `Inkopslista`.
- **Inköp:** Läs tre rader i `while (!namn.equals("klar"))` — stoppord `"klar"` add:as inte (kräver `equals`, inte `==`).
- **Total vikt:** Lägg parallell `int[] antal` med samma index som produkter om du vill spara antal också (fast array + växande lista — tänk på index).

---

## Nästa steg

När alla tre uppgifter klarar klart-checken: [04 — AI-träning](./04-ai-traning.md).
