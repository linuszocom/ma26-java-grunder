# 02 — Visuellt: Git-kedjan (eget repo)

Samma **verkstadsjournal**-bild som i teoriguiden — nu som flöde. Ingen gren-karta: add → commit → push + fliken Commits räcker.

GitHub renderar diagrammen nedan automatiskt.

---

## Var sakerna bor

```mermaid
flowchart LR
  disk["Java-filer på disken<br/>IDE Spara"]
  git["Git — lokal journal<br/>på DIN dator"]
  gh["GitHub — arkivskåp<br/>på nätet"]

  disk -->|"git add + commit"| git
  git -->|"git push"| gh
```

**Vad diagrammet visar:** Spara i IDE:n stannar till vänster. Historiken sitter i mitten. Examinationen tittar till höger.  
**Kom ihåg / INTE:** Git ≠ GitHub. Utan push syns inget under Commits på github.com.

---

## Kedjan när du har en ändring

```mermaid
flowchart TD
  A["Liten, begriplig ändring?"] --> B["git status — vad är nytt?"]
  B --> C["git add filerna"]
  C --> D["git commit -m meddelande"]
  D --> E["git push"]
  E --> F["Kolla github.com → Commits"]
```

**Om du hoppar till push direkt:** ofta inget att skicka, eller fel filer. Gå tillbaka till status → add → commit.

**Målsvar (säg högt / skriv i README):**  
*“Add väljer, commit sparar ögonblicksbilden, push skickar den till GitHub. Sedan kollar jag fliken Commits.”*

---

## Lokalt vs GitHub — två platser, samma historik (efter push)

```mermaid
flowchart TB
  subgraph lokal [På din dator]
    L1["Working folder<br/>Main.java"]
    L2["Git-commits<br/>lokala stämplar"]
  end
  subgraph remote [På GitHub]
    R1["Filer under Code"]
    R2["Fliken Commits<br/>Exam tittar här"]
  end
  L1 -->|"add + commit"| L2
  L2 -->|"push"| R1
  L2 -->|"push"| R2
```

**Vad det INTE är:** Att filerna syns under **Code** räcker inte ensamt — öppna också **Commits** och läs meddelandena.

---

## Exam 1 — vad som ska synas

```mermaid
flowchart LR
  A["Eget repo"] --> B["Publikt"]
  B --> C["≥ 5 commits"]
  C --> D["Begripliga meddelanden"]
  D --> E["Syns under Commits"]
```

Till vänster utan kedjan: “det ligger på min dator”.  
Till höger: något en bedömare kan öppna via din Moodle-länk.

---

## Checkpoint (privat)

Utan att titta på teoriguiden: säg kedjan högt (status → add → commit → push → Commits) och varför Exam 1 kräver publikt repo. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
