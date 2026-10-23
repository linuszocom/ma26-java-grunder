# Gruppexamination: Klubbens medlemsregister

Ni ska i era tilldelade grupper (2–4 personer) bygga en konsolapplikation i Java: ett enkelt medlemsregister för en klubb.  
[Länk till Grupperna](https://docs.google.com/spreadsheets/d/1CwIpGnE4ipsBLFjRZ-2RwmsaFvojqkY3dd81BIZugy8/edit?gid=0#gid=0)

Målet är att appen går att köra i er IDE, att koden använder objektorientering med klasser och objekt, samt att hela gruppen samarbetar och syns i Git-historiken. Ingen muntlig presentation inför klassen krävs.

## Viktigt att veta innan ni startar

- **Vad som bedöms:** Java-koden, klassernas struktur och ansvarsområden, gruppens samarbete i Git samt er gemensamma `README.md`.
- **Fokusera på en stabil grund först:** Säkerställ att baskraven nedan fungerar felfritt innan ni eventuellt bygger vidare. Det finns inget krav på extra funktioner för godkänt, men grupper som vill utmana sig själva är mycket välkomna att expandera appen!
- **Håll er till konsolen:** Bygg inget grafiskt gränssnitt (GUI) och använd inga externa databaser – fokusera på ren Java i konsolen.
- **Klassnamn på svenska:** Använd de tre namngivna basklasserna nedan utan svenska tecken i kod (`Medlem`, `Register`, `Main`).
- **Betyg:** Examinationen ger Underkänd (U) eller Godkänd (G).

## Del 1: Vad appen minst ska innehålla (Baskrav)

Ert system ska minst bestå av följande tre filer i `src/`:

### 1. Medlem.java (Objektet)

- Fälten ska minst innehålla namn (`String`) och medlemsnummer (`int`).
- Fälten ska vara `private` (inkapsling för att skydda datan från direkt manipulering utifrån).
- En konstruktor som sätter fälten när ett nytt medlemsobjekt skapas.
- Getters (t.ex. `getNamn()` och `getMedlemsnummer()`) för att kunna läsa informationen.

### 2. Register.java (Samlingen)

- Äger en privat lista av medlemmar (t.ex. `private List<Medlem> medlemmar = new ArrayList<>();`).
- Ska innehålla minst tre metoder:
  - Lägga till en ny medlem i listan.
  - Lista alla medlemmar (skriva ut namn och nummer, eller meddela om registret är tomt).
  - Söka på namn och visa medlemmens uppgifter, eller meddela att medlemmen saknas utan att programmet kraschar.

### 3. Main.java (Startpunkten och menyn)

- Innehåller en menyloop med `Scanner` som snurrar tills användaren väljer att avsluta:

1. Lägg till medlem
2. Lista alla medlemmar
3. Sök medlem
4. Avsluta
  *(Fler menyval är välkomna om ni bygger ut programmet!)*

- Hanterar inmatningen rent och kraschar inte om en sökning inte ger träff.

## Frivilliga utmaningar (För grupper som vill utmana sig själva)

När era baskrav fungerar stabilt är ni välkomna att bygga ut applikationen. Här är några idéer på vad ni kan lägga till:

- **Ta bort & redigera:** Metoder i `Register` för att radera en medlem eller uppdatera medlemmens uppgifter.
- **Arv och subklasser:** Skapa specialmedlemmar (t.ex. `PremiumMedlem`, `JuniorMedlem` eller `StyrelseMedlem`) som ärver från `Medlem` och har unika fält eller rabatter.
- **Statistik & sortering:** Möjlighet att sortera medlemslistan i bokstavsordning eller skriva ut hur många medlemmar som finns totalt.
- **Utökade kontroller:** Skydd mot dubbletter så att två medlemmar inte kan ha samma medlemsnummer.

## Del 2: Hur ni samarbetar i Git & GitHub

Skapa ett gemensamt publikt GitHub-repo per grupp. Ni väljer själva vilken samarbetsform som passar gruppen bäst:

### Alternativ A: Parprogrammering / Mobbprogrammering (Koda ihop)

Ni sitter tillsammans (Teams/Discord) och löser koden gemensamt. Den som sitter vid tangentbordet anger gruppmedlemmarnas namn i commit-meddelandet, t.ex.:

`git commit -m "feat: skapa sokfunktion i Register - Anna och Johan"`

### Alternativ B: Feature-branches (Dela upp)

Ni delar upp uppgifterna på egna grenar (`git switch -c feature-ditt-namn`), pushar till GitHub och mergar ihop koden till main (via GitHub Pull Request eller direkt merge).

### Gemensamma Git-krav för alla grupper

- Minst 6 commits totalt i repot.
- Alla gruppmedlemmar ska synas i historiken (genom egna commits från sitt GitHub-konto eller via tydlig namngivning i commit-meddelandena vid parprogrammering).
- Tydliga commit-meddelanden som beskriver vad som gjorts (undvik intetsägande meddelanden som "fix", "asdf" eller tomma rader).

## Del 3: Gemensam README.md

Skapa en fil med namnet `README.md` i projektets rotmapp och svara gemensamt på följande frågor (ca 2–4 meningar per fråga):

1. **Datalogiskt tänkande:** Hur bröt ni ner uppgiften i delsteg och en att-göra-lista innan ni började skriva Java-koden?
2. **Klass vs Objekt:** Varför är `Medlem` en egen klass och inte bara variabler i `Main`? Vad representerar ett objekt i er app?
3. **Samarbete i Git:** Vilken samarbetsstrategi valde ni (parprogrammering eller branches) och hur gjorde ni för att inte skriva över varandras arbete?
4. **Ett problem ni löste:** Beskriv ett problem som uppstod och hur ni löste det tillsammans. Det kan vara en bugg/krock i koden eller Git, men även en utmaning kring planering och samarbete.
5. **Reflektion kring AI och externa hjälpmedel (ca 3–5 meningar):**
  Har ni använt AI-verktyg eller andra källor under arbetet?
  - **Om ja:** Beskriv hur ni använde verktyget och ge ett konkret exempel: vad frågade ni om, och behövde ni ändra eller anpassa förslaget för att det skulle passa er app?
  - **Om nej:** Hur resonerade ni kring att lösa uppgiften helt på egen hand och var det något moment där ni funderade på att ta hjälp?

## Klart-check (Kryssa av innan inlämning)

- [ ] Programmet startar och går att köra från konsolen i er IDE.
- [ ] Koden är minst uppdelad på de tre klasserna: `Medlem.java`, `Register.java` och `Main.java`.
- [ ] `Medlem` har privata fält, konstruktor och getters.
- [ ] `Register` kan lägga till, lista alla samt söka på namn.
- [ ] En sökning på ett namn som inte finns ger ett tydligt meddelande utan att programmet kraschar.
- [ ] Menyn i `Main` snurrar i en loop tills användaren väljer att avsluta.
- [ ] Repot är publikt på GitHub och innehåller minst 6 commits.
- [ ] Alla i gruppen syns i Git-historiken (via egna commits eller namngivna par-commits).
- [ ] Filen `README.md` är komplett ifylld i projektets rotmapp.

## Inlämning & Bedömning

- **Individuell inlämning i Moodle:** Varje person i gruppen ska göra en egen inlämning i Moodle och klistra in länken till ert gemensamma, publika GitHub-repo innan deadline. (Det räcker alltså inte att bara en i gruppen lämnar in).
- **Ingen klassredovisning:** Ni behöver inte hålla någon presentation. Bedömningen sker direkt mot koden, Git-historiken och er `README.md`.
- **Gemensamt och individuellt ansvar:** Alla i gruppen ansvarar gemensamt för helheten. AI och hjälpmedel är tillåtna, men varje person i gruppen måste vid eventuell stickprovsavstämning kunna redogöra för koden och hur ni har arbetat.

## Deadline
Fredag 30:e oktober, klockan 23:59

