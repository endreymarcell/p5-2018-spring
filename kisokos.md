# p5.js kisokos

## p5 modell
p5-ben a kódot speciális nevű "blokkokba" írjuk, attól függően, hogy mikor kell végrehajtódniuk.

`preload() { ... }`  
A program indulásakor ez a függvény fut le legelőször.  
Arra használjuk, hogy képeket töltsünk be vele.  

`setup() { ... }`  
A program indulásakor egyszer fut le.  
Ebbe tesszük azokat a parancsokat, beállításokat, amiknek csak egyszer kell lefutniuk.  
(Pl. vászon létrehozása, sprite-ok létrehozása, kezdeti beállítása.)  

`draw() { ... }`  
A program indulása után folyamatosan újra és újra lefut, másodpercenként akár harmincszor.  
Változáshoz, interakcióhoz kapcsolódó logikát írunk bele.  

`mouseClicked() { ... }`  
Akkor fut le, ha kattintunk az egérrel.  

`keyPressed() { ... }`  
Akkor fut le, ha lenyomunk egy billentyűt.  

## p5 változók (csakis olvasható)

__Ezeket a változókat csak használjuk, kiolvassuk a tartalmukat, de nem állítjuk át őket.__  

`windowWidth` - a rendelkezésünkre álló böngészőablak szélessége (szám).  
Tipikusan a `createCanvas()` paramétereként használjuk a `setup()` függvényben.  

`windowHeight` - a rendelkezésünkre álló böngészőablak magassága (szám). 
Tipikusan a `createCanvas()` paramétereként használjuk a `setup()` függvényben.  

`width` - a létrehozott vászon szélessége (szám).  
Csak akkor elérhető, ha már meghívtuk a `createCanvas()` függvényt.  

`height` - a létrehozott vászon magassága (szám).  
Csak akkor elérhető, ha már meghívtuk a `createCanvas()` függvényt.  

`mouseX` - megadja az egér aktuális helyének x koordinátáját a vásznon (szám). `setup()`-ban _nem_ szoktuk használni, bárhol máshol igen.  

`mouseY` - megadja az egér aktuális helyének y koordinátáját a vásznon (szám). `setup()`-ban _nem_ szoktuk használni, bárhol máshol igen.  

`mouseIsPressed` - megadja, hogy le van-e épp nyomva az egér gombja (igaz/hamis).  
Tipikusan a `draw()`-ban használjuk.  

`keyIsPressed` - megadja, hogy van-e épp billentyű lenyomva (igaz/hamis).  
Tipikusan a `draw()`-ban használjuk.  

`key` - megadja a legutoljára lenyomott billentyűt (betű).  
Általában a `keyPressed()`-ben használjuk.  

`keyCode` - megadja a legutoljára lenyomott speciális billentyű kódját (szám).  
Általában a `keyPressed()`-ben használjuk.  

`NORTH`, `SOUTH`, `EAST`, `WEST` - az északi, déli, keleti, illetve nyugati irány.  
A sprite-ok `setSpeed()` és az `addSpeed()` függvényében használhatjuk őket, vagy mint a sprite `rotation` változója.   

`frameCount` - megadja, hogy a program indulása óta hányszor futott le a `draw()` függvény (szám).  
Tipikusan a `draw()`-ban használjuk.  

## p5 függvények

`createCanvas(w, h)` - létrehoz egy `w` szélességű és `h` magasságú vásznat.  
A `setup()`-ban használjuk.  

`background(c)` - az egész vásznat `c` színűre színezi, ezzel elfed (letöröl) mindent, ami eddig a vásznon volt.  
A `c` lehet egy szín neve szövegként (pl. `"red"`) vagy egy RGB színkód, amihez a `color()` függvényt használjuk, pl. `color(100, 10, 207)`.  

`random(a, b)` - visszaad egy véletlenszámot `a` és `b` között.  

`round(n)` - visszaadja `n` egész számra kerekített értékét.  

`preloadImage(url)` - az `url` alapján betölt és visszaad egy képet, amit változóban tudunk eltárolni.  
A `preload()` függvényben használjuk.  

`image(img, x, y)` - kirajzolja az `img` változóba korábban `preloadImage()`-dzsel beletöltött képet úgy, hogy annak bal felső sarka az (x, y) pontba kerül.  

`noCursor()` - eltüntetni az egeret a vásznon.  

`cursor()` - megjeleníti az egeret a vásznon.  

`print(s)` - kiírja `s` szöveget a konzolra.

`alert(s)` - felugró ablakot dob fel benne az `s` szöveggel.    

`noLoop()` - leállítja a `draw()` függvény folyamatos meghívását.  

`loop()` - újraindítja a `draw()` függvény folyamatos meghívását.  

## Sprite-ok

### Létrehozás, beállítás

`createSprite()` - létrehoz és visszaad egy sprite-ot, amit változóba tudunk menteni.  

`sprite.remove()` - eltávolít egy sprite-ot a programból.  

`sprite.position.x` - megadja vagy beállítja a sprite (középpontjának) x koordinátáját (szám).  

`sprite.position.y` - megadja vagy beállítja a sprite (középpontjának) y koordinátáját (szám).  

`sprite.scale` - megadja vagy beállítja a sprite "nagyítását".  
Ha 1, a sprite pont akkora, amekkoraként létrehoztuk; egynél kisebb vagy nagyobb számnál a sprite arányosan csökken vagy növekszik.  
Alapesetben: 1.  

`sprite.rotation` - megadja vagy beállítja a sprite forgásirányát (szám).  
Alapesetben: 0 (a sprite Kelet felé néz).  

`sprite.shapeColor` - beállítja a sprite színét (szín).  
Átadhatunk neki szöveget (`sprite.shapeColor = "blue"`) vagy RGB színkódot a `color()` függvény használatával (`sprite.shapeColor = color(123, 65, 210, 150)`).  

`sprite.addImage(img)` - a sprite-nak alakul ad egy képet, amit korábban `preloadImage()`-dzsel beletöltöttünk az `img` változóba.  

`sprite.width` - megadja vagy beállítja a sprite szélességét (szám).  

`sprite.height` - megadja vagy beállítja a sprite magasságát (szám).  

`sprite.visible` -  megadja vagy beállítja, hogy a sprite látható-e (igaz/hamis).  
Alapesetben: `true`.  

### Mozgatás, találkozás, interakció

`sprite.setSpeed(v, d)` - `v` nagyságú sebességet ad meg egy sprite-nak `d` irányba.  
A sprite esetleges korábbi sebessége _törlődik_.  

`sprite.addSpeed(v, d)` - `v` nagyságú sebességet ad hozzá egy sprite eddigi sebességéhez `d` irányba.  
A sprite esetleges korábbi sebessége _megőrződik és összeadódik_ a most megadottal.  

`sprite.rotationSpeed` - megadja vagy beállítja a sprite folyamatos, automatikus forgásának sebességét (szám).  
Alapesetben: 0 (a sprite nem forog).  

`sprite.overlap(otherSprite)` - megmondja, hogy a sprite fedésben van-e épp a megadott másik sprite-tal.  

`sprite.collide(otherSprite)` - nekiütközteti a sprite-ot a megadott másik sprite-nak.  
Ez azt jelenti, hogy ha `sprite` és `otherSprite` találkoznak, akkor `sprite` megáll, nem tud tovább menni.  
A `draw()` függvényben használjuk.  

`sprite.displace(other)` - `sprite` eltolja a megadott másik sprite-ot.  
Ez azt jelenti, hogy ha `sprite` és `otherSprite` találkoznak, `sprite` változtatás nélkül halad tovább, `otherSprite`-ot pedig eltolja az útjából.  
A `draw()` függvényben használjuk.  

`sprite.bounce(otherSprite)` - `sprite` lepattan a megadott másik sprite-ról.  
Ha azt szeretnénk, hogy a másik sprite maga ne mozduljon el, akkor őt előtte mozdíthatatlanná kell tennünk (`immovable`).  
A `draw()` függvényben használjuk.  

`sprite.immovable` - beállítja, hogy egy sprite mozdíthatatlan-e (igaz/hamis).  
Csak akkor kell beállítani, ha azt akarjuk, hogy más sprite-ok le tudjak pattanni erről (`bounce()`).  

`sprite.rotateToDirection` - beállítja, hogy a sprite mindig arra forduljon (`rotation`), amerre épp halad (igaz/hamis).  
Alapesetben: `false`. Elég egyszer beállítani, ezt tipikusan a `setup()`-ban tesszük meg (vagy akkor, amikor a sprite létrejön).  

`sprite.friction` - a sprite "csúszóssága" (szám).  
Ha 1, akkor a sprite egyenletes sebességgel halad. Ha kisebb egynél, mozgás közben veszít a sebességéből (súrlódik). Alapesetben: 1.

`sprite.mouseActive` - beállítja, hogy a sprite figyelje az egér helyzetét (igaz/hamis).  
Alapesetbe: `false`. Ha szeretnénk használni a sprite `mouseIsOver` vagy `mouseIsPressed` változóját, előbb ezt igazra kell állítanunk.   

`sprite.mouseIsOver` - megmondja, hogy az egér éppen a sprite fölött van-e (igaz/hamis, read only).  
Csak akkor működik, ha korábban a sprite `mouseActive` változóját igazra állítottuk!    

## szerkezetek (feltétel, ciklus, csoport)

TODO

## JSBin használata

TODO


## Példaprogramok

TODO
