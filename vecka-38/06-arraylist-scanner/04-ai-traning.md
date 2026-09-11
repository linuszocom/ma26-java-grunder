# 04 — AI-träning: Array, lista och Scanner & ägarskap

AI kan skriva packlistor och inköpsprogram på sekunder. Det betyder inte att *du* äger dem. Här tränar du samma färdighet som examinationen kräver: **se index-fällor, fel listtyp och Scanner-kön** — innan du trycker Run.

Det är inte magi att granska AI. Det är att läsa Exception-namn och veta **vad som låg kvar i Scanner efter ett tal**.

---

## Scenario — problem först

Du ber AI: *“Skriv ett Java-program som läser produktnamn och antal, sparar namn i en ArrayList, och skriver ut listan. Läs två produkter.”*

Du får tillbaka:

```java
import java.util.ArrayList;
import java.util.Scanner;

public class AiInkopslista {
    public static void main(String[] args) {
        ArrayList<String> produkter = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);

        for (int i = 0; i < 2; i++) {
            System.out.println("Antal:");
            int antal = scanner.nextInt();
            System.out.println("Produkt:");
            String namn = scanner.nextLine();
            produkter.add(namn);
            System.out.println(namn + " x " + antal);
        }

        System.out.println(produkter.get(2));
    }
}
```

**AI:s kommentar:** “Använd ArrayList som typ — det är enklare. get(2) visar sista produkten efter två varor. nextInt och nextLine funkar i valfri ordning.”

Det *låter* nästan rimligt. Men flera saker stoppar dig från att **äga** koden — och från att klara muntligt där du ska förklara index och inläsning.

**Vad du tränar:** Feedback på AI-kod + omskrivning du äger.  
**Varför:** `ArrayIndexOutOfBounds` / `IndexOutOfBounds`, tomma strängar efter `nextInt`, och `List` vs `ArrayList` i deklarationen — det här kommer tillbaka i Kontoappen och medlemsregistret.  
**Vad det INTE är:** “AI skrev det, alltså är inköpslistan klar.”

---

## Din uppgift (ca 45–60 min)

### Steg 1 — Prompt
Skriv en egen prompt till AI (eller jobba bara mot snutten ovan) där du ber om array/lista/Scanner enligt [03 — Övningar](./03-ovningar.md). Spara prompten.

### Steg 2 — Granska (checklist)
Gå igenom koden och kryssa:

- [ ] Variabel deklarerad som **`List<String>`** med **`new ArrayList<>()`** — inte `ArrayList` som vänster typ?  
- [ ] **`import java.util.List;`** finns?  
- [ ] Ordning: produktnamn **före** eller **efter** antal — stämmer med prompts och är **medveten**?  
- [ ] Efter **`nextInt()`** — finns **extra `nextLine()`** innan nästa **`nextLine()`** som sparar text?  
- [ ] Loop för inläsning: rätt antal iterationer?  
- [ ] **`get(2)`** efter **två** `add` — vilket index är sista lagliga?  
- [ ] Array/lista-index: någon `[length]` eller `get(size())` utan `-1`?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst fyra** konkreta feedback-punkter:  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

**Ledtrådar (titta själv först):** tom `namn` efter `nextInt`; `get(2)` när size är 2; fel deklarationstyp; imports; ordning antal före produkt utan extra `nextLine`.

### Steg 3 — Anpassa
Skriv om till kod **du äger** — ny klass `AiInkopslistaFix` i eget projekt:

- `List<String> produkter = new ArrayList<>();`
- Läs **produkt** med `nextLine`, **antal** med `nextInt`, **släng Enter**, spara produkt, skriv rad
- Två produkter, sedan loop som skriver `"Inköpt: …"` för varje `get(i)`
- **Ingen** `get(2)` om du bara har två rader — visa sista med `get(produkter.size() - 1)` om du vill demonstrera

Kör med egna inmatningar. Fixa tills konsolen visar **båda** produktnamn korrekt.

### Steg 4 — Bonus-granskning (index i array)
AI ger också:

```java
int[] dagTemp = new int[3];
dagTemp[0] = 14;
dagTemp[1] = 16;
dagTemp[2] = 11;
System.out.println("Medel: " + dagTemp[3]);
```

Skriv **en** FEEDBACK-rad om detta (inga kodändringar krävs — bara diagnos).

### Steg 5 — Reflektion (3 meningar)
Skriv i `REFLEKTION.txt` eller anteckningar:

1. Vad var fel eller vilseledande i AI-förslaget (inköpslistan)?  
2. Vad ändrade du — särskilt Scanner och listtyp?  
3. Varför spelar index 0 och `size()-1` roll inför Exam 1 (lista konton) och Exam 2 (lista medlemmar)?

---

## Klart-check (peka i DIN omskrivna kod)

- [ ] Minst **fyra** FEEDBACK-rader sparade (+ gärna en om array-index)  
- [ ] Peka på **`List`**-deklarationen och **`new ArrayList<>()`** — varför båda?  
- [ ] Peka på **extra `nextLine()`** efter `nextInt()` — simulera utan den: vad blir `namn`?  
- [ ] Peka på loop med **`get(i)`** — vilket index är sista när size är 2?  
- [ ] Kör programmet — peka i **konsolen** på båda produktnamn  
- [ ] Reflektionens tre meningar klara  

---

## Facit-riktning (titta efter du granskat själv)

Exempel på giltig feedback (dina ord får skilja sig):

- `FEEDBACK: ArrayList<String> som deklaration → ska vara List<String> enligt kodstandard; skapa med new ArrayList<>().`  
- `FEEDBACK: nextInt före nextLine utan släng-rad → nextLine läser tom rad; produktnamn blir "".`  
- `FEEDBACK: get(2) efter två add → lagliga index 0 och 1; get(2) kastar IndexOutOfBoundsException.`  
- `FEEDBACK: AI säger get(2) är sista → sista index är size()-1, alltså get(1) vid två rader.`  
- `FEEDBACK: Saknar import List → compilern hittar inte List om jag fixar deklarationen.`  
- `FEEDBACK: dagTemp[3] i length 3 → ArrayIndexOutOfBoundsException; sista index är 2.`

**Målsvar (säg högt / skriv i README) — ägarskap:**  
*“Jag granskar AI-kod för index (0 … size−1), List-deklaration, och Scanner-kön efter nextInt — behåller bara det jag kan köra och förklara.”*

---

## Ägarskaps-checklista (spara)

Innan du räknar lista/Scanner-kod som “klar”:

- [ ] Jag vet skillnad `length` vs `size()`  
- [ ] Jag kan rita index 0 … size−1 för min lista  
- [ ] Jag har testat **utan** extra `nextLine()` en gång och sett tom sträng  
- [ ] Jag deklarerar `List`, skapar `ArrayList`  
- [ ] Jag har kört med **egen** inmatning — inte bara läst AI i chatten  

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
