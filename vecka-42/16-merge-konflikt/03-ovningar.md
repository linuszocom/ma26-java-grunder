# 03 — Övningar: röd Pull Request, grön efter lokal städning

**Omfång:** Du jobbar ensam, i repot från [15-tre-klasser](../15-tre-klasser/). Konflikten sitter i en `println` i `src/Main.java`. Du mergar inte konflikten i webbläsaren. Du står på feature-grenen, drar in `main`, städar i editorn, kör `javac`, pushar, och klickar Merge när Pull Requesten är grön.

**Lämna orört:** `Medlem.java`, `Register.java`, Scanner, listor, nya klasser, rebase, `--force`.

---

## Uppgift 1 — Ren `main`

**Mål:** Båda grenarna ska kunna utgå från samma commit.

**Krav:**

1. Kör:

```text
git switch main && git pull origin main
git status
```

2. `git status` ska säga att arbetsträdet är rent.
3. `src/Main.java` finns och innehåller minst en `System.out.println`.
4. Skriv upp basen:

```text
git log -1 --oneline
```

Spara den raden. Den är committen båda grenarna ska utgå från.

**Klart-check:**

- [ ] Du står på `main`
- [ ] Arbetsträdet är rent
- [ ] Du har bascommitten nedskriven

---

## Uppgift 2 — Två tidslinjer, en spärrad Pull Request

**Mål:** GitHub visar *This branch has conflicts that must be resolved*.

**Krav:**

1. Från den rena `main`:

```text
git switch -c feature-valkomst-a
```

2. I `src/Main.java`: ersätt den första `System.out.println(...)` med exakt den här raden. Lägg inte till en extra rad under. Rör inget annat.

```java
        System.out.println("Välkommen till Klubbens Register!");
```

3. Committa och pusha:

```text
git add src/Main.java
git commit -m "docs: välkomst a — Namn"
git push -u origin feature-valkomst-a
```

4. Öppna Pull Request mot `main`. Läs diffen. Klicka **Merge pull request**.
5. Gå tillbaka till basen **utan** att pulla:

```text
git switch main
git log -1 --oneline
```

Raden ska vara samma bascommit som i uppgift 1. Ser du A:s merge har du pullat för tidigt. Skapa då B från hashens bas, med kommandot `git switch -c feature-valkomst-b <bascommitten>`. Hoppa över steg 6.

6. Skapa den andra grenen från den basen:

```text
git switch -c feature-valkomst-b
```

7. Ersätt **samma** `println` med:

```java
        System.out.println("Medlemsregister v1.0");
```

8. Committa, pusha och öppna Pull Request:

```text
git add src/Main.java
git commit -m "docs: välkomst b — Namn"
git push -u origin feature-valkomst-b
```

9. Läs varningen på GitHub. Klicka inte på webbredigeraren för konflikter. Merga inte.

**Klart-check:**

- [ ] A:s Pull Request är mergad
- [ ] B:s Pull Request är öppen och spärrad
- [ ] Varningen innehåller *This branch has conflicts that must be resolved*
- [ ] B skapades från bascommitten, inte från A:s redan pullade `main`

---

## Uppgift 3 — Skiljedom i editorn

**Mål:** Filen kompilerar, med en mening och inga staket.

**Krav:**

1. Stå kvar på `feature-valkomst-b`. Kontrollera med `git status` om du är osäker.
2. Dra in originalet:

```text
git pull origin main
```

3. Terminalen ska nämna `CONFLICT` och `src/Main.java`. Öppna filen. Du ska se `<<<<<<< HEAD`, `=======` och `>>>>>>>`.
4. Läs båda meningarna. `HEAD` är `Medlemsregister v1.0`. Under likamed-raden ligger A:s mening från `origin/main`.
5. Behåll en mening. Ta bort de tre staketraderna. Spara.
6. Provkör:

```text
javac src/*.java && java -cp src Main
```

Konsolen visar meningen du behöll. Stannar kompileringen på ett `<` ligger ett staket kvar.

**Klart-check:**

- [ ] Du körde `git pull origin main` på `feature-valkomst-b`, inte på `main`
- [ ] Filen har en `println` och inga staket
- [ ] `javac` gick igenom
- [ ] Du har inte kört `git add` än om du vill stanna och läsa filen en gång till. Nästa uppgift tar add

---

## Uppgift 4 — Gör Pull Requesten grön

**Mål:** GitHub släpper Merge, och din lokala `main` har samma historik.

**Krav:**

1. Fortfarande på `feature-valkomst-b`, efter en grön `javac`:

```text
git add src/Main.java
git commit -m "fix: lös konflikt i välkomsttext"
git push
```

2. Öppna Pull Requesten för `feature-valkomst-b`. Den ska vara grön. Klicka **Merge pull request**.
3. Hämta hem originalet:

```text
git switch main && git pull origin main
git log --oneline --graph
```

4. Öppna `src/Main.java` på disk. Meningen du valde ska ligga där. Inga staket.

**Klart-check:**

- [ ] Commit-meddelandet är `fix: lös konflikt i välkomsttext`
- [ ] Pull Requesten mergades efter att den blivit grön
- [ ] `git log --oneline --graph` visar mötet mellan grenarna
- [ ] Ingen `--force`

---

## Uppgift 5 — Dokumentera i README

**Mål:** Avsnittet "Ett problem vi löste" ligger på `main`, via en egen Pull Request.

**Krav:**

1. Utgå från `main` efter uppgift 4, så att pullen redan är gjord.

```text
git switch -c feature-problem-doc
```

2. Lägg avsnittet i `README.md`. Egna ord räcker om fil, rad, markörer och avslut finns med. Utgå från det här:

```markdown
## Ett problem vi löste

Vi ändrade samma println i src/Main.java på två feature-grenar.
feature-valkomst-a mergades. GitHub spärrade feature-valkomst-b:
This branch has conflicts that must be resolved.
git pull origin main skrev staket i filen.
HEAD var Medlemsregister v1.0. Under likamed-raden låg meningen från origin/main.
Vi läste båda, valde en mening och tog bort de tre staketraderna.
javac gick igenom. git add, git commit och git push gjorde Pull Requesten grön.
```

3. Rör inte `println`-raden igen.

```text
git add README.md
git commit -m "docs: ett problem vi löste — Namn"
git push -u origin feature-problem-doc
```

4. Öppna Pull Request, läs diffen, klicka **Merge pull request**.
5. Synka:

```text
git switch main && git pull origin main
```

**Klart-check:**

- [ ] README på din dator har avsnittet
- [ ] Texten nämner `src/Main.java`, de tre markörerna och `javac`
- [ ] `src/Main.java` är oförändrad i den här Pull Requesten
- [ ] "Vi fixade Git" är inte hela svaret

---

## När du kört fast

1. Ingen konflikt: du ändrade olika rader, eller B skapades efter pull av A. Gör om från samma bascommit, på samma `println`.
2. `javac` nämner `<<<<<<<`: staket kvar. Ta bort tre rader, spara, kompilera.
3. Pull Requesten är fortfarande röd efter push: du pushade fel gren, eller markörerna är committade. `git status` och filen på disk.
4. Webbläsaren erbjuder att lösa konflikten: stanna i editorn. Där kan du köra `javac`.

Nästa: [04 — AI-träning](./04-ai-traning.md).
