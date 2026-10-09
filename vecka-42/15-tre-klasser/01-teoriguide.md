# 01 — Teoriguide: tre klasser med ett ansvar var

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt eller skriva i README. Tar du materialet från noll: läs klart, titta på [02 — Visuellt](./02-visuell.md), gör sedan [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Exam 1 är stängd. Medlemsregistret är ett nytt projekt med svenska typnamn: `Medlem`, `Register`, `Main`. I det här paketet finns tre filer, ett `Medlem`-objekt och ett Pull Request-flöde du kör själv. Samlingen, sökningen och menyn kommer i senare paket.

**Förkunskaper:** `private`, konstruktor och getters från [10-inkapsling](../../vecka-40/10-inkapsling/). Klass och objekt från [08-klasser-objekt](../../vecka-39/08-klasser-objekt/). Feature-gren och Pull Request från [14-git-team](../14-git-team/).

---

## Lösa variabler i `Main` driver isär data

Många tänker: "Jag sparar namn och nummer som vanliga variabler i `main`. Det kompilerar." Det gör det. Problemet syns när uppgiften växer.

```java
String namn1 = "Kim";
int nummer1 = 1001;
String namn2 = "Moa";
int nummer2 = 1002;
```

Namn och nummer hör ihop i verkligheten. I den här koden är de två variabler som råkar stå på raderna under varandra. Byter du `namn2` och glömmer `nummer2` har programmet fortfarande en siffra. Den siffran tillhör inte längre samma person. Inget i språket säger att paret måste hänga ihop.

`Main` får dessutom två jobb samtidigt: starta programmet och äga medlemsdatan. Varje nytt fält, till exempel en e-postadress, betyder ännu ett variabelpar i samma metod. Filen sväller, och felet kan ligga i vilken rad som helst.

**Single Responsibility Principle** säger att en klass ska ha ett skäl att ändras.

| Klass | Ett skäl att ändras |
| :--- | :--- |
| `Medlem` | Medlemmens data ändras |
| `Register` | Sättet samlingen hålls ändras |
| `Main` | Starten eller utskriften ändras |

Ligger allting i `Main` har den klassen alla tre skälen. En ändring i utskriften riskerar datan. En ändring i datan riskerar starten.

**Målsvar (säg högt / skriv i README):** *"Lösa namn och nummer i Main kan glida isär, och Main får flera skäl att ändras. Medlem samlar en persons data i en typ."*

---

## Systemmodellen: entitet, samlingsägare, entré

Tre filer. Tre adresser i systemet.

**`Medlem.java` är entitetsmodellen**, databäraren. Den beskriver en medlem: inkapslat tillstånd, en konstruktor som sätter tillståndet, och getters som läser det. En instans är en konkret medlem.

**`Register.java` är domänens samlingsägare.** Klassen finns redan nu, med tom kropp. Adressen är bokad. När samlingen kommer senare är det den här klassen som ändras. `Main` behöver inte svälla för att rymma den.

**`Main.java` är applikationsentrén.** `main` startar programmet, skapar en `Medlem` och läser den via publika metoder. Entrén äger inte fälten.

Samma uppdelning fanns i Kontoappen, med andra namn: `Account`, `AccountRegister`, `Main`. Examination 2 låser de svenska namnen. Du skapar nya filer i ett nytt repo. En omdöpning av bankens klasser drar med sig `owner`, `balance` och metoder som hör till en annan domän.

**Målsvar (säg högt / skriv i README):** *"Medlem är databäraren. Register är samlingsägaren, tom i det här skedet. Main är applikationsentrén. Tre filer, ett ansvar var."*

---

## Inkapsling skyddar tillståndet

Fälten i `Medlem` är `private`. Bara metoder i samma klass läser och skriver dem. Konstruktorn skriver dem en gång, när objektet skapas. Getters lämnar ut värdet till den som anropar.

```java
public class Medlem {
    private String namn;
    private int medlemsnummer;

    public Medlem(String namn, int medlemsnummer) {
        this.namn = namn;
        this.medlemsnummer = medlemsnummer;
    }

    public String getNamn() {
        return namn;
    }
}
```

`this.namn` är fältet på objektet som just skapas. `namn` till höger är parametern från anropet.

`Main` som skriver `kim.namn` kompilerar inte. javac säger att fältet har private access. Inkapslingen gör sitt jobb. Anropet som kompilerar är `kim.getNamn()`.

Utan `private` kan vilken klass som helst skriva över namnet efter `new`, förbi konstruktorn. Då finns det två sätt att ändra samma tillstånd, och du vet inte vilket som gällde. Getters ger en väg ut. Setters behövs inte i det här paketet: värdena sätts i konstruktorn.

**Målsvar (säg högt / skriv i README):** *"private fält ändras i konstruktorn. Main läser med getNamn och getMedlemsnummer. kim.namn kompilerar inte, och jag tar inte bort private för att tysta felet."*

---

## Konstruktorn skapar en hel medlem

```java
Medlem kim = new Medlem("Kim", 1001);
```

`new` kör konstruktorn. Båda fälten får värde i samma anrop. Det finns inget mellanläge där namnet finns och numret saknas. `Main` skickar argumenten. `Medlem` lägger dem i fälten.

Klassen heter `Medlem`, så filen heter `Medlem.java`. Konstruktorn har samma namn som klassen och ingen returtyp.

**Målsvar (säg högt / skriv i README):** *"new Medlem(\"Kim\", 1001) kör konstruktorn. this.namn och this.medlemsnummer sätts inuti klassen. Objektet kim är den konkreta medlemmen."*

---

## `Register` är en adress, även när kroppen är tom

```java
public class Register {
    // Domänens samlingsägare. Inget tillstånd i det här skedet.
}
```

Filen kompilerar. Den har inga fält och inga metoder. Den finns för att samlingens ansvar redan har en klass. När den ansvarigheten ska fyllas är det `Register.java` som öppnas. `Main` fortsätter vara starten.

Tar du bort filen för att den är tom har systemet två klasser. Nästa krav på en samling landar då i `Main`, och entrén sväller igen.

I det här paketet skapar `Main` ingen `Register`. Det finns inget publikt beteende att anropa än.

**Målsvar (säg högt / skriv i README):** *"Register.java finns som samlingsägarens adress. Klassen är tom nu, så Main inte blir platsen där samlingen hamnar senare."*

---

## Du granskar din egen Pull Request

Du behöver ingen partner för det här paketet. Flödet är detsamma som i ett team. Du är både den som skriver och den som läser diffen.

1. `git switch main && git pull origin main`
2. `git switch -c feature/<namn>`
3. Ändra filerna. `git add` på de filer som hör till steget. `git commit -m "… — Namn"`
4. `git push -u origin feature/<namn>`
5. Öppna en Pull Request mot `main`. Skriv vad som ändrats.
6. Öppna **Files changed**. Läs raderna själv: `private` kvar, `Register` tom, inga kvarlevor från Kontoappen, ingen samling i `Main`.
7. Klicka **Merge pull request**.
8. `git switch main && git pull origin main`

Steg 7 uppdaterar `main` på GitHub. Din dator har den gamla kopian tills steg 8. Nästa `git switch -c` utgår från den `main` du står på. Utan pull föds nästa gren innan skelettet, eller innan `getNamn`, finns lokalt.

I övningarna heter grenarna `feature-skelett`, `feature-main-start` och `feature-medlemsnummer`.

**Målsvar (säg högt / skriv i README):** *"Jag pushar feature-grenen, läser min egen diff på GitHub och klickar Merge. Sedan git switch main och git pull origin main, så nästa gren utgår från det som faktiskt mergats."*

---

## Examensfrågan om klass och objekt

Examination 2 frågar i README, med egna ord: varför `Medlem` är en klass och inte bara variabler i `Main`, och vad ett objekt är i appen.

Klassen är mallen: fält, konstruktor, getters. Objektet är instansen efter `new`. `kim` pekar på en medlem med namnet Kim och numret 1001. Mallen kan skapa fler instanser senare. Variablerna `namn1` och `nummer1` är inte den mallen.

**Målsvar (säg högt / skriv i README):** *"Medlem är klassen, mallen. kim är objektet, instansen efter new Medlem(\"Kim\", 1001)."*

---

## Vanliga fel och vad du gör

| Vad du ser | Vad du gör |
| :--- | :--- |
| `namn has private access in Medlem` | Anropa `getNamn()`. Låt `private` stå kvar |
| `constructor Medlem cannot be applied` | Skicka namn och medlemsnummer till `new Medlem(...)` |
| `should be declared in a file named Medlem.java` | Döp filen till klassnamnet |
| Nästa gren saknar `Medlem.java` | Du mergade på GitHub och glömde `git switch main && git pull origin main` |
| `owner`, `balance`, `deposit` | Nya filer. Fälten heter `namn` och `medlemsnummer` |
| En samling deklarerad i `Main` | Ta bort den. Samlingens adress är `Register`, och den klassen är tom i det här paketet |
| `Register.java` saknas | Skapa den tomma klassen igen och ta in den via Pull Request |

---

## När du tvekar

1. Vems data är det? Öppna `Medlem`.
2. Är det samlingen? Öppna `Register`. I det här paketet lämnar du kroppen tom.
3. Är det start eller utskrift? Öppna `Main` och anropa en getter.
4. Står du på `main`, och är den pullad, innan du skapar nästa gren?
5. Har du läst diffen på GitHub innan du klickat Merge?

När målsvaren sitter: [02 — Visuellt](./02-visuell.md).
