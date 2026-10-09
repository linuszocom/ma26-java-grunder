# 02 — Visuellt: original i arkiv, kopia på remiss

Samma modell som i [01 — Teoriguide](./01-teoriguide.md): **`main` är master-dokumentet i arkivet**, feature-grenen är **arbetskopian på remiss**. Kartorna nedan är flödet, gapet mellan moln och disk, och vad loggen visar efter pull. Ingen konfliktmarkör-karta och ingen klassarkitektur.

GitHub renderar diagrammen automatiskt.

---

## Diagram 1 — remissen blir Pull Request, sedan original

```mermaid
flowchart LR
  a["Person A<br/>feature-titel"]
  b["Person B<br/>feature-medlemmar"]
  pr["GitHub<br/>Pull Request och diff"]
  main["main på GitHub<br/>originalet i arkivet"]

  a -->|"git push -u origin"| pr
  b -->|"git push -u origin"| pr
  pr -->|"kollegan läser raderna<br/>Merge pull request"| main
```

**Vad diagrammet visar:** Arbetskopian lämnar din dator och landar som en Pull Request. En annan person läser diffen innan originalet rör sig.  
**Kom ihåg:** Tre Exam 1-repos är inte ett team. `git push origin main` från din dator är inte det här flödet.

---

## Diagram 2 — de sju stegen

```mermaid
flowchart TD
  A["1. git switch -c feature/namn"] --> B["2. Ändra, git add, git commit"]
  B --> C["3. git push -u origin feature/namn"]
  C --> D["4. Pull Request med kort beskrivning"]
  D --> E["5. Code review och Merge"]
  E --> F["6. git switch main"]
  F --> G["7. git pull origin main"]
```

Läs uppifrån och ner. Steg 4 och 5 händer i webbläsaren. Steg 6 och 7 händer i terminalen, **efter** klicket, och båda i gruppen kör dem. I övningarna heter grenarna `feature-titel`, `feature-medlemmar` och `feature-src-start`.

**Målsvar (säg högt / skriv i README):** *"switch -c, add, commit med namn, push -u origin, Pull Request, en kollega mergar, switch main, pull origin main."*

---

## Direkt efter Merge — två exemplar

Knappen är klickad. Inget mer har hänt i din terminal.

```mermaid
flowchart TB
  subgraph gh ["Vad GitHub vet direkt efter Merge"]
    G1["main har den nya committen"]
    G2["Pull Requesten är mergad"]
  end
  subgraph disk ["Vad min lokala dator vet tills jag pullar"]
    D1["lokal main saknar committen"]
    D2["jag kan stå kvar på feature-grenen"]
  end
```

De två rutorna har ingen pil mellan sig. GitHub stänger inte gapet åt dig.

| | GitHub, sekunden efter Merge | Din dator, innan pull |
| :--- | :--- | :--- |
| `main` | Har titeln, sektionen eller `src/Main.java` | Saknar det som just mergades |
| Var du står | Spelar ingen roll för molnet | Ofta kvar på feature-grenen |
| Nästa `git switch -c` | Skulle utgå från ny `main` | Utgår från gammal `main` om du inte pullat |

Nästa gren föds då i det förflutna: tidslinjen startar innan arkivet fick den senaste committen.

**Målsvar (säg högt / skriv i README):** *"Merge uppdaterar bara GitHub. Utan git switch main och git pull origin main föds nästa feature-gren från en gammal main."*

---

## Efter pull — samma historik på två ställen

```mermaid
flowchart TB
  subgraph remote [Gruppens GitHub]
    R1["Commits — samma meddelanden"]
    R2["Stängd Pull Request"]
  end
  subgraph lokal [Din dator efter pull]
    L1["main"]
    L2["git log --oneline --graph"]
  end
  R1 -->|"git pull origin main"| L1
  R1 -->|"samma namn i meddelandena"| L2
```

Pilen går från arkivet till din dator. Varje rad i grafen är en commit. Namnet i meddelandet är personen. En skarv betyder att en feature-gren mött `main`, oftast vid Merge. Det är inte en konflikt i filen.

Öppna fliken **Commits**. Att filerna syns under **Code** räcker inte ensamt.

---

## Vad arkivet inte ska ta emot

| Mönster i `.gitignore` | Vad det är | Varför det stannar på din dator |
| :--- | :--- | :--- |
| `*.class` | Det `javac` skriver | Binärt resultat, olika varje kompilering |
| `target/` | Byggmapp | Genereras. Hör inte till källkoden |
| `.idea/` | IDE:ns egna filer | Din maskins inställningar, inte gruppens |

**Målsvar (säg högt / skriv i README):** *".gitignore håller *.class, target/ och .idea/ borta. De är resultat på min dator, inte källkod gruppen delar."*

---

## Nytt projekt

```mermaid
flowchart LR
  bad["Kontoappen<br/>Account byter namn"]
  good["Nytt grupprepo<br/>README, gitignore, src/Main.java"]
  exam["Exam 2"]

  bad -.->|"INTE detta"| exam
  good -->|"detta"| exam
```

**Kom ihåg:** Exam 2 är ett nytt projekt. `src/Main.java` i det här paketet är en startkommentar. Klasser kommer senare.

**Målsvar (säg högt / skriv i README):** *"Exam 2 är ett nytt projekt. Vi kopierar inte Kontoappen och byter inte namn på Account."*

---

## Checkpoint (privat)

Utan att titta på teoriguiden: säg högt (1) de sju stegen, (2) skillnaden mellan GitHubs `main` och din `main` direkt efter Merge, (3) varför `*.class` inte ska committas. Jämför sedan med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
