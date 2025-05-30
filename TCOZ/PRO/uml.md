<div align="center">
    <div align="left">
        <a href="/README.md">Domov</a>
        >
        <a href="./PROGRAMOVANIE.md">PRO</a>
    </div>
    <div align="right">
        <a href="../OKRUHY.md#programovanie">Okruhy</a>
        |
        <a href="https://drive.google.com/drive/folders/1-R0QweppWve7l7rt23FboOdxdV9U58OT?usp=sharing">Materály</a>
    </div>


# UML

</div>

## Staticke Diagramy
<ul>
    <li>
        <b>Tried<br></b>
        <ul>
            <li>
                Modifikátory prístupu
                <ul type=none>
                    <li>
                        - súkromný člen (private)
                    </li><li>
                        + verejný člen (public)
                    </li><li>
                        # chránený člen (protected)
                    </li><li>
                        ~ člen viditeľný v rámci balíka (menného priestoru)
                    </li>
                </ul>
                <br><img src="./Materialy/cla0.png" width=100%>
            </li><li>
                Realizácia - medzi rozhraním a triedou
                <br><img src="./Materialy/cla1.png" width=40%>
            </li><li>
                Asociačná trieda - medzi 2 entitami, môžeme rozšíriť o ďalšie atribúty
                <br><img src="./Materialy/cla2.png" width=80%>
            </li>
        </ul>
        <i>Domenovy model</i>
        <ul>
            <li>
                Asociácia - entity <B>nezávisle</B> na sebe vzájomne na seba odkazujú
                <br><img src="./Materialy/dom1.png" width=200%>
            </li><li>
                Agregácia - vzťah typu celok a časť<br> 
                - časť môže existovať sama o sebe a byť súčasťou aj iných kolekcií
                <br><img src="./Materialy/dom2.png" width=100%>
            </li><li>
                Kompozícia -  silnejšia agregacia
                - ak zanikne celok, zanikajú automaticky i jeho časti
                <br><img src="./Materialy/dom3.png" width=100%>
            </li><li>
                Generalizácia - jedná o dedičnosť<br>
                - Odvodená entita dedí vlastnosti a funkcionality hlavnej entity
                <br><img src="./Materialy/dom4.png" width=40%>
            </li><li>
                Multiplicita (Násobnosť) - môže byť uvedená u väzieb<br>
                1 - označuje konkrétnu hodnotu (práve 1)<br>
                * - označuje ľubovoľný počet vrátane 0<br>
                1 .. * (interval) – označenie intervalu
            </LI>
        </ul>
    </li>
    <li><b>Komponent</b></li>
    <li><b>Nasadenia</b></li>
</ul>

## Dynamicke Diagramy
<ul>
    <li><i>Objektov</i></li>
    <li><i>Use Casov</i> (pripadov uzitia)</li>
        <ul>
            <li>Relacie
                <ul>
                    <li>
                        Generalization (zovšeobecnenie) -  medzi aktérmi a prípadmi použiti
                        <br><img src="./Materialy/uc1.png" width=60%><img src="./Materialy/uc2.png" width=50%>
                    </li><li>
                        Include 
                        <br><img src="./Materialy/uc3.png" width=100%>
                    </li><li>
                        Extened
                        <br><img src="./Materialy/uc4.png" width=100%>
                    </li>
                </ul>
            </li>
        </ul>
    <li><i>Sekvencne</i></li>
    <li><i>Spoluprace</i></li>
    <li><i>Stavov</i></li>
    <li>
        <i>Aktivit</i>
        <ul>
            <li>
                Zahájenie a ukončenie (počiatočný a koncový uzol)
            </li><li>
                Akcia (aktivita)
            </li><li>
                Tok (prechod)
            </li><li>
                Rozhodnutie, zlúčenie
            </li><li>
                Vetvenie a spojenie
            </li><li>
                Oddelenie aktivít (plavecké dráhy)
            </li>
        </ul>
    </li>
</ul>

## Definovanie požiadaviek:
- Funkčné požiadavky    - Určujú, aké funkcionality bude systém poskytovať
<br>PR: Bankomat overí validitu vloženej platobnej karty.

- Nefunkčné požiadavky  - Vlastnosti alebo obmedzujúce podmienky daného systému
<br>PR: Riadiaci systém overí validitu karty do 3 sekúnd.