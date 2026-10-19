# 03 — Övningar

**Omfång det här paketet:** README-utkast till Examination 2 (Q1 datalogiskt, Q2 klass/objekt, Q3 Git i grupp, ett problem, AI-reflektion). **Klart-check mot grupprepo** — gap-lista, inte färdig lösning. Fortsätt examinationskod i **gemensamt** repo. **Ingen** full exam-dump, **ingen** factory/arv, **ingen** `Account`, **ingen** muntlig.

AI får föreslå text. Ni måste kunna **peka och förklara** README-svar och er kod.

**Var ni kör:** Gruppens **publika** GitHub-repo + IDE med JDK. Läs [Examination 2 — Medlemsregistret](../../examination_2_medlemsregistret.md).

**Bygger på:** [17-lista-register](../17-lista-register/), [18-sok-meny](../18-sok-meny/), gruppgit från [14-git-team](../../vecka-42/14-git-team/). Saknar ni meny/sök — gör README + gap-lista ändå, och bygg minimalt skelett.

---

## Uppgift 1 — Gap mot Klart-check (grupprepo)

**Mål:** Veta **exakt** vad som saknas innan ni kodar mer.

**Scenario:** Examinationen bedömer kod **och** historik. Övningskod räcker inte om den ligger kvar utanför grupprepots eller saknar README.

**Krav:**
1. Öppna [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md) — sektionen **Klart-check**.
2. I grupprepots (eller gemensam anteckning) skapa en **gap-lista**: tre kolumner `Krav | Har vi? | Nästa steg`.
3. Bocka av privat: Main körbar · tre filer · private+konstruktor+get · meny · sök träff+miss · två medlemmar i körning · publikt repo · ≥6 commits-plan · alla syns · README.
4. Skriv **en mening**: vad Exam 2 **inte** är (t.ex. ingen VG, ingen muntlig, ingen Account-kopia).

**Klart-check (peka i ER miljö):**
- [ ] Gap-listan finns i repo eller Docs som **alla** i gruppen ser  
- [ ] Ni vet om remote är **publikt** och gemensamt  
- [ ] Ni har skrivit vad Exam 2 **inte** är  

**INTE krav nu:** Att alla rutor är gröna — det är målbilden för v8.

**Ägarskap:** Varje person ska kunna säga **sin** nästa uppgift från gap-listan.

---

## Uppgift 2 — README Q1–Q3 (egna ord, peka i kod)

**Mål:** Skriv **utkast** (~2–4 meningar per fråga) i gruppens `README.md`. Text ska matcha **er** kod — inte kopierad brief.

**Brief:** Examinationen kräver att ni förstår nedbrytning, klass/objekt och Git i grupp.

Lägg in rubrikstruktur om den saknas:

```markdown
# Klubbens medlemsregister
Kort: konsolapp — lägg till, lista, sök medlemmar.

## Köra
JDK + IDE. Main.

## Teori
### 1. Datalogiskt tänkande
(utkast)

### 2. Klass och objekt
(utkast)

### 3. Git i grupp
(utkast)

## Ett problem vi löste
(utkast)

## AI-reflektion
(utkast)
```

### Q1 — Datalogiskt tänkande

**Krav:**
1. Beskriv hur ni bröt ner “medlemsregister” **innan** (eller medan) ni kodade.
2. Använd kedjan **data → klasser → meny**.
3. Nämn filerna `Medlem`, `Register`, `Main`.

**Klart-check:**
- [ ] Orden **data**, **klasser** och **meny** (eller motsvarande steg) syns  
- [ ] Ni kan peka på tre filer när ni säger Q1  

### Q2 — Klass / objekt

**Krav:**
1. Varför `Medlem` som **klass** — inte bara variabler i `Main`?
2. Vad är ett **objekt** hos er? (t.ex. `new Medlem(...)` i listan)
3. Peka på `List<Medlem>` (eller `ArrayList<Medlem>`) i `Register`.

**Klart-check:**
- [ ] Ordet **objekt** och **`new`** (eller “skapad medlem”) finns  
- [ ] Ni skiljer mall (klass) från konkret medlem  

### Q3 — Git i grupp

**Krav:**
1. Ge ett konkret flöde med `add` / `commit` / `pull` / `push`.
2. En mening: hur ni undvek att **skriva över** varandra (filansvar, synka ofta, pull först…).
3. Nämn att **alla** ska synas under Commits (≥6 totalt inför inlämning).

**Klart-check:**
- [ ] `pull` nämns **före** eller i samband med `push`  
- [ ] INTE bara “vi använde Git”  

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning README Q1–Q3 (efter eget utkast)</summary>

**Q1:** Data namn+nummer → klasser Medlem/Register/Main → meny lägg till/lista/sök/avsluta.  
**Q2:** Medlem = mall; objekt = konkret medlem i List&lt;Medlem&gt;; variabler i Main räcker inte.  
**Q3:** Ändra → add → commit → pull → push; filansvar/synka; alla syns under Commits.

</details>

---

## Uppgift 3 — Problem + AI i README (inte lösningdump)

**Mål:** Fylla de två sista blocken med **konkreta** meningar — träning inför inlämning.

**Krav:**
1. Under **Ett problem vi löste:** några meningar. Vad strulade (konfliktmarkörer, rejected push, fel remote, sök som kraschade…)? Vad gjorde ni? Fil/kommando om ni minns.
2. Under **AI-reflektion:** 3–5 meningar. Hur när ni körde fast? Om AI: **ett exempel** där ni **ändrade** förslaget (t.ex. Account-namn → Medlem, lista i Main → Register, vag README → pekning).
3. **Committa** README-utkastet med begripligt meddelande (t.ex. `docs: README utkast Q1–Q3`). `git pull` före `git push`.

**Klart-check:**
- [ ] Problem-stycket har **händelse**, inte “det löste sig”  
- [ ] AI-stycket har **en konkret ändring** (eller tydligt “vi körde utan AI + hur vi felsökte”)  
- [ ] Commit syns på GitHub med **ditt/ert** namn  

**Ägarskap:** README får vara utkast — men varje person ska kunna utöka **sin** del utan att läsa upp andras text.

---

## Uppgift 4 — Start/fortsätt examinationskod (gap, inte dump)

**Mål:** Minska gapet från uppgift 1. **Inte** klistra in en färdig lösning från AI.

**Krav:**
1. Välj **ett** gap från listan (t.ex. sök-miss-meddelande, menyval, private på Medlem, första körning med två medlemmar).
2. Implementera **bara det** i grupprepots — svenska namn, lista i `Register`.
3. Kör igenom det ni kan: lägg till → lista → sök (om klart).
4. Minst **en meningsfull commit** per person som kodar idag (eller gemensam commit med **båda namnen** i meddelandet om samma dator).

**Klart-check (peka i ER kod):**
- [ ] Ändringen syns i **grupprepots**, inte bara lokalt hos en  
- [ ] Ingen `Account` / factory / arv tillagd “för säkerhets skull”  
- [ ] Commit-meddelandet beskriver **vad** som hände  

**INTE krav nu:** Färdig app, sex commits totalt, polerad README-prosa — det är v8.

**Stretch (valfritt, inom G):** Polera en vag README-mening; öva högt att peka på sök träff **och** miss; kolla att **alla** syns under Commits och planera nästa commits.

---

## Exam Klart-check (referens — inte allt ska vara klart idag)

Använd [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md) som **målbild**. Markera det ni **redan** har efter v7 — resten v8.

**Kod (G):**
- [ ] `Main` körbar i IDE  
- [ ] `Medlem` / `Register` / `Main`  
- [ ] private + konstruktor + get  
- [ ] Meny: lägg till, lista, sök, avsluta  
- [ ] Sök träff **och** miss  
- [ ] Två medlemmar i testkörning  

**Git + README:**
- [ ] Publikt gemensamt repo  
- [ ] ≥6 commits; **alla** syns  
- [ ] README Q1–Q3 + problem + AI (utkast OK här)  

**INTE:**
- [ ] VG / muntlig / PR som krav  

---

## När ni kört fast

1. README känns tomt → peka en **fil** eller **steg**, skriv från pekningen.  
2. Osäker på krav → öppna Klart-check i briefen, inte AI-gissning.  
3. AI ger `Account` / factory → stryk; behåll svenska tre filer.  
4. Push rejected → `git pull`, lös, commit, push — dokumentera under “problem”.  
5. Jämför [01-teoriguide](./01-teoriguide.md), [04 — AI-träning](./04-ai-traning.md).

Nästa: [04 — AI-träning](./04-ai-traning.md).
