# 01 — Teoriguide: Datalogiskt tänkande, README och start av Exam 2

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriva i README. Tar du paketet från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Läs också [Examination 2 — Medlemsregistret](../../examination_2_medlemsregistret.md). Se [mappens README](./README.md).

Du har redan grupprepo, tre klassfiler, lista, sök och meny. Nu: **äg** examinationen — README med egna ord, Klart-check, och kod som gruppen kan stå för. Det är inte magi. Det är nedbrytning före kod + Git-historik där alla syns.

**Förutsättning:** [14-git-team](../../vecka-42/14-git-team/) + [15-tre-klasser](../../vecka-42/15-tre-klasser/) + [16-merge-konflikt](../../vecka-42/16-merge-konflikt/) + [17-lista-register](../17-lista-register/) + [18-sok-meny](../18-sok-meny/). Här: Exam 2-krav, README Q1–Q3 + problem + AI, gap mot Klart-check. **Ingen** factory. **Ingen** arv. **Ingen** `Account`. **Ingen** muntlig för Exam 2. Betyg **IG/G** — **ingen VG**.

---

## Problemet först — “vi kodar först, tänker sen”

Många tänker: “Vi har ju tre filer — klistra in allt i `Main` och lämna in.” Andas. Då får ni en spagetti-app, en vag README, och en historik som ser ut som en dump sista kvällen.

**Dåligt läge** — allt i ett huvud:

```java
public class Main {
    public static void main(String[] args) {
        // namn1, nr1, namn2, nr2, ArrayList av String...
        // meny, sök, allt här — ingen Medlem, ingen Register
    }
}
```

**Bättre tanke:** Bryt ner **innan** ni kodar färdigt: vilken **data** → vilka **klasser** → vilken **meny**. Det är datalogiskt tänkande — och det är README Q1.

---

## Datalogiskt tänkande — data → klasser → meny

**Metafor:** **Klubbreception.** Först: vilka uppgifter behövs på visitkortet (namn, medlemsnummer)? Sedan: vilka rum (filer) — visitkort (`Medlem`), pärm (`Register`), disk (`Main`)? Sist: vilka knappar på disken (menyval)?

**Vad det är:** Att **dela upp** “ett medlemsregister” i steg innan (och under) kodningen.  
**Varför det finns:** Ni undviker att allt växer i `Main`. Examinationen mäter att ni kan **planera** — README Q1.  
**Om det saknas / vad det INTE är:** INTE “vi samarbetade bra”. INTE att kopiera briefen. INTE att börja med GUI/databas.

| Steg | Fråga | Er app |
|------|--------|--------|
| 1. Data | Vad ska lagras per medlem? | `namn` (`String`), `medlemsnummer` (`int`) |
| 2. Klasser | Vilka ansvar? | `Medlem` · `Register` · `Main` |
| 3. Meny | Vad kan användaren göra? | lägg till · lista · sök · avsluta |

**Målsvar (säg högt / skriv i README):**  
*“Vi bröt ner registret: data (namn, nummer) → klasser (Medlem, Register, Main) → meny (lägg till, lista, sök, avsluta) innan vi kodade klart.”*

---

## Klass och objekt — varför inte bara variabler i Main?

**Metafor:** **Visitkortmall vs ett tryckt kort.** Klassen `Medlem` är mallen. Ett **objekt** är ett konkret kort i pärmen — skapat med `new`.

**Vad det är:** `Medlem` = typen (mall). `new Medlem("Kim", 1001)` = ett objekt i minnet. `Register` håller en `List<Medlem>`.  
**Varför:** Lista, sök och lägg-till behöver **objekt** — inte lösa `String`-variabler i `Main`.  
**Om det saknas / vad det INTE är:** INTE “klass är bara en fil”. INTE engelska `Account`/`Member`. INTE factory-mönster från Examination 1 som krav här.

```java
Medlem m = new Medlem("Kim", 1001);  // objekt
register.laggTill(m);                 // objektet i listan
```

**Målsvar (säg högt / skriv i README):**  
*“Medlem är klassen. Ett objekt är en konkret medlem i listan. Variabler bara i Main räcker inte — då kan Register inte hålla `List<Medlem>`.”*

---

## Exam 2 — vad G kräver (och vad som INTE ingår)

**Vad det är:** Gruppens **konsolapp** i Java + **gemensamt publikt** GitHub-repo + **README**.  
**Varför:** Kursmål: datalogiskt tänkande, OOP, Git i grupp, körbar app.  
**Om det saknas / vad det INTE är:**

| Det **är** | Det är **INTE** |
|------------|-----------------|
| `Medlem` / `Register` / `Main` (svenska) | Kopiera `Account.java` / engelska namn |
| Meny: lägg till, lista, sök, avsluta | GUI, databas, Android |
| Sök **träff** och **miss** | Bara träff — miss måste synas utan krasch |
| ≥ **6** commits; **alla** syns | En dump-commit / bara en syns |
| README Q1–Q3 + problem + AI | Tomma fraser utan pekning |
| Betyg **IG / G** | **VG** (finns inte här) |
| Länk i Moodle **v44** | Muntlig redovisning för Exam 2 |
| Ett **grupprepo** | Individuellt Exam 1-repo / kurs-hubb |
| `pull` före `push` | Pull request som krav |

**Målsvar (säg högt / skriv i README):**  
*“Exam 2 = gruppens Medlem/Register/Main, meny med sök träff+miss, publikt grupprepo, ≥6 commits där alla syns, README — IG eller G, ingen VG, ingen muntlig.”*

---

## Klart-check — måltavlan innan inlämning

Kryssa i huvudet (full lista i [examination_2_medlemsregistret.md](../../examination_2_medlemsregistret.md)):

- [ ] **Main går att köra** i IDE:n  
- [ ] Minst tre `.java`-filer: `Medlem`, `Register`, `Main`  
- [ ] `Medlem` har **private** fält, **konstruktor** och get-metoder  
- [ ] Menyn: lägg till, lista, sök (träff + miss), avsluta  
- [ ] Körning: två medlemmar; sök träff; sök miss  
- [ ] Publikt gemensamt GitHub-repo  
- [ ] Minst **6** commits; **alla** i gruppen syns  
- [ ] `README.md` enligt Q1–Q3 + problem + AI  

Det här paketet kräver **utkast + gap-lista + påbörjad kod** — inte att allt är kryssat idag.

---

## README — fem block (egna ord)

Examinationen kräver **gemensam** `README.md`. Ungefär **2–4 meningar** per fråga. Peka på **er** kod och **era** commits.

### Q1 — Datalogiskt tänkande

Hur bröt ni ner “ett medlemsregister” i steg **innan** ni kodade?  
**Målsvar:** data → klasser → meny (se ovan).  
**INTE:** “Vi planerade bra.”

### Q2 — Klass / objekt

Varför är `Medlem` en **klass** och inte bara variabler i `Main`? Vad är ett **objekt** i er app?  
**Målsvar:** mall vs konkret medlem i `List<Medlem>`.  
**INTE:** “OOP är viktigt.”

### Q3 — Git i grupp

Ge ett exempel: `add` / `commit` / `pull` / `push`. Hur undvek ni att skriva över varandra?  
**Målsvar:** pull före push, filansvar, synka ofta.  
**INTE:** “Vi använde Git.”

### Ett problem ni löste

Vad strulade (konflikt, rejected push, fel remote, NullPointer…)? Vad gjorde ni?  
**INTE:** “Det löste sig.”

### AI-reflektion (3–5 meningar)

Hur när ni körde fast? Om AI: **ett exempel** där ni **ändrade** förslaget.  
**Ägarskap:** Varje person måste kunna förklara **sin** del. Kan du inte = IG för dig.

---

## Fortsätt i grupprepo — inte nytt individuellt

**Vad det är:** Samma gemensamma publika repo ni byggt i vecka 42–7.  
**Varför:** Examination 2 är **grupp**. Historiken ska visa alla.  
**Om det saknas / vad det INTE är:** INTE nytt eget repo. INTE klistra Kontoappen. INTE PR som krav.

**Metod — när ni tvekar:**

1. Öppna **Klart-check** — vad saknas?  
2. Jobba mot **gapet** (lista, sök, meny från tidigare paket).  
3. Skriv README-utkast **med pekning**.  
4. **Minst en meningsfull commit** nu — inte sex sista kvällen.  
5. `git pull` innan `git push`.

**Målsvar (säg högt / skriv i README) — metod:**  
*“Gap mot Klart-check först. README egna ord med fil/steg. Commitar smått så alla syns. Pull före push.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| Kopierar `Account` / engelska namn | Nytt projekt — svenska `Medlem`/`Register`/`Main` |
| Lista bara i `Main` | Listan ska ligga i `Register` |
| Individuellt repo | Ett gemensamt publikt grupprepo |
| Förväntar VG / muntlig / PR | IG/G; ingen muntlig; ingen PR som krav |
| README = briefen copy-paste | Egna meningar + pekning i kod/historik |
| `"fix"` / en dump-commit | Beskriv vad som hände; ≥6 commits; alla syns |
| AI-reflektion: “vi använde ChatGPT” | Ett exempel där ni **ändrade** förslaget |
| GUI / DB / Android | Konsol + IDE + JDK |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar:

1. README Q1 i **en** mening (data → klasser → meny).  
2. README Q2: vad är ett **objekt** i er app?  
3. Lista tre saker Exam 2 **inte** är.  
4. Tre punkter från Klart-check ni redan har / saknar.  
5. En konkret händelse till “Ett problem ni löste” (eller planerad).

När du kan säga svaren högt: gå vidare.

---

## Nästa steg

[02 — Visuellt](./02-visuell.md), sedan [03 — Övningar](./03-ovningar.md).
