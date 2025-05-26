<div align="center">
    <div align="left">
        <a href="/README.md">Domov</a>
    </div>
    <div align="right">
        <a href="../OKRUHY.md#web">Okruhy</a>
        |
        <a href=".">Materály</a>
    </div>

# Databazové Aplikácie

</div>

# Návrh a vytvorenie relačnej databázy

## Celkový proces návrhu databázy je nasledovný:

![Untitled](https://file.notion.so/f/f/c04f8c6f-ce46-46fd-8b96-6f8ebd000ca1/394d5f5e-4d94-4ef5-b6b9-93c7f4cfda1c/Untitled.png?table=block&id=729e8538-4325-4228-95bf-332cad26503a&spaceId=c04f8c6f-ce46-46fd-8b96-6f8ebd000ca1&expirationTimestamp=1748275200000&signature=wtHd05VzNUI80XE5lhNrA0RFLCdkrwWBf5IHIoSc2GI&downloadName=Untitled.png)

## Konceptuálny model

Prvým krokom pri vytváraní databázy a zameriava sa na identifikáciu entít, ich vzťahov a atribútov. Ide o abstraktnú úroveň návrhu, ktorá rieši štruktúru a vzťahy medzi údajmi, bez zamerania sa na technické detaily ako typ databázového systému alebo optimalizácie. Pri konceptuálnom návrhu identifikujeme hlavné entitné typy, ich vzájomné vzťahy a atribúty. Zvyčajne sa používajú techniky ako entitno-relačný diagram (ER diagram) na vizuálnu reprezentáciu týchto informácií.

       

## Logický návrh databázy

Logický model vyjadruje väzby medzi objektmi s ohľadom na zabezpečenie integrity dát, normalizáciu dátového modelu a pod.
**Obsahuje:**

- návrh tabuliek
    - každá entita sa zmení na tabuľku
    - atribút sa stane stĺpcom tabuľky
- relácie s referenčnou integritou
    - určí sa kardinalita (typ) relácie
    - prepojenie medzi tabuľkami sa zabezpečí pomocou hlavných a cudzích kľúčov
- normalizáciu (proces odstránenia duplicitných údajov v relačných databázach)

### Návrh tabuliek

Relačná databáza sa vyznačuje tým, že údaje sú uložené v tabuľkách. Nie sú usporiadané do jednej tabuľky, pretože by bola neprehľadná, dlhá a obsahovala by nadbytočné, opakujúce sa údaje. Údaje sú rozdelené do niekoľkých tabuliek, ktoré sú navzájom poprepájané pomocou určitých vzťahov, relácií. Tabuľka je dvojrozmerná štruktúra, ktorá sa skladá z riadkov a stĺpcov. Tabuľka obsahuje údaje o jedinej entite.
**Vlastnosti relačných tabuliek:**

- každá tabuľka má svoj jednoznačný názov,
- polia (stĺpce) predstavujú jednotlivé vlastnosti (atribúty) daného typu údajov,
- každé pole tabuľky má svoj názov, na ich poradí v tabuľke nezáleží,
- každý záznam (riadok) v tabuľke reprezentuje jeden výskyt daného typu údajov, vždy má rovnakú štruktúru,
- každý záznam je jednoznačne identifikovateľný hlavným (primárnym) kľúčom, na poradí záznamov nezáleží,
- položky tabuľky uchovávajú jedinú hodnotu a nesmú obsahovať opakujúce sa prvky.

V rámci logického návrhu databázy zmeníme všetky entity na tabuľky. Atribúty sa stanú poľami tabuľky.

### Určenie kardinality relácií

Vzťahy medzi tabuľkami nazývame relácie. Relácia = väzba vytvorená medzi spoločnými poľami (stĺpcami) v dvoch tabuľkách. Obvykle sa vyjadruje ako vzťah medzi hlavným kľúčom jednej tabuľky a cudzím kľúčom druhej tabuľky.

**Hlavný (primárny) kľúč**
je jednoznačný identifikátor každého záznamu v tabuľke. Jeho hodnota musí byť jedinečná. Často sa ako hlavný kľúč v tabuľke používa identifikačné číslo, poradové číslo alebo kód.
Vlastnosti hlavného kľúča:

- jednoznačne identifikuje každý záznam (riadok) tabuľky,
- nikdy neobsahuje hodnotu null (nie je prázdny)
- nemení sa.

V relačnej databáze sa vyžaduje, aby bol každý riadok v tabuľke jedinečný. V prípade, keď v tabuľke nie je pole, ktoré by zaručovalo jedinečnosť každého záznamu (tzv. prirodzený kľúč), pridáva sa do tabuľky stĺpec navyše, najčastejšie pomenovaný ako ID (Identifikácia). Databázový systém môže v tomto stĺpci prideľovať automaticky hodnoty, čím zabezpečí, aby žiadne dva záznamy neboli rovnaké.

**Cudzí kľúč**

Hodnoty hlavného kľúča môžeme použiť aj v iných tabuľkách na prepojenie s tabuľkou s hlavným kľúčom. Ak sa v tabuľke nachádza stĺpec s primárnym kľúčom inej tabuľky, tak sa nazýva cudzí kľúč.

![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2Fed0ac859-0a68-48bd-90ce-f50487267f85%2FUntitled.png/size/w=1250?exp=1748335289&sig=i9duC-1_XZSENwVjF9OZJZFH726KjIHssi3vuB-pOQc&id=4eb74373-00e0-4e89-8ba6-016f3233e352&table=block)

**Kardinalita**

sa vzťahuje na maximálny počet, koľkokrát môže byť záznam jednej tabuľky prepojený so záznamami inej, súvisiacej tabuľky. V relačnej databáze môžu mať údaje v tabuľkách medzi sebou 3 typy väzieb:

- `1 : 1 (one-to-one)`
    - Každému záznamu jednej tabuľky odpovedá práve jeden záznam z druhej tabuľky. Reláciu 1 : 1 je nutné použiť v týchto prípadoch:
        - v jednej tabuľke potrebujeme viac než 255 polí (rozdelíme údaje do dvoch tabuliek – tie budú spojené cez primárne kľúče relácií 1 : 1)
        - pre jeden objekt požadujeme pre rôzne polia odlišné užívateľské práva (pole rozdelíme do viacerých tabuliek prepojených reláciou 1 : 1)
        (príklady : človek – číslo platného občianskeho preukazu; mesto – telefónne smerové číslo).
- `1 : N (one-to-many)`
    - Jednému záznamu v nadradenej tabuľke zodpovedá viacero záznamov v podriadenej tabuľke. Tzn. hodnota hlavného kľúča každého záznamu hlavnej tabuľky súhlasí s hodnotou odpovedajúceho poľa niekoľkých záznamov v prepojenej tabuľke. Je to najbežnejší typ relácie.
- `M : N (many-to-many)`
    - Každému záznamu v jednej tabuľke môže zodpovedať viacero záznamov v druhej tabuľke a naopak. Tento typ vzťahu sa obvykle implementuje pomocou tzv. **spojovacej tabuľky**, ktorá obsahuje záznamy, ktoré mapujú vzťahy medzi záznamami v oboch tabuľkách. Táto tabuľka má obvykle dva cudzie kľúče, ktoré odkazujú na primárne kľúče z oboch tabuliek, ktoré spojuje.
    - Príkladom môže byť relácia medzi tabuľkami "Študenti" a "Predmety". Študent môže byť zapísaný na viacero predmetov a jeden predmet môže mať viacero študentov. Takže medzikrížová tabuľka by mohla byť napríklad "Zápis do predmetov", kde by boli zapísané záznamy, ktoré určujú, ktorý študent je zapísaný na ktorý predmet a naopak.

### Normalizácia

- V relačnom modeli sú údaje uložené v tabuľkách, na
ktoré sú kladené určité požiadavky
- Po splnení týchto požiadaviek je tabuľka označovaná
ako normalizovaná

**Cieľ normalizácie**

- Odstrániť redundanciu (nadbytočnosť) údajov
v databáze
- Zabrániť tzv. aktualizačným anomáliám (napr. aby pri
vymazaní záznamu nedošlo k vymazaniu celej entity
    - vymazanie záznamu o výpožičke nesmie zapríčiniť
    zrušenie údajov o knihe)
- Hlavný cieľ – spoľahlivosť počítačového spracovania

**1NF**

1. Je definovaný primárny kľúč.
2. Tabuľky majú presne definované stĺpce a ich počet je stály a nemenný. Neexistujú stĺpce s obsahom rovnakého typu.
3. Každý riadok obsahuje jeden záznam. Záznam je iný ako
všetky ostatné. Líši sa od nich prinajmenšom hodnotou
primárneho kľúča.
4. Každý stĺpec obsahuje údaje rovnakého druhu.
5. Každá položka obsahuje práve jednu hodnotu.

**2NF**

- Tabuľka je v 1NF
- Hodnoty atribútov, ktoré nie sú súčasťou primárneho kľúča, sú funkčne závislé iba od hodnôt primárneho kľúča.
- *Často sa jedná o tabuľky,ktoré majú zložený primárny kľúč.*

**3NF**

- Tabuľka je v 2NF
- Hodnoty atribútov, ktoré nie sú súčasťou primárneho kľúča, nie sú funkčne závislé na hodnotách iných atribútov – ani jednotlivo, ani po skupinách.
- *Relácia je v tretej NF práve vtedy, keď je v druhej normálnej forme a neobsahuje žiadnu tranzitívnu závislosť. O tranzitívnej závislosti medzi atribútmi A a C (C je primárny kľúč) hovoríme vtedy ak atribút A je závislý od atribútu B a až atribút B je závislý od C.*

| **Cislo PK** | **Meno** | **Priezvisko** | **Funkcia** | **Plat** |
| --- | --- | --- | --- | --- |
| 1 | Ján | Dzurek | technik | 500 |
| 2 | Peter | Košík | vedúci | 1000 |
| 3 | Róbert | Drábecký | správca | 750 |
| 4 | Karol | Pokorný | technik | 500 |

Atribút **cislo** bude primárnym kľúčom, na ktorom závisia atribúty **meno, priezvisko**. Ďalej môžeme vidieť, že atribút **plat** je funkčne závislý na atribúte **funkcia** (**plat** je tarifne definovaný **funkciou**). Platí tak, že **cislo** a **funkcia** sú vzájomne závislé a **plat** závisí na zastávanej **funkcii**. Tak sa vytvorila tranzitivita, to je že **cislo** a **plat** sú tranzitívne závislé.

| **Cislo PK** | **Meno** | **Priezvisko** | **Funkcia FK** |
| --- | --- | --- | --- |
| 1 | Ján | Dzurek | technik |
| 2 | Peter | Košík | vedúci |
| 3 | Róbert | Drábecký | správca |
| 4 | Karol | Pokorný | technik |

| **Funkcia_cislo PK** | **Funkcia** | **Plat** |
| --- | --- | --- |
| 121 | technik | 500 |
| 122 | vedúci | 1000 |
| 123 | správca | 750 |

### Ak si to stále nepochopil

Predstavte si databázu ako skriňu na šanóny. V nej máte rôzne priečinky a v nich súbory s informáciami. Cieľom normalizácie je usporiadať tieto priečinky a súbory tak, aby ste mali k dátam ľahký prístup a aby ste sa vyhli chybám.

**1. Normálna forma (1NF):**

- V každom priečinku (tabuľke) máte pevný počet šuplíkov (stĺpcov) a každý šuplík má presne definovaný typ obsahu (typ údajov).
- V každom šuplíku (riadku) máte jeden súbor (záznam) a každý súbor je jedinečný (má unikátny identifikátor - primárny kľúč).
- V jednom súbore (položke) máte len jeden typ informácie (hodnotu).

**2. Normálna forma (2NF):**

- Všetky informácie v šuplíkoch (atribúty, ktoré nie sú súčasťou primárneho kľúča) musia priamo súvisieť s informáciami v názve šuplíka (primárnym kľúčom).
- Ak máte zložený šuplík (zložený primárny kľúč), všetky informácie v ňom musia súvisieť s celým názvom šuplíka, nie len s jeho časťou.

**3. Normálna forma (3NF):**

- Všetky informácie v šuplíkoch musia súvisieť priamo s názvom šuplíka, a nie s informáciami v iných šuplíkoch.
- Ak je informácia v šuplíku závislá od inej informácie v inom šuplíku, cez túto informáciu sa nesmie dať zistiť aj názov šuplíka.

**Zjednodušene:**

- **1NF:** Odstráňte duplicitné súbory a usporiadajte ich do logických priečinkov.
- **2NF:** Uistite sa, že všetky súbory v priečinku súvisia s názvom priečinka.
- **3NF:** Uistite sa, že žiadny súbor v priečinku nie je závislý od informácií v inom priečinku, okrem názvu priečinka.

## Fyzický model databázy

- prevedie tabuľky a vzťahy navrhnuté v logickom modeli do konkrétneho databázového systému. Kým doteraz sme navrhovali databázu bez ohľadu na databázový program, v ktorom sa bude realizovať, fyzický návrh už musí túto skutočnosť zohľadňovať.
- Postup:
1. vytvoríme tabuľky, zadáme názvy polí a každému poľu pridelíme príslušný údajový typ, vytvoríme hlavné kľúče
2. vytvoríme obmedzenia pre jednotlivé polia (masky, overovacie pravidlá) a pre riadky tabuľky (overenie nad celým riadkom),
3. vytvoríme relácie medzi tabuľkami a zadefinujeme referenčnú integritu.

# Entitno-relačný diagram

![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2F57f5a76e-2a82-4730-bed7-130d40681309%2FUntitled.png/size/w=1360?exp=1748335356&sig=BvqiiTuaPo9VmJUjK9fVI_DC8E4Ow9wacXIyzqWRq1Y&id=6a252b2c-5faa-4b82-a59a-8582e400541c&table=block)
![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2Fd8819e3b-5403-416f-b2a0-92c0aafa8f10%2FUntitled.png/size/w=1360?exp=1748335371&sig=dbOYkXpNwGcLvwC_Q9kZMeTM608l-Y0y1-umhAECyt0&id=c5819c9c-ad7e-4e10-8676-f15c78fec116&table=block)
![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2F2b949e79-820a-46d4-922a-e536f86ecb1f%2FUntitled.png/size/w=1360?exp=1748335373&sig=47EARJsfTODpT5IBsmjLMBww2Y6aeFd1AJyTwx5W3hY&id=dca517bc-b01a-4183-bd34-e9f9eec4e09f&table=block)
![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2F8fc10387-7c37-4696-805d-ae552bc5a21d%2FUntitled.png/size/w=1360?exp=1748335376&sig=NiseSi7B8HfXXqL7MwVcrB_VBPHB1Yroxg0k3IxlY5I&id=03dd354b-ed6e-4999-8f46-670d8af1dde5&table=block)

[príklady na normalizáciu riešenia.xlsx](./príklady%20na%20normalizáciu%20riešenia.xlsx)

# Základné objekty databázy

### Tabuľky

súbor polí (stĺpcov), ktoré obsahujú informácie jedného typu a záznamov (riadky), kam sa ukladajú všetky údaje vzťahujúce sa ku konkrétnej položke - osobe, firme, veci.

![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2Fc41f967a-cf27-42e2-bba2-cf2bc8f46c77%2FUntitled.png/size/w=1360?exp=1748335740&sig=ZEsnDlooOvjB0biq_yCiXFiQNd0X14HBpPFYs0JFjok&id=a394983e-058f-4ab8-a5c7-a26e6a246dec&table=block)

![](http://server.gphmi.sk/spisakova/accesshtml/obr/tabulka.gif)

### Formuláre

uľahčujú zadávať, prezerať a upravovať údaje databázy. Formuláre tvoria rozhranie medzi používateľom a údajmi v databáze. Ponúkajú spôsob ako najpríjemnejšie sprostredkovať užívateľovi prácu s databázou.

![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2Fc5885b40-4351-42bd-a4af-3ec9c89684d2%2FUntitled.png/size/w=990?exp=1748335813&sig=NBBe7BBBCHa2_2x0D-qyu6wX2yiWVigAlttCnDCDkUY&id=fb23e4d8-e516-4c29-ba5a-cd0838d5d377&table=block)

![](http://server.gphmi.sk/spisakova/accesshtml/obr/formular.gif)

### Dotazy

vyberajú alebo aktualizujú informácie z tabuliek a dotazov v databáze, umožňujú zhromaždiť údaje z niekoľkých tabuliek a ďalej spracúvať. Tabuľky musia byť spojené vzťahom, reláciou. Výsledok dotazu je tiež tabuľka.

![Untitled](https://img.notionusercontent.com/s3/prod-files-secure%2Fc04f8c6f-ce46-46fd-8b96-6f8ebd000ca1%2F2c71daa6-4fcf-4fc2-808c-dfe4cc8970d7%2FUntitled.png/size/w=1000?exp=1748335828&sig=XWiKc-V8xd-OWs5LfWQlEzkSphakVatgIm8lantr6YY&id=459e735c-85b4-46a3-9b8c-d4e825c1a5c3&table=block)

![](http://server.gphmi.sk/spisakova/accesshtml/obr/dotaz1.gif)

# Jazyk SQL – charakteristika a typy príkazov

SQL (Structured Query Language) je štandardizovaný programovací jazyk, ktorý sa používa na správu a manipuláciu s relačnými databázami. SQL umožňuje definovať dáta v databáze, manipulovať s nimi, vykonávať dotazy na dáta, upravovať štruktúru databázy a riadiť prístup k dátam. 

Typy príkazov v SQL zahŕňajú:

1. **DDL (Data Definition Language - Jazyk definície dát)**: Slúži na definovanie, modifikáciu a odstraňovanie štruktúry databázy a jej objektov. Medzi príklady patria príkazy ako **`CREATE TABLE`**, **`ALTER TABLE`** a **`DROP TABLE`**.
2. **DML (Data Manipulation Language - Jazyk manipulácie dát)**: Používa sa na manipuláciu s dátami v databáze. To zahŕňa pridávanie, upravovanie, vymazávanie a vyhľadávanie dát. Medzi príklady patria príkazy ako **`INSERT`**, **`UPDATE`**, **`DELETE`** a **`SELECT`**.