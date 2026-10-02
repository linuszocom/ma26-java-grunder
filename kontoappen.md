# Individuell examination 1: Kontoappen

Du ska på egen hand bygga en fungerande konsolapplikation i Java som hanterar bankkonton. Projektet ska lämnas in via GitHub och redovisas muntligt (live eller video).

Målet är att bygga ett väldesignat, objektorienterat system med skyddad data och bra ansvarsfördelning mellan klasserna.

---

### Förutsättningar
* **Språk i koden:** All kod (klasser, metoder, variabler) skrivs på engelska med namn som du väljer själv. Menyer och utskrifter i konsolen får vara på svenska.
* **Filstruktur:** Systemet ska **minst** delas upp i tre filer: `Account.java`, `AccountRegister.java` och `Main.java`.
* **Programkrav:** Appen ska kunna köras i konsolen och hantera felaktig inmatning utan att krascha.
* **Flexibilitet:** Kraven nedan beskriver vad systemet **minst** måste innehålla. Du är fri att lägga till fler metoder, fält eller menyval om du vill utveckla din app vidare.
* **Behöver du stöd?** Kör du fast på hur kraven ska tolkas eller lösas i kod, ta hjälp under schemalagd handledningstid för att bolla lösningar innan inlämning.

---

### Kravspecifikation (Vad systemet minst ska klara)

#### 1. Kontot (`Account.java`)
Ett konto representerar en enskild kunds bankkonto och ska **minst**:
* Hålla reda på vem som äger kontot och dess saldo.
* **Datasäkerhet (Inkapsling):** Kontots information måste vara skyddad mot otillåten åtkomst eller direkt manipulering utifrån.
* Kunna skapas med en ägare och ett startbelopp.
* Erbjuda metoder för att läsa av vem som äger kontot och vad det aktuella saldot är.
* Erbjuda en metod för att göra en insättning som ökar saldot.
* Erbjuda en metod för att göra ett uttag som minskar saldot. **Regel:** Ett uttag får aldrig göra att saldot blir negativt. Om pengarna inte räcker ska uttaget nekas med ett tydligt felmeddelande och saldot lämnas orört.

#### 2. Kontoregistret (`AccountRegister.java`)
Registret ansvarar för att hantera samlingen av konton och ska **minst**:
* Hålla alla skapade konton i en gemensam lista.
* **Skapa konton (Factory):** Innehålla en metod som tar emot nödvändig information, skapar ett nytt konto och sparar det i listan. (*Regel: Konton ska skapas via registret, inte direkt ute i menykoden!*)
* Erbjuda en metod för att visa/skriva ut alla sparade konton med ägare och saldo.
* Erbjuda en metod för att söka/hitta ett specifikt konto i listan (t.ex. via ägarens namn) så att insättningar och uttag kan genomföras på rätt konto.

#### 3. Användargränssnittet (`Main.java`)
Startar programmet och driver en interaktiv konsolmeny i en loop tills användaren väljer att avsluta. Menyn ska **minst** innehålla följande val:
1. Skapa konto
2. Lista konton
3. Sätt in pengar
4. Ta ut pengar
5. Avsluta  
*(Det är helt okej att lägga till fler val om du vill!)*

---

### GitHub & Versionshantering
* Skapa ett **eget publikt GitHub-repo**.
* Gör **minst 5 commits** som visar hur projektet har växt fram steg för steg under utvecklingen.
* Projektet ska vara helt eget arbete (inga grupprepos). Inget grafiskt gränssnitt (GUI) och ingen databas behövs.

---

### Skriv i `README.md`
Besvara följande frågor kort med egna ord (ca 2–4 meningar per fråga) i ditt repo:
1. **Datasäkerhet/Inkapsling:** Hur har du skyddat kontots uppgifter i din kod, och vad hade kunnat hända om du inte gjorde det?
2. **Skapande-mönster (Factory):** Varför skapas kontot via registrets metod istället för direkt ute i `Main`?
3. **Flöde:** Beskriv ett av menyvalen steg för steg (vad användaren matar in → vilket objekt som hanterar det → vilken metod som körs → vad som skrivs ut).
4. **Reflektion (3–5 meningar):** Hur gjorde du när du körde fast eller stötte på ett problem? Om du använde verktyg som AI, Google eller kursmaterial: ge ett konkret exempel på hur du tog hjälp för att förstå och lösa problemet själv.

---

### Muntlig redovisning
Du redovisar samma projekt som du lämnat in på GitHub genom att visa källkoden i din utvecklingsmiljö (t.ex. IntelliJ) och förklara hur den fungerar.

* **Video:** En kort skärminspelning (**max 5 minuter**) via Teams där du delar IntelliJ/VS Code, pekar med muspekaren och förklarar källkoden.

**Uppgiften under redovisningen:**  
Välj ut **2–3 metoder** i din kod och förklara dem:
* Minst en metod i `Account.java`
* Minst en metod i `AccountRegister.java`

  🔗 [Instruktion för muntlig videoinspelning](instruktion_videoinspelning.md)

---

### Inlämning
Inlämningen sker via moodle, under vecka 41 har ni länk till inlämningssidan, där lämnar ni en länk (url) till erat repo.
Länk till den muntliga redovisningen ska ligga i eran README i ert repo.

Senast inlämningsdag är Fredag 9:e oktober.

---

### Betygskriterier

#### Godkänt (G)
* Appen uppfyller minimikraven i specifikationen och kan köras utan att krascha.
* Repot är publikt med minst 5 commits och en ifylld `README.md`.
* **Muntligt (Vad koden gör):** Du går igenom dina utvalda metoder och kan förklara vad koden gör rad för rad (vad som skickas in, vad metoden gör och vad som returneras).

#### Väl godkänt (VG)
* Alla krav för Godkänt (G) är uppfyllda.
* **I koden:** Du har skapat minst en subklass som ärver från `Account` (t.ex. ett sparkonto med en extra funktion/egenskap) och som används praktiskt i programmets meny och lista.
* **Muntligt (Varför och bakom kulisserna):** Du förklarar tanken bakom designen i din app. Du kan motivera *varför* en metod är placerad där den är, vad som händer om en rad tas bort, samt visa hur din subklass (arvet) samarbetar med resten av systemet.

---

### Snabbcheck innan du lämnar in
- [ ] Programmet startar och grundmenyn går att använda.
- [ ] Det går att skapa minst två konton och lista dem.
- [ ] Insättning ökar saldot på rätt konto.
- [ ] Uttag som överskrider saldot stoppas utan att programmet kraschar.
- [ ] Kontot skapas via registret, inte direkt ute i `Main`.
- [ ] Minst 5 commits finns på GitHub.
- [ ] `README.md` är besvarad.
- [ ] Redovisningslänk (om video) är inlagd och fungerar att öppna för läraren. (Se till att ge behörighet till alla med länk)
