# 04 — AI-träning: Svag README, Account-kopia & ägarskap

AI kan skriva README som **låter** rätt och kod som **ser** ut som Examination 1. Det betyder inte att gruppen äger Examination 2. Här tränar du: **tom mall-README**, **Account-kopia / engelska namn** — granska, ändra, förklara.

Det är inte magi. Det är egna ord + svenska klasser + Klart-check.

---

## Scenario A — problem först: README utan pekning

Ni ber AI: *“Skriv README till vår Java medlemsapp för gruppexamination.”* Ni får:

```markdown
## 1. Datalogiskt tänkande
Vi använde datalogiskt tänkande för att planera systemet.

## 2. Klass och objekt
OOP är viktigt. Vi har klasser och objekt.

## 3. Git i grupp
Vi samarbetade bra med GitHub.
```

**Svagheter:**
- **Q1:** Ingen kedja **data → klasser → meny**, inga filnamn.  
- **Q2:** Inget **`Medlem`**, inget **`new`**, ingen lista.  
- **Q3:** Inga kommandon (`pull`/`push`), ingen strategi mot överskrivning.  
- **Problem** och **AI-reflektion** saknas.  
- Texten går att klistra i **vilken** kurs som helst — den pekar inte på **er** app.

**Vad du tränar:** Feedback + README ni kan **peka** i IDE:n / på GitHub.  
**Varför:** Examinationen kräver konkreta svar — malltext räcker inte.  
**Vad det INTE är:** “AI skrev README klart.”

---

## Scenario B — problem först: Account-kopia / fel råd

AI föreslår:

```java
// "Samma som din kontoapp — byt bara namn"
public class Account {
    private String owner;
    private double balance;
    // factory createAccount, SavingsAccount extends Account ...
}
```

eller README-råd:

> Lägg till muntlig redovisning och sikta på VG med arv. Skapa pull request för varje feature. Individuellt repo per person.

**Svagheter:**
- **Engelska / Exam 1-namn** — briefen kräver `Medlem` / `Register` / `Main`.  
- **Factory / arv** — NOLL SPILL för Exam 2.  
- **Muntlig + VG** — finns **inte** på gruppexamen.  
- **PR / individuellt repo** — fel leveransform.  
- Risk: ni “klarar” AI-checklist men **missar** Klart-check.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv egen prompt (eller använd scenariorna) där du ber om:
- README Q1–Q3 + problem + AI till **medlemsregistret**;
- tre klassfiler för klubbens register.

Spara prompten.

### Steg 2 — Granska README (checklist)
- [ ] Q1 nämner **data → klasser → meny** (eller tydliga steg)?  
- [ ] Q2 nämner **`Medlem`**, **objekt** / **`new`**, lista?  
- [ ] Q3 nämner **`pull`** och hur ni undviker överskrivning?  
- [ ] Problem-stycke med **händelse**?  
- [ ] AI-reflektion med **konkret ändring**?  
- [ ] Kan ni peka i **gruppens** kod utan att läsa mallen?

Skriv **minst tre** rader:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Exempel:**
- `FEEDBACK: Q1 säger bara "datalogiskt" → skriv data namn/nummer → Medlem/Register/Main → meny.`  
- `FEEDBACK: Q3 säger "samarbetade bra" → lägg pull före push + filansvar.`  
- `FEEDBACK: saknar AI-exempel → en mening där vi strök Account och behöll Medlem.`

### Steg 3 — Skriv om README (egna ord)
I **grupprepots** `README.md`: ersätt AI-mallen med utkast enligt [03 — Uppgift 2–3](./03-ovningar.md). Max ~2–4 meningar per fråga.

### Steg 4 — Granska kodråd (checklist)
- [ ] Klassnamn **svenska** (`Medlem`, `Register`, `Main`)?  
- [ ] **Ingen** `Account` / `SavingsAccount` / factory som “bonus”?  
- [ ] Lista i **`Register`**, inte bara i `Main`?  
- [ ] **Ingen** muntlig/VG/PR som krav i text ni behåller?  
- [ ] Ett **gemensamt** publikt repo — inte individuellt?

Skriv **minst två** FEEDBACK-rader om kod/råd.

**Exempel:**
- `FEEDBACK: AI gav Account → byt till Medlem med namn + medlemsnummer.`  
- `FEEDBACK: AI nämnde VG/muntlig → stryk; Exam 2 är IG/G + repo-länk.`

### Steg 5 — Anpassa det ni äger
Behåll bara det som matchar [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md). Om AI gav engelsk skelettkod: skriv om filnamn och fält till svenska — eller kasta och utgå från er kod i [17-lista-register](../17-lista-register/) / [18-sok-meny](../18-sok-meny/).

### Steg 6 — Reflektion (3 meningar)
1. Vilket README-bristfall hade AI (tom fras, fel Q)?  
2. Vilket fel råd (Account, VG, PR, individuellt repo)?  
3. Varför räcker inte “det låter professionellt” för examinationen?

---

## Klart-check (peka i ERA filer)

- [ ] Minst **tre** FEEDBACK-rader om README  
- [ ] Minst **två** FEEDBACK-rader om Account-kopia / fel examråd  
- [ ] README-utkast med **Q1-kedja**, **klass/objekt**, **Git-flöde**  
- [ ] Ingen **Account**/factory/arv kvar i det ni behållit från AI  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

**README Q1 (kort):**

> Vi bröt ner registret innan vi kodade klart: data (namn, medlemsnummer) → klasser (Medlem, Register, Main) → meny (lägg till, lista, sök, avsluta).

**README Q2 (kort):**

> Medlem är mallen. Ett objekt är en konkret medlem skapad med new och lagrad i Register:s lista. Lösa variabler i Main räcker inte.

**README Q3 (kort):**

> Vi ändrar, add, commit, pull före push. Vi delar filer och synkar ofta så vi inte skriver över varandra. Alla syns under Commits.

Typiska FEEDBACK-rader:

- `FEEDBACK: Q1 utan steg → data → klasser → meny + tre filnamn.`  
- `FEEDBACK: Q2 buzzwords → peka List<Medlem> och new Medlem.`  
- `FEEDBACK: Account.java i AI-svar → Medlem.java med private namn/nummer.`  
- `FEEDBACK: "sikta VG + muntlig" → stryk; IG/G och Moodle-länk v8.`  
- `FEEDBACK: individuellt repo → ett gemensamt publikt grupprepo.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag granskar AI-README mot pekning i vår kod och AI-kod mot Klart-check. Behåller bara det varje person kan förklara.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
