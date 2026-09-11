# 04 — AI-träning: Metoder, return & ägarskap

AI kan spotta ur sig metoder på sekunder. Det betyder inte att *du* äger parametrarna, returtypen eller anropet. Här tränar du: **fel return, saknad return, parameter-mismatch** — ändra, förklara.

Det är inte magi. Det är rätt returtyp + rätt antal argument + metod utanför `main`.

---

## Scenario — problem först

Du ber AI: *“Skriv Java med en metod som räknar rabatterat pris från ordinarie pris och rabatt i procent, och skriv ut resultatet för 500 kr med 20 % rabatt.”*  
Du får tillbaka något i stil med:

```java
public class Main {
    public static void main(String[] args) {
        double slutpris = rabatteratPris(500.0, 20.0);
        System.out.println("Slutpris: " + slutpris);
    }

    public static void rabatteratPris(double pris, double rabattProcent) {
        double faktor = 1 - rabattProcent / 100.0;
        return pris * faktor;
    }
}
```

Det *ser ut* som en metod med parametrar — men det kompilerar inte (eller beter sig fel). Svagheter:

- **`void` men `return` med värde** — javac: *unexpected return value* / returtyp matchar inte.  
- **Saknad returtyp** om AI byter till `void` och **tar bort** `return` — då får `main` inget värde att spara i `slutpris`.  
- **Parameter-mismatch** i andra varianter AI ger: `rabatteratPris(500)` (ett argument när två krävs), eller `rabatteratPris("500", 20)` (String där `double` ska).  
- **Fel returtyp:** `int rabatteratPris(...)` när uttrycket är `double`.  
- **Metod inuti `main`** — *illegal start of expression*.  
- **`return` saknas** helt i `double`-metod — *missing return statement*.  
- **`Account`, ArrayList, Scanner`** AI lägger till “för säkerhets skull” — stryk om du inte bett om det (NOLL SPILL för paketet).

**Vad du tränar:** Feedback + en version *du* kan köra i IDE:n.  
**Varför:** Examination 1 kräver metoder med parametrar och getters som **returnerar** — du måste se när AI blandar `void` och `return`.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan förklara metodhuvud och anrop.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snutten ovan) där du ber om:
- en **`static`-metod i `Main`** som tar **pris + rabattprocent** och **returnerar** slutpris (`double`);
- anrop från `main` som sparar returvärdet och skriver ut.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Returtyp **`void`** men **`return` med värde**?  
- [ ] Returtyp **`double`** men **ingen `return`**?  
- [ ] **`main` tilldelar** från `void`-metod? (`double x = voidMetod(...)`)  
- [ ] **Fel antal** argument i anrop?  
- [ ] **Fel typ** i argument (String istället för double)?  
- [ ] Metod **inuti** `main`?  
- [ ] Formeln **duplicerad** i både `main` och metod (onödig copy-paste kvar)?  
- [ ] Egna klasser, `ArrayList`, `Scanner` som du **inte** bett om?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa
Skriv en **ren version du äger** — koppla gärna till [03 — Uppgift 1](./03-ovningar.md) (`beraknaFrakt`) eller rabatt-scenario:

```java
public static double rabatteratPris(double pris, double rabattProcent) {
    double faktor = 1 - rabattProcent / 100.0;
    return pris * faktor;
}
```

Anropa med t.ex. `500.0` och `20.0`. Spara i ditt Java-projekt. **En** formel i metoden — inte kvar i `main`.

### Steg 4 — Andra AI-felet (parameter-mismatch)
Be AI igen om en **`kmTillMil`**-metod — eller använd denna medvetet trasiga variant:

```java
public static double kmTillMil(double km, double faktor) {
    return km * faktor;
}

// main:
double mil = kmTillMil(10.0);
```

Skriv **minst en** FEEDBACK-rad om **parameter-mismatch** (för få argument / fel signatur). Fixa till **en** parameter om det var meningen, eller skicka **två** argument medvetet.

### Steg 5 — Reflektion (3 meningar)
1. Vilket return-fel hade AI gjort (`void`+värde, saknad `return`, fel typ)?  
2. Vad ändrade du (peka på metodhuvud **och** anrop)?  
3. Varför ska `deposit(amount)` i Kontoappen likna en metod med **parameter** — inte tre kopior av samma insättningslogik i `main`?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade (inkl. minst ett return- **eller** parameter-problem)  
- [ ] Peka på **returtypen** och **`return`-raden** — de matchar  
- [ ] Peka på **anropet** — rätt antal och typ av argument  
- [ ] Peka på något du *tog bort* (klass, ArrayList, metod i main, duplicerad formel)  
- [ ] Programmet **kompilerar och kör** — rimligt slutpris / mil-värde  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Rabatt-exempel:

```java
public class Main {
    public static void main(String[] args) {
        double slutpris = rabatteratPris(500.0, 20.0);
        System.out.println("Slutpris: " + slutpris);
    }

    public static double rabatteratPris(double pris, double rabattProcent) {
        double faktor = 1 - rabattProcent / 100.0;
        return pris * faktor;
    }
}
```

Konsol: `Slutpris: 400.0`.

Typiska FEEDBACK-rader:

- `FEEDBACK: void rabatteratPris men return pris * faktor → byt till double som returtyp.`  
- `FEEDBACK: double slutpris = voidMetod(...) → void ger inget värde; antingen returnera double eller ta bort tilldelningen.`  
- `FEEDBACK: missing return statement → lägg till return uttryck; i enkel metod räcker en return i slutet.`  
- `FEEDBACK: kmTillMil(10.0) men metoden kräver två parametrar → skicka andra argument eller ta bort extra parameter.`  
- `FEEDBACK: rabatteratPris("500", 20) → double pris = 500.0; String passar inte.`  
- `FEEDBACK: metod inuti main → flytta ut som syskon till main.`  
- `FEEDBACK: ArrayList/Account tillagt → stryk; paketet kör static-metoder i Main bara.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag tar emot AI-metoder som utkast, fixar returtyp, return och argument, och behåller bara kod jag kan förklara rad för rad.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
