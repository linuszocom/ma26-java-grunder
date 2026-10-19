# 04 — AI-träning: Sök och meny

AI kan spotta ur sig “komplett medlemsregister” på sekunder — med **sök-loop i `Main`**, **glömd `nextLine` efter `nextInt`**, eller **miss-meddelande som aldrig syns**. Det betyder inte att *du* äger `sökNamn` eller meny-I/O. Här tränar du: **fel rum för sök**, **Scanner-fällan**, **saknad miss-rad** — ändra, förklara.

Det är inte magi. Det är rätt fil + newline-ätare + miss efter `for`.

---

## Scenario — problem först

Du ber AI: *“Skriv sök på namn och meny 1–4 för medlemsregistret Elsa/Nova.”*  
Du får tillbaka något i stil med tre typiska fel (ibland i samma svar):

### Fel A — sök i Main

```java
// Main — AI "förenklar"
case 3 -> {
    System.out.print("Sök namn: ");
    String q = scanner.nextLine();
    for (Medlem m : register.getMedlemmar()) {  // läckt lista
        if (m.getNamn().equals(q)) {
            System.out.println(m.getNamn());
        }
    }
}
```

### Fel B — nextInt / nextLine

```java
int val = scanner.nextInt();
// AI glömmer scanner.nextLine();
case 1 -> {
    System.out.print("Namn: ");
    String namn = scanner.nextLine();  // blir ofta ""
    …
}
```

### Fel C — miss-meddelande saknas eller sitter fel

```java
public void sökNamn(String namn) {
    for (Medlem m : medlemmar) {
        if (m.getNamn().equalsIgnoreCase(namn)) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
            // AI glömmer return
        } else {
            System.out.println("Medlemmen saknas");  // storm varje varv
        }
    }
    // ingen ren miss-rad efter for — eller ingen miss alls om return saknas och ingen else
}
```

Svagheter:

- **Sök-loop i `Main`** / `getMedlemmar()` — bryter kapsling och Exam-pekkrav.  
- **Glömd `nextLine` efter `nextInt`** — tomt namn, hoppad fråga.  
- **Miss saknas eller i `else` varje varv** — fel Exam-beteende.  
- **`equals` utan IgnoreCase** — `"elsa"` missar `"Elsa"`.  
- **Factory / arv / README-mall** du inte bett om — NOLL SPILL; stryk.  
- **Klassisk `switch` + `break`** när `case n ->` räcker.

**Vad du tränar:** Feedback + en version *du* kan köra och peka på i IDE.  
**Varför:** Exam 2 — sökmetod + meny. Du måste se när AI “nästan” har rätt men lägger loopen i fel fil.  
**Vad det INTE är:** “AI fixade så det körde” utan att du kan peka på `sökNamn`.

---

## Din uppgift (ca 45–75 min)

### Steg 1 — Prompt
Skriv en egen prompt (eller jobba mot snuttarna ovan) där du ber om:
- `Register` med `private List<Medlem>`, `läggTill`, `listaAlla`, **`sökNamn`**;
- `Main` med meny 1–4, `Scanner`, `while`, **switch expression**;
- hit skriver namn+nummer, miss skriver `Medlemmen saknas`.

**Uttryckligen:** ingen sök-loop i `Main`, ingen factory, inget arv, ingen README-uppsats.

Spara prompten.

### Steg 2 — Granska (checklist)
- [ ] Finns for-each / sök i `Main`?  
- [ ] Saknas `sökNamn` i `Register`?  
- [ ] Miss-rad efter `for` — eller i `else` varje varv / saknas helt?  
- [ ] Saknas `return` efter hit?  
- [ ] Glömd `nextLine()` efter `nextInt()`?  
- [ ] `equals` utan `IgnoreCase`?  
- [ ] Publik lista / `getMedlemmar()`?  
- [ ] Factory, arv, `Account`, README-frågor du inte bett om?  
- [ ] Kan du förklara varje rad muntligt?

Skriv **minst tre** rader (täck **alla tre** felen A/B/C om de finns):  
`FEEDBACK: [vad jag ser] → [vad som måste ändras]`

### Steg 3 — Anpassa sök (Fel A)
Skriv en **ren `sökNamn` du äger** — koppla till [03 — Uppgift 1](./03-ovningar.md):

```java
public void sökNamn(String namn) {
    for (Medlem m : medlemmar) {
        if (m.getNamn().equalsIgnoreCase(namn)) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
            return;
        }
    }
    System.out.println("Medlemmen saknas");
}
```

Stryk for-each i `Main`. case 3 ska bara anropa.

### Steg 4 — Anpassa Scanner (Fel B)
Lägg in medveten ätare:

```java
int val = scanner.nextInt();
scanner.nextLine();  // ät \n
```

Testa case 1: skriv namn — det ska **vänta** på dig, inte bli tomt.

### Steg 5 — Anpassa miss (Fel C)
Kör sök på `"Rune"` när listan bara har Elsa/Nova. Du ska se **exakt en** rad: `Medlemmen saknas`. Inte storm. Inte tystnad.

### Steg 6 — Reflektion (3 meningar)
1. Vilket sök-brott hade AI gjort (loop i Main, läckt lista, saknad metod)?  
2. Vad ändrade du kring `nextInt`/`nextLine`?  
3. Var sitter miss-raden nu — och varför inte i `else` varje varv?

---

## Klart-check (peka i DIN fil)

- [ ] Minst **tre** FEEDBACK-rader sparade (sök i Main **och** Scanner **och** miss)  
- [ ] Peka på **`sökNamn`** i `Register` — for-each här  
- [ ] Peka på **`nextLine()`** efter meny-`nextInt`  
- [ ] Peka på **miss-raden efter `for`**  
- [ ] Testkörning: två medlemmar via meny, hit, miss, exit  
- [ ] Reflektion klar  

---

## Facit-riktning (titta efter du granskat själv)

Ren sök + case 3 (utdrag):

```java
// Register
public void sökNamn(String namn) {
    for (Medlem m : medlemmar) {
        if (m.getNamn().equalsIgnoreCase(namn)) {
            System.out.println(m.getNamn() + " " + m.getMedlemsnummer());
            return;
        }
    }
    System.out.println("Medlemmen saknas");
}

// Main case 3
case 3 -> {
    System.out.print("Sök namn: ");
    register.sökNamn(scanner.nextLine());
}
```

Typiska FEEDBACK-rader:

- `FEEDBACK: for-each sök i Main → flytta till Register.sökNamn; Main anropar bara.`  
- `FEEDBACK: getMedlemmar() / publik lista → ta bort; lista private + metoder.`  
- `FEEDBACK: nextInt utan nextLine → ät newline innan namn läses.`  
- `FEEDBACK: saknas i else varje varv → en println efter for.`  
- `FEEDBACK: hit utan return → return direkt efter utskrift.`  
- `FEEDBACK: factory/arv tillagt → stryk; paketet är sök + meny 1–4.`

**Målsvar (säg högt) — ägarskap:**  
*“Jag tar emot AI-utkast, flyttar sök till Register, fixar nextLine efter nextInt, och behåller bara kod jag kan peka på rad för rad.”*

---

Nästa: [05 — Självtest](./05-sjalvtest.md).
