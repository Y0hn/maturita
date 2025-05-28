<div align="center">
    <div align="left">
        <a href="/README.md">Domov</a>
    </div>
    <div align="right">
        <a href="../OKRUHY.md#serverové-technológie">Okruhy</a>
        |
        <a href="https://drive.google.com/drive/folders/1wjpJihfR4WzJx883IoB3Nfm7O8y1ADC-?usp=sharing">Materály</a>
    </div>

# Serverové Technológie
</div>

# Windows Server
## Konfigurácia presného času

### NTP (Network Time Protocol)
- Jeden Windows server ako NTP server, ostatné klienti.
- Synchronizácia času v sieti – dôležité pre presnosť logov a aplikácií.

---

## DNS Hierarchia

- **TLD (Top-Level Domain)**: `.com`, `.sk`
- **Root doména**: `jozo.sk`
- **Subdoména**: `maturita.jozo.sk`

---

## DMZ (Demilitarizovaná zóna)
- Izolovaná sieť medzi internou a externou sieťou.
    - Poskytuje vrstvu ochrany tým, že izoluje citlivé interné systémy od priameho prístupu z internetu.
- Obsahuje servery ako e-mail, web, DNS – prístupné z internetu.
    - Tieto servery sú zabezpečené tak, aby minimalizovali riziko preniknutia do internej siete.
- Funkcie:
  - Ochrana internej siete
  - Testovanie firewallov
  - Filtrácia pripojení
  - Zabezpečuje, že len schválené spojenia prechádzajú medzi sieťami.
- Implementované pomocou **dvoch firewallov** pre vyššiu bezpečnosť.

---

## DHCP Server

- Automatické prideľovanie IP adries a iných parametrov.
- Zjednodušená správa IP adries.

### Spôsoby alokácie:
- **Statická** – pevná IP viazaná na MAC.
    - Vhodné pre zariadenia, ktoré potrebujú stálu adresu, ako servery.
- **Dynamická** – IP z rozsahu, časovo obmedzená.
    - Umožňuje efektívne využitie IP adries v rámci definovaného rozsahu.

### Postup komunikácie:
- Proces zahŕňa komunikáciu medzi klientom a serverom na pridelenie IP adresy.  
`DISCOVER → OFFER → REQUEST → ACK`

---

## DNS Server
- Preklad doménových mien na IP adresy a späť.
    - Zabezpečuje, aby užívatelia mohli používať názvy domén namiesto číselných IP adries.
- Podporuje reverzné názvy (IP na doménu).
    - Umožňuje identifikovať doménu na základe IP adresy, čo je užitočné pri diagnostike.
- Typy záznamov: host aliasing, mail aliasing, distribúcia záťaže.
    - Zvyšujú flexibilitu a výkonnosť DNS systému.
- **TLD**: Spravujú ich špecializované servery.
    - Tieto servery zabezpečujú spoľahlivosť doménového systému na globálnej úrovni.

### Typy záznamov:
- *Host* aliasing
- *Mail* aliasing
- Distribúcia záťaže

### Metódy získavania záznamov:
- **Rekurzívny** – DNS nájde celú odpoveď.
    - Zabezpečuje kompletnú odpoveď na žiadosť užívateľa.
- **Nerekurzívny** – odkaz na iný server.
    - Používa sa pri komunikácii medzi DNS servermi.

---

## IIS Server

- Webový server pre Windows (Internet Information Services).

### Funkcie:
- Hostovanie webových stránok/aplikácií.
    - Zabezpečuje dostupnosť obsahu pre užívateľov prostredníctvom prehliadačov.
- Podpora technológií (HTML, ASP.NET).
    - Umožňuje vývojárom vytvárať dynamické a moderné webové aplikácie.
- Bezpečnostné funkcie (HTTPS, autentifikácia).
    - Chránia komunikáciu a údaje pred neoprávneným prístupom.
- Podpora protokolov (HTTP, FTP).
    - Zabezpečuje flexibilitu v poskytovaní rôznych typov služieb.
- Rozšíriteľnosť pomocou modulov.
    - Používatelia môžu pridať špecifické funkcie podľa svojich potrieb.


---

## AD Server (Active Directory)

- Hierarchická databáza pre správu používateľov a zariadení.
- Centrálne riadenie prístupu a zdrojov.

### Štruktúra:

### Les (Forest)
- Najvyššia úroveň hierarchie v AD, ktorá môže obsahovať viacero domén s dôveryhodnými vzťahmi medzi nimi.
    - Slúži na zabezpečenie spolupráce medzi rôznymi organizačnými jednotkami.


### Doména (Domain)
- Logická skupina objektov so spoločnou politikou a databázou.
    - Poskytuje centralizované riadenie prístupu v rámci konkrétneho administratívneho celku

### Organizačné jednotky (OU)
- Štruktúrované skupiny v doméne na logické usporiadanie používateľov, počítačov a zariadení.
- Umožňujú:
    - Jednoduchšiu správu (podľa oddelení, tímov alebo lokácií).
    - Delegáciu oprávnení (napr. pre vedúcich oddelení).


---

## Užívateľ (User)
- Účet reprezentujúci osobu alebo systém (meno, heslo, atribúty).
- Každý účet má unikátny SID (Security Identifier) – identifikátor používaný systémom na riadenie prístupových práv.
- Slúži na autentifikáciu a riadenie prístupu k sieťovým zdrojom.


## Skupiny (Groups)

### Distribučné skupiny
- Na hromadnú komunikáciu (napr. e-mailové rozosielanie)
- Nepoužívajú SID – slúžia len na správu kontaktov


### Bezpečnostné skupiny
- Majú pridelený SID (ako používatelia)
- Zjednodušujú správu práv – oprávnenia sa priraďujú skupine, nie jednotlivcom
- Napr.: "Prístup k súborovému serveru" sa nastaví pre skupinu, nie pre každého užívateľa zvlášť

### Prečo SID záleží?
- Systém pracuje so SID, nie s menami.
- Umožňuje jednoduché premenovanie alebo migráciu účtov.

---
### Objekty v AD
- **Počítače** – Zariadenia pripojené do domény. Umožňujú centrálne nastavenia a správu (politiky, aktualizácie).
- **Tlačiarne** – Zdieľané v sieti. Uľahčujú používateľom tlač a správcom správu prístupov.

### Dôveryhodné vzťahy (Trusts)

- Spojenie medzi doménami/lesmi.
- Umožňuje zdieľanie zdrojov medzi d

---
# Linux

## Architektúra OS Linux
Linux pozostáva z jadra (kernel), ktoré riadi hardvér a základné funkcie systému. Nad jadrom pracuje shell (príkazový riadok) a grafické rozhranie. Všetky aplikácie a služby využívajú tieto základné vrstvy.

## Sieťové rozhrania
Sieťové rozhrania predstavujú spojenie medzi počítačom a sieťou. Každé rozhranie má svoje nastavenia, ako je IP adresa alebo sieťová maska. Konfigurácia sa ukladá do špeciálnych súborov, ktoré systém načíta pri štarte.

## Sieťové zariadenia
Sieťové zariadenia, ako sú routery alebo switche, sa dajú v Linuxe nastaviť pomocou systémových nástrojov. Tieto nastavenia určujú, ako počítač komunikuje s ostatnými zariadeniami v sieti.

## Správa služieb
Služby sú programy, ktoré bežia na pozadí a poskytujú rôzne funkcie (napríklad webový server). Dajú sa spúšťať, zastavovať alebo nastaviť, aby sa spúšťali automaticky pri štarte systému.

## Správa procesov
Procesy sú bežiace programy. Každý proces má svoje číslo (PID) a dá sa kontrolovať alebo ukončiť. Systémové nástroje umožňujú sledovať, ktoré procesy bežia a koľko systémových zdrojov využívajú.

## Oprávnenia súborov
Každý súbor a priečinok má nastavené oprávnenia, ktoré určujú, kto s ním môže pracovať. Oprávnenia sa delia na tri skupiny: pre vlastníka (read - čítanie, write - zápis, execute - spustenie), pre skupinu a pre ostatných používateľov.

## Používatelia a skupiny
Každý používateľ má svoj účet a môže patriť do jednej alebo viacerých skupín. Skupiny zjednodušujú správu prístupových práv, pretože oprávnenia sa dajú nastaviť pre celú skupinu naraz.

## Objekty v systéme
V systéme existujú rôzne typy objektov: obyčajné súbory, priečinky, symbolické odkazy (symlinky - ako skratky), pevné odkazy (hardlinky - viac mien pre ten istý súbor) a rúry (pipe - prepojenie medzi procesmi).

## Súborové systémy
Súborový systém určuje, ako sa ukladajú dáta na disk. Najbežnejší je ext4, ktorý je stabilný a dobre otestovaný. Novší btrfs ponúka pokročilé funkcie, ako sú okamžité snapshoty alebo automatická oprava chýb.

## Inštalácia programov
Programy sa v Linuxe inštalujú pomocou balíčkových manažérov, ktoré automaticky vyhľadajú a nainštalujú všetky potrebné súčasti. Rôzne distribúcie majú rôzne nástroje na správu softvéru.

## Systém Netfilter (firewall)
Tento systém filtruje sieťovú komunikáciu a chráni počítač pred neoprávneným prístupom. Umožňuje nastaviť pravidlá, ktoré určujú, aké spojenia sú povolené a aké nie.

## Konfigurácia Nginx
Nginx je výkonný webový server. Jeho konfigurácia určuje, ako server spracováva požiadavky, kde hľadá webové stránky a aké doplnkové funkcie sú k dispozícii.

## Autentifikácia v SSH
SSH umožňuje bezpečné pripojenie k vzdialenému počítaču. Bezpečnosť sa dá zvýšiť zakázaním prihlasovania cez heslo a povolením prihlasovania len pomocou šifrovaných kľúčov.