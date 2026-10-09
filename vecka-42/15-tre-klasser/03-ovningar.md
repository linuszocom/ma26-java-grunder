# 03 — Övningar: tre klasser, en Pull Request i taget

**Omfång:** Du jobbar ensam. Ett publikt repo med `main`. Filerna ligger i `src/`. `Medlem` med `private` fält, konstruktor och getters. `Register` som tom klass. `Main` skapar en medlem och skriver ut via getters. Varje färdig ändring går in via Pull Request: du läser din egen diff och klickar **Merge pull request**, sedan `git switch main && git pull origin main`.

**Inte i det här paketet:** lista, sökmetod, Scanner, meny, arv, factory, och en omdöpt Kontoapp.

Har du repot från [14-git-team](../14-git-team/) använder du det. Annars skapar du ett publikt repo med en README, klonar, och står på `main` innan uppgift 2.

---

## Uppgift 1 — Reflektion: lösa variabler

**Mål:** Se vad som saknas när namn och nummer är vanliga variabler i `Main`.

**Krav:**

1. Stå på `main`. Skapa en gren du **inte** mergar:

```text
git switch -c experiment-losa-variabler
```

2. Ersätt innehållet i `src/Main.java` med:

```java
public class Main {
    public static void main(String[] args) {
        String namn1 = "Kim";
        int nummer1 = 1001;
        String namn2 = "Moa";
        int nummer2 = 1002;

        System.out.println(namn1 + " " + nummer1);
        System.out.println(namn2 + " " + nummer2);
    }
}
```

3. Kör:

```text
javac src/Main.java && java -cp src Main
```

4. Skriv tre meningar i en anteckning: vad som händer om `namn2` byts och `nummer2` glöms, var en persons data hör hemma, och var samlingen ska ha sin adress.
5. Gå tillbaka till `main` utan att merga experimentet:

```text
git switch main
```

**Klart-check:**

- [ ] Konsolen visar två rader
- [ ] Anteckningen finns
- [ ] `main` har inte experimentet. Ingen Pull Request öppnades för de lösa variablerna

---

## Uppgift 2 — Skelettet via första Pull Requesten

**Mål:** `Medlem` och en tom `Register` ligger på `main`, efter att du själv läst diffen.

**Krav:**

1. `git switch main && git pull origin main`
2. `git switch -c feature-skelett`
3. Skapa `src/Medlem.java`:

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

4. Skapa `src/Register.java`:

```java
public class Register {
    // Domänens samlingsägare. Inget tillstånd i det här skedet.
}
```

5. Lämna `src/Main.java` som den var på `main`. Ingen lista i någon fil.

```text
git add src/Medlem.java src/Register.java
git commit -m "feat: Medlem och tom Register — Namn"
git push -u origin feature-skelett
```

6. Öppna Pull Request mot `main`. Under **Files changed**: båda fälten är `private`, konstruktorn sätter dem med `this`, `getNamn` finns, `Register` har inga fält. Klicka **Merge pull request**.
7. Lokalt:

```text
git switch main && git pull origin main
```

Öppna filerna på disk. De ska finnas under `src/` utan att du tittar på webben.

**Klart-check:**

- [ ] Pull Requesten för `feature-skelett` är mergad
- [ ] `src/Medlem.java` och `src/Register.java` finns på din `main`
- [ ] `Register` har ingen lista

---

## Uppgift 3 — Systemstart i `Main` via Pull Request

**Mål:** Entrén skapar Kim och skriver ut namnet. Konsolen visar `Kim`.

**Krav:**

1. `git switch main && git pull origin main` så att `Medlem.java` finns lokalt.
2. `git switch -c feature-main-start`
3. Skriv `src/Main.java`:

```java
public class Main {
    public static void main(String[] args) {
        Medlem kim = new Medlem("Kim", 1001);
        System.out.println(kim.getNamn());
    }
}
```

4. Pusha och öppna Pull Request:

```text
git add src/Main.java
git commit -m "feat: Main skapar Kim och skriver ut namnet — Namn"
git push -u origin feature-main-start
```

5. Läs diffen. Utskriften går via `getNamn()`. Ingen lista. Merga.
6. `git switch main && git pull origin main`
7. Provkör:

```text
javac src/*.java && java -cp src Main
```

**Klart-check:**

- [ ] Konsolen visar `Kim`
- [ ] `Register.java` är orörd och tom
- [ ] Du pullade innan du kompilerade, så `Medlem.java` låg på den lokala `main`

---

## Uppgift 4 — Utöka entiteten via Pull Request

**Mål:** `Main` kan läsa medlemsnumret. Konsolen visar Kim och 1001.

**Krav:**

1. `git switch main && git pull origin main`
2. `git switch -c feature-medlemsnummer`
3. Lägg till i `Medlem`, under `getNamn`:

```java
public int getMedlemsnummer() {
    return medlemsnummer;
}
```

4. I `Main`, lägg till anropet:

```java
System.out.println(kim.getMedlemsnummer());
```

5. Pusha båda filerna, öppna Pull Request, läs diffen, merga.

```text
git add src/Medlem.java src/Main.java
git commit -m "feat: getMedlemsnummer och utskrift — Namn"
git push -u origin feature-medlemsnummer
```

6. `git switch main && git pull origin main`
7. `javac src/*.java && java -cp src Main`

**Klart-check:**

- [ ] Konsolen visar `Kim` och `1001`
- [ ] Fältet är fortfarande `private`. Du läser det inte som `kim.medlemsnummer`
- [ ] `Register.java` är fortfarande tom

---

## Uppgift 5 — Verifiering och examensfrågan

**Mål:** Historiken visar de mergade grenarna, och README svarar på Examination 2, fråga 2.

**Krav:**

1. På uppdaterad `main`:

```text
git switch main && git pull origin main
git log --oneline --graph
```

Leta upp commits för skelett, systemstart och medlemsnummer. En skarv är mötet vid Merge.

2. Ny gren för svaret:

```text
git switch -c feature-readme-q2
```

3. Skriv i `README.md`, egna ord, ungefär 2–4 meningar. Frågan är: varför är `Medlem` en klass och inte bara variabler i `Main`? Vad är ett objekt i appen? Nämn mallen, instansen `kim`, och att namn och nummer sätts tillsammans i konstruktorn.
4. `git push -u origin feature-readme-q2`. Öppna Pull Request, läs diffen, merga.
5. `git switch main && git pull origin main`. Öppna `README.md` på disk.

**Klart-check:**

- [ ] `git log --oneline --graph` visar mer än en gren som mött `main`
- [ ] README på din dator innehåller svaret
- [ ] Du kan säga svaret högt utan att läsa innantill

---

## Valfritt — en andra instans

På `feature-andra-medlem`: skapa `Medlem moa = new Medlem("Moa", 1002);` och skriv ut båda via getters. Samma Pull Request-flöde. `Register` förblir tom. Två objekt, två egna tillstånd, fortfarande ingen samling.

---

## När du kört fast

1. *has private access* — anropa gettern. Låt `private` stå kvar.
2. Konstruktorn klagar — skicka namn och `1001` till `new Medlem`.
3. Filen saknas efter Merge — `git switch main && git pull origin main`.
4. AI lämnar `Account`, `owner` eller en lista i `Main` — stryk det innan du mergar. Jämför med [01 — Teoriguide](./01-teoriguide.md).

Nästa: [04 — AI-träning](./04-ai-traning.md).
