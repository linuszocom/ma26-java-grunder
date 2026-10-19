# 01 — Teoriguide: Sök och meny

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du har redan `private List<Medlem>`, `läggTill` och `listaAlla` i `Register`. Nu: **hitta en specifik medlem** utan att speja i hela listan med ögonen — och **köra registret via meny** tills användaren avslutar. Det är inte magi. Det är en sökmetod i rätt fil + samma loop-idé som i vecka 38, nu med fyra val.

**Förutsättning:** [17-lista-register](../17-lista-register/) (lista + `läggTill` / `listaAlla`). [15-tre-klasser](../../vecka-42/15-tre-klasser/) (`Medlem` / `Register` / `Main`). [04-loopar-meny](../../vecka-38/04-loopar-meny/) (`while`, `Scanner`). Här: **`sökNamn`**, **meny 1–4**, **switch expression**. Ingen factory. Inget arv. Ingen README-uppsats.

---

## Problemet först — sök-loop i `Main`

Många tänker: “Jag ska hitta Elsa — då loopar jag väl listan i `Main`?” Andas. Det **kan** kompilera *om* listan läckt ut. Men Examination 2 kräver att **registret** äger samlingen — och att du kan **peka på vilken metod som söker**.

**Dåligt läge** (fel rum):

```java
// Main.java — trasigt mönster (kapsling / ansvar)
for (Medlem m : register.getMedlemmar()) {  // eller läckt lista
    if (m.getNamn().equalsIgnoreCase("Elsa")) {
        System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
    }
}
```

Koden “letar”. Men **Main öppnar pärmen**. Listan är `private` i `Register` — Main ska **fråga**, inte bläddra. Flytta loopen till `sökNamn`.

**Målsvar (säg högt):**  
*“Söklogiken bor i Register. Main anropar sökNamn med en sträng — den loopar inte själv över medlemmarna.”*

---

## Tre filer — vem gör vad *nu*

| Fil | Ansvar | INTE |
|-----|--------|------|
| `Medlem.java` | Data + getters | Lista, sök, meny |
| `Register.java` | `List<Medlem>`, `läggTill`, `listaAlla`, **`sökNamn`** | `Scanner`, menytext |
| `Main.java` | Meny-loop, `Scanner`, anropa register | for-each över medlemmar, “speja” via `listaAlla` som sök |

**Målsvar (säg högt):**  
*“Main styr I/O och meny. Register äger listan och sök. Medlem är kortet.”*

---

## `sökNamn` — ett kort ur pärmen

**Metafor:** Receptionisten bläddrar **pärmen** efter **ett namn**. Hittar kortet → läser upp namn + nummer och **släpper pärmen**. Finns det inte → säger **en gång**: medlemmen saknas. Det är INTE att ropa “saknas” efter varje fel kort. Det är INTE att skriva ut hela pärmen och be dig speja.

**Vad det är:** `public void sökNamn(String namn)` i `Register` — for-each, jämför, skriv ut, `return` vid träff; miss-rad **efter** loopen.

```java
public void sökNamn(String namn) {
    for (Medlem m : medlemmar) {
        if (m.getNamn().equalsIgnoreCase(namn)) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
            return;  // klar — sluta leta
        }
    }
    System.out.println("Medlemmen saknas");
}
```

**Varför `void` + utskrift:** Examination 2 säger: skriv ut träffen **eller** att medlemmen saknas. Metoden svarar i konsolen. (Jämför Exam 1: `findAccount` returnerade objekt/`null` — annan exam, annan kontrakt.)

**Varför `equalsIgnoreCase`:** `"elsa"` ska hitta `"Elsa"`. INTE `==` på strängar. INTE jämföra utan `getNamn()`.

**Varför `return` vid hit:** Annars kan loopen fortsätta och skriva mer. Early return = “klart”.

**Varför miss efter `for`:** En rad. Om du skriver saknas i `else` varje varv får du en storm av felmeddelanden.

**Om det saknas / vad det INTE är:** INTE sök-loop i `Main`. INTE `listaAlla` som “sök”. INTE factory. INTE att skapa `new Medlem` i sökmetoden.

**Anropa från `Main` (hardcoded, innan meny):**

```java
register.läggTill(new Medlem("Elsa", 201));
register.läggTill(new Medlem("Nova", 202));
register.sökNamn("Elsa");  // → Elsa 201
register.sökNamn("Rune");  // → Medlemmen saknas
```

**Målsvar (säg högt) — sök:**  
*“sökNamn loopar, jämför med equalsIgnoreCase, skriver träff och returnerar — eller Medlemmen saknas efter loopen.”*

---

## `List<Medlem>` — samma deklaration som i listpaketet

**Påminnelse:** Fältet i `Register` deklareras mot gränssnittet:

```java
private List<Medlem> medlemmar = new ArrayList<>();
```

**Vad det INTE är:** INTE `ArrayList<Medlem>` som enda typ i fältdeklarationen (kursstandard: `List` deklarerad, `ArrayList` skapas). INTE lista i `Main`.

---

## Meny i `Main` — loop tills 4

**Metafor:** Receptionisten står kvar och frågar om och om igen tills gästen säger hejdå. Varje siffra är ett **uppdrag** till registret — inte ny arkitektur.

Hardcoded `new Medlem` + två anrop **räcker för att testa sök**. Examination 2 kräver **interaktiv meny**: lägg till, lista, sök, avsluta.

| Val | Handling |
|-----|----------|
| 1 | Lägg till — läs namn + nummer → `läggTill(new Medlem(…))` |
| 2 | Lista alla → `listaAlla()` |
| 3 | Sök — läs namn → `sökNamn(…)` |
| 4 | Avsluta — `kör = false` (lämna `while`) |

**Stomme:**

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
Register register = new Register();
boolean kör = true;

while (kör) {
    System.out.println("1 Lägg till  2 Lista  3 Sök  4 Avsluta");
    int val = scanner.nextInt();
    scanner.nextLine();  // ät newline innan namn

    switch (val) {
        case 1 -> {
            System.out.print("Namn: ");
            String namn = scanner.nextLine();
            System.out.print("Nummer: ");
            int nr = scanner.nextInt();
            scanner.nextLine();  // ät newline efter tal
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
```

**Switch expression:** `case n -> …` är **OK** (Java 21, kursstandard). Ingen `break`, ingen fall-through. Klassisk `switch` med `break` undviks när uttrycksformen räcker.

**Scanner — `nextInt` / `nextLine`:** Efter `nextInt()` ligger Enter (`\n`) kvar. Nästa `nextLine()` utan “ätare” ger **tom sträng** — namnfrågan hoppas över. Regel: **ät newline medvetet** efter varje `nextInt()` innan du läser text.

**Om det saknas / vad det INTE är:** INTE fem menyval (det var Exam 1). INTE `Scanner` i `Register`. INTE sök-loop i `case 3`. INTE ny `Scanner` varje varv.

**Målsvar (säg högt) — meny:**  
*“Main läser val med Scanner. Register gör listjobbet. case 3 anropar sökNamn — den söker inte själv.”*

---

## Exam-körning — vad du ska se

Kör via menyn (inte bara hardcoded):

1. Val **1** — Elsa, 201  
2. Val **1** — Nova, 202  
3. Val **2** — två rader  
4. Val **3** — sök `Elsa` → `Elsa 201`  
5. Val **3** — sök `Rune` → `Medlemmen saknas`  
6. Val **4** — programmet avslutar utan krasch  

**Peka:** Vilken metod söker? → `sökNamn` i `Register.java`.

**Målsvar (säg högt) — helheten:**  
*“Två medlemmar, lista, hit, miss, exit. Sök pekar jag på i Register — inte i Main.”*

---

## Metod — när du tvekar

1. **Hitta medlem?** → `register.sökNamn(namn)` — aldrig for-each i `Main`.  
2. **Alltid saknas?** → Stavning, tom lista, glömd `equalsIgnoreCase`, eller saknas-rad inne i loopen.  
3. **Tomt namn / hoppad fråga?** → `nextLine()` efter `nextInt()`.  
4. **Loopen dör aldrig?** → case 4 måste sätta `kör = false`.  
5. **Exam: vilken metod söker?** → Öppna `Register.java`, peka på `sökNamn`.

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| for-each sök i `Main` | Flytta till `sökNamn` i `Register` |
| `"Medlemmen saknas"` i varje `else` | En rad **efter** `for` |
| Hit utan `return` | Flera utskrifter / konstigt flöde |
| `m.namn` | `m.getNamn()` — muren står |
| `==` på strängar | `equalsIgnoreCase` |
| Glömd `nextLine` efter `nextInt` | Tomt namn |
| `break`-switch | Byt till `case n ->` |
| Factory / arv / README-frågor “för säkerhets skull” | NOLL SPILL — senare paket / annan exam |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför sök-loop i `Main` är fel rum.  
2. Skillnad hit (`println` + `return`) vs miss (efter `for`).  
3. Varför `nextLine()` efter `nextInt()`.  
4. Exam-kedjan i sex steg (två lägg till → lista → hit → miss → exit).

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
