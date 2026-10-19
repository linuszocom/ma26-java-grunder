# 01 — Teoriguide: Lista i Register (`läggTill` + `listaAlla`)

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du har tre rum från [15-tre-klasser](../../vecka-42/15-tre-klasser/): `Medlem` (ett arkivkort), `Register` (tomt), `Main` (start). Nu fylls **kartoteklådan**. Listan av medlemmar bor **i** `Register`. `Main` skapar kort och ber lådan *stoppa in* och *bläddra* — aldrig håller själva lådan i fickan. Det är inte magi. Det är `List` + `läggTill` + `listaAlla`.

**Förutsättning:** `Medlem` med `private`, konstruktor, `getNamn` / `getMedlemsnummer`. Tom `Register` som fil. Här: **lista i Register**, två hardkodade medlemmar, utskrift. Ingen sök. Ingen meny. Ingen `Scanner`.

---

## Problemet först — listan i expeditionen

Många tänker: “Jag kan redan `ArrayList` — då lägger jag listan i `Main`.” Andas. Det **kompilerar**. Men Examination 2 frågar: *var ligger listan?* Rätt svar är **`Register.java`**.

**Dåligt läge** — föreningen **“Nordljus”** stoppar alla arkivkort i expeditionsfickan:

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Medlem> medlemmar = new ArrayList<>();  // FEL RUM
        medlemmar.add(new Medlem("Kim", 101));
        medlemmar.add(new Medlem("Moa", 102));
        for (Medlem m : medlemmar) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
        }
    }
}
```

Konsolen kan visa Kim och Moa. Ändå: `Register` är fortfarande tom. Du pekar fel fil när exam kräver listan i registret.

**Målsvar (säg högt / skriv i README):**  
*“Listan hör hemma i Register. Om den ligger i Main pekar jag fel rum.”*

---

## Kartoteklådan — metafor

**Metafor:** I klubbens expedition står en **kartoteklåda** (`Register`). Varje **arkivkort** är en `Medlem` (namn + nummer bakom plast). På lådans skylt står **“Lista av medlemmar”** (`List<Medlem>`). Inuti ligger en `ArrayList` — men skylten utåt heter `List`. **Expeditionsfönstret** (`Main`) lämnar in kort och ber om utskrift. Fönstret **äger inte** lådan.

**Vad det är:** Ett fält `private List<Medlem> medlemmar` **inuti** `Register`.  
**Varför det finns:** Samlingen av objekt ska ha **en ägare**. Exam 2 låser listan till registret.  
**Om det saknas / vad det INTE är:** INTE lista i `Main`. INTE `public List` som läcker ut. INTE sök eller meny idag.

| Fil | Ansvar idag | Hör **inte** hit idag |
|-----|-------------|------------------------|
| `Medlem.java` | Ett arkivkort (redan byggt) | Lista, `läggTill` |
| `Register.java` | Lådan: fält + `läggTill` + `listaAlla` | `sökNamn`, `Scanner`, meny |
| `Main.java` | `new Register`, skapa `Medlem`, anropa metoder | Äga `List`, `medlemmar.add` direkt |

---

## `List` vs `ArrayList` — skylt och innehåll

**Metafor:** Skylten på lådan säger **Lista**. Det du *stoppar in* är en konkret `ArrayList`. Kursens kodstandard: deklarera mot **`List`**, skapa med **`new ArrayList<>()`**.

```java
import java.util.ArrayList;
import java.util.List;

public class Register {
    private List<Medlem> medlemmar = new ArrayList<>();
}
```

**Vad det är:**  
- `List<Medlem>` = **deklarerad typ** (fältet).  
- `new ArrayList<>()` = **skapandet** (tom låda vid `new Register()`).

**Varför:** Examination och kodstandard — interface utåt, implementation inuti. Samma grepp som `List<Account>` i Kontoappen, nu med svenska `Medlem`.

**Om det saknas / vad det INTE är:**  
- INTE `private ArrayList<Medlem> medlemmar` som deklarerad typ (fungerar tekniskt — följer **inte** kursmönstret).  
- INTE raw `ArrayList` utan `<>`.  
- INTE att du måste kunna alla `List`-implementationer — bara mönstret ovan.

**Import:** Både `java.util.List` och `java.util.ArrayList`. Glömmer du `List` → *cannot find symbol: class List*.

**Målsvar (säg högt / skriv i README):**  
*“Fälttypen är List av Medlem. Jag skapar med new ArrayList. Jag deklarerar inte fältet som ArrayList.”*

---

## Tom låda efter `new Register()`

```java
Register register = new Register();
// medlemmar finns — size 0. listaAlla skriver inga rader ännu.
```

**Vad det är:** Fältet skapas med listan. Den är **tom** tills någon anropar `läggTill`.  
**Varför det spelar roll:** Tom konsol efter `listaAlla` betyder “inga kort ännu” — inte “fältet saknas”.  
**Vad det INTE är:** INTE att du behöver `Scanner` för att skapa lådan. INTE att fältet “inte finns” för att utskriften är tom.

---

## `läggTill` — stoppa in ett kort

**Metafor:** Receptionisten tar emot ett arkivkort och **lägger det i lådan**. Utifrån anropar du `register.läggTill(...)` — du gräver **inte** i `medlemmar` från `Main` (fältet är `private`).

```java
public void läggTill(Medlem m) {
    medlemmar.add(m);
}
```

**Vad det är:** Metod i `Register` som tar emot en `Medlem` och anropar `add` **inuti** klassen.  
**Varför den finns:** Enda dörren in när listan är `private`. Exam 2: lägg till medlemmar via registret.  
**Om den saknas / vad den INTE är:** INTE `register.medlemmar.add(...)` från `Main`. INTE factory/`createMedlem` (utanför paketet). INTE sök.

Från `Main`:

```java
register.läggTill(new Medlem("Kim", 101));
register.läggTill(new Medlem("Moa", 102));
```

**Målsvar (säg högt / skriv i README):**  
*“läggTill tar emot en Medlem och gör add inuti Register. Main anropar metoden — inte listan direkt.”*

---

## `listaAlla` — bläddra och skriv ut

**Metafor:** Du drar ut lådan och **läser varje kort högt** — namn och nummer. Du ger inte bort hela lådan till fönstret.

```java
public void listaAlla() {
    for (Medlem m : medlemmar) {
        System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
    }
}
```

**Vad det är:** Loop över listan. Utskrift via **getters** (muren på `Medlem` finns kvar).  
**Varför:** Exam 2 kräver lista alla med namn + nummer.  
**Om det saknas / vad det INTE är:** INTE `sökNamn` (senare paket). INTE att returnera listan som `public`. INTE `m.namn` (private).

**for-each:** `for (Medlem m : medlemmar)` = ett kort i taget. Du behöver **inte** index för den här utskriften.

Efter två `läggTill` + `listaAlla` ska konsolen visa ungefär:

```text
Kim 101
Moa 102
```

**Målsvar (säg högt / skriv i README):**  
*“listaAlla loopar medlemmar och skriver getNamn plus getMedlemsnummer. Jag pekar listfältet i Register, inte i Main.”*

---

## Hela `Register` — målbild

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

---

## `Main` idag — två kort, ingen egen lista

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

**Vad `Main` får ha:** En `Register`-referens. Skapa `Medlem` med `new`. Anropa `läggTill` / `listaAlla`.  
**Vad `Main` INTE får ha idag:** `List<Medlem>`, `ArrayList`, `.add` på listan, sök-loop, meny, `Scanner`.

---

## Exam-förebåd — “Var ligger listan?”

När Examination 2 (eller en muntlig fråga) lyder *var ligger listan?* svarar du med **pekning**:

1. Öppna `Register.java`.  
2. Peka på `private List<Medlem> medlemmar`.  
3. Säg: *Main anropar bara metoder.*

Det är **list-delen** av Exam 2. Sök och meny kommer i nästa paket.

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| `List` / `ArrayList` i `Main` | Flytta fältet till `Register` |
| `private ArrayList<Medlem> …` som typ | Byt deklaration till `List<Medlem>` |
| `register.medlemmar.add(...)` | Fältet är private → `läggTill` |
| Glömmer `import java.util.List` | Importera både `List` och `ArrayList` |
| `listaAlla` utan `läggTill` först | Tom konsol — förväntat tills du stoppat in kort |
| `m.namn` i loopen | Använd `getNamn()` / `getMedlemsnummer()` |
| `sökNamn` / meny / `Scanner` “för att bli klar” | Utanför det här paketet |
| Factory / `createMedlem` | Inte krav här — `new Medlem` + `läggTill` räcker |

---

## Metod — när du tvekar

1. **Var ska listan bo?** → `Register` (private fält).  
2. **Vilken typ på fältet?** → `List<Medlem> = new ArrayList<>()`.  
3. **Stoppa in medlem?** → `läggTill` → `add` inuti.  
4. **Skriv ut alla?** → `listaAlla` → for-each + getters.  
5. **Vad gör Main?** → `new Register`, två `läggTill`, `listaAlla`.  
6. **AI lade listan i Main?** → Stryk. Flytta till Register.

**Målsvar (säg högt / skriv i README) — helhet:**  
*“Register äger private List av Medlem. läggTill addar. listaAlla skriver namn och nummer. Main har ingen egen lista — jag pekar fältet i Register.”*

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför listan **inte** ska ligga i `Main`.  
2. Skillnad `List` (deklaration) vs `ArrayList` (skapande).  
3. Vad `läggTill` gör med parametern.  
4. Vad `listaAlla` skriver ut — och via vilka metoder.  
5. Exam-svar i en mening: *var ligger listan?*

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
