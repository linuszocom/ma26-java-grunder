# 01 — Teoriguide: Variabler och datatyper

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när du skriver ut ett värde som inte finns — sedan ger vi varje värde en etikett på lagret. Det är inte magi. Det är deklaration, tilldelning och rätt typ. Ingen `if`. Ingen loop. Ingen `Scanner`. Bara `main`.

---

## Problemet först — “jag skriver ut innan platsen finns”

Många tänker nu: “Java… det är klasser och bankappar.” Andas. Idag är det **en plats i minnet** och **ett värde av rätt sort**. Du kör i **konsolen** i IDE:n.

**Dåligt läge:**

```java
public class Main {
    public static void main(String[] args) {
        System.out.println(antalPaHylla);
    }
}
```

Kompilatorn stoppar: `antalPaHylla` finns inte. Du bad konsolen titta i en hylla som aldrig märktes upp. Det är därför **deklaration** kommer före **utskrift**.

---

## Variabel — etikett på en lagerhylla

**Metafor:** Ett lager har hyllor. På varje hylla sitter en **etikett** (`antalPaHylla`, `temperatur`, `stationsNamn`). Inuti ligger **innehållet** (5, 18.5, `"Göteborg"`). Du pekar på etiketten när koden ska läsa eller byta innehåll — du skriver inte om samma siffra på tio rader.

**Vad det är:** En **variabel** = namngiven plats i minnet för ett värde.  
**Varför den finns:** Ett ställe att spara, läsa och (vid behov) uppdatera — i stället för hårdkodade tal överallt.  
**Om den saknas / vad den INTE är:** INTE utskriften i konsolen (7 på skärmen är en kopia). INTE klasser eller metoder idag. Utan variabel jagar du samma värde på flera rader.

**Målsvar (säg högt / skriv i README):**  
*“En variabel är en namngiven plats i minnet för ett värde. Etiketten är namnet. Innehållet kan bytas med tilldelning.”*

---

## Deklaration — reservera hyllan

**Vad det är:** Raden som **skapar** platsen och säger **vilken typ** innehållet får ha.

```java
int antalPaHylla;
```

**Varför den finns:** Java måste veta vilken sorts data som får ligga där — som att välja rätt hylltyp (heltalsfack, textfack, ja/nej-fack).  
**Om den saknas / vad den INTE är:** INTE samma sak som att fylla hyllan. En tom deklaration utan tilldelning ger fel om du skriver ut direkt: *variable might not have been initialized*.

---

## Tilldelning — fyll hyllan

**Vad det är:** `=` **fyller** platsen (eller byter innehåll).

```java
int antalPaHylla;
antalPaHylla = 5;
antalPaHylla = 12;   // samma hylla, nytt innehåll
```

**Varför den finns:** Programmet behöver veta *vad* som ligger på hyllan just nu.  
**Om den saknas / vad den INTE är:** INTE matematisk “lika med” i vardagsmening — det är **tilldelning**: höger sida in, vänster plats. `int antalPaHylla = 5;` på en rad gör två jobb: skapa + fylla.

**Målsvar (säg högt / skriv i README) — tilldelning:**  
*“Tilldelning med ett likamedtecken fyller variabeln. Samma namn kan få nytt värde — det är inte en ny hylla varje gång.”*

---

## System.out.println — titta i hyllan

**Vad det är:** Skriver **innehållet** till konsolen så du ser det.

```java
int antalPaHylla = 7;
System.out.println(antalPaHylla);
System.out.println(antalPaHylla);   // 7 igen — hyllan töms inte
```

**Varför den finns:** Annars körs koden tyst. Du gissar.  
**Om den saknas / vad den INTE är:** INTE samma sak som tilldelning. INTE en metod du skriver själv idag. Utskriften **ändrar inte** värdet i variabeln.

---

## Fyra datatyper — rätt hylltyp för rätt innehåll

Java är **strikt**: fel sort i fel fack → kompileringsfel (*incompatible types*).

| Typ | Vad som får ligga där | Exempel | Vanligt miss |
|-----|------------------------|---------|--------------|
| **`int`** | heltal | `42`, `0`, `-3` | `3.5` (decimal) |
| **`double`** | decimaltal | `19.90`, `0.25` | komma `19,90` — använd **punkt** |
| **`String`** | text | `"Stockholm"`, `"Hej"` | glöm citattecken |
| **`boolean`** | ja/nej | `true`, `false` | `"ja"` som text — fel fack |

**Målsvar (säg högt / skriv i README) — välj typ:**  
*“Heltal → int. Decimal → double. Text → String med citattecken. Ja/nej → boolean med true eller false.”*

### int — heltalsfacket

```java
int paket = 12;
System.out.println(paket);
```

`3.5` i `int` → nej. `"12"` (text) i `int` → nej.

### double — decimalfacket

```java
double viktKg = 2.75;
System.out.println(viktKg);
```

Pris, temperatur med decimal, procent — ofta `double`. Komma i svenska vardagsspråk; **punkt** i Java-kod.

### String — textfacket

```java
String stationsNamn = "Nordstationen";
System.out.println(stationsNamn);
```

Citattecknen `"..."` säger till Java: det här är **text**, inte ett variabelnamn.

### boolean — ja/nej-facket

```java
boolean regnAktivt = true;
System.out.println(regnAktivt);
```

Bara `true` eller `false` — små bokstäver. Inte `"true"` (det vore String).

---

## Fyra typer i samma program

Mönster du ska kunna återskapa:

```java
public class Main {
    public static void main(String[] args) {
        int antalSensorer = 4;
        double temperaturC = 18.5;
        String stationsNamn = "Väderlunden";
        boolean regnAktivt = false;

        System.out.println(antalSensorer);
        System.out.println(temperaturC);
        System.out.println(stationsNamn);
        System.out.println(regnAktivt);
    }
}
```

**Vad det visar:** Fyra etiketter, fyra typer, fyra utskrifter.  
**Varför det räcker idag:** Exam 1 bygger på att du kan hålla reda på *data* innan menyer och klasser kommer.

---

## Problem först — typfel i lagret

**Trasigt:**

```java
int temperaturC = 18.5;          // decimal i heltalsfack
String antal = 4;                // tal utan citat i textfack
boolean aktiv = "true";          // text i ja/nej-fack
double pris = 19,90;             // komma i stället för punkt
```

**Rättare tanke:** Matcha **innehåll** mot **hylltyp**. Decimal → byt till `double` eller ta bort decimalen medvetet. Text → citattecken. Boolean → `true`/`false` utan citat.

---

## Metod — när du tvekar

Det är inte magi. Fyra steg:

1. **Vilken data?** (heltal, decimal, text, ja/nej)  
2. **Deklarera** med rätt typ och tydligt namn  
3. **Tilldela** värde med `=`  
4. **Skriv ut** med `System.out.println` och läs konsolen

**Målsvar (säg högt / skriv i README) — metod:**  
*“Deklarera först, tilldela sedan, skriv ut sist. Läs felmeddelandet: cannot find symbol = platsen saknas. might not have been initialized = tom plats.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Skriva ut före deklaration | Etikett först — `int x;` eller `int x = 5;` |
| Tro att `println` tömmer variabeln | Utskrift läser bara — värdet ligger kvar |
| `"42"` när du menar tal | Citat → String. Heltal skrivs utan citat |
| `19,90` i kod | Punkt: `19.90` |
| `boolean ok = "false"` | `"false"` är text. Skriv `false` |
| Blanda `=` och `==` | Idag: bara `=` för tilldelning. `==` kommer med villkor senare |
| Egna metoder / `Scanner` / `if` | Inte i det här paketet — håll allt i `main` |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Vad är en variabel? (sikta på lagerhylla + etikett)  
2. Skillnad deklaration vs tilldelning i en mening  
3. När väljer du `int`, `double`, `String`, `boolean`?  
4. Vad gör `System.out.println` — och vad gör den **inte**?

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
