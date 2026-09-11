# 01 — Teoriguide: Metoder, parametrar och retur

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **samma formel kopierad fem gånger** i `main` — sedan flyttar vi formeln till ett ställe och anropar den. Det är inte magi. Det är metod, parameter, `return` och anrop. Allt i **samma klass** (`Main.java`). Inga egna klasser. Inga objekt än.

---

## Problemet först — duplicerad logik i `main`

Många tänker: “Metoder… det är väl bankappar och klasser?” Andas. Idag är det **ett namngivet kodblock** du kan köra om och om igen.

**Dåligt läge** — samma frakträkning kopierad:

```java
public class Main {
    public static void main(String[] args) {
        double fraktOrder1 = 120.0 * 0.15 + 29.0;
        double fraktOrder2 = 85.0 * 0.15 + 29.0;
        double fraktOrder3 = 200.0 * 0.15 + 29.0;

        System.out.println(fraktOrder1);
        System.out.println(fraktOrder2);
        System.out.println(fraktOrder3);
    }
}
```

Koden **kör** — men om procenten ändras till `0.18` måste du jaga **tre rader**. Glömmer du en rad får olika ordrar olika regler. Det är därför metoder finns: **en kropp, flera anrop**.

---

## Metod — namngivet kodblock utanför `main`

**Metafor:** En **miniräknarfunktion** på telefonen. Du trycker “km → mil” — appen kör samma formel varje gång. Du skriver inte formeln på nytt för varje resa.

**Vad det är:** En **metod** = namn + (valfritt) parametrar + kropp `{ ... }`. Den ligger **utanför** `main`, fortfarande inuti klassen `Main`.  
**Varför den finns:** Samma logik ska köras många gånger utan copy-paste.  
**Om den saknas / vad den INTE är:** INTE en variabel. INTE `println` i sig. INTE en egen fil/klass idag (`Account` kommer senare). Metoden **inuti** `main` är ogiltig syntax.

**Målsvar (säg högt / skriv i README):**  
*“En metod är ett namngivet kodblock utanför main. Jag anropar det med metodnamn och parentes. Samma kropp, flera gånger — utan duplicerade rader.”*

### Minsta metod — `void` utan parametrar

```java
public class Main {
    public static void main(String[] args) {
        skrivRubrik();
    }

    public static void skrivRubrik() {
        System.out.println("=== Orderlogg ===");
    }
}
```

**Vad det visar:** `main` **anropar** `skrivRubrik();` — Java hoppar till kroppen, kör den, hoppar tillbaka.  
**Kom ihåg / INTE:** `static` här betyder “metoden hör till klassen” — du behöver inget objekt i det här paketet.

---

## Anrop — starta metoden

**Vad det är:** Raden `metodnamn(...);` **kör** metoden.  
**Varför den finns:** `main` styr flödet; metoder gör deljobb.  
**Om den saknas / vad den INTE är:** INTE deklaration (det är metodhuvudet). Glömda parenteser `()` på metod utan parametrar ger ofta fel.

```java
skrivRubrik();          // anrop
skrivRubrik();          // samma kropp igen
```

**Målsvar (säg högt / skriv i README) — anrop:**  
*“Anropet metodnamn(); säger till Java: kör den metodens kropp nu. Parenteserna måste finnas även när inga värden skickas in.”*

---

## `void` — metoden ger inget värde tillbaka

**Metafor:** En **skrivare** som bara skriver på kvittot — den levererar text till konsolen, inte ett tal du kan spara i en variabel.

**Vad det är:** Returtypen **`void`** = “ingen data tillbaka till anroparen”.  
**Varför den finns:** Utskrift, rubriker, enkel presentation — jobb där `main` inte behöver ett beräknat tal efteråt.  
**Om den saknas / vad den INTE är:** INTE samma sak som `return` med värde. Du kan **inte** skriva `double x = skrivRubrik();` — javac: *void cannot be converted to double*.

```java
public static void skrivOrderRad(int orderNr, double total) {
    System.out.println("Order " + orderNr + ": " + total + " kr");
}
```

Parametrar (`orderNr`, `total`) tar emot data — men metoden **returnerar** inget tal; den skriver bara.

---

## Parameter — ingångar i parentesen

**Metafor:** **Ingångsslussar** på maskinen. Du matar in km — formeln får km, inte dina variabelnamn från `main`.

**Vad det är:** I metodhuvudet: `typ namn, typ namn` **inuti parentesen**. Dessa **parametrar** får värden när någon **anropar** metoden.  
**Varför de finns:** Samma formel ska fungera för **olika** indata utan att hårdkoda i kroppen.  
**Om de saknas / vad de INTE är:** INTE variabler i `main` (de lever i metodens eget scope). Namnen **behöver inte** matcha mellan anrop och deklaration — **antal och typ** måste matcha.

```java
public static double beraknaFrakt(double varuvardet, double procent, double fastAvgift) {
    return varuvardet * procent + fastAvgift;
}

// I main:
double kostnad = beraknaFrakt(120.0, 0.15, 29.0);
```

**Anrop:** värdena `120.0`, `0.15`, `29.0` = **argument**.  
**Deklaration:** `varuvardet`, `procent`, `fastAvgift` = **parametrar**.

**Målsvar (säg högt / skriv i README) — parameter:**  
*“Parametrar deklareras i metodens parentes. Argument skickas i anropet. Första argumentet till första parametern — typ och antal måste stämma.”*

---

## Returtyp och `return` — skicka tillbaka resultat

**Metafor:** Vågen visar **ett tal** på displayen — du **plockar upp** talet och lägger det i en burk (`double frakt`) i `main`. Displayen (`return`) är inte samma sak som att ropa ut talet i butiken (`println`).

**Vad det är:** Returtypen (t.ex. `double`, `int`, `boolean`) säger **vilken sort data** metoden lämnar tillbaka. **`return uttryck;`** avslutar metoden och **ger** värdet till anropet.  
**Varför det finns:** `main` (eller en loop) ska **spara**, **jämföra** eller **skriva ut** resultatet — inte bara räkna inuti metoden utan att något kommer tillbaka.  
**Om det saknas / vad det INTE är:** INTE `void`. INTE `println` — utskrift syns i konsol men **returnerar inget** till Java. Metod med returtyp **måste** nå en `return` (eller javac klagar: *missing return statement*).

```java
public static double kmTillMil(double km) {
    return km * 0.621371;
}

public static void main(String[] args) {
    double resaKm = 10.0;
    double resaMil = kmTillMil(resaKm);   // spara returvärdet
    System.out.println(resaMil);          // 6.21371...
}
```

**Målsvar (säg högt / skriv i README) — return:**  
*“Om main behöver talet: deklarera returtyp, returnera med return, spara i variabel vid anropet. println visar — return levererar till koden.”*

---

## `void` vs retur — när väljer du?

| Behov | Returtyp | Exempel |
|-------|----------|---------|
| Bara skriva till konsolen | `void` | `skrivOrderRad(...)` |
| `main` ska **använda** ett beräknat tal | `double`, `int`, `boolean`, … | `beraknaFrakt(...)`, `kmTillMil(...)` |

Exam 1 (Kontoappen) använder **båda**: utskrift av kontoinfo (`void` eller println i rätt lager) och metoder som **returnerar** saldo via getters — samt `deposit`/`withdraw` som tar belopp som **parameter**. Samma tänk som idag, fast på konto senare.

---

## Deklarera och anropa — hela mönstret

```java
public class Main {
    public static void main(String[] args) {
        double a = 80.0;
        double b = 0.25;
        double prisInkl = prisMedPåslag(a, b);
        System.out.println(prisInkl);
    }

    public static double prisMedPåslag(double grundpris, double påslagAndel) {
        return grundpris * (1 + påslagAndel);
    }
}
```

**Ordning i filen:** `main` får ligga var som helst **om** metoderna är **syskon** (båda direkt i klassen). Vanlig stil: `main` överst, hjälpmetoder under.

**Målsvar (säg högt / skriv i README) — helheten:**  
*“Deklarera metoden utanför main. Anropa med argument. Om returtyp inte är void: spara resultatet i en variabel eller skicka vidare. Skriv ut i main om användaren ska se det.”*

---

## Refaktorera — från duplicerat till metod

**Före:**

```java
double fraktA = 50.0 * 0.15 + 29.0;
double fraktB = 90.0 * 0.15 + 29.0;
```

**Efter:**

```java
double fraktA = beraknaFrakt(50.0, 0.15, 29.0);
double fraktB = beraknaFrakt(90.0, 0.15, 29.0);
```

**Varför:** En formel. En ändring. Färre misstag. Det är **återanvändning** — kursplanens kärna.

---

## Loop + metod — samma kropp, många värden

Loopar från föregående paket passar ihop med metoder — metoden håller **formeln**, loopen styr **hur många gånger** du anropar:

```java
for (int orderNr = 101; orderNr <= 103; orderNr++) {
    double varde = 50.0 * orderNr;   // exempel — olika värden per varv
    double frakt = beraknaFrakt(varde, 0.15, 29.0);
    System.out.println("Order " + orderNr + ": " + frakt + " kr");
}
```

**Kom ihåg / INTE:** Du **behöver** ingen array eller `ArrayList` i det här paketet. Tre separata variabler + tre anrop räcker lika bra.

---

## BMI-liknande beräkning utan klasser

Hälsoindex är **ren matematik** — perfekt som `return`-metod:

```java
public static double beraknaBmi(double viktKg, double langdMeter) {
    return viktKg / (langdMeter * langdMeter);
}
```

Ingen person-klass. Bara indata → formel → utdata. Samma mönster som frakt och enhetsomvandling.

---

## Scope — parametrar syns bara i metoden

```java
public static double dubbla(int tal) {
    int lokalt = tal * 2;
    return lokalt;
}

public static void main(String[] args) {
    int x = 5;
    int y = dubbla(x);
    // System.out.println(lokalt);  // FEL — lokalt finns inte här
    // System.out.println(tal);     // FEL — tal finns bara inuti dubbla
}
```

**Målsvar (säg högt / skriv i README) — scope:**  
*“Parametrar och variabler inuti metoden lever bara där. main når returvärdet via anropet — inte parametrarnas namn.”*

---

## Metod — när du tvekar

Det är inte magi. Fem steg:

1. **Duplicerar jag samma logik?** → Bryt ut till metod.  
2. **Behöver main ett tal tillbaka?** → Returtyp + `return`. Annars `void`.  
3. **Behöver formeln olika indata?** → Parametrar i parentesen.  
4. **Deklarera utanför `main`**, `public static` i `Main`.  
5. **Anropa** med rätt antal argument — spara returvärde om det inte är `void`.

**Målsvar (säg högt / skriv i README) — metod:**  
*“En kropp, flera anrop. Parametrar in, return ut när main behöver resultatet. void när jobbet bara är utskrift.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Metod **inuti** `main` | Flytta ut — syskon till `main` i klassen |
| `double summa = skrivRubrik();` på `void` | void ger inget värde — anropa utan att tilldela |
| Glömd `return` i `double`-metod | *missing return statement* — lägg till `return uttryck;` |
| Fel antal argument | `beraknaFrakt(10)` när metoden kräver tre parametrar |
| Fel typ i argument | `beraknaFrakt("120", 0.15, 29)` — String där double ska |
| Bara `println` inuti metod när main ska räkna vidare | Använd `return` — println visar, return levererar |
| Egen klass / `Account` / `ArrayList` för tidigt | Håll dig till `static` i `Main` enligt det här paketet |
| Försöka anropa utan `static` i `main` | I det här paketet: `public static void metod(...)` |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför duplicerad kod är farlig — ett exempel.  
2. Skillnad **parameter** vs **argument**.  
3. Skillnad **`void`** vs metod med **`return`**.  
4. Varför `main` sparar returvärdet i en variabel innan `println`.  
5. Hur Exam 1:s `deposit(belopp)` liknar en metod med parameter (utan att du skrivit klassen än).

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
