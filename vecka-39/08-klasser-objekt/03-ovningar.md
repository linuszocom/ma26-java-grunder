# 03 — Övningar

**Omfång det här paketet:** `Account.java` med fält `owner` (`String`) och `balance` (`double`). Skapa objekt med `new` i `Main.java`. Sätt fält. Skriv ut fält. Engelska namn. **Ingen** `deposit` / `withdraw`. **Ingen** `private`, konstruktor, factory eller `ArrayList`. **Ingen** Git krävs här.

AI får föreslå rader. Du måste kunna **peka och förklara** klass vs objekt, `new`, punktnotation och varför filen heter `Account.java`.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK. Lägg `Account.java` och `Main.java` i samma `src` (eller samma paket). Kör `Main` och läs **konsolen**.

---

## Uppgift 1 — Från lösa variabler till `Account` (problem-först)

**Mål:** Se varför lösa `owner`/`balance`-par i `main` inte räcker — skapa klassen `Account` och ett objekt i stället.

**Scenario / startläge:** Gymmet “PulseHall” sparar medlemskredit som **lösa variabler**. Det funkar för en person — men Exam 1 kräver en **`Account`-klass**. Din jobb: samma data, men som **klass + objekt**.

**Trasig / lös startkod** (kopiera till `Main.java` först — kör gärna en gång):

```java
public class Main {
    public static void main(String[] args) {
        String owner = "Alex";
        double balance = 350.0;

        System.out.println(owner);
        System.out.println(balance);
    }
}
```

**Krav:**
1. Skapa filen **`Account.java`** med `public class Account` och fälten `String owner;` och `double balance;` (inga metoder behövs).
2. I `main`: skapa **ett** objekt med `Account card = new Account();`.
3. Sätt `card.owner` och `card.balance` till samma värden som ovan (`"Alex"`, `350.0`).
4. Ta bort de lösa variablerna `owner` / `balance` i `main` — data ska bo **på objektet**.
5. Skriv ut **fälten** med `System.out.println` (minst ägare och saldo på varsin rad eller samma rad).

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

`Account.java`:

```java
public class Account {
    String owner;
    double balance;
}
```

`Main.java`:

```java
public class Main {
    public static void main(String[] args) {
        Account card = new Account();
        card.owner = "Alex";
        card.balance = 350.0;

        System.out.println(card.owner);
        System.out.println(card.balance);
    }
}
```

Konsol: `Alex` och `350.0` (eller `350`).

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på **filen** `Account.java` — matchar `public class Account`?  
- [ ] Peka på **fälten** i klassen — inte lokala variabler i `main`  
- [ ] Peka på **`new Account()`** — var skapas objektet?  
- [ ] Peka på **punktnotation** (`card.owner`) — varför behövs den?  
- [ ] Förklara **varför** lösa `String owner` i `main` inte är samma sak som klassen `Account`  
- [ ] Programmet kompilerar och skriver ut rätt värden

**Ägarskap:** AI ok som bollplank — du ska kunna säga högt: “klassen är mallen, card är objektet”.

---

## Uppgift 2 — Två objekt, egna fält

**Mål:** Skapa **två** `Account`-objekt, ge dem olika `owner` / `balance`, och bevisa att de är oberoende.

**Brief:** Biljettkassan “GateNine” har två förköp: ett till Mira (420 kr kvar i tillgodohavande) och ett till Noel (90 kr). Samma klass, två instanser.

**Krav:**
1. Återanvänd din `Account`-klass från uppgift 1 (inga nya fält).
2. I `main`: skapa **två** objekt (t.ex. `ticketMira` och `ticketNoel`) med **var sitt** `new Account()`.
3. Sätt:
   - Mira: `owner = "Mira"`, `balance = 420.0`
   - Noel: `owner = "Noel"`, `balance = 90.0`
4. Skriv ut **båda** objektens fält (tydliga etiketter i texten hjälper, t.ex. `"Mira: …"`).
5. Ändra **bara** Miras saldo till `380.0`. Skriv ut **igen** — Noels saldo ska vara **oförändrat** (`90.0`).
6. Gör **en** medveten “fel-utskrift”: `System.out.println(ticketMira);` en gång. Notera vad som syns (ofta `Account@…`). Skriv en mening i Docs: *varför det inte är namnet Mira*.

**Exempel på rimlig konsol** (efter ändringen):

```
Mira: 380.0
Noel: 90.0
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på **två** `new` — två instanser  
- [ ] Peka på raden som ändrar **bara** Miras `balance`  
- [ ] Förklara **varför** Noel inte följde med  
- [ ] Förklara vad `println(ticketMira)` visar — och varför du skriver ut **fält** till vardags  
- [ ] Bekräfta: ingen `deposit`, ingen lista, ingen konstruktor

**Ägarskap:** Du ska kunna rita (eller säga) “två lådor, två saldon” utan att titta i teoriguiden.

---

## Uppgift 3 — Stretch (valfritt)

Skapa ett **tredje** `Account` (t.ex. gymkort för `"Eden"` med `balance = 0.0`). Skriv ut alla tre ägare i en radsekvens. Byt sedan bara det tredje saldot till `50.0` och verifiera att de två första är orörda.

**Klart-check:** Tre `new`, tre egna `balance` — peka och säg det högt.

---

## När du kört fast

1. *cannot find symbol: class Account* → filen saknas, fel namn, eller fel mapp/paket.  
2. *class Account is public, should be declared in a file named Account.java* → döp om filen.  
3. *NullPointerException* på `.owner` → du glömde `new` innan punkten.  
4. Konsolen visar `Account@1a2b3c` i stället för namn → du skrev ut objektet, inte fälten.  
5. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
6. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
