# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför ska listan av `Medlem` ligga i **`Register`** och inte i **`Main`**?  
2. Vad är skillnaden mellan **`List<Medlem>`** som deklarerad typ och **`new ArrayList<>()`**?  
3. Vad betyder det att fältet är **`private`** — och hur lägger `Main` då till en medlem?  
4. Vad gör **`läggTill(Medlem m)`** — en mening?  
5. Vad gör **`listaAlla()`** — och vilka metoder på `Medlem` använder den?  
6. Vad ser du i konsolen efter `new Register()` + `listaAlla()` **utan** `läggTill`? Är det ett fel?  
7. Skriv (ungefär) de **tre raderna** i `Main` efter `new Register()` som lägger till Kim och Moa och skriver ut.  
8. Nämn **två saker** som hör till **senare paket**, inte till det här.  
9. *(Exam-förebåd)* Någon frågar: *“Var ligger listan?”* — vad svarar du, och **vilken fil** öppnar du?  
10. Varför är **`private ArrayList<Medlem> medlemmar`** sämre än **`private List<Medlem> medlemmar`** enligt kursens kodstandard?  
11. Vad händer om `Main` skriver `register.medlemmar.add(...)`?  
12. Peka i *din* övningskod: listfältet, `läggTill`, `listaAlla`, två anrop i `Main`.  
13. Vilka **två imports** behövs typiskt i `Register` för listfältet?

---

## Facit

<details>
<summary>Fråga 1 — hemvist</summary>

Samlingen ska ägas av registret. Examination 2 kräver att du pekar listan i `Register`. Lista i `Main` kompilerar men är fel rum.

**Målsvar-nivå:** *“Listan bor i Register. Main anropar bara metoder.”*

</details>

<details>
<summary>Fråga 2 — List vs ArrayList</summary>

`List<Medlem>` = deklarerad typ (skylten). `new ArrayList<>()` = hur den tomma listan skapas. Kursmönster: interface utåt, `ArrayList` vid `new`.

</details>

<details>
<summary>Fråga 3 — private</summary>

Bara kod **inuti** `Register` når fältet direkt. `Main` anropar `läggTill` — inte `medlemmar.add`.

</details>

<details>
<summary>Fråga 4 — läggTill</summary>

Tar emot en `Medlem` och gör `medlemmar.add(m)` inuti `Register`.

</details>

<details>
<summary>Fråga 5 — listaAlla</summary>

Loopar listan och skriver namn + medlemsnummer via `getNamn()` och `getMedlemsnummer()`. Skapar inte medlemmar och söker inte.

</details>

<details>
<summary>Fråga 6 — tom lista</summary>

Ingen (eller tom) utskrift. Förväntat — size 0. Inte bevis att fältet saknas.

</details>

<details>
<summary>Fråga 7 — Main-rader</summary>

Ungefär:

```java
register.läggTill(new Medlem("Kim", 101));
register.läggTill(new Medlem("Moa", 102));
register.listaAlla();
```

</details>

<details>
<summary>Fråga 8 — senare</summary>

T.ex. `sökNamn`, Scanner-meny 1–4, factory, arv — **inte** i slug 17.

</details>

<details>
<summary>Fråga 9 — Exam-peka</summary>

Öppna **`Register.java`**. Peka på `private List<Medlem> medlemmar`. Säg att `Main` inte äger listan.

</details>

<details>
<summary>Fråga 10 — ArrayList som typ</summary>

Kodstandarden: deklarera `List`, skapa med `ArrayList`. `ArrayList` som fälttyp läcker implementationstypen.

</details>

<details>
<summary>Fråga 11 — add från Main</summary>

Kompileringsfel (*has private access*) — eller du har gjort fältet publikt (fel). Fix: `läggTill`.

</details>

<details>
<summary>Fråga 12 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- `private List<Medlem> medlemmar = new ArrayList<>();` i `Register`  
- metoden **`läggTill`** med `add`  
- metoden **`listaAlla`** med for-each + getters  
- två **`läggTill`** + **`listaAlla`** i `Main`  

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 13 — imports</summary>

`java.util.List` och `java.util.ArrayList`.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar listans hem — egna ord, högt  
- [ ] Målsvar `List` vs `ArrayList` — egna ord, högt  
- [ ] Målsvar `läggTill` + `listaAlla` — egna ord, högt  
- [ ] Uppgift 1–3 körda (problem → flytta → två medlemmar + utskrift)  
- [ ] AI-träning med minst tre FEEDBACK-rader  

Då har du landat listan i medlemsregistret. Nästa steg i veckan: [18-sok-meny](../18-sok-meny/). Saknar du tre filer / `Medlem`-mur: [15-tre-klasser](../../vecka-42/15-tre-klasser/). Behöver du fräscha `List`/`ArrayList`: [06-arraylist-scanner](../../vecka-38/06-arraylist-scanner/).
