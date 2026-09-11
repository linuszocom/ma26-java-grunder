# 02 — Visuellt: miniräknare, ingång och retur

Samma bilder som i teoriguiden — nu som flöde. Metoder i `Main.java`. Ingen egen klass. GitHub renderar diagrammen automatiskt.

---

## Duplicerat vs en metod

```mermaid
flowchart TB
  subgraph daligt["main med copy-paste"]
    L1["120 * 0.15 + 29"]
    L2["85 * 0.15 + 29"]
    L3["200 * 0.15 + 29"]
  end
  subgraph bra["main + metod"]
    M["beraknaFrakt(...)"]
    A1["anrop order 1"]
    A2["anrop order 2"]
    A3["anrop order 3"]
    A1 --> M
    A2 --> M
    A3 --> M
  end
```

**Vad diagrammet visar:** En kropp, flera anrop. Ändrar du formeln ändras alla ordrar samtidigt.  
**Kom ihåg / INTE:** Copy-paste är inte “snabbare” — det är fler ställen att glömma.

---

## Anrop hoppar in och tillbaka

```mermaid
flowchart LR
  main["main kör"] --> anrop["kmTillMil(10.0);"]
  anrop --> kropp["Metodkropp<br/>return km * 0.621371"]
  kropp --> tillbaka["Tillbaka till main<br/>med returvärde"]
  tillbaka --> spara["resaMil = 6.21..."]
```

**Målsvar (säg högt / skriv i README):** *“Anropet pausar main, kör metoden, fortsätter med returvärdet om typen inte är void.”*

---

## Parameter in — return ut

```mermaid
flowchart LR
  arg1["Argument i main<br/>10.0 km"]
  param["Parameter km<br/>i metoden"]
  calc["Formel<br/>km * 0.621371"]
  ret["return 6.213..."]
  var["Variabel resaMil<br/>i main"]

  arg1 --> param
  param --> calc
  calc --> ret
  ret --> var
```

**Kom ihåg / INTE:** Argument och parameter **behöver inte heta likadant**. Antal och typ måste matcha.

---

## void vs return

```mermaid
flowchart TB
  subgraph voidMetod["void — skrivOrderRad"]
    v1["Parameter: orderNr, total"]
    v2["println till konsol"]
    v3["Inget värde tillbaka"]
  end
  subgraph retMetod["double — beraknaFrakt"]
    r1["Parameter: varde, procent, avgift"]
    r2["return varde * procent + avgift"]
    r3["main sparar i double frakt"]
  end
```

**Vad diagrammet visar:** `void` = jobb klart efter utskrift. `return` = main får ett tal att använda vidare.  
**Kom ihåg / INTE:** `int x = skrivOrderRad(...);` på void → kompileringsfel.

---

## Scope — parametrar stannar i metoden

```mermaid
flowchart TB
  mainScope["main: x = 5"]
  metodScope["metod dubbla(tal):<br/>lokalt = tal * 2<br/>return lokalt"]
  mainScope -->|"anrop dubbla(x)"| metodScope
  metodScope -->|"returvärde y"| mainScope
  ghost["main kan INTE läsa tal eller lokalt"]
  metodScope -.-> ghost
```

**Målsvar (säg högt / skriv i README) — scope:** *“Parametrar och lokala variabler syns bara inuti metoden. main får bara returvärdet.”*

---

## Refaktorering — före och efter

```mermaid
flowchart LR
  fore["Före: samma rad<br/>upprepad 3 gånger"]
  efter["Efter: beraknaFrakt(...)<br/>anropas 3 gånger"]
  fore -->|"bryt ut"| efter
```

**Kom ihåg / INTE:** Refaktorering = samma beteende, renare struktur — inte ny funktion som användaren inte bad om.

---

## Loop + metod

```mermaid
flowchart TD
  loop["for i = 0 .. length-1"]
  hamta["Hämta ordervärde"]
  anrop["frakt = beraknaFrakt(...)"]
  skriv["println frakt"]
  loop --> hamta --> anrop --> skriv
  skriv --> loop
```

**Vad diagrammet visar:** Loopen styr **hur många gånger**; metoden styr **hur** varje frakt räknas.

---

## Checkpoint (privat)

Säg högt: en kropp flera anrop, parameter vs argument, void vs return, varför scope stoppar `main` från att läsa parametrar. Jämför sen med diagrammen.

När kartan sitter: [03 — Övningar](./03-ovningar.md).
