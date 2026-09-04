# 05 — Självtest

Svara **först** utan att titta på facit. Skriv i Docs/anteckningar — privat, för dig. Sikta på målsvar du kan *säga högt*.

Sedan: öppna facit och rätta dig.

---

## Frågor

1. Vad betyder **data**, **handlingar** och **ordning** i datalogiskt tänkande? Ge ett kort vardagsexempel (inte samma som i teoriguiden om du kan — t.ex. packa resväska eller baka).  
2. Varför är det fel att `println` totalpriset **innan** du räknat ut det?  
3. Vad gör **JDK** — och vad gör **IDE:n**? Varför är de inte samma sak?  
4. Var ser du **output** när ett Java-program kör i kursens setup?  
5. Vad är **`main`** — varför behöver ett enkelt konsolprogram den?  
6. Filen heter `MinApp.java` men klassen inuti heter `minapp` (liten bokstav). Vad kan hända — och vad är konventionen för klassnamn?  
7. IDE:n visar röd markering och text i stil med `';' expected`. Vilken **metod** (tre steg) använder du innan du börjar gissa?  
8. Peka i *din* kod från [03 — Övningar](./03-ovningar.md): nämn **`main`** och **en** `println` — förklara vad som händer när programmet kör (i vilken ordning).  
9. Kursen kör Java i **konsol** i IDE. Nämn **två saker** kursen *inte* fokuserar på i den här startdelen (t.ex. typ av app eller verktyg).  
10. **Ägarskap:** Du fick AI-kod med fel filnamn och fel `main`. Nämn **två** saker du alltid kontrollerar innan du litar på förslaget.

---

## Facit

<details>
<summary>Visa facit (målsvar-nivå)</summary>

1. **Data** = vad som finns (värden, status, namn). **Handlingar** = vad som görs (räkna, kontrollera, skriv ut). **Ordning** = i vilken följd stegen måste ske. Exempel: resväska — först lista (data), sedan packa kläder (handling), sist låsa (handling); låsa före packning är meningslöst.  
2. Datorn kör rad för rad. Då finns inget korrekt värde att skriva ut än — du får fel, tomt eller gammalt skräp. Data och beräkning måste komma **före** utskrift.  
3. **JDK** kompilerar och kör Java (javac + JVM). **IDE** är editor + Run + felvy. IDE:n **använder** JDK men ersätter det inte. Inte webbläsare, inte samma program.  
4. I **konsolen** i IDE:n (Run-fönstret / terminalpanelen) — efter lyckad körning.  
5. **`main`** = startmetod; JVM börjar där. Utan korrekt `main` startar inte konsolprogrammet som förväntat.  
6. Kompileringsfel / klass hittas inte — filnamn ska matcha **public class**-namnet; klassnamn börjar med **stor bokstav** (`MinApp`).  
7. (1) Läs **första tydliga** felraden. (2) Gå till **radnumret** IDE visar. (3) Fixa **en** sak (ofta semikolon/stavfel) och kör igen.  
8. Subjektivt — rimligt om du beskriver: JVM går in i `main`, sedan körs `println` rad för rad, text hamnar i konsolen. Fel om svaret bara är “koden står där”.  
9. T.ex. **Android-app**, **GUI med knappar**, **webbläsare som kör Java**, **databas** — inget av detta är fokus i startdelen; konsol i IDE med JDK. (Två räcker.)  
10. T.ex. filnamn = klassnamn; korrekt `public static void main(String[] args)`; semikolon; att det ska köras i IDE/konsol — inte webbläsare. (Två räcker.)

</details>

---

## Klart för Pass 1?

Om dina svar ligger nära facit, övningarna är gjorda, och du kan peka i egen kod:

- [ ] Målsvar data/handlingar/ordning — egna ord, högt  
- [ ] Målsvar JDK vs IDE — egna ord, högt  
- [ ] `main` + konsol — peka i projektet och förklara  
- [ ] Minst tre FEEDBACK-rader från AI-träningen sparade  

Då har du landat startmålen. Nästa del i veckan: variabler och datatyper (`02-variabler-datatyper/` när den publiceras).
