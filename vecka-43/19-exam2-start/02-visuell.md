# 02 — Visuellt: nedbrytning, Klart-check och examination

Samma bilder som i teoriguiden — nu som flöde. GitHub renderar diagrammen automatiskt.

---

## Datalogiskt — data → klasser → meny

```mermaid
flowchart LR
  data["1. Data<br/>namn, medlemsnummer"] --> klasser["2. Klasser<br/>Medlem · Register · Main"]
  klasser --> meny["3. Meny<br/>lägg till · lista · sök · avsluta"]
```

**Vad diagrammet visar:** Ordning före (och under) kod — inte “allt i Main”.  
**Kom ihåg / INTE:** INTE tom fras “vi planerade”.

**Målsvar (säg högt / skriv i README):** *“Datalogiskt = data → klasser → meny.”*

---

## Tre rum — ansvar

```mermaid
flowchart TB
  Main["Main<br/>meny + Scanner"] --> Register["Register<br/>List&lt;Medlem&gt;<br/>läggTill · listaAlla · sök"]
  Register --> Medlem["Medlem<br/>private namn, nummer<br/>konstruktor + get"]
```

**Vad diagrammet visar:** Disken anropar pärmen; pärmen håller visitkort.  
**Kom ihåg / INTE:** INTE lista av råa `String` i `Main` som enda modell.

---

## Klass vs objekt

```mermaid
flowchart LR
  klass["Klass Medlem<br/>= mall / visitkortmall"] --> obj1["Objekt: Kim 1001"]
  klass --> obj2["Objekt: Moa 1002"]
  obj1 --> list["List&lt;Medlem&gt; i Register"]
  obj2 --> list
```

**Målsvar (säg högt / skriv i README):** *“Klassen är mallen. Objektet är en konkret medlem i listan.”*

**Kom ihåg / INTE:** INTE “klass = bara en fil utan objekt”.

---

## Meny + sök träff/miss

```mermaid
flowchart TD
  loop["Meny-loop tills avsluta"] --> add["1 Lägg till"]
  loop --> listAll["2 Lista alla"]
  loop --> search["3 Sök"]
  loop --> quit["4 Avsluta"]
  search --> hit["Träff → skriv ut namn + nummer"]
  search --> miss["Miss → tydligt meddelande, ingen krasch"]
```

**Kom ihåg / INTE:** Miss är **krav** — inte “bara om vi hinner”.

---

## Git i grupp — flöde

```mermaid
flowchart LR
  edit["Ändra"] --> add["git add"]
  add --> commit["git commit"]
  commit --> pull["git pull"]
  pull --> push["git push"]
```

**Vad diagrammet visar:** Pull **före** push när ni delar remote.  
**Kom ihåg / INTE:** INTE PR som examkrav. INTE sex commits sista kvällen utan att alla syns.

**Målsvar (säg högt / skriv i README):** *“Ändra → add → commit → pull → push. Alla syns under Commits.”*

---

## README — fem block

```mermaid
flowchart TB
  r1["Q1 Datalogiskt"]
  r2["Q2 Klass / objekt"]
  r3["Q3 Git i grupp"]
  r4["Ett problem ni löste"]
  r5["AI-reflektion"]
  r1 --> r2 --> r3 --> r4 --> r5
```

**Kom ihåg / INTE:** Varje block = egna meningar + pekning — inte briefen copy-paste.

---

## Klart-check → gap → commit

```mermaid
flowchart LR
  check["Klart-check"] --> gap["Vad saknas?"]
  gap --> code["Jobba i grupprepo"]
  code --> readme["README-utkast"]
  readme --> c1["Meningsfull commit"]
```

**Vad diagrammet visar:** Det här paketet = utkast + gap + start — färdig app = examinationsveckan (v8).  
**Kom ihåg / INTE:** INTE nytt individuellt repo. INTE Account-kopia.

---

## Leverans Exam 2

```mermaid
flowchart TB
  repo["Gemensamt publikt GitHub-repo<br/>kod + README + ≥6 commits · alla syns"]
  moodle["Moodle v8 — klistra in länken"]
  repo --> moodle
```

**Vad diagrammet visar:** En leverans: **repo-länk**. Ingen muntlig för Exam 2.  
**Kom ihåg / INTE:** Betyg **IG/G** — **ingen VG**.

---

## Checkpoint (privat)

Säg högt: data→klasser→meny, klass vs objekt, sök miss, pull före push, fem README-block, Moodle v8 utan muntlig. Jämför med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
