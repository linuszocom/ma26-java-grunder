# 01 — Teoriguide: Villkor och logik

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när programmet alltid gör samma sak — oavsett om spelpoängen räcker eller temperaturen är farlig. Sedan bygger vi frågor som väljer väg. Det är inte magi. Det är `if`. Ingen loop. Ingen `Scanner`. Bara `main` och hårdkodade värden.

---

## Problemet först — “samma utskrift varje gång”

Många tänker nu: “Jag har redan variabler — räcker inte det?” Andas. Variabler **lagrar**. Villkor **väljer** vad som ska hända utifrån värdet.

**Dåligt läge:**

```java
int score = 850;
System.out.println("Bonus unlocked!");
System.out.println("Keep grinding!");
```

Spelaren har 200 poäng. Samma två rader skrivs ändå. Programmet **frågade aldrig** om 850 räcker.

**Bättre:** ställ en fråga som blir `true` eller `false`, och kör bara rätt block.

---

## `if` — trafikljuset i koden

**Metafor:** Ett trafikljus vid en korsning. Frågan är grönt eller rött. Grönt → du kör rakt fram. Rött → du tar annan väg (`else`) eller stannar.

**Vad det är:** `if (fråga) { … }` — parentesen **måste** bli `boolean`. Koden inuti klamrarna körs **bara** om frågan är `true`.  
**Varför det finns:** Samma program ska bete sig olika beroende på data — utan att du skriver två separata program.  
**Om det saknas / vad det INTE är:** INTE en loop (inget upprepas). INTE tilldelning. Utan `if` kör du alltid samma rader.

```java
int score = 850;
if (score >= 800) {
    System.out.println("Bonus unlocked!");
}
System.out.println("Keep grinding!");
```

**Målsvar (säg högt / skriv i README):**  
*“Ett `if` är en fråga som blir true eller false. Programmet tar bara grenen där svaret är true — annars hoppar det över eller tar `else`.”*

---

## `else` — när frågan är false

**Vad det är:** `else { … }` direkt efter ett `if`-block — körs när frågan blev `false`.  
**Varför det finns:** Du behöver ett tydligt “annars”-svar, inte tystnad.  
**Om det saknas:** Programmet gör ingenting i false-fallet — ibland räcker det, ibland glömmer du att hantera andra fallet.

```java
double tempC = -4.0;
if (tempC <= 0) {
    System.out.println("Frost — ta in känsliga växter.");
} else {
    System.out.println("Ingen frostvarning.");
}
```

---

## Jämförelser — operatorerna i parentesen

Frågan inuti `if` byggs med **jämförelseoperatorer**. Resultatet är alltid `boolean`.

| Operator | Betydelse | Exempel (score = 850) |
|----------|-----------|------------------------|
| `>` | större än | `score > 900` → false |
| `<` | mindre än | `score < 100` → false |
| `>=` | större eller lika | `score >= 800` → true |
| `<=` | mindre eller lika | `score <= 800` → false |
| `==` | lika med (jämför) | `score == 850` → true |
| `!=` | inte lika med | `score != 0` → true |

**Vad det är:** Sätt att jämföra tal (eller booleans) och få true/false.  
**Varför det finns:** Utan dem kan du inte fråga “är poängen tillräcklig?” — bara “finns poängen”.  
**Om det saknas / vad det INTE är:** `==` är **inte** samma som `=` (se nedan).

**Målsvar (säg högt / skriv i README) — `=` vs `==`:**  
*“`=` tilldelar — stoppar in värde i variabeln. `==` jämför — frågar om två värden är lika. I `if` ska du nästan alltid ha `==`, inte `=`.”*

---

## `=` i `if` — det vanligaste logiska misstaget

```java
int level = 3;
if (level = 5) {   // FEL — tilldelar 5 till level, inte en jämförelse
    System.out.println("Max level");
}
```

I Java ger `level = 5` **inte** en boolean — kompilatorn klagar. Men detta **luras** ofta med booleans:

```java
boolean frostWarning = false;
if (frostWarning = true) {   // FEL — sätter frostWarning till true och går alltid in
    System.out.println("Frost!");
}
```

**Problem-först:** Du ville *fråga* om varningen är aktiv. Du *ändrade* variabeln i stället. Grenen körs nästan alltid.

**Rätt:**

```java
if (frostWarning == true) { … }   // funkar
if (frostWarning) { … }            // enklare när variabeln redan är boolean
```

---

## Klamrar `{ }` — ett block, en väg

**Vad det är:** Klamrar grupperar flera rader till **ett** block som hör till `if` eller `else`.  
**Varför det finns:** Utan klamrar gäller bara **nästa rad** — resten körs oavsett villkor.

```java
if (score >= 800)
    System.out.println("Bonus!");
    System.out.println("Alltid den här raden");  // INTE inuti if — saknar klammer
```

**Metod:** Skriv alltid `{ }` tills vanan sitter — även för en rad.

---

## `else if` — fler än två dörrar

**Metafor:** Automaten med flera knappar: “Barn”, “Ungdom”, “Vuxen”. Första knappen som matchar vinner; resten trycks aldrig.

**Vad det är:** Kedja: `if` → `else if` → `else if` → … → `else`. Java testar **uppifrån**; första **sanna** gren körs, resten hoppas över.  
**Varför det finns:** Mer än två utfall (t.ex. flera temperaturzoner) utan att skriva många fria `if`.  
**Om det saknas / vad det INTE är:** INTE flera oberoende `if` om grenerna ska vara **ömsesidigt uteslutande** — då kan flera block köras i onödan.

```java
int age = 14;
if (age < 13) {
    System.out.println("Barnbiljett");
} else if (age < 18) {
    System.out.println("Ungdomsbiljett");
} else {
    System.out.println("Vuxenbiljett");
}
```

---

## Logiska operatorer — `&&`, `||`, `!`

Ibland räcker en jämförelse inte. Du behöver **kombinera** frågor.

| Operator | Namn | Regel |
|----------|------|-------|
| `&&` | OCH | Båda måste vara true |
| `\|\|` | ELLER | Minst en måste vara true |
| `!` | INTE | Vänder true ↔ false |

**Exempel — spelbonus kräver båda:**

```java
int score = 920;
boolean dailyQuestDone = true;
if (score >= 800 && dailyQuestDone) {
    System.out.println("Dubbel bonus!");
}
```

**Exempel — fri frakt om medlem ELLER order över gräns:**

```java
boolean isMember = false;
double orderTotal = 749.0;
if (isMember || orderTotal >= 500) {
    System.out.println("Fri frakt");
}
```

**Exempel — `!`:**

```java
boolean accountLocked = false;
if (!accountLocked) {
    System.out.println("Välkommen in");
}
```

**Målsvar (säg högt / skriv i README):**  
*"`&&` kräver att båda sidor är true. `||` räcker med en true. `!` vänder — true blir false och tvärtom."*

---

## Död gren — kod som aldrig körs

**Vad det är:** En `else if`- eller `else`-gren som **aldrig** kan bli true eftersom en tidigare gren redan tar alla fall.  
**Varför det spelar roll:** Du tror programmet hanterar ett fall — men det gör det inte. Tyst bugg.

```java
int points = 50;
if (points > 0) {
    System.out.println("Poäng kvar");
} else if (points > 100) {   // DÖD GREN — om points > 100 hade första redan varit true
    System.out.println("Hög poäng");
}
```

**Metod:** Rita stege på papper. För varje gren: “Kan jag nå hit om en tidigare gren redan var true?”

**Målsvar (säg högt / skriv i README):**  
*“En död gren är kod efter ett villkor som redan täcker alla fall — den körs aldrig. Peka på ordningen i else if-kedjan.”*

---

## Metod — när du tvekar “vilken gren körs?”

Det är inte magi. Fyra steg:

1. **Skriv frågan** i parentesen — ska den bli boolean? (`==`, inte `=`)  
2. **Beräkna true/false** med hårdkodade värden (på papper)  
3. **Följ kedjan uppifrån** — första sanna vinner  
4. **Peka:** Finns död gren? Saknas `{ }`?

**Målsvar (säg högt / skriv i README) — metod:**  
*“Skriv frågan i parentesen. Peka: kan den här grenen nås? Jämför med `==`, tilldela med `=`.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| `if (x = 5)` | Tilldelning — använd `==` för jämförelse |
| Glömt klamrar — bara en rad “inuti” if | Alltid `{ }` tills vanan sitter |
| `else if` efter ett `if` som redan täcker allt | Död gren — byt ordning eller smalare fråga först |
| `if (score > 800);` med semikolon efter parentesen | Tomt if — nästa rad körs alltid |
| `&&` när du menade “eller” | Två krav vs ett av två — testa med papper |
| Loop / `Scanner` i övningen | Inte i det här paketet — hårdkodade värden i `main` |
| Egna metoder utöver `main` | Inte här — en `main` räcker |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Vad gör `if` — och vad händer när frågan är false utan `else`?  
2. Skillnad `=` och `==` i en mening  
3. När väljer du `else if` framför ett nytt fristående `if`?  
4. Vad är en död gren — hur hittar du den?

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna i IDE:n.
