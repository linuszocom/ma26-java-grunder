# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt* och skriva i README.

Sedan: öppna facit och rätta dig.

---

## Frågor — Exam 2-krav

1. Vilka **tre** `.java`-filer kräver Examination 2 (svenska namn)?  
2. Vilka fält ska `Medlem` minst ha — och vilken synlighet?  
3. Vilka **tre** metoder ska `Register` minst ha?  
4. Vilka **fyra** menyval ska `Main` ha?  
5. Vad betyder sök **träff + miss** i en mening?  
6. Vad ska ni **se när ni kör** (minst) innan inlämning?  
7. Hur många **commits** minst — och vad mer krävs under Commits?  
8. Finns **VG** på Examination 2? Finns **muntlig**?  
9. Vad lämnar ni in i Moodle — och **när** (kalendervecka)?  
10. Nämn **tre** saker Exam 2 **inte** är (utöver “inte VG”).

---

## Frågor — README

11. README Q1: skriv kedjan **data → … → …** med era fil-/menyord.  
12. README Q2: vad är skillnaden mellan **klass** och **objekt** i er app?  
13. README Q3: ge flödet med fyra Git-steg och hur ni undviker överskrivning.  
14. Vad ska stycket **“Ett problem ni löste”** innehålla (minst två saker)?  
15. Vad ska **AI-reflektion** innehålla om ni använt AI?

---

## Frågor — felsökning / ägarskap

16. Varför är det fel att lämna in **Exam 1-repot** eller kurs-hubben som Exam 2?  
17. AI ger `Account` + factory + “sikta VG”. Vad gör du?  
18. AI skriver README Q1: *“Vi planerade bra med datalogiskt tänkande.”* Varför räcker det inte?  
19. Peka i *ert* grupprepo eller gap-lista: en rad för Q1, en för Q2, en för Q3, en för problem **eller** AI.

---

## Facit

<details>
<summary>Fråga 1 — tre filer</summary>

`Medlem.java`, `Register.java`, `Main.java` (svenska namn).

</details>

<details>
<summary>Fråga 2 — Medlem</summary>

Minst **namn** (`String`) och **medlemsnummer** (`int`), fälten **private**, plus konstruktor och get-metoder (t.ex. `getNamn()`).

</details>

<details>
<summary>Fråga 3 — Register</summary>

**Lägg till** medlem, **lista alla**, **sök på namn** (träff eller saknas). Listan t.ex. `ArrayList<Medlem>`.

</details>

<details>
<summary>Fråga 4 — meny</summary>

1. Lägg till medlem · 2. Lista alla · 3. Sök medlem · 4. Avsluta — i loop med Scanner.

</details>

<details>
<summary>Fråga 5 — träff + miss</summary>

Hitta och skriv ut medlem som **finns**, **och** visa tydligt när namnet **saknas** — utan krasch.

</details>

<details>
<summary>Fråga 6 — körning</summary>

Minst **två** medlemmar, lista dem, sök en som finns, sök en som inte finns, avsluta utan krasch.

</details>

<details>
<summary>Fråga 7 — commits</summary>

Minst **6** commits totalt. **Alla** i gruppen syns under Commits (egna commits eller båda namnen i meddelandet).

</details>

<details>
<summary>Fråga 8 — VG / muntlig</summary>

**Nej** till båda. Bara **IG/G**. VG och muntligt djup sitter på Examination 1. Exam 2 = repo-länk.

</details>

<details>
<summary>Fråga 9 — Moodle</summary>

Länk till gruppens **publika** GitHub-repo, under **examinationsveckan (v8)** — deadline enligt schema.

</details>

<details>
<summary>Fråga 10 — INTE</summary>

Exempel: INTE GUI/DB/Android · INTE kopiera `Account` · INTE factory/arv som krav · INTE PR som krav · INTE individuellt repo · INTE muntlig.

</details>

<details>
<summary>Fråga 11 — Q1</summary>

**Data** (namn, nummer) → **klasser** (`Medlem`, `Register`, `Main`) → **meny** (lägg till, lista, sök, avsluta).

</details>

<details>
<summary>Fråga 12 — Q2</summary>

**Klass** = mall (`Medlem`). **Objekt** = konkret medlem (`new`) i listan. Variabler bara i `Main` räcker inte för `List<Medlem>`.

</details>

<details>
<summary>Fråga 13 — Q3</summary>

Ändra → `add` → `commit` → `pull` → `push`. Undvik överskrivning: filansvar, synka ofta, pull före push.

</details>

<details>
<summary>Fråga 14 — problem</summary>

**Vad** som strulade (konkret) och **hur** ni löste det — inte “det löste sig”.

</details>

<details>
<summary>Fråga 15 — AI</summary>

Hur ni körde fast; **ett exempel** där ni **ändrade** AI-förslaget. Inte bara “vi använde AI”.

</details>

<details>
<summary>Fråga 16 — fel repo</summary>

Exam 2 är **grupp** och ett **nytt** medlemsprojekt. Exam 1-repo / kurs-hubb har fel historik, fel namn och fel leveransform.

</details>

<details>
<summary>Fråga 17 — AI Account/VG</summary>

Stryk. Behåll svenska tre filer enligt Klart-check. Ingen factory/arv/VG/muntlig som Exam 2-krav.

</details>

<details>
<summary>Fråga 18 — svag Q1</summary>

Saknar **steg** och **pekning** (data, klassfiler, meny). Tom fras går inte att koppla till er app.

</details>

<details>
<summary>Fråga 19 — peka</summary>

Subjektivt — rimligt svar pekar på:

- **Q1:** data→klasser→meny med era filnamn  
- **Q2:** `Medlem` + `List<Medlem>` / `new`  
- **Q3:** pull/push eller commit där flera syns  
- **Problem/AI:** konkret händelse eller ändrat förslag  

Fel: “README finns” utan pekning.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, README-utkast finns, gap-lista är gjord, och examinationskod är påbörjad i grupprepots:

- [ ] Målsvar **data → klasser → meny** — egna ord, högt  
- [ ] Målsvar **klass vs objekt** — egna ord, högt  
- [ ] Vet **Klart-check** + vad Exam 2 **inte** är (ingen VG, ingen muntlig)  
- [ ] README-utkast Q1–Q3 (+ problem/AI påbörjat)  
- [ ] Gap-lista mot grupprepo + minst en meningsfull commit  
- [ ] AI-träning med FEEDBACK-rader (svag README + Account-råd)  

Då har du landat v43 Pass 3. Nästa: vecka 44 — färdigställ medlemsregistret och lämna in GitHub-länk (*publiceras i* `20-exam-2/`). Repetera [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md).
