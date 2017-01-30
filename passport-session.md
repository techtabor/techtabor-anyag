# Sütik és sessionök, avagy hogy jegyzünk meg egy felhasználót?

Miután valakit bejelentkeztetünk, szeretnénk, hogy a szerver megjegyezze, hogy az adott user már egyszer belépett. Képzeljük el milyen kényelmetlen lenne, ha például minden külön e-mail megnézéséhez újra és újra be kéne jelentkeznünk az e-mail postafiókunkba. Erre találták ki a sessiont és a sütit\(cookie\).

### Süti

A süti egy a felhasználó böngészőjében tárolt pici adatcsomag\(egy value-key pair\), amely lehetővé teszi azt, hogy a szerver azonosítani tudja a felhasználót. Ha nem használunk sütiket, akkor nem tudjuk megkülönböztetni az egyes requesteket - mindegyiket ugyanúgy dolgozzuk fel, és nem tudhatjuk, hogy a user ezelőtt járt-e az oldalunkon, vagy sem, bejelentkezett-e vagy sem. A süti úgy oldja meg ezt a problémát, hogy miután beállítunk egy sütit a user számítógépén, a böngészője ezt a sütit újra és újra elküldi nekünk bármilyen requesttel együtt, amit a szerverünknek küld.

**Példa:**

```js
var cookieParser = require('cookie-parser');
var express = require('express');

var app = express();

app.use(cookieParser());

app.get('/', function(req, res){
    if( req.cookies.volt_e_itt == "igen"){
        res.send('Hi old user!');
    } else {
        res.cookie('volt_e_itt', 'igen');
        res.send('Hi new user!');
    }
});

app.listen(3000);
```

* Mit csinál a fenti példa?
* A böngésződ developer-toolsában nézd meg, hogy milyen sütit küldött el a böngésződnek a fenti program!
* Próbáld meg átírni a programot úgy, hogy most egy másik süti alapján döntődjön el, hogy már jártunk-e az oldalon. Például ha a user már betöltötte az oldalt, akkor hozzunk létre egy `Bagoly` nevű sütit, melynek `Bohóchal` az értéke.
* Nézd meg, hogy vajon más oldalak használnak-e sütiket!

### Session

A session hasonlóan működik, mint a cookie, de ilyenkor nem a user tárolja a kapcsolatról az információt, hanem maga a szerver. Például bejelentkezett egy felhasználó, és éppen aktívan használja az oldalunkat. Nem szeretnénk az adatbázisunkból újra és újra lekérdezni, hogy hány éves\(tegyük fel, hogy ez sokat van használva, mert mondjuk Tinderezik\), ezért eltároljuk ezt az információt a userhez tartozó sessionben. Ez jelentősen megkönnyíti az interakciót a felhasználókkal.

A session tehát igazából egy kisebb adatstruktúra. Itt pár példát láthattok:

```
'54351513186' : { 
                    id: 128, 
                    username: "Jancsi", 
                    tetszoleges_hasznos_informacio: "felemás zoknit hord"
                },

/*              .
                .
                .
                .
                .         */

'98444464642' : {
                    id: 865,
                    username: "Bagoly",
                    rajzkeszsegek: "szépen rajzol baglyot"
                }
```

Az első random szám a** session-id** - ez alapján tudjuk eldönteni, hogy éppen kivel folyik az interakció \(egyszerre akár ezren is használhatják az oldalt\). Ennek olyan előnye is van, hogy nem kell hatalmas mennyiségű cookie-t elküldenünk, ha meg akarunk jegyezni valakiről valamit, csak egyszerűen elküldjük neki sütiként a session-id-t és a továbbiakban elég ha ezt az egyet tudjuk, hiszen a szerveren már eltároltunk minden lényeges adatot.

### A kettő együtt

Tehát akkor hogy is működik ez a két technika együtt? Valahogy így:

1. A user beírja a böngészője címsorába, hogy \[techtabor-url\]
2. A böngésző megnézi, hogy tartozik-e ehhez az oldalhoz süti. Mivel nem talál, hiszen először próbáljuk elérni az oldalt, ezért nem küld semmit.
3. A szerverhez megérkezik a request. A szerver látja, hogy egy olyan userrel van dolga, aki teljesen új, ezért generál egy random számot, mint session-id, és létrehoz neki a sessionben egy új rekordot.
4. A szerver a válasszal együtt visszaküld egy sütit, ami tartalmazza a user session-idjét
5. A böngésző megkapja a választ, elmenti a sütit.
6. A további interakció innentől már a fent leírt módon történik \(így viszonylag kevés információval terhelve a user böngészőjét, és az egész kapcsolatot, viszonylag sokat tudunk a userünkről\).



