# Szervíz és orvosi robotika 

követelmények:
- zh 20%
  - lehet házit írni és akkor nem kell ZH, házik neptun üzenetben
    - sebészeti eszközök szegmentálása, synthetic miccai adatsor alapján
    - sebészeti eszközök szegmenseinek szegmentálása ugyanazon az adadsoron <- nehéz feladat
    - sebészeti eszközök 6D pozícióbecslése <- matekos feladat, 2D kameraképen megmondnai az eszközök 3D pozícióját
    - kinematikai és endoszkópos kamerakép lapú sebészeti kézségfelmérés jellemzőkinyerő <- sebészeti készségeket értékelünk pontok alapján, amiket látunk a képen
- vizsga félév végén 20%
  - ha félév végéig dolgozol a projekten akkor nincs vizsga

https://robotacademy.net.au/

---------------

## EA1

ppt: https://docplayer.hu/14015312-Robotok-diadalmenetben-a-sebeszrobotika-elso-20-eve.html

Mit nevezünk robotnak: *"I can't define a robot, but I know one when I see one" ~ J. Engelberger*

-ipari robotok
 - kollaboratív robotok
   - szervíz robotok <- nagyobb autonómiájuk van
- személyi szervízrobotok
  - orvosi robotok
    - sebészeti robotok

Az első műtét amit automatán megoldottak az a csontfúrás volt.

![számítógéppel integrált sebészet](https://docplayer.hu/docs-images/43/14015312/images/page_7.jpg)
- Digitális információ
  - beteg specifikus informáci
    - modell
      - tervezés
        - műtéti beavatkozás
          - betegspecifikus kiértékelés ()
            - statisztikai analízis  

**leggyakoribb rovidítések:**
- `CIS` computer integratedd surgery
- `IGS(T)` image guided surgery
- `MIS` minimally invasive surgery
- `surgical CAD/CAM` számítógéppel támogatott tervezés
- `CIIM` computer integrated inerventionoal medicine
- `CAS` computer assisted surgery


## EA-GY2
| | |
| ------------- |:-------------:| 
|![kuka orvosi robot](https://raw.githubusercontent.com/gabboraron/szerviz_robotok-orvosi_robotika/main/IMG_20210915_115429.jpg) | ![da vinci robotkar](https://github.com/gabboraron/szerviz_robotok-orvosi_robotika/blob/main/IMG_20210915_120840.jpg)|

## EA-GY3
*Szilágyi Áron**

![robot típusok](https://www.sardi.com/wp-content/uploads/2020/05/SARDI_INNOVATION_Cobot_expert_in_robot.jpg)

![robot részegységei](https://www.researchgate.net/profile/M-Arslan-2/publication/285590368/figure/fig5/AS:639520680710169@1529485020595/Movement-Structure-and-the-Main-Robot-Parts-22.png)

![kinematic structure](https://www.researchgate.net/publication/341034960/figure/fig2/AS:885873201655808@1588220038554/a-Robotic-arm-anatomy-b-Detail-view-of-gripper-assembly-attached-with-camera-c.jpg)

### fontos tulajdonságai egy robotnak:
- **pontosság:** a hiba átlaga. Nagyrészt a szoftvertől függ!
- **ismétlési pontosság:** felhasználás szempontjából ez a fontosabb adat, mert ez adja meg mennyire tud pontosan megismételni egy adott folyamatot, azaz a szórása a pontosságnak tulajdonképpen. Nagyrészt a hardwaretől függ!
- **maximum terhelhetőség:** ez egy függvény, mert a robotkar végpontján más az érték mint a közepén, stb. Tehát a robot végoontjától függ a terhelhetősége.
- **mozgathatóság határa:** meddig ér el a kar, stb
- **vezérlőszoftver**
- **holtjáték:** az ismétlési pontosságot befolyásolja, hogy ha megfogod a robotot miközben áll mennyit tud mozogni.

> ### Kinematika
> A geometriai leírásai a mozgásoknak. 

> ### Szbadságfok
> Ha egy 7 csuklós mechanizmus akkor 7 motorral kezelhető, tehát egy `7x7`es mátrixal írható le.

> ### kinematikai csukló szabadsgi foka
> Két szegmens összekötése hány szabadsági fokot ír le? Tehát két merev test három forgást és három elmozdulást tud leírni.

> ### mechanizmus szabadsági foka
> Valamilyen szegmens összekötve csuklókkal amit valahogy tudsz mozgatni.

### Kinemaatika definíciói:
- direkt kinematika: A transzformáció a csuklóváltozókból a térbeli pontját adja meg a robot végpontjának, csuklóról csuklóra számolva. 
- inverz kinematika: HA van egy célpont a térben akkor merről tudja robot elérni azt. Itt egy vektor egy eredményt ad.

![kinamtics definitons](https://www.researchgate.net/profile/Karl_Wallkum/post/What-is-the-difference-between-forward-kinematics-and-inverse-kinematics/attachment/5e542a253843b0499fe97e13/AS%3A862192492630020%401582574117930/image/FWDvsINV_Kinematics_HighResTransp.png)

`F=M*a` alapon a motor a csuklóban erőt és/vagy nyomatékot ad a szegmensekre amik között van. Ebből sebességet és gyorsulást sázmolhatunk idő szerinti integrálással.

Ezért mer itt nem gegyértelmű merre a `+` és a `-` irány bevezettk a Denavit-Hartenberg formát:
[YouTube: Denavit-Hartenberg Reference Frame Layout](https://www.youtube.com/watch?v=rA9tm0gTln8)

![matematikája](https://i.ytimg.com/vi/IKOGwoJ2HLk/maxresdefault.jpg)

> https://robotacademy.net.au/lesson/inverse-kinematics-for-a-2-joint-robot-arm-using-geometry/

Szögsebességekből kiszámoljuka végpont sebességét és szögsebességét jacobi mátrixal. Ha a mátrix rangja nem egyezik meg a méretével akkor a robot szinguláris pozícióban van. 

### Robot munkatere:
> **def:** 
> - elérhető munkatér: a teljes munkatér amit nem minden szabadsági fokával, de elég nehezen akár ér el a robot. 
> - dexterous munkatér: megvan mindne szabadsági foka és mindne irányba mozgatható.

### Aktivátorok
- DC motorok elektromágneses motork, kefés és kefe nélküli motorok állandó mágneses és savas gerjeszétsű motor. 
- piezoelektromos motor: egy kristályra

![piezolektromos motor működése](https://d1otjdv2bf0507.cloudfront.net/images/Article_Images/ImageForArticle_5307(4).png)

![mechanizmusok](https://eschool.iaspaper.net/wp-content/uploads/2018/06/Types-of-gear.jpg)

### Enkóderek
> Egy tárcsán kivágunk lyukakat és egyik oldlaára teszünk egy lámpát a másik oldalán egy fényérzékelőt amivel meghatározhatjuk, hogy a tárcsa milyen gyorsan forog, vagy milyen irányba. Ehhez használjuka grey codeot:
> 
> ![grey code]()https://scienceprog.com/wp-content/uploads/2021/02/image-6.png)

EGy vezeték ellenállása arányos a hosszával és fordítottan arányos a szélességével, tehát ha megnyújtnk egy vezetéket akkor annak ellnállásával mérhetjük a nyúlás hosszát.

### Robot control
Lemodellezzük matematikailag egy olyan szintre ahol nem érdekel minket, hogy fizikailag micsoda.
- elméleti modellje a plantnek főleg az inputokra adott válaszok értelmében.
- bementeke és kimenetek köött szeretnénk tiszátn matamtikai modelleket alkotni ahol nincs külöjnbség abban, hogy folyadékról vagy miről van szó.

> **irányítás:** mindne esetben visszacsatolást tartalmaz.
> 
> **vezérlés:** minden külső paramétert/surlódást ismerek és nem mérek vissza.
> 
> **PID controller** egy lineáris szabályozó, a hibához arányosan, a hiba integráljával arányosan, és a hiba deriváltjával is arányso jelet ad. 

## EA-GY4
- 95-ben alakult a cég ami létrehozta a davincit
- 98-ban volt az első emberes műtét davincivel

Az erő erősségét vissza tudjuk adni a vezérlésnek a motor áramfelvételéből tudjuk kiszámolni

A karokat a műtét elején beállítjuk egy pontba és a műtét során onnan nem mozdul, ezzel a 6 szabadsági fokból 4 marad meg, de ez rögzíti a bemeneti pontot a testen, így nem lehet véletlenül onnnan elmozdullni.









