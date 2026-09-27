# 01 — Teoriguide: Factory, sök och meny

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Du har redan `Account` med inkapsling och `AccountRegister` med en `List<Account>`. Nu ska **Main sluta föda nya konton direkt** — och **hitta rätt konto** innan insättning eller uttag. Sedan kopplar du ihop allt med en meny. Det är inte magi. Det är factory + linjär sökning + samma loop du lärde dig i vecka 38.

**Förutsättning:** [10-inkapsling](../10-inkapsling/) (`private`, konstruktor, getters, lista i register). [09-transaktioner](../../vecka-39/09-transaktioner/) (`deposit` / `withdraw`). [04-loopar-meny](../../vecka-38/04-loopar-meny/) (`while`, `Scanner`). Här: **factory**, **`findAccount`**, **meny 1–5**. Inget arv. Ingen Git.

---

## Problemet först — `new Account` i `Main` sprider kaos

Många tänker: “Menyn ska skapa konto — då skriver jag väl `new Account` i `Main`?” Andas. Det **kompilerar**. Men du får två hål i väggen:

1. **`new` utan `add`** — kontot finns i minnet men **inte** i listan. `printAll` visar det inte.  
2. **`new` på flera ställen** — Exam 1 README Q2 frågar var objekten skapas. Utspritt `new` i `Main` = fel svar.

**Dåligt läge:**

```java
// Main.java — trasigt mönster
AccountRegister register = new AccountRegister();

Account alva = new Account("Alva", 200);
register.addAccount(alva);           // väg 1 — funkar om add finns

Account ghost = new Account("Bo", 50);  // väg 2 — aldrig add
ghost.deposit(10);                      // Bo finns inte i listan

register.printAll();  // bara Alva syns — Bo är spöke
```

Koden **kör**. Men registret och verkligheten divergerar. Factory flyttar **all** skapelse till **en** metod som både `new`:ar **och** `add`:ar.

---

## Tre filer — vem gör vad

| Fil | Ansvar | INTE |
|-----|--------|------|
| `Account.java` | Data + `deposit` / `withdraw` | Lista, meny, `new` från användarval |
| `AccountRegister.java` | `List<Account>`, `createAccount`, `findAccount`, `printAll` | `Scanner`, menytext |
| `Main.java` | Meny-loop, läsa val, anropa register | `new Account`, direkt `accounts.add` |

**Målsvar (säg högt / skriv i README):**  
*“Main styr flödet. AccountRegister äger listan och skapandet. Account gör transaktioner på sig själv.”*

---

## `List<Account>` — samma lista, rätt deklarationstyp

**Metafor:** Postfacket i receptionen. På skylten står **“Lista av konton”** (`List<Account>`). Inuti ligger en `ArrayList` — men dörren utåt heter `List`.

**Vad det är:** Fält i `AccountRegister`:

```java
import java.util.ArrayList;
import java.util.List;

public class AccountRegister {
    private List<Account> accounts = new ArrayList<>();
}
```

**Varför `List` som typ:** Examination och kodstandard: deklarera mot **gränssnittet** `List`, skapa med `ArrayList`. Samma idé som `List<String>` i vecka 38 — idag är elementen `Account`-objekt, inte text.

**Om det saknas / vad det INTE är:** INTE lista i `Main` (listan bor i registret). INTE `ArrayList` som enda typ i fältdeklarationen om du följer kursens mönster. INTE primitiv array — du behöver `add` utan fast storlek.

---

## `findAccount(String owner)` — hitta rätt hus, inte gissa fack 0

**Metafor:** Namnskyltar på postfack. Du går fack 0, 1, 2 … tills skylten matchar. Hittar du ingen → **tomt** (`null`) — inte ett nytt konto.

**Problem först — hårdkodat index:**

```java
// Anti-mönster — gissa index 0 (i registret eller via läckt lista):
accounts.get(0).deposit(100);  // vem är fack 0 idag?
```

Nytt konto lades **först** i listan? Då fick fel person pengar. **Index är inte identitet.**

**Vad det är:** Metod i `AccountRegister` som returnerar `Account` (pekare) eller `null`.

```java
public Account findAccount(String owner) {
    for (int i = 0; i < accounts.size(); i++) {
        Account a = accounts.get(i);
        if (a.getOwner().equalsIgnoreCase(owner)) {
            return a;
        }
    }
    return null;
}
```

**Varför `getOwner()`:** Fälten är `private`. Gettern är dörren ut.  
**Varför `equalsIgnoreCase`:** `"alva"` ska hitta `"Alva"`. INTE `==` på strängar.  
**Varför `null` sist:** Ingen träff = ingen pekare. INTE `new Account("…")` i sök — **sök skapar inte**.

**Anropa säkert från `Main`:**

```java
Account found = register.findAccount(ownerName);
if (found != null) {
    found.deposit(amount);
} else {
    System.out.println("Kontot finns inte.");
}
```

Utan `null`-koll: `NullPointerException` när du anropar `found.deposit(...)`.

**Målsvar (säg högt / skriv i README) — sök:**  
*“findAccount loopar, jämför ägare, returnerar objekt eller null. Jag kollar null innan deposit eller withdraw.”*

---

## Factory — `createAccount` är enda dörren för `new`

**Metafor:** Fabriksporten. Alla nya konton lastas på samma lastkaj: validera (senare), **`new`**, **`add`**. Main står utanför och **beställer** — bygger inte själv.

**Problem först — två sätt att skapa:**

```java
// Main — FEL mot Exam
Account a = new Account("Alva", 100);
register.addAccount(a);   // glömmer någon? extra new någon annanstans?

Account b = new Account("Bo", 50);
b.deposit(5);             // aldrig add — spöke
```

**Vad det är:**

```java
public void createAccount(String owner, double startBalance) {
    Account account = new Account(owner, startBalance);
    accounts.add(account);
}
```

**Varför:** En plats för `new Account` → README Q2. Varje skapat konto hamnar i listan. Main säger bara **vem** och **startsaldo**.

**Main efter factory:**

```java
register.createAccount("Alva", 200);
register.createAccount("Bo", 50);
// Sök i Main efter "new Account" — ska vara noll träffar
```

**Om det saknas / vad det INTE är:** INTE factory i `Account`. INTE `findAccount` som skapar. INTE `SavingsAccount` (kommer i nästa paket). INTE Git-krav i den här övningen.

**Målsvar (säg högt / skriv i README) — factory:**  
*“new Account står bara i createAccount i AccountRegister. Main anropar createAccount så listan och skapandet hänger ihop.”*

---

## Meny i `Main` — loop, `Scanner`, val 1–5

**Metafor:** Bankomat som frågar om och om igen tills du trycker avsluta. Varje val är ett **uppdrag** till registret eller ett konto — inte ny arkitektur.

**Meny (Exam 1 — svensk text, engelska klassnamn):**

| Val | Handling |
|-----|----------|
| 1 | Skapa konto (`owner`, startsaldo) → `createAccount` |
| 2 | Lista alla → `printAll` |
| 3 | Sätt in (`owner`, belopp) → `findAccount` → `deposit` |
| 4 | Ta ut (`owner`, belopp) → `findAccount` → `withdraw` |
| 5 | Avsluta — lämna loopen |

**Skelett:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        AccountRegister register = new AccountRegister();
        Scanner scanner = new Scanner(System.in);
        int choice = 0;

        while (choice != 5) {
            System.out.println("1. Skapa konto");
            System.out.println("2. Lista konton");
            System.out.println("3. Sätt in pengar");
            System.out.println("4. Ta ut pengar");
            System.out.println("5. Avsluta");
            System.out.print("Val: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1 -> {
                    System.out.print("Ägare: ");
                    String owner = scanner.nextLine();
                    System.out.print("Startsaldo: ");
                    double start = scanner.nextDouble();
                    register.createAccount(owner, start);
                }
                case 2 -> register.printAll();
                case 3 -> { /* owner + amount, findAccount, deposit */ }
                case 4 -> { /* owner + amount, findAccount, withdraw */ }
                case 5 -> System.out.println("Hej då.");
                default -> System.out.println("Ogiltigt val.");
            }
        }
        scanner.close();
    }
}
```

**Scanner — text efter tal:** Efter `nextInt()` / `nextDouble()` ligger Enter kvar. Innan `nextLine()` för ägarnamn: ofta en **extra** `nextLine()` som slänger radbrytningen (samma mönster som vecka 38).

**Switch expression:** `switch (choice) { case 1 -> { … } … }` är OK i modern Java (21). `if` / `else if` fungerar också — välj det du kan förklara.

**Stegkedja (Exam README Q3) — exempel val 3:**

1. Användaren väljer 3 och skriver ägare + belopp.  
2. `Main` anropar `findAccount(owner)`.  
3. Träff → `deposit(amount)` på **det** objektet.  
4. Konsolen visar ev. bekräftelse / uppdaterat saldo vid lista.

**Målsvar (säg högt / skriv i README) — meny:**  
*“Main läser val. Registret skapar eller söker. Transaktionen körs på objektet som findAccount returnerade.”*

---

## `printAll` — loopa listan (påminnelse)

```java
public void printAll() {
    for (int i = 0; i < accounts.size(); i++) {
        Account a = accounts.get(i);
        System.out.println(a.getOwner() + ": " + a.getBalance());
    }
}
```

Tom lista → inga rader (OK). Efter två `createAccount` ska du se **två** rader.

---

## Testkedja innan Exam — två konton, insättning, stoppat uttag

Kör via menyn (inte bara hårdkodat i `main`):

1. Skapa konto 1 (t.ex. Alva, 200).  
2. Skapa konto 2 (t.ex. Bo, 80).  
3. Lista — **två** rader.  
4. Sätt in på Alva — saldo ökar.  
5. Ta ut mer än Bos saldo — **meddelande**, saldo **oförändrat** ([09-transaktioner](../../vecka-39/09-transaktioner/)).

**Målsvar (säg högt / skriv i README) — helheten:**  
*“Factory skapar. Sök hittar. Menyn kopplar användaren till rätt metod på rätt objekt.”*

---

## Metod — när du tvekar

1. **Skapa konto?** → `createAccount` — aldrig `new Account` i `Main`.  
2. **Hitta konto?** → `findAccount` — aldrig gissa `get(0)`.  
3. **Ändra saldo?** → `deposit` / `withdraw` på **returnerad** pekare, efter `null`-koll.  
4. **Lista?** → `printAll` i registret.  
5. **Sök i projektet:** `new Account` ska bara träffa `createAccount` (eller konstruktorn internt).

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| `new Account` kvar i `Main` | Flytta till `createAccount`; Main anropar bara |
| `createAccount` utan `add` | Kontot syns inte i lista |
| `get(0).deposit` | Sök på ägare — index skiftar |
| `a.equalsIgnoreCase(owner)` | `Account` har inte det — `a.getOwner().equalsIgnoreCase(owner)` |
| Glömd `return null` i `findAccount` | `missing return statement` |
| `deposit` utan null-koll | NPE vid miss |
| Lista i `Main` | Listan bor i `AccountRegister` |
| `SavingsAccount` / arv "för säkerhets skull" | Nästa paket — NOLL SPILL här |
| Git / README i övning 1–2 | README-träning = stretch i README-filen här |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Varför `new Account` i `Main` är dåligt för Exam Q2.  
2. Skillnad `findAccount` träff vs miss (`null`).  
3. Stegkedja för menyval 4 i fem korta steg.  
4. Vad som händer om du glömmer `accounts.add` i `createAccount`.

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
