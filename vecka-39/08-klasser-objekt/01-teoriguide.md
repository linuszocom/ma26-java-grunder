# 01 — Teoriguide: Klass, objekt och fält

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **lösa variabler** i `main` — sedan samlar vi dem i en klass och skapar **objekt** med `new`. Det är inte magi. Det är mall, instans, fält och punktnotation. **Ingen** `deposit` / `withdraw` här. **Ingen** `private` eller konstruktor.

---

## Problemet först — lösa variabler i `main`

Många tänker: “Klasser… det är väl bankappar och arv?” Andas. Idag är det **en fil som beskriver en sak**, och **`new` som skapar en konkret sak i minnet**.

**Dåligt läge** — två konton som lösa variabler:

```java
public class Main {
    public static void main(String[] args) {
        String owner1 = "Alex";
        double balance1 = 500.0;

        String owner2 = "Sam";
        double balance2 = 1200.0;

        System.out.println(owner1);
        System.out.println(balance1);
        System.out.println(owner2);
        System.out.println(balance2);
    }
}
```

Koden **kör** — men du har ingen typ som heter “konto”. Ägare och saldo hör ihop i verkligheten, men i koden är de **lösa namn**. När Exam 1 kräver `Account.java` räcker det inte med `owner1` / `balance1`. Du behöver en **klass** och **objekt**.

---

## Klass — mall / typ

**Metafor:** Ett **gymkort-formulär** från gymmet. Formuläret säger: varje medlemskort ska ha **namn** och **saldo** (kredit kvar). Formuläret i sig är inte ett kort du swipar — det är mallen.

**Vad det är:** En **klass** = namngiven typ i en `.java`-fil. Här: `public class Account` i filen `Account.java`.  
**Varför den finns:** Du vill beskriva *vad ett konto är* en gång — fält som hör ihop — och sedan skapa många konkreta konton.  
**Om den saknas / vad den INTE är:** INTE samma sak som ett objekt. INTE `Main`. INTE en metod. Klassen **håller inte** “Alex saldo” — det gör varje **objekt**.

**Målsvar (säg högt / skriv i README):**  
*“Klassen Account är mallen. Den ligger i Account.java och beskriver vilka fält ett konto har. Själva kontot skapas först när jag skriver new.”*

### Minsta klass — bara fält

```java
// Fil: Account.java
public class Account {
    String owner;
    double balance;
}
```

**Vad det visar:** Två **fält** (data som hör till varje framtida objekt). Inga metoder än. Fälten får vara utan `private` i det här paketet — du ska kunna sätta och läsa dem direkt.  
**Kom ihåg / INTE:** Lägg **inte** `main` inuti `Account` idag. `main` bor i `Main.java`.

---

## Filnamn måste matcha klassen

**Vad det är:** `public class Account` → filen **måste** heta `Account.java` (samma mapp/paket som `Main.java` i nybörjarprojekt).  
**Varför det finns:** Java kräver att publika klassnamn och filnamn stämmer.  
**Om det saknas / vad det INTE är:** INTE “nästan rätt” (`account.java`, `Accounts.java`, `Konto.java`). Fel namn → kompileringsfel. Svenska klassnamn (`Konto`) hör **inte** till Exam 1.

```text
src/
  Main.java      ← public class Main
  Account.java   ← public class Account
```

**Målsvar (säg högt / skriv i README) — fil:**  
*“public class Account måste ligga i Account.java. Fel filnamn stoppar kompileringen.”*

---

## Objekt — konkret instans efter `new`

**Metafor:** Du **skriver ut** ett gymkort från formuläret. Nu finns ett **verkligt kort** i din plånbok. Nästa medlem får ett **annat** kort från samma formulär — samma fält, andra värden.

**Vad det är:** Ett **objekt** (instans) = konkret `Account` i minnet. Du skapar det med **`new Account()`**.  
**Varför det finns:** Klassen är typen; objektet är *en* sak du kan fylla och skriva ut.  
**Om det saknas / vad det INTE är:** INTE “två klassfiler för två konton”. INTE att klassen redan har ett saldo. Utan `new` pekar variabeln **ingenstans** — `NullPointerException` när du tar punkten.

```java
Account gym = new Account();
```

**Vad raden gör:**
1. `Account gym` — deklarerar en variabel av typen `Account`.
2. `new Account()` — skapar **ett** objekt i minnet.
3. `=` — låter `gym` peka på det objektet.

**Målsvar (säg högt / skriv i README) — objekt:**  
*“Ett objekt är en instans. new Account() bygger den i minnet. Variabeln gym pekar på den instansen.”*

---

## Fält — owner och balance

**Metafor:** På biljetten till en konsert står **köparens namn** och **pris**. Det är inte två lösa lappar — det är två rutor **på samma biljett**.

**Vad det är:** **Fält** = data som hör till objektet. Exam 1 (och det här paketet): minst `owner` (`String`) och `balance` (`double` eller `int`) — **engelska namn**.  
**Varför de finns:** Ett konto *har* ägare och saldo. Du läser/skriver dem med **punkt**: `objekt.fält`.  
**Om de saknas / vad de INTE är:** INTE lokala variabler i `main` (`String owner1`). INTE samma värde för alla objekt automatiskt — varje objekt har **egna** fältvärden.

```java
Account gym = new Account();
gym.owner = "Alex";
gym.balance = 500.0;

System.out.println(gym.owner);    // Alex
System.out.println(gym.balance);  // 500.0
```

**Målsvar (säg högt / skriv i README) — fält:**  
*“owner och balance är fält på objektet. Jag sätter dem med punkt efter new, och skriver ut fälten — inte bara variabelnamnet.”*

---

## Skriv ut fält — inte hela objektet

```java
System.out.println(gym);           // oftast något i stil med Account@1a2b3c
System.out.println(gym.owner);     // Alex
System.out.println(gym.balance);   // 500.0
```

**Vad det är:** `println(objekt)` visar oftast **typ + adress**, inte “Alex / 500”.  
**Varför:** Objektet är en låda — du måste öppna luckorna (`owner`, `balance`) för att se innehållet.  
**Om saknas / INTE:** Tro inte att `println(gym)` är “fel program” — det är förväntat. Skriv ut **fälten**.

**Målsvar (säg högt / skriv i README) — utskrift:**  
*“println på objektet ger inte ägare och saldo. Jag skriver ut gym.owner och gym.balance.”*

---

## Två objekt — samma klass, egna värden

```java
Account a = new Account();
a.owner = "Alex";
a.balance = 500.0;

Account b = new Account();
b.owner = "Sam";
b.balance = 1200.0;

a.balance = 800.0;   // ändrar bara a

System.out.println(a.balance);  // 800.0
System.out.println(b.balance);  // 1200.0 — oförändrat
```

**Vad det visar:** Två `new` → två instanser. Ändrar du `a` följer **inte** `b` med.  
**Kom ihåg / INTE:** Det är INTE två klassfiler. Det är INTE samma objekt med två namn (om du inte tilldelar `b = a` medvetet).

**Målsvar (säg högt / skriv i README) — två objekt:**  
*“Samma klass, två new, två egna saldon. Ändrar jag det ena objektet rör jag inte det andra.”*

---

## Main skapar — Account beskriver

```java
// Fil: Main.java
public class Main {
    public static void main(String[] args) {
        Account card = new Account();
        card.owner = "Alex";
        card.balance = 500.0;
        System.out.println(card.owner + " / " + card.balance);
    }
}
```

**Ansvar:**
| Fil | Jobb idag |
|-----|-----------|
| `Account.java` | Klassen + fälten |
| `Main.java` | `new`, sätta fält, skriva ut |

**Kom ihåg / INTE:** Du behöver **inte** `deposit`, `withdraw`, `private`, konstruktor eller `ArrayList` i det här paketet. Det kommer i senare mappar.

---

## Klass vs objekt — när du tvekar

Det är inte magi. Fyra steg:

1. **Hör data ihop?** → Klass med fält (`Account` + `owner` / `balance`).  
2. **Ny fil** `Account.java` — namn matchar `public class Account`.  
3. **`new Account()`** innan du tar punkten.  
4. **Skriv ut fälten** (`konto.owner`, `konto.balance`).

**Målsvar (säg högt / skriv i README) — helheten:**  
*“Klassen är mallen i Account.java. new skapar objektet. Fälten sätter jag med punkt. Utskrift = fält, inte bara variabeln.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Allt i lösa `owner1` / `balance1` | Samla i `Account` — det Exam 1 kräver |
| `Account` inuti `Main.java` som inre klass “för enkelt” | Separat fil `Account.java` — öva Exam 1-strukturen |
| Fil `account.java` eller `Konto.java` | `Account.java` + engelska namn |
| `Account x;` utan `new` sen `x.owner = ...` | `NullPointerException` — skapa med `new` först |
| `println(x)` och förvänta “Alex” | Skriv ut `x.owner` och `x.balance` |
| Tro att två objekt delar saldo | Två `new` → två egna fält |
| Lägga till `deposit` / `private` / konstruktor nu | Nästa paket / senare veckor — håll dig till fält + `new` |
| `ArrayList<Account>` för tidigt | Ett eller två objekt med egna variabler räcker |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Skillnad **klass** vs **objekt** — en mening vardera.  
2. Varför `Account.java` måste heta så.  
3. Vad `new Account()` gör.  
4. Varför `println(konto)` inte räcker.  
5. Hur det här är första steget mot Exam 1:s `Account.java` (utan metoder än).

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
