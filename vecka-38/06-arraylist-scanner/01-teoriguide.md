# 01 — Teoriguide: Arrayer, ArrayList och Scanner

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriv i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när du har fem variabler för fem packningsföremål — och när du försöker lägga till ett sjätte i en array som bara har fem fack. Sedan bygger vi listor som växer och läsning från tangentbordet. Det är inte magi. Det är index, `add` och `nextLine`.

**Omfång:** Bara `Main.java`. Loopar och metoder från tidigare paket är OK. Ingen objektlista, inga extra klasser, ingen Git.

---

## Problemet först — fem burkar mot ett facksystem

Många tänker: “Jag kan väl bara ha `item1`, `item2`, `item3`?” Andas. Det funkar tills antalet ändras — eller tills du ska loopa ut allt utan att kopiera fem `println`.

**Dåligt läge (tre lösa variabler):**

```java
int vikt1 = 800;
int vikt2 = 1200;
int vikt3 = 450;
System.out.println(vikt1);
System.out.println(vikt2);
System.out.println(vikt3);
// Fyra föremål? Ny variabel. Tjugo? Omöjligt att underhålla.
```

**Bättre:** ett namn (`packVikt`), många **fack** med **index**.

---

## Array — hyllplan med fast antal fack

**Metafor:** Ett skåp med fem hyllor numrerade **0–4** på insidan (inte 1–5 på etiketten). Du bestämmer antal hyllor när skåpet byggs — du kan inte magiskt skapa hylla 6 utan nytt skåp.

**Vad det är:** `int[] packVikt = new int[5];` skapar fem fack. `packVikt[0] = 800;` fyller **första** facket.  
**Varför det finns:** Ett namn, många värden — och en `for`-loop kan gå igenom alla utan att du vet varje värde i förväg.  
**Om det saknas / vad det INTE är:** INTE dynamisk storlek (fem fack är fem, punkt). INTE `ArrayList` (det kommer strax). INTE `println(array)` för att få alla tal — det skriver en adress, inte innehållet.

```java
int[] packVikt = new int[5];
packVikt[0] = 800;
packVikt[1] = 1200;
packVikt[2] = 450;
packVikt[3] = 300;
packVikt[4] = 950;

for (int i = 0; i < packVikt.length; i++) {
    System.out.println("Fack " + i + ": " + packVikt[i] + " g");
}
```

**Målsvar (säg högt / skriv i README):**  
*“Array har fast storlek. Index börjar på 0. `length` är antal fack. Jag loopar `i` från 0 till length minus 1 och läser `array[i]`.”*

---

## Index 0 — människor räknar 1, Java räknar 0

| Antal fack | `length` | Första index | Sista index |
|------------|----------|--------------|-------------|
| 3 | 3 | 0 | 2 |
| 5 | 5 | 0 | 4 |

**Minnesregel:** Sista lagliga index = `length - 1`. Index `length` finns **inte**.

**Vad det INTE är:** Att “fack 1 saknas” — fack 0 **är** det första.

---

## Problem först — `tal[3]` i en array med length 3

**Scenario:** Tre dagar, tre temperaturer. Någon skriver:

```java
int[] temp = new int[3];
temp[0] = 12;
temp[1] = 15;
temp[2] = 9;
System.out.println(temp[3]);  // fjärde dagen?
```

**Konsolen:**

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
```

**Vad det betyder:** Du pekade på hylla 3 i ett skåp med bara hyllor 0, 1, 2. Programmet **kraschar** — det gissar inte.

**Metod — innan du ändrar index:**
1. Hur många fack? → `array.length`
2. Sista OK index? → `length - 1`
3. Mitt index ≤ sista OK?

**Målsvar (säg högt / skriv i README) — index:**  
*“Index utanför 0 … length−1 ger ArrayIndexOutOfBoundsException. Jag kollar length innan jag pekar — samma idé på listor senare med get.”*

---

## ArrayList — hyllplan som växer vid `add`

**Metafor:** Spellistan på telefonen. Du trycker “lägg till låt” — appen skapar plats. Du säger inte “jag har exakt 12 låtar” i förväg.

**Problem först:** Fjärde låten i en array med plats för tre:

```java
String[] fast = new String[3];
fast[0] = "Intro";
fast[1] = "Vers";
fast[2] = "Refräng";
fast[3] = "Outro";  // samma krasch — fast storlek
```

**Lösning:** `List` / `ArrayList` — tom lista, sedan `add`.

**Vad det är:** `List<String> spellista = new ArrayList<>();` — variabeltypen är **`List`**, skapandet är **`new ArrayList<>()`**. `add("Låt")` lägger sist. `get(0)` läser första — samma 0 som array.  
**Varför det finns:** När du **inte** vet antal rader i förväg (inköp, låtar, namn från användaren).  
**Om det saknas / vad det INTE är:** INTE samma syntax som array (`lista[0]` funkar inte — använd `get(0)`). INTE `length` — listan har **`size()`** med parentes. INTE objekt av egna klasser i listan **än** (`List<Account>` kommer senare).

```java
import java.util.List;
import java.util.ArrayList;

List<String> spellista = new ArrayList<>();
spellista.add("Midnight Run");
spellista.add("Static Echo");
spellista.add("Low Tide");

for (int i = 0; i < spellista.size(); i++) {
    System.out.println((i + 1) + ". " + spellista.get(i));
}
```

**Målsvar (säg högt / skriv i README):**  
*“Jag deklarerar List, skapar ArrayList. add lägger till. get(i) läser. size() räknar. Loop: i från 0 till size() minus 1 — samma mönster som array men byt length mot size() och [i] mot get(i).”*

---

## Skriv ut hela listan — `println(lista)` räcker inte alltid

`System.out.println(spellista);` kan visa `[Midnight Run, Static Echo, …]` — ibrev OK, ibland vill du formatera (nummer, bindestreck). Då: **`for` + `get(i)`** — samma som array-loopen.

**Vad det INTE är:** Att array och lista delar exakt samma utskriftsknapp — array har ingen inbyggd “skriv snyggt”; du loopar.

---

## Scanner — från hårdkodat till tangentbordet

**Metafor:** Kassan i mataffären. Hittills fyllde **du** varorna i koden. Nu står **kunden** vid kassan och skriver.

**Vad det är:** `Scanner scanner = new Scanner(System.in);` — `System.in` är tangentbordet. `nextLine()` läser **en hel rad** till `String`.  
**Varför det finns:** Menyer, inköpslistor och register ska ta emot det användaren skriver — inte bara det du skrev i går.  
**Om det saknas / vad det INTE är:** INTE `println` (det **skriver**, läser inte). INTE samma som `nextInt()` (det läser bara siffror).

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
System.out.println("Skriv en låt:");
String rad = scanner.nextLine();
System.out.println("Du skrev: " + rad);
```

Programmet **väntar** tills användaren trycker Enter.

---

## Blanda text och tal — inköpslista

Typiskt flöde: **produktnamn** (text) + **antal** (tal).

```java
System.out.println("Produkt:");
String produkt = scanner.nextLine();
System.out.println("Antal:");
int antal = scanner.nextInt();
scanner.nextLine();  // släng Enter efter talet — se nästa avsnitt
System.out.println(produkt + " × " + antal);
```

`add(produkt)` i en `List<String>` sparar namnet; antal kan du skriva ut direkt eller spara i en array om du har **samma antal rader** varje gång.

**Målsvar (säg högt / skriv i README) — Scanner:**  
*“nextLine för text, nextInt för heltal. Efter nextInt lägger jag en extra nextLine() som jag inte sparar — den tar bort kvarvarande Enter innan nästa riktiga nextLine().”*

---

## Problem först — tomt namn efter `nextInt`

**Scenario:**

```java
System.out.println("Antal:");
int antal = scanner.nextInt();
System.out.println("Produkt:");
String produkt = scanner.nextLine();
System.out.println("[" + produkt + "]");
```

Användaren skriver `3` + Enter, sedan `Mjölk` + Enter.

**Output:**

```
Antal:
3
Produkt:
[]
```

**Varför:** `nextInt()` tog `3` men **lämnade Enter i kön**. Nästa `nextLine()` läste den tomma raden — inte `"Mjölk"`.

**Fix:**

```java
int antal = scanner.nextInt();
scanner.nextLine();  // släng radbrytningen
String produkt = scanner.nextLine();  // nu läser den Mjölk
```

Det är INTE att användaren “glömde skriva”. Det är **kön** från tangentbordet.

---

## Array vs List — när välja?

| | Array | `List` (`ArrayList`) |
|--|-------|----------------------|
| **Storlek** | Fast vid skapande | Växer med `add` |
| **Index/läs** | `arr[i]` | `lista.get(i)` |
| **Antal** | `arr.length` (ingen `()`) | `lista.size()` |
| **Passar** | Packlista med 5 fack, veckotemperaturer | Spellista, inköp, okänt antal rader |

**Målsvar (säg högt / skriv i README) — val:**  
*“Fast antal kända platser → array. Okänt eller växande antal rader → List med add. Båda använder index 0 och for-loop med rätt längd/size.”*

---

## Metod — när du tvekar

1. **Array eller lista?** Fast storlek → array. Växande → `List` + `ArrayList`.
2. **Index OK?** 0 … length−1 eller 0 … size()−1.
3. **Scanner:** Text före tal eller efter? Efter `nextInt` → extra `nextLine()` innan nästa text.
4. **Krasch?** Läs Exception-namnet — `ArrayIndexOutOfBounds` = fel index i array; `IndexOutOfBounds` på lista = fel `get`.

Du får flytta utskrift till en **`static`-metod** med `List<String>` som parameter — samma idé som i [05 — Metoder](../05-metoder/).

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Första facket är index 1 | Index 0 är första — alltid |
| `tal[3]` i `new int[3]` | Sista är `tal[2]` |
| `ArrayList<String> x = …` som deklaration | Deklarera `List<String>`, skapa `new ArrayList<>()` |
| `lista[0]` på ArrayList | Använd `lista.get(0)` |
| `tal.length()` | Array: `.length` utan parentes. Lista: `.size()` **med** parentes |
| `nextInt()` sen direkt `nextLine()` för namn | Extra `nextLine()` emellan — släng Enter |
| `println(minLista)` och förvänta dig fin format | Loopa med `get(i)` om du vill styra format |
| `List<MinKlass>` i den här veckan | Bara primitiva/`String` i listan än — objekt kommer senare |

---

## Checkpoint (privat)

Skriv i anteckningar — för dig:

1. Array med 4 fack — vilket är sista index?  
2. Skillnad `length` vs `size()`?  
3. Varför blir `produkt` tom efter `nextInt()` utan extra `nextLine()`?

När du kan säga svaren högt: [02 — Visuellt](./02-visuell.md) eller [03 — Övningar](./03-ovningar.md).

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
