# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Varför ska sök-loopen stå i `Register.sökNamn` och **inte** i `Main`?  
2. Vad skrivs ut vid **hit** respektive **miss** — och var i metoden sitter miss-raden?  
3. Varför `getNamn().equalsIgnoreCase(namn)` — inte `m == namn` eller `m.namn`?  
4. Vad händer om du glömmer `return` efter träff?  
5. Vad händer om `"Medlemmen saknas"` står i `else` inne i loopen?  
6. Vilka menyval (1–4) ska finnas — och hur avslutas loopen?  
7. Varför behövs `scanner.nextLine()` direkt efter `scanner.nextInt()` för menyvalet?  
8. Vad gör case 3 i `Main` — och vad ska den **inte** göra?  
9. Varför deklareras listan som `List<Medlem>` men skapas med `new ArrayList<>()`?  
10. Peka i *din* övningskod: `sökNamn`, miss-raden, `nextLine` efter `nextInt`, case 4.  
11. *(Koppling Exam 2)* Vilken kedja ska du kunna **köra** innan inlämning (sex steg)?  
12. *(Koppling Exam 2)* Om någon frågar “vilken metod söker?” — vad pekar du på?

---

## Facit

<details>
<summary>Fråga 1 — varför inte sök i Main</summary>

Listan är `private` i `Register`. Main ska fråga via metod, inte bläddra. Exam kräver att du kan peka på sökmetoden — den hör hemma i registret.

**Målsvar-nivå:** *“Main anropar sökNamn. Loopen över medlemmar bor i Register.”*

</details>

<details>
<summary>Fråga 2 — hit vs miss</summary>

**Hit:** namn + medlemsnummer, sedan `return`.  
**Miss:** `Medlemmen saknas` — **en** gång **efter** `for`, när ingen träff returnerat.

</details>

<details>
<summary>Fråga 3 — equalsIgnoreCase</summary>

`==` jämför referenser, inte text. `namn` är `private` — använd `getNamn()`. `equalsIgnoreCase` gör att `"elsa"` hittar `"Elsa"`.

</details>

<details>
<summary>Fråga 4 — glömd return</summary>

Loopen fortsätter. Du kan få fler utskrifter eller konstigt flöde. Early `return` = “klart, sluta leta”.

</details>

<details>
<summary>Fråga 5 — saknas i else</summary>

Varje icke-matchande medlem ger en saknas-rad → **storm** i konsolen. Miss hör efter hela genomsökningen.

</details>

<details>
<summary>Fråga 6 — meny</summary>

1 Lägg till · 2 Lista · 3 Sök · **4 Avsluta** (`kör = false` så `while` stannar).

</details>

<details>
<summary>Fråga 7 — nextLine efter nextInt</summary>

`nextInt()` lämnar `\n` i bufferten. Utan ätare äter nästa `nextLine()` den tomma raden → namn blir `""` / frågan hoppas över.

</details>

<details>
<summary>Fråga 8 — case 3</summary>

**Gör:** läs söksträng, anropa `register.sökNamn(...)`.  
**Gör inte:** for-each över listan, speja via bara `listaAlla`, skapa medlem i sök.

</details>

<details>
<summary>Fråga 9 — List vs ArrayList</summary>

**`List`** = deklarationstyp (kursstandard / gränssnitt). **`ArrayList`** = konkret implementation som skapas. Samma mönster som tidigare paket.

</details>

<details>
<summary>Fråga 10 — peka i din kod</summary>

Subjektivt — rimligt svar pekar på:

- **`sökNamn`:** for-each + `equalsIgnoreCase` + `return` vid hit  
- **Miss:** println efter `for`  
- **Scanner:** `nextLine()` efter meny-`nextInt`  
- **case 4:** `kör = false`

Fel svar: “AI skrev det” utan pekning.

</details>

<details>
<summary>Fråga 11 — Exam-körning</summary>

(1) Lägg till medlem 1 · (2) Lägg till medlem 2 · (3) Lista → två rader · (4) Sök träff · (5) Sök miss · (6) Avsluta utan krasch.

</details>

<details>
<summary>Fråga 12 — peka sökmetod</summary>

Öppna `Register.java` och peka på **`sökNamn`**. Inte en for-each i `Main`. Inte “jag tittar i listan”.

</details>

---

## Klart för paketet?

Om dina svar ligger nära facit, övningarna körts i IDE:n, och du kan peka i egen kod:

- [ ] Målsvar sök (Register, hit/miss) — egna ord, högt  
- [ ] Målsvar meny (Scanner, switch →, case 3 anropar) — egna ord, högt  
- [ ] Uppgift 1 (`sökNamn`) och uppgift 2 (full meny-demo) körda  
- [ ] AI-träning med minst tre FEEDBACK-rader (sök / Scanner / miss)  

Då har du landat sök + meny för medlemsregistret. Nästa steg: [19-exam2-start](../19-exam2-start/) — README och gap mot Klart-check. Saknar du listan: [17-lista-register](../17-lista-register/). Saknar du tre filer: [15-tre-klasser](../../vecka-42/15-tre-klasser/).
