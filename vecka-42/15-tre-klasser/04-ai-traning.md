# 04 — AI-träning: äg koden och diffen

AI kan skriva ett “färdigt medlemsregister” på sekunder. Ofta är det Kontoappen med nya namn, eller en lista i `Main`. Här tränar du att stryka det, behålla tre klasser med ett ansvar var, och ta in resultatet via en Pull Request du själv granskar.

Du jobbar ensam. En kollega som klickar Merge är inte ett krav i det här paketet.

---

## Scenario

Du ber AI: *"Bygg medlemsregister enligt Exam 2, snabbt."*  
Du får tillbaka något i den här stilen:

```java
public class Medlem {
    public String owner;
    public double balance;

    public void deposit(double amount) {
        balance += amount;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Medlem> lista = new ArrayList<>();
        Medlem m = new Medlem();
        m.owner = "Kim";
        lista.add(m);
    }
}
```

Och ett Git-råd under koden:

```text
git add .
git commit -m "update"
git push origin main
# "Hoppa över Pull Request, det är bara tre filer.
#  Din dator uppdateras när du pushat."
```

| Det AI lämnade | Varför det inte håller |
| :--- | :--- |
| `owner`, `balance`, `deposit` | Det är kontots domän. Medlemmen har `namn` och `medlemsnummer` |
| Publika fält och `m.owner = "Kim"` | Tillståndet kan skrivas över utanför konstruktorn |
| `ArrayList` i `Main` | Samlingens adress är `Register`. Den klassen är tom i det här paketet |
| Saknad `Register.java` | Systemet har då ingen samlingsägare |
| `git push origin main` | `main` uppdateras utan att diffen lästs |
| "Datorn uppdateras när du pushat" | Merge på GitHub uppdaterar molnet. Lokalt behövs `git switch main` och `git pull origin main` |

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt

Skriv en egen, snäv prompt. Spara den. Den ska be om:

- nya filer `Medlem`, `Register`, `Main` i `src/`
- `private String namn`, `private int medlemsnummer`, konstruktor, `getNamn`, `getMedlemsnummer`
- tom `Register` med en kommentar
- `Main` som gör `new Medlem("Kim", 1001)` och skriver ut via getters
- inget annat

### Steg 2 — Granska utkastet

Kryssa mot svaret, eller mot snutten ovan om du inte anropar AI:

- [ ] `Account`, `owner`, `balance`, `deposit` eller `getOwner`
- [ ] En samling i `Main`
- [ ] `Register` saknas, eller AI kallar den onödig
- [ ] Publika fält eller setters
- [ ] Factory, sökmetod, Scanner eller meny
- [ ] Push rakt till `main`, eller ett råd att hoppa över Pull Request och pull

Skriv **minst fyra** rader:

`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Den kedja du äger

Koppla till [03 — Övningar](./03-ovningar.md). Den version du behåller:

- `Medlem` med `private`, konstruktor och båda getters
- tom `Register`
- `Main` med ett objekt, utskrift av Kim och 1001
- feature-gren, `git push -u origin`, Pull Request, **Files changed** läst av dig, Merge
- `git switch main && git pull origin main`
- `javac src/*.java && java -cp src Main`

### Steg 4 — Reflektion (fyra meningar)

1. Vad strök du från AI-utkastet?
2. Varför räcker det inte att döpa om `Account` till `Medlem`?
3. Varför ligger samlingen inte i `Main` i det här paketet?
4. Vad tittade du efter i din egen diff innan du klickade Merge?

---

## Klart-check

- [ ] Minst fyra FEEDBACK-rader
- [ ] Du pekar på `private`, konstruktorn och en getter i din kod
- [ ] Du pekar på tom `Register` och på utskriften i `Main`
- [ ] Konsolen visar `Kim` och `1001`
- [ ] Du pekar på en mergad Pull Request som du själv läste
- [ ] Reflektionens fyra meningar är skrivna

---

## Facit-riktning

Kärnan du behåller:

```java
private String namn;
private int medlemsnummer;

public Medlem(String namn, int medlemsnummer) {
    this.namn = namn;
    this.medlemsnummer = medlemsnummer;
}

public String getNamn() {
    return namn;
}

public int getMedlemsnummer() {
    return medlemsnummer;
}
```

```java
public class Register {
    // Domänens samlingsägare. Inget tillstånd i det här skedet.
}
```

Exempel på feedback:

- `FEEDBACK: owner och balance → fälten heter namn och medlemsnummer, satta i konstruktorn.`
- `FEEDBACK: ArrayList i Main → stryk. Register finns och är tom.`
- `FEEDBACK: push origin main → feature-gren, Pull Request, läs diffen, Merge.`
- `FEEDBACK: "datorn uppdateras själv" → git switch main && git pull origin main.`
- `FEEDBACK: Register borttagen → skapa filen igen. Den är samlingsägarens adress.`

**Målsvar (säg högt / skriv i README):** *"Jag tar emot AI-utkast och stryker Account-kopior, listor i Main och push rakt till main. Jag mergar först efter att jag läst diffen, och jag pullar main innan nästa gren."*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
