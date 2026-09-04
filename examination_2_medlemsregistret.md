# **Gruppexamination 2: Klubbens medlemsregister**

Ni ska i **grupp** bygga en **konsolapp i Java**: ett medlemsregister för en fiktiv klubb.  
Målet är att appen **går att köra i IDE:n**, att ni använder **klasser och objekt**, och att **alla syns i Git-historiken** — inte GUI, webb eller mobilapp.


### **Viktigt innan ni börjar**

**Det som ger betyg:** Java-koden och Git-samarbetet.  
Håll registret litet. Extra menyer ger inga poäng.

Det här är **ett nytt projekt** — kopiera inte Kontoappen. Klassnamnen här är **svenska**.

Den här examinationen kan ge **IG eller G** — inte VG.

---

### **Vad gruppen ska göra**

#### **A. Bygg appen i Java**

1. Skapa ett Java-projekt i er **IDE** (IntelliJ eller VS Code) med **JDK**. Appen körs i konsolen i IDE:n.

2. Dela koden i **minst tre `.java`-filer**:
   - `Medlem.java` — en medlem som objekt  
   - `Register.java` — samlingen av medlemmar  
   - `Main.java` — menyn och programstart  

3. **`Medlem`** ska ha:
   - minst fälten **namn** (`String`) och **medlemsnummer** (`int`)  
   - fälten **private**  
   - en **konstruktor** som sätter fälten när objektet skapas  
   - metoder för att **läsa** namn och nummer (t.ex. `getNamn()`)

4. **`Register`** ska hålla medlemmarna i en **lista** (t.ex. `ArrayList<Medlem>`). Minst tre metoder:
   - **lägg till** en medlem  
   - **lista alla** (skriv ut namn + nummer)  
   - **sök på namn** (skriv ut träffen eller att medlemmen saknas)

5. **`Main`** — meny i loop tills avsluta:

   1. Lägg till medlem  
   2. Lista alla medlemmar  
   3. Sök medlem  
   4. Avsluta  

   Inmatning från konsolen (t.ex. `Scanner`).

6. **Kör igenom:** minst **två** medlemmar, lista dem, sök en som finns och en som inte finns, avsluta utan krasch.

#### **B. Git & GitHub (samarbete)**

1. Skapa **ett gemensamt publikt GitHub-repo**. Alla jobbar mot samma repo.

2. **Alla ska synas under Commits.** Egna commits, eller vid samma dator: båda namnen i meddelandet (t.ex. `"Lade till sök i Register — Anna och Johan"`).

3. Flöde: **ändra → `git add` → `git commit` → `git push`**. Gör **`git pull`** innan ni pushar. Minst **6 commits** totalt.

4. Commit-meddelanden beskriver vad som hände — inte `"fix"` eller `"asdf"`.

**Gruppstorlek:** 2–4 personer.

**Gör inte:** GUI, databas, Android. Kopiera inte `Account.java`. Factory och arv hör till Examination 1. Pull request är inte ett krav.

---

### **Klart-check (kryssa av innan inlämning)**

- [ ] **Main går att köra** i IDE:n  
- [ ] Minst tre `.java`-filer: `Medlem`, `Register`, `Main`  
- [ ] `Medlem` har **private** fält, **konstruktor** och get-metoder  
- [ ] Menyn: lägg till, lista, sök (träff + miss), avsluta  
- [ ] **Vad ni ska se när ni kör:** två medlemmar i listan; sök träff; sök miss  
- [ ] Publikt gemensamt GitHub-repo  
- [ ] **Vad ni ska se på GitHub → Commits:** minst **6** commits; **alla** i gruppen syns  
- [ ] `README.md` enligt nedan  

---

### **Skriv i README.md (gemensamt)**

Svara tillsammans. Ungefär **2–4 meningar per fråga**.

1. Vad är **datalogiskt tänkande** här — hur bröt ni ner “ett medlemsregister” i steg innan ni kodade?
2. Varför är `Medlem` en **klass** och inte bara variabler i `Main`? Vad är ett **objekt** i er app?
3. Hur versionshanterade ni med **Git i grupp**? Ge ett exempel (`add` / `commit` / `pull` / `push`) och hur ni undvek att skriva över varandra.

**Ett problem ni löste** (några meningar): vad som strulade och hur ni löste det.

**AI-reflektion** (ca 3–5 meningar):  
Hur gjorde ni när ni körde fast? Om ni använde AI: **ett exempel** där ni ändrade förslaget.

---

### **Lämna in**

Klistra in länken till gruppens GitHub-repo i Moodle **under examinationsveckan** (deadline enligt schema).

---

### **AI och ägarskap**

AI är tillåtet. **Varje person** måste kunna förklara sin del. Kan du inte = IG för dig.

---

### **Betyg**

#### **Godkänt (G)**

- Allt under “Vad gruppen ska göra” och Klart-check är uppfyllt.
- README enligt ovan.
- Historiken visar att alla bidragit.

#### **Väl godkänt (VG)**

Ges **inte** på gruppexaminationen. VG finns på Examination 1 (kod + muntligt djup).

---
