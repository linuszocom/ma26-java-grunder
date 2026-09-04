# 03 — Övningar

**Omfång det här paketet:** Deklaration, tilldelning, `System.out.println`, datatyperna `int`, `double`, `String`, `boolean`. Allt i **`main`**. Ingen `if`/`else`. Ingen loop. Ingen `Scanner`. Inga egna metoder.

AI får föreslå rader. Du måste kunna **peka och förklara** varje etikett, varje typ och varför koden kompilerar.

**Var du kör:** Java-projekt i IntelliJ eller VS Code med JDK. Kör `Main` och läs **konsolen** i IDE:n.

---

## Uppgift 1 — Lagerinventering (problem-först)

**Mål:** Hitta och fixa typfel och saknade deklarationer tills programmet kompilerar och skriver rätt värden.

**Scenario / startläge:** Ett lager ska skriva ut dagens inventering. Någon har blandat hylltyper — javac vägrar. Din jobb: städa koden, inte byta scenario.

**Trasig startkod** (kopiera till `Main.java`):

```java
public class Main {
    public static void main(String[] args) {
        int artikelNamn = "Skruv M6";
        String antalLador = 24;
        double helaPallar = 3;
        boolean pallKomplett = "true";

        System.out.println(artikelNamn);
        System.out.println(antalLador);
        System.out.println(helaPallar);
        System.out.println(pallKomplett);

        System.out.println(enhet);
    }
}
```

**Krav:**
1. Fixa så varje variabel har **rätt datatyp** för sitt värde (artikelnamn = text, antal = heltal, osv.).
2. Byt till **meningsfulla namn** om du vill — men håll kvar fyra variabler som motsvarar: text, heltal, decimal, boolean.
3. Raden med `enhet` ska antingen **deklareras och tilldelas** (t.ex. `String enhet = "st";`) eller tas bort medvetet — inte lämnas odeklarerad.
4. Programmet ska **kompilera** och skriva ut **fyra rader** med dina slutvärden + eventuellt `enhet`.
5. Inga nya språkfeatures — bara det som ingår i paketet.

**Facit-riktning (titta först själv):**

<details>
<summary>Visa facit-riktning (efter eget försök)</summary>

```java
public class Main {
    public static void main(String[] args) {
        String artikelNamn = "Skruv M6";
        int antalLador = 24;
        double helaPallar = 3.0;   // 3 funkar också — double tar heltal
        boolean pallKomplett = true;
        String enhet = "st";

        System.out.println(artikelNamn);
        System.out.println(antalLador);
        System.out.println(helaPallar);
        System.out.println(pallKomplett);
        System.out.println(enhet);
    }
}
```

Vanliga fixar: `"Skruv M6"` → `String`. `24` → `int`. `"true"` → `true`. `enhet` deklareras. Namn kan variera om typerna stämmer.

</details>

**Klart-check (peka i DIN kod):**
- [ ] Peka på varje datatyp och säg *varför* just den typen passar innehållet  
- [ ] Peka på raden som **deklarerar** en variabel vs raden som **tilldelar** (eller gör båda på samma rad)  
- [ ] Peka på felet som fanns i startkoden — *cannot find symbol* eller *incompatible types*?  
- [ ] Konsolen visar text, heltal, decimal och `true`/`false` — inte krasch

**Ägarskap:** AI ok som bollplank — du ska kunna förklara varje rad du behåller och varje typbyte du gjorde.

---

## Uppgift 2 — Väderstation (bygg från noll)

**Mål:** Skapa fyra variabler — en av varje datatyp — och skriv ut en liten **stationsprofil** i konsolen.

**Brief:** Du rapporterar från en väderstation. Bygg programmet själv från tom `main` (eller ny `Main.java`).

**Krav:**
1. **`int`** — antal aktiva sensorer (t.ex. `4`)  
2. **`double`** — temperatur i Celsius med decimal (t.ex. `6.25`) — **punkt**, inte komma  
3. **`String`** — stationens namn (t.ex. `"Kuststation Alfa"`)  
4. **`boolean`** — om nederbörd registreras just nu (`true` eller `false`)  
5. Minst **fyra** `System.out.println` — en per variabel (du får lägga till etiketttext i utskriften, t.ex. `"Sensorer: " + antalSensorer`, men `+` för text ihop kommer mer senare; enklast: en rad per värde)  
6. Kör programmet — konsolen ska visa **fyra tydliga rader**

**Exempel på rimlig konsol** (dina värden får skilja):

```
4
6.25
Kuststation Alfa
false
```

**Klart-check (peka i DIN kod):**
- [ ] Peka på **int**-raden och säg varför sensorantal är heltal  
- [ ] Peka på **double**-raden och säg varför temperatur inte är `int`  
- [ ] Peka på **String**-raden och peka på **citattecknen** — vad händer utan dem?  
- [ ] Peka på **boolean**-raden och säg varför `"false"` skulle varit fel typ  
- [ ] All kod ligger i `main` — inga egna metoder

**Ägarskap:** Skriv själv först. Med AI: spara prompten + en mening om vad du ändrade. Du ska kunna förklara varje rad muntligt.

---

## Uppgift 3 — Stretch (valfritt)

Byt **scenario** till ett **träningspass** — samma fyra typer, nya värden och etiketter:

| Typ | Förslag |
|-----|---------|
| `int` | antal övningar |
| `double` | genomsnittlig puls eller vikt på vikt i kg |
| `String` | passets namn |
| `boolean` | om passet är avslutat |

Samma struktur som uppgift 2. En mening i anteckningar: vad som är **samma** (fyra typer, println) och vad som bara är **nytt innehåll**.

**Klart-check:** Du kan peka på samma typ-mönster i båda programmen.

---

## När du kört fast

1. Läs felraden i IDE:n — röd markering = ofta fel typ eller odeklarerat namn.  
2. *cannot find symbol* → deklarera variabeln först.  
3. *might not have been initialized* → tilldela värde före `println`.  
4. *incompatible types* → byt typ eller byt innehåll.  
5. Jämför med [01-teoriguide](./01-teoriguide.md) och [02-visuell](./02-visuell.md).  
6. Gå vidare till [04 — AI-träning](./04-ai-traning.md).
