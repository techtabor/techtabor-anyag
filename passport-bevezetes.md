# Passport.js Tutorial

### Mi az a [Passport](http://passportjs.org/)?

> Passport is an authentication middleware for Node.js.

A Passport tehát egy _middleware_ ami azért felelős, hogy a usereinket be- és kiléptethessük, valamint számontartja azt, hogy éppen be vagy ki vannak jelentkezve. Na de mi az middleware?

### Middleware

A middleware-függvények olyan függvények, amik \(legalább\) 3 adathoz férnek hozzá: a _request object_-hoz, a _response object_-hoz, és a _next_ függvényhez, amely egy tetszőleges függvény, ami a middleware-függvény futása után hajtódik végre.

Mit tud csinálni egy middleware-függvény? Egy middleware függvény a következőkre képes:

* Végre tud hajtani parancsokat
* Tud változtatni a request- és response-objecteken
* Be tudja fejezni a request-response ciklust
* Meg tudja hívni a next függvényt

Ha egy middleware függvény nem fejezi be a request-response ciklust, akkor meg kell hívnia a next függvényt, különben a request nem lesz kiértékelve és nem lesz válasz a userhez visszaküldve\(ilyet nem akarunk\).

### Példa

```js
var express = require('express')
var app = express()

var myLogger = function (req, res, next) {
  console.log('LOGGED')
  next()
}

app.use(myLogger)

var count = 0

app.get('/', function (req, res) {
  res.send( "Ez ma a " + String(count) + ". oldalbetöltés!" )
  count = count + 1
})

app.listen(3000)
```

A fenti kódban lévő myLogger függvény semmi mást nem csinál, csak a req és res változóktól függetlenül kiírja a console-ra azt, hogy 'LOGGED'. Ez után meghívja a next függvényt. Ahhoz, hogy a Node appunk ezt a _middleware_-t használni tudja, jeleznünk kell neki a use paranccsal, hogy mi ezt a függvényt szándékosan middleware-ként akarjuk használni - úgy is definiáltuk \(hiszen a req\(request\), res\(response\) és next\(ez egy függvény\) a paraméterei\).

Ez után az appunkban ez a middleware mindig le fog futni, ahányszor egy request érkezik a szerverünk felé.

* Próbáld ki párszor frissíteni a localhost oldalt a böngésződben! Figyeld a konzolt is! Mi történik?
* Mi történik, ha nem hívjuk meg a next függvényt?



