# 01 — Teoriguide: Datalogiskt tänkande & Java-verktyg

> **Så använder du denna guide:** Här slipar du **målsvar** du ska kunna säga högt / skriv i README. Tar du veckan från noll — läs klart, gör sen [03 — Övningar](./03-ovningar.md) och [04 — AI-träning](./04-ai-traning.md). Se också [mappens README](./README.md).

Vi börjar med **vad som går sönder** när steg blandas — sedan bygger vi upp hur du tänker innan du skriver kod, och hur du kommer igång i Java. Det är inte magi. Det är en metod.

---

## Datalogiskt tänkande — postpaket, inte kaos

Många tänker nu: “Programmering… måste jag kunna all syntax direkt?” Andas.

**Metafor:** Tänk att du skickar ett **postpaket**. **Data** = innehållet och adressen (vad som finns, vem det gäller). **Handlingar** = väga, frimärka, scanna, lasta på bilen. **Ordning** = du kan inte scanna paketet innan det är packat, och du kan inte frimärka efter att det redan lämnat terminalen.

**Vad det är:** Datalogiskt tänkande = dela ett problem i **data**, **handlingar** och **ordning** — innan du skriver Java.  
**Varför det finns:** Datorn gör exakt det du säger, i den ordning du säger det. Blandar du ordning får du fel resultat eller krasch.  
**Om det saknas / vad det INTE är:** Det är INTE Java-syntax. Det är INTE “gissa tills det funkar”. Det är planen på papper.

**Målsvar (säg högt / skriv i README):** *“Ett program handlar om data (vad vi har), handlingar (vad vi gör) och ordning (i vilken följd). Fel ordning ger fel resultat.”*

---

## Problem först — fel ordning

**Scenario:** Pizzerian ska räkna ut totalpris: en pizza kostar 95 kr, kunden beställer 2 stycken.

**Fel ordning (tänk högt):**
1. Skriv ut “Totalt: 190 kr”
2. Räkna ut 95 × 2
3. Sätt pris = 95 och antal = 2

Vad händer? Steg 1 skriver ut något **innan** priset ens finns. Datorn kan inte gissa 190 — den följer ordningen slaviskt.

**Bättre ordning:**
1. Data: `pris = 95`, `antal = 2`
2. Handling: räkna `totalt = pris × antal`
3. Handling: skriv ut `totalt`

**Vad det visar:** Samma siffror, annan ordning — helt annat (eller trasigt) resultat.  
**Varför det spelar roll:** I Java kommer `System.out.println` **efter** att värdena finns — inte före.

**Målsvar (säg högt / skriv i README) — ordning:** *“Jag sätter data först, gör beräkningar eller val i mitten, och skriver ut sist — annars finns inget att skriva ut.”*

---

## Program och konsol — var syns resultatet?

**Metafor:** Java-filen är **fraktsedeln** — instruktionerna. **Konsolen** är **leveransaviseringen** där du ser vad som faktiskt hände när paketet kördes.

**Vad det är:** Ett **program** = instruktioner i filer (t.ex. `.java`). **Konsolen** = textutmatning i IDE:n när programmet kör.  
**Varför det finns:** Du måste se att koden *gjorde* något — inte bara att den *står* i editorn.  
**Om det saknas / vad det INTE är:** Konsolen är INTE själva kodfilen. Den är INTE en webbsida, INTE Android och INTE ett fönster med knappar (GUI). Kursen kör **Java i konsol** i IDE:n.

**Målsvar (säg högt / skriv i README):** *“Konsolen är där programmet skriver ut text när jag trycker Run. Det är där jag ser resultatet.”*

---

## JDK vs IDE — terminal vs expedition

Många blandar ihop: “Jag har ju IntelliJ — behöver jag JDK?” Ja. De gör olika jobb.

**Metafor:** **JDK** = postterminalens maskineri (tar emot `.java`, kompilerar till `.class`, kör via JVM). **IDE:n** = expeditionssdisken där du fyller i formulär, trycker **Run** och läser felmeddelanden när något är fel.

| | JDK | IDE (IntelliJ / VS Code) |
|--|-----|---------------------------|
| **Vad** | Java Development Kit — kompilator + JVM | Skrivbord: editor, Run-knapp, felsökarvy |
| **Varför** | Datorn måste kunna översätta och köra Java | Du behöver ett ställe att skriva och testa |
| **INTE** | Inte samma sak som IDE | Inte samma sak som JDK; inte webbläsare |

**Flöde i en mening:** Du skriver i IDE:n → IDE:n anropar JDK → resultat syns i **konsolen**.

**Vad det är:** JDK = verktyg som *kör* Java. IDE = verktyg där du *jobbar* med Java.  
**Varför det finns:** Utan JDK kan ingen köra din kod. Utan IDE blir det jobbigt att skriva och felsöka — men JDK behövs ändå.  
**Om det saknas:** “Cannot find JDK” / inget program startar → kontrollera JDK-installation och att IDE:n pekar på rätt JDK.

**Målsvar (säg högt / skriv i README):** *“JDK kompilerar och kör Java. IDE:n är där jag skriver kod och trycker Run. De är två olika verktyg som samarbetar.”*

---

## Minsta Java-program — `main` som startknapp

Nästan varje konsolapp börjar så här. Tänk **startknappen** — programmet måste veta var det ska börja.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hej från konsolen!");
    }
}
```

| Del | Vad det är | Varför | Om saknas / INTE |
|-----|------------|--------|------------------|
| `public class HelloWorld` | En klass — filens “namnbricka” | Java organiserar kod i klasser | Klassnamn ska matcha filnamnet (`HelloWorld.java`) |
| `main` | Startmetoden | JVM börjar här | Utan `main` startar inte konsolprogrammet |
| `System.out.println(...)` | Skriv rad till konsolen | Du ser output | INTE samma som att skriva text i editorn — måste **köras** |

**Vad det INTE är:** Du behöver inte fler metoder, loopar eller klasser ännu. Bara `main` och en utskrift räcker för att bevisa att kedjan IDE → JDK → konsol funkar.

---

## Läsa felmeddelanden — problem först

**Scenario:** Du glömmer semikolon:

```java
System.out.println("Hej")
```

**Kompilatorn** (via JDK) stoppar dig. IDE:n visar oftast **röd markering** och ett meddelande — t.ex. `';' expected` eller liknande.

**Metod — tre steg:**
1. **Läs första tydliga raden** i felrutan (inte allt på en gång).
2. **Peka på radnumret** IDE:n visar — öppna den raden.
3. **Fråga:** “Vad förväntade sig Java här?” (ofta semikolon, `{`, eller stavfel).

**Vad det är:** Kompileringsfel = syntaxen är trasig — programmet körs inte.  
**Varför det finns:** Bättre ett tydligt stopp nu än att programmet gör fel saker senare.  
**Om det saknas / INTE:** Att ignorera röda markeringar och “hoppas på Run” är INTE felsökning.

**Målsvar (säg högt / skriv i README) — fel:** *“Jag läser felraden, går till radnumret IDE:n pekar på, och fixar syntaxen — oftast semikolon eller stavfel.”*

---

## Metod — innan du kodar

Många sitter nu och tänker: “Jag vet inte var jag ska börja i Java.” Stopp. Börja utan kod.

1. **Vad är datan?** (tal, text, ja/nej — vad behöver finnas?)  
2. **Vilka handlingar?** (räkna, jämför, skriv ut — i vilken ordning?)  
3. **Vad ska synas i konsolen sist?** (det är ditt facit innan du skriver `println`)

Sedan: öppna IDE → nytt Java-projekt → en klass med `main` → skriv ut → Run → läs konsolen.

**Målsvar (säg högt / skriv i README) — metod:** *“Jag delar problemet i data, handlingar och ordning utan kod först. Sedan skriver jag main och println, kör, och läser konsolen.”*

---

## Vanliga missar

| Miss | Rättare tanke |
|------|----------------|
| “Jag har IDE — JDK spelar ingen roll” | IDE:n **använder** JDK. Båda behövs. |
| Skriva ut före data finns | Sätt värden / räkna först — `println` sist |
| Leta resultat i kodfilen | Resultat syns i **konsolen** efter Run |
| Klass heter `Foo` men filen `Bar.java` | Filnamn = klassnamn (med stor bokstav) |
| Panik vid röd text | Läs radnummer + första felraden — fixa en sak i taget |
| “Java = Android-app” | Kursen = **konsol** i IDE — inte mobil-GUI |

---

## Checkpoint (privat)

Skriv i Docs/anteckningar — för dig:

1. Data, handlingar, ordning — vad betyder de tre? (sikta på målsvaret)  
2. JDK vs IDE — en mening vardera  
3. Var ser du output när programmet kör?

När du kan säga svaren högt utan att titta: gå vidare.

---

## Nästa steg

Gå till [02 — Visuellt](./02-visuell.md), sedan övningarna.
