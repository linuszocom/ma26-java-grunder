# **Individuell examination 1: Kontoappen**

Du ska **på egen hand** bygga en **konsolapp i Java** som hanterar **bankkonton**, lämna in den på GitHub och **redovisa koden** (live eller video).  
Målet är objektorienterad kod och ett enkelt designmönster — inte ett grafiskt bankgränssnitt, ingen databas och ingen mobilapp.


### **Viktigt innan du börjar**

**Det som ger betyg:** klasserna, inkapsling, hur objekt skapas, att appen går att köra, och att **du kan förklara koden** i IDE:n.  
Håll antalet konton litet. Extra menyer ger inga poäng.

**Namn i koden är låsta (engelska).** Klasser, fält och metoder ska heta exakt som nedan. Menyn mot användaren får vara på svenska. README och redovisning är på svenska — du pekar på den engelska koden.

Examinationen har två delar som hör ihop: **inlämning** (repo) och **muntlig redovisning** (samma repo).

---

### **Vad du ska göra — koden**

1. Skapa ett Java-projekt i din **IDE** (IntelliJ eller VS Code) med **JDK**. Kör appen i **konsolen** i IDE:n.

2. Dela koden i **minst tre `.java`-filer**:
   - `Account.java` — ett konto som objekt  
   - `AccountRegister.java` — samlingen av konton  
   - `Main.java` — menyn  

3. **`Account`** ska ha:
   - minst fälten **`owner`** (`String`) och **`balance`** (`double` eller `int`) — **private**  
   - en **konstruktor** som sätter `owner` och startvärde för `balance`  
   - `deposit(amount)` — öka `balance`  
   - `withdraw(amount)` — minska `balance` **bara om** beloppet inte är större än saldot (annars skriv ett tydligt meddelande och lämna `balance` oförändrat)  
   - `getOwner()` och `getBalance()` så menyn kan skriva ut ägare och saldo  

4. **Skapande-mönster (factory):** I `AccountRegister` ska det finnas metoden `createAccount(String owner, int startBalance)` (eller `double` om du valt det till `balance`). Dess jobb är att **skapa** ett `Account` och lägga det i listan.  
   **Vad du ska se:** `new Account(...)` står i den metoden — **inte** utspridd i `Main` varje gång användaren väljer “nytt konto”.

5. **`AccountRegister`** håller kontona i en **lista**. Minst:
   - skapa/lägg till via `createAccount`  
   - lista alla konton (`owner` + `balance`)  
   - hitta ett konto (t.ex. på `owner`) så `deposit`/`withdraw` kan köras på **rätt objekt**

6. **`Main`** — meny i loop tills avsluta (texten i menyn får vara svenska):

   1. Skapa konto  
   2. Lista konton  
   3. Sätt in pengar  
   4. Ta ut pengar  
   5. Avsluta  

7. **Kör igenom innan inlämning:** skapa minst **två** konton, lista dem, sätt in på det ena, gör ett uttag som **lyckas** och ett som **stoppas** (för stort belopp).

8. **Git:** eget **publikt** GitHub-repo. Minst **5 commits** med begripliga meddelanden (`add` → `commit` → `push`).

**Gör inte:** grupprepo, GUI, databas, svenska klassnamn (`Konto.java`).

---

### **Klart-check — koden**

- [ ] `Main` går att köra i IDE:n  
- [ ] Minst tre `.java`-filer: `Account`, `AccountRegister`, `Main`  
- [ ] Private fält `owner` och `balance` + konstruktor på `Account`  
- [ ] `deposit` ökar `balance`; för stort `withdraw` **ändrar inte** `balance` och ger ett meddelande  
- [ ] **Vad du ska se i koden:** `new Account` i `createAccount` i `AccountRegister`, inte i `Main`  
- [ ] **Vad du ska se när du kör:** två konton i listan; saldo uppdateras efter insättning; ett stoppat uttag lämnar samma saldo  
- [ ] Publikt GitHub-repo, minst **5** commits under **Commits**  
- [ ] `README.md` enligt nedan  

---

### **Skriv i README.md**

Egna ord (svenska). Ungefär **2–4 meningar per fråga**. Peka på de engelska namnen i koden.

1. Vad är **inkapsling**? Peka på ett **private** fält (`owner` eller `balance`) och vad som hade hänt om det varit publikt.
2. Vad är ett **skapande-mönster (factory)** i din app — var skapas `Account`-objekten (`createAccount`) och varför inte i `Main`?
3. Beskriv **datalogiskt** ett av menyvalen som en kort stegkedja (inmatning → vilket objekt → vilken metod → vad som skrivs ut).

**AI-reflektion** (ca 3–5 meningar):  
Hur gjorde du när du körde fast? Om du använde AI: **ett exempel** där du ändrade förslaget innan det fungerade hos dig.

---

### **Lämna in koden**

Klistra in länken till ditt GitHub-repo i Moodle **under examinationsveckan** (deadline enligt schema).  
Redovisningen (live eller video) sker **samma vecka** — inte en senare tom vecka.

---

### **Muntlig redovisning**

Du redovisar **samma repo**. Du bygger inget nytt projekt.  
Du **förklarar koden i IDE:n** — inte en demo i webbläsaren.  
Gör detta **under samma examinationsvecka** som kodinlämningen.

Välj **ett** sätt:

1. **Live** med läraren (på plats eller i samtal) — koden öppen i IDE:n.  
2. **Video** — skärminspelning där man **ser IDE:n** och **hör din röst**. **4–8 minuter.** Peka med markören. Klipp inte bort koden. Inget krav på webbkamera.

**Vad du ska göra**

1. Ha `Account.java`, `AccountRegister.java` och `Main.java` öppna.  
2. Välj **2–3 delar**. Minst en ska vara OOP (ett objekt + en metod), inte bara meny-loopen. Exempel: konstruktor + `private`; `createAccount` och var `new` står; `withdraw` när beloppet är för stort; (VG) `SavingsAccount`.  
3. Peka på raderna och berätta vad som händer när programmet körs.

**Live:** om läraren frågar om en annan rad ska du kunna följa den utan att gissa.  
**Gör inte:** bara läsa README. Låta någon annan prata.

**Klart-check — redovisning**

- [ ] Repot öppnas i IDE:n  
- [ ] Jag har valt 2–3 delar och vet fil/rad  
- [ ] Jag kan förklara `createAccount` och ett `deposit`/`withdraw`  
- [ ] Jag har valt live eller video enligt Moodle  

**Lämna in redovisning:** boka live **eller** lämna video/länk i Moodle — **samma examinationsvecka** som koden.

---

### **AI och ägarskap**

AI är tillåtet när du bygger. På redovisningen är det **du** som ska förklara. Kan du inte = IG.

---

### **Betyg**

#### **Godkänt (G)**

- Allt under koden och Klart-check (kod) är uppfyllt.
- README enligt ovan.
- **Muntligt:** ensam, i IDE:n (live eller video), **övergripande** förklaring av 2–3 delar.

#### **Väl godkänt (VG)**

- Allt för G.
- **I koden:** minst en subklass som ärver från `Account` (t.ex. `SavingsAccount` med extra metod) och **används i appen** (meny + lista).
- **Muntligt under huven:** t.ex. varför fält är private, vad konstruktor gör, hur listan hänger ihop med objekten, skillnad factory vs `new` i `Main`, och arvet om du har det.
- Kursplanens VG: god förståelse för OOP-principer **och** att du tillämpat dem i koden du pekar på.

---
