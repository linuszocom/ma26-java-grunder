# 04 — AI-träning: skiljedom du kan köra

AI kan föreslå ett kommando som får Pull Requesten att se grön ut, utan att programmet har körts. Här tränar du att känna igen det rådet, städa `src/Main.java` själv, och pusha först efter `javac`.

Du jobbar ensam. De två grenarna är dina.

---

## Scenario

Du ber AI: *"Min Pull Request säger This branch has conflicts that must be resolved. Fixa snabbt."*  
Du får tillbaka något i den här stilen:

```text
# Öppna Resolve conflicts på GitHub och klicka dig fram.
# Eller, snabbare, på main:
git merge feature-valkomst-b
# Om det strular:
git push --force
git rebase origin/main
# Behåll båda raderna och lägg en Scanner så användaren väljer.
# Skapa KonfliktHanterare.java som skriver ut rätt mening.
# Markörerna kan ligga kvar, GitHub bryr sig bara om att du pushar.
```

| Råd | Varför det inte håller |
| :--- | :--- |
| Lös texten i webbläsaren | Där kör du inte `javac`. En grön Pull Request kan innehålla en rad som inte startar |
| `git merge` på `main` i terminalen | Du hoppar över den spärrade Pull Requesten och dess diff |
| `--force` eller rebase | Historiken skrivs om. Båda commits ska finnas kvar |
| Scanner, eller en ny klass | Konflikten sitter i en `println` i `src/Main.java`. Inget mer ska in i paketet |
| Pusha med staket kvar | `<<<<<<<` är inte Java. Kompileringen faller |
| "Välj alltid HEAD utan att läsa" | `HEAD` är grenen du står på, inte automatiskt den mening som ska gälla |

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt

Skriv en egen prompt där du ber om hjälp att lösa en konflikt i en `println` i `src/Main.java`, på grenen `feature-valkomst-b`, så att Pull Requesten blir grön. Spara prompten.

### Steg 2 — Granska

Kryssa mot svaret, eller mot snutten ovan:

- [ ] Förslag att lösa konflikten i GitHubs webbläsare
- [ ] `git merge` av feature-grenen in i `main` i terminalen
- [ ] `--force` eller rebase
- [ ] Scanner, lista eller en ny klass
- [ ] Push utan `javac`
- [ ] Rådet att behålla båda staketen, eller att ta bort `println` tillsammans med dem

Skriv **minst fyra** rader:

`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Kedjan du äger

Den ska matcha [03 — Övningar](./03-ovningar.md):

- Du står på `feature-valkomst-b`
- `git pull origin main`
- En mening kvar, tre staketrader borta
- `javac src/*.java && java -cp src Main`
- `git add src/Main.java`
- `git commit -m "fix: lös konflikt i välkomsttext"`
- `git push`
- Pull Requesten är grön, sedan **Merge pull request**
- `git switch main && git pull origin main`

### Steg 4 — Reflektion (fyra meningar)

1. Vilket råd strök du, och varför?
2. Vad betyder `HEAD` när du har dragit in `main` i feature-grenen?
3. Varför sitter `javac` före `git push`?
4. Vad ska avsnittet "Ett problem vi löste" nämna för att en läsare ska förstå händelsen?

---

## Klart-check

- [ ] Minst fyra FEEDBACK-rader
- [ ] Du pekar i `src/Main.java` på en `println` utan staket
- [ ] Du pekar på committen `fix: lös konflikt i välkomsttext`
- [ ] Du pekar på en Pull Request som var spärrad och sedan blev grön
- [ ] Konsolen visar meningen du valde
- [ ] Reflektionens fyra meningar är skrivna

---

## Facit-riktning

- `FEEDBACK: Resolve conflicts i webbläsaren → git pull origin main på feature-grenen, städa i editorn, javac, push.`
- `FEEDBACK: git merge på main → låt Pull Requesten bli grön och klicka Merge där.`
- `FEEDBACK: push --force → stryk. Add, commit, push på grenen.`
- `FEEDBACK: Scanner eller ny klass → stryk. Bara println-raden i src/Main.java.`
- `FEEDBACK: pusha med markörer kvar → javac först. De tre staketraderna ska vara borta.`
- `FEEDBACK: välj HEAD utan att läsa → läs båda meningarna. HEAD är grenen du står på.`

**Målsvar (säg högt / skriv i README):** *"Jag stryker webblösning, force och nya klasser. Jag drar in main på feature-grenen, städar, kör javac och pushar. Då blir Pull Requesten grön."*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
