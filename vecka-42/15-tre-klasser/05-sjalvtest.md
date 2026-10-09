# 05 — Självtest

Svara först utan facit. Skriv i anteckningar. Sikta på meningar du kan säga högt.

Öppna facit efteråt och rätta dig.

---

## Frågor

1. Varför blir lösa `namn1` och `nummer1` i `Main` ostadiga när registret växer?
2. Vad är ansvaret för `Medlem`, `Register` och `Main` i det här paketet?
3. Varför finns `Register.java` när klassen är tom?
4. Vad betyder `namn has private access in Medlem`, och vad ändrar du?
5. Vad gör `getNamn()` och `getMedlemsnummer()`?
6. Vad händer vid `new Medlem("Kim", 1001)`? Vem sätter fälten?
7. Vad betyder `this.namn = namn` i konstruktorn?
8. Varför är en omdöpning av `Account` till `Medlem` en dålig start?
9. Var ska samlingen av medlemmar bo, och varför deklarerar du den inte i `Main` nu?
10. Nämn tre saker som hör till senare paket, inte till det här.
11. Skriv två till fyra meningar till Examination 2, fråga 2: varför är `Medlem` en klass, och vad är ett objekt i appen?
12. Du har mergat din egen Pull Request. Nästa gren saknar `Medlem.java`. Vad hoppade du över?
13. Vad läser du under **Files changed** innan du klickar Merge, när ingen annan granskar?
14. Vilka tre klassnamn använder medlemsregistret?

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. Namn och nummer är två variabler som kan ändras var för sig. `Main` blir både start och datalager, så klassen har flera skäl att ändras. `Medlem` samlar en persons data i en typ, satt i ett anrop.
2. `Medlem` är entitetsmodellen: `private` fält, konstruktor, getters. `Register` är domänens samlingsägare, med tom kropp. `Main` är applikationsentrén: `new Medlem("Kim", 1001)` och utskrift via getters.
3. Filen bokar adressen för samlingen. Utan den landar nästa krav på en samling i `Main`, och entrén sväller. Klassen anropas inte i det här paketet, eftersom den inte har något publikt beteende än.
4. `Main` försöker läsa ett fält som bara `Medlem` får röra. javac stoppar före körning. Anropa `getNamn()`. Låt `private` stå kvar.
5. De returnerar namnet och numret. De skriver inte om fälten. De söker inte och de håller ingen samling.
6. Konstruktorn körs. Den sätter `this.namn` och `this.medlemsnummer` inuti `Medlem`. `kim` är instansen.
7. `this.namn` är fältet på objektet som skapas. `namn` till höger är parametern från `new`.
8. Kontoappen har andra fält och andra metoder. En omdöpning lämnar kvar `owner`, `balance` och `deposit` i ett projekt som ska heta medlemsregister. Nya filer, svenska fält.
9. Samlingen hör hemma i `Register`. I det här paketet är klassen tom. En lista i `Main` ger entrén samlingens ansvar.
10. Exempel: samlingen i `Register`, en sökmetod, en Scanner-meny. Ett räcker inte. Factory och arv hör inte heller hit.
11. Ungefär: `Medlem` är mallen för en person med namn och medlemsnummer. Objektet är instansen efter `new Medlem("Kim", 1001)`, till exempel `kim`. Lösa variabler i `Main` håller inte ihop paret och ger inte tre klassfiler.
12. Merge uppdaterade GitHub. Du körde inte `git switch main` och `git pull origin main`. Nästa `git switch -c` utgick från den gamla lokala `main`.
13. Att fälten är `private`, att konstruktorn använder `this`, att `Register` saknar fält, att `Main` anropar getters, och att inga namn från Kontoappen eller en samling följt med.
14. `Medlem`, `Register`, `Main`.

</details>

---

## Klart för paketet?

- [ ] Målsvar om tre ansvar, egna ord, högt
- [ ] Målsvar om `private`, konstruktor och getters, egna ord, högt
- [ ] Målsvar om tom `Register`, egna ord, högt
- [ ] Målsvar om egen Pull Request och pull efter Merge, egna ord, högt
- [ ] Målsvar om klass och objekt, egna ord, högt
- [ ] `javac src/*.java && java -cp src Main` visar `Kim` och `1001`
- [ ] Minst en mergad Pull Request som du själv läst
- [ ] AI-träningen har minst fyra FEEDBACK-rader

Nästa paket i veckan: [16-merge-konflikt](../16-merge-konflikt/). Samlingen i `Register`: [17-lista-register](../../vecka-43/17-lista-register/). Inkapsling igen om den skaver: [10-inkapsling](../../vecka-40/10-inkapsling/).
