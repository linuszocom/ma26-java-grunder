# 01 — Teoriguide: Loopar och meny-val

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när programmet bara kör en gång — en meny som visar sig en enda gång och försvinner, eller en räknare som aldrig når målet. Sedan bygger vi upprepning med `while` och `for`, och avslutar med en riktig meny som läser val tills användaren trycker avsluta. Det är inte magi. Det är loop-villkor, räknare och `Scanner`. Inga egna metoder utöver `main`. Ingen `ArrayList`. Ingen OOP.

---

## Problemet först — “programmet gör bara ett varv”

Många tänker nu: “Jag kan redan `if` — räcker inte det?” Andas. `if` **väljer en gång**. En bankmeny eller en parkeringsautomat ska **fråga om och om igen** tills användaren är klar.

**Dåligt läge:**

```java
int val = 1;
System.out.println("1. Köp biljett");
System.out.println("0. Avsluta");
// Användaren hinner aldrig välja igen — programmet tar slut efter en utskrift
```

Du visade menyn **en gång**. Nästa val finns inte. Du behöver **hoppa tillbaka** till samma ställe i koden.

---

## `while` — hissturen som frågar våning för våning

**Metafor:** En hiss på ett hotell. Du står på våning 1. Hissen frågar: “Ska jag åka upp?” (`while`-villkoret). Om ja — den kör **kroppen** (en våning upp, dörrarna öppnas, `count++`). Sedan **hoppar den tillbaka** och frågar igen. När du nått våning 8 blir svaret nej — loopen **slutar** och programmet fortsätter efter klamrarna.

**Vad det är:** `while (villkor) { … }` — så länge villkoret är `true` körs blocket, sedan testas villkoret igen.  
**Varför det finns:** Upprepning när du **inte vet exakt** hur många varv i förväg — eller när användaren ska bestämma när det är klart (menyn).  
**Om det saknas / vad det INTE är:** INTE samma som `if` (ett enda test). INTE magi som “upprepar automatiskt” — **du** måste ändra något i kroppen så villkoret till slut blir `false`.

```java
int vaning = 1;
while (vaning < 8) {
    System.out.println("Nu på våning " + vaning);
    vaning++;   // count++ — ett steg närmare stopp
}
System.out.println("Toppen — hiss stannar.");
```

**Målsvar (säg högt / skriv i README):**  
*“while frågar om villkoret är true, kör kroppen, hoppar tillbaka och frågar igen. När villkoret blir false lämnar loopen. Det är INTE ett if som bara körs en gång.”*

---

## Räknare — `count++` och `count--`

**Vad det är:** `count++` ökar variabeln med 1 efter varje varv; `count--` minskar med 1.  
**Varför det finns:** Utan förändring i kroppen **ändras aldrig villkoret** — se oändlig loop nedan.  
**Om det saknas:** Loopen fastnar eller springer förbi målet utan att du märker det.

```java
int count = 0;
while (count < 5) {
    System.out.println("Varv " + count);
    count++;
}
// Skriver Varv 0 … Varv 4 — fem varv totalt
```

**Kom ihåg:** `count++` **efter** utskriften om du vill börja på 0 och stanna före 5. Ordningen i kroppen spelar roll för **vad** som skrivs ut.

---

## Oändlig loop vs avslutande loop — löpbandet som aldrig stängs av

**Metafor:** Ett löpband på gymmet. **Terminerande loop** = du sänker hastigheten steg för steg tills bandet stannar (villkoret blir false). **Oändlig loop** = hastigheten ändras aldrig — du springer i evighet (programmet hänger tills du stoppar det i IDE:n).

**Vad det är:** Oändlig loop = villkoret förblir **alltid true** (glömt `count++`, fel jämförelse, eller med flit `while (true)` utan `break` — sista mönstret kommer senare i kursen).  
**Varför det spelar roll:** Examination och meny-appar ska **avsluta** när användaren vill — inte låsa konsolen.  
**Om det saknas / vad det INTE är:** INTE “Java kör för snabbt”. Det är **logik** — något i kroppen uppdaterar inte villkoret.

```java
int count = 0;
while (count < 5) {
    System.out.println("Fastnat: " + count);
    // count++;  ← GLÖMT — oändlig loop, count förblir 0
}
```

**Metod:** Efter varje `while` — peka: **Vad i kroppen gör att villkoret en dag blir false?** Om inget → oändlig loop.

**Målsvar (säg högt / skriv i README):**  
*“En oändlig loop händer när villkoret aldrig blir false — oftast glömt steg som count++. Terminerande loop ändrar något varje varv tills villkoret släpper.”*

---

## `for` — tåg som stannar vid varje station längs sträckan

**Metafor:** Ett pendeltåg med fast tidtabell. Du vet **startstation**, **sista station** och **att det stannar vid varje hållplats**. Tre uppgifter i en rad — du behöver inte manuellt `count++` utanför om du litar på `for`-huvudet.

**Vad det är:** `for (start; villkor; steg) { … }` — start körs en gång, sedan: testa villkor → kropp → steg → testa igen.  
**Varför det finns:** När du **vet** hur många iterationer (1 till 10, summa av tal, skriv ut fem rader).  
**Om det saknas / vad det INTE är:** INTE bättre eller sämre än `while` — **rätt verktyg för rätt jobb**. Meny tills användaren avslutar = oftast `while`. Fem fasta varv = oftast `for`.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Station " + i);
}
```

**Målsvar (säg högt / skriv i README) — for:**  
*“for samlar start, villkor och steg i en rad. Jag använder den när jag vet hur många varv jag ska köra — till exempel summa från 1 till 10.”*

---

## Off-by-one — `<` mot `<=` (ett steg fel i tidtabellen)

**Problem-först:** Du vill skriva ut talen **1, 2, 3, 4, 5**. Du skriver:

```java
for (int i = 1; i < 5; i++) {
    System.out.println(i);
}
```

Utskrift: **1, 2, 3, 4** — fem saknas. Ett steg fel: `< 5` stoppar **före** 5.

**Rätt när 5 ska ingå:**

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

**Vad det är:** Off-by-one = en iteration **för mycket** eller **för lite** p.g.a. fel operator i villkoret.  
**Varför det spelar roll:** Fel antal varv i loop = fel summa, fel antal rader, fel “sista biljetten”.  
**Metod:** Skriv **första** och **sista** värde du vill ha på papper. Ska sista ingå? → ofta `<=`. Ska loopen stanna **före** sista? → `<`.

| Mål | Vanlig loop |
|-----|-------------|
| 0, 1, 2, 3, 4 (fem tal, börjar 0) | `i = 0; i < 5; i++` |
| 1, 2, 3, 4, 5 (fem tal, börjar 1) | `i = 1; i <= 5; i++` |
| 1, 2, 3, 4 (fyra tal) | `i = 1; i < 5; i++` |

**Målsvar (säg högt / skriv i README):**  
*“Off-by-one är ett steg fel i antal varv. Jag väljer < eller <= utifrån om sista talet ska ingå. Ett steg fel ger en extra eller en saknad iteration.”*

---

## Summering i loop — `sum += i`

**Vad det är:** `sum = sum + i` i kort form — ackumulera värde över varv.  
**Varför det finns:** Många uppgifter (total kostnad, antal biljetter) bygger på att **lägga ihop** resultat från varje iteration.

```java
int sum = 0;
for (int i = 1; i <= 10; i++) {
    sum += i;
}
System.out.println("Summa 1–10: " + sum);  // 55
```

**Kom ihåg:** Initiera `sum = 0` **före** loopen — annars vet du inte vad du adderar till.

---

## `Scanner` och `nextInt()` — läsa menyval från tangentbordet

**Metafor:** Parkeringsautomaten väntar på att du trycker en siffra på knappsatsen. `Scanner` är “örat” mot konsolen; `nextInt()` läser **nästa heltal** användaren skriver.

**Vad det är:**

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
System.out.print("Välj (0–3): ");
int val = scanner.nextInt();
```

**Varför det finns:** Hårdkodat `val = 1` räcker inte i en riktig meny — användaren ska välja vid körning.  
**Om det saknas / vad det INTE är:** INTE samma som `println` (det **skriver**, läser inte). Att **inte** stänga `scanner.close()` i övningskod är ok här — fokus är läsa val korrekt; stängning kommer i senare sammanhang.

**Vanlig ordning i meny-kropp:**
1. Visa alternativ  
2. `System.out.print` + `nextInt()`  
3. `if` / `else if` på `val` (ingen `switch` i det här paketet)

---

## Meny-loop — automaten som frågar tills du trycker avsluta

**Metafor:** En biljettautomat vid P-huset. Den visar alltid samma knappar tills du trycker **0 — Avsluta**. Varje annat val hanteras (köp timme, förläng, visa pris) — sedan **börjar automaten om** och visar menyn igen.

**Vad det är:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int val = -1;   // startvärde så första varvet körs

        while (val != 0) {
            System.out.println("--- P-automat ---");
            System.out.println("1. Köp 1 timme");
            System.out.println("2. Visa pris");
            System.out.println("0. Avsluta");
            System.out.print("Val: ");
            val = scanner.nextInt();

            if (val == 1) {
                System.out.println("Biljett utskriven.");
            } else if (val == 2) {
                System.out.println("Pris: 25 kr/tim.");
            } else if (val != 0) {
                System.out.println("Ogiltigt val.");
            }
        }
        System.out.println("Hej då!");
    }
}
```

**Varför `while (val != 0)`:** Avslut är **medvetet** — loopen fortsätter tills användaren väljer 0.  
**Om det saknas:** Programmet kör ett val och dör — eller fastnar om du aldrig sätter `val` till 0.

**Målsvar (säg högt / skriv i README):**  
*“while (val != 0) visar menyn, läser val med Scanner.nextInt(), hanterar valet, och loopar tills användaren väljer 0. Programmet stannar inte av sig själv — avslut är ett medvetet val.”*

---

## När `while` — när `for`?

| Situation | Vanligt val |
|-----------|-------------|
| Meny tills användaren avslutar | `while (val != 0)` |
| Exakt N varv (summa 1–10, skriv 5 rader) | `for` |
| Räknare upp/ner tills gräns | `while` med `count++` / `count--` |
| Vet inte antal varv i förväg | `while` |

**Målsvar (säg högt / skriv i README) — metod:**  
*“Tre frågor: Vet jag antal varv? → for. Ska användaren bestämma stopp? → while. Ändras något i kroppen så villkoret kan bli false?”*

---

## Metod — när du tvekar “loopar den för evigt?”

Det är inte magi. Fyra steg:

1. **Skriv villkoret** — vad måste bli false?  
2. **Peka i kroppen** — vad ändrar variabeln i villkoret (`count++`, `val = nextInt()`, …)?  
3. **Räkna på papper** — första varv, andra varv, när stannar det?  
4. **Kör i IDE** — hänger den? Saknas sista utskrift? → off-by-one eller glömt steg.

**Målsvar (säg högt / skriv i README) — metod:**  
*“Jag pekar på villkoret och på raden i kroppen som gör att villkoret en gång blir false. Annars är det oändlig loop.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Glömt `count++` i `while` | Oändlig loop — villkoret ändras aldrig |
| `i < 5` när du ville inkludera 5 | Off-by-one — använd `<=` eller `< 6` |
| Meny utan loop — bara en `println`-meny | Använd `while (val != 0)` |
| `if` i stället för loop för “tills användaren avslutar” | `if` körs en gång |
| `Scanner` inuti loopen skapas om varje varv | Skapa **en** `Scanner` före loopen |
| Semikolon efter `while (...)` | Tom loop — kroppen körs inte som du tror |
| `ArrayList`, egna metoder, `switch`, Git i övningen | NOLL SPILL — bara loop + Scanner + `main` |
| `=` i stället för `==` i `if (val == 1)` | Samma som vecka 37 — tilldelning vs jämförelse |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Skillnad `while` och `if` i en mening  
2. Vad gör `count++` i en loop — och vad händer om du glömmer det?  
3. När väljer du `i < 5` framför `i <= 5`?  
4. Varför `while (val != 0)` för en meny?  
5. Vad läser `scanner.nextInt()` — och var i koden ska `Scanner` skapas?

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna i IDE:n.
