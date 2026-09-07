**1\. DiscountCalculator hibái**

*   A kód nem ellenőrzi a negatív rendelési értéket, így tiltás helyett tévesen számol velük.
    
*   Pontosan 10000 Ft-os rendelés esetén nem lép be az első feltételbe, így az 5% kedvezmény helyett 0% lesz az alap.
    
*   Pontosan 25000 Ft-os rendelés esetén az első két feltétel átfedése miatt nem egyértelmű a működés, de itt szerencsére a második érvényesül.
    
*   A 50000 Ft feletti feltételben a >= helyett > szerepel, így pontosan 50000 Ft esetén a 15% helyett tévesen 10% kedvezményt ad.
    
*   A VIP kedvezménynél a százalékpont (0.05) hozzáadása helyett egy egész 5-ös számot ad hozzá a kód, ami 500%-os kedvezményt jelent.
    
*   A függvény a végén a kedvezményes ár helyett a rendelési értékből csak a kedvezmény tizedes tört értékét vonja ki a teljes kedvezményes összeg helyett.
    

**2\. ParkingFeeCalculator hibái**

*   A kód nem tartalmaz ellenőrzést a negatív parkolási időre, így negatív percek esetén is hibásan nullát vagy negatív díjat adhat vissza.
    
*   Pontosan 15 perces parkolás esetén a kód nem lép be az első feltételbe, és a díjszámításnál tévesen 0 Ft-ot számol az ingyenesség helyett.
    
*   A Math.floor használata miatt lefelé kerekít a kód, így minden megkezdett óra helyett csak a teljesen letelt órákat számlázza ki.
    
*   A hétvégi 50%-os kedvezményt a kód fixen lefelezi, így a VIP vagy a napi maximum korlát előtt hibás sorrendben alkalmazza a levonást.
    
*   A VIP kedvezménynél a 20%-os levonás helyett fixen 20 Ft-ot von le a kód a díjból.
    

**3\. CinemaTicketCalculator hibái**

*   A kód nem ellenőrzi a negatív életkort és a 120 év feletti korlátot, így az érvénytelen korúak is kaphatnak jegyet.
    
*   Pontosan 6 éves kor esetén az első feltétel miatt ingyenes a jegy, holott a specifikáció szerint 6 éves kortól már 30% kedvezmény járna.
    
*   Pontosan 65 éves kor esetén egyik korcsoportos feltétel sem teljesül, így az illető nem kapja meg a neki járó 40%-os kedvezményt.
    
*   A diák kedvezményt a kód független if-ként kezeli, így a legnagyobb kedvezmény kiválasztása helyett összevonja azt a karkockázati kedvezménnyel.
    
*   A 3D felárnál a kód a 800 Ft-os fix összeg hozzáadása helyett 80%-kal megemeli az addig kalkulált jegyárat.
    
*   A 3D felárra is rávetül a korábbi százalékos kedvezmény hatása, mivel a kód a felárat még a kedvezményes alapárból szorozva számítja ki.
    

**4\. ExamGradeCalculator hibái**

*   A kód nem ellenőrzi az elméleti (max 60) és gyakorlati (max 40) pontok felső határait, valamint a negatív pontszámokat sem az érvénytelenséghez.
    
*   Sikertelen vizsga esetén az if ágban az && (ÉS) operátor miatt csak akkor ad elégtelent, ha _mindkét_ részpontszám elmarad a minimumtól, holott az egyik bukása is elég lenne.
    
*   Pontosan 50, 60 és 70 pont esetén a kód a szigorú kisebb-egyenlő feltételek miatt eggyel rosszabb osztályzatot ad a határértékeken.
    
*   Pontosan 85 pont esetén a kód 4-es osztályzatot ad vissza a specifikációban meghatározott 5-ös helyett.
    

**5\. PackageClassifier hibái**

*   A kód egyáltalán nem ellenőrzi a 0 vagy negatív méreteket és tömeget, így az érvénytelen csomagokra nem adja vissza az INVALID jelzést.
    
*   A Small kategóriánál a <= (kisebb-egyenlő) helyett szigorú < (kisebb) relációt használ, így a pontosan 2 kg-os vagy 30 cm-es csomagok kiesnek innen.
    
*   A Medium kategóriánál a kód a méretek között || (VAGY) operátort használ az && (ÉS) helyett, így elég egyetlen méretnek 60 cm alatt lennie a besoroláshoz.
    
*   Ha egy csomag súly alapján Large lenne, de méretei alapján Small, a kód a merev sorrend miatt tévesen az OVERSIZE felé is csúszhat, ha a Medium feltétel hibásan igazat ad rá.