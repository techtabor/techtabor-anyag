# Passport

Nézzük hát, hogy mit csinál a Passport.js. Több applikációnál is fontos az, hogy el tudjuk dönteni, hogy kitől jön egy-egy request. Ehhez először általában be kell jelentkezni, ami történhet több módon is \(Google accounttal, Facebookkal, OpenID-vel stb.\). A Passport ezeket ún. stratégiákba sorolja, és azok alapján jelentkezteti be a usereket. A passporton keresztül tehát több modulhoz is hozzáférünk és válogathatunk aszerint, hogy milyen bejelentkeztető rendszert szeretnénk.

### Npm install

A Passport.js-t könnyen lehet telepíteni az npm-mel:

```bash
$ npm install passport
```

Ajánlatos használni az `npm install passport --save`parancsot, ez automatikusan elmenti a Passportot a `package.json` fájlba, mint függőség.

### Autentikáció

Ha már installáltuk a Passportot, akkor már nem maradt túl sok dolgunk:

1. Ki kell találnunk, hogy milyen stratégiát használjunk
2. Konfigurálnunk kell a stratégiát a saját igényeink\(pl. az adatbázisunk\) szerint
3. Használnunk kell az autentikációt, amit előzőleg megprogramoztunk azokon az oldalokon, amelyikeken szeretnénk\(pl. regisztráció, belépés, a user profiljának szerkesztése stb.\)

### Stratégia

Az ember leggyakrabban még mindig a hagyományos username-jelszó párosítást látja a weben. Ezért a `passport-local`modul felelős. Az első kihagyhatatlan lépés az installálás:

```bash
$ npm install passport-local --save
```

### A stratégia konfigurálása

```js
// Használjuk a package-eket
var passport = require('passport');
var LocalStrategy = require('passport-local').Strategy;

// megmondjuk az app-nak, hogy használja a LocalStrategyből csinált middleware-ünket
passport.use(new LocalStrategy(
    function(username, password, done){
        // itt vizsgáljuk meg, hogy a (username, password) pár az megfelel-e egy usernek
        // ha igen, akkor beléptetjük, ha nem, akkor csak megmondjuk, hogy sikertelen volt a bejelentkezés
    }
));
```

### A done függvény

Amikor a saját stratégiánkat írjuk, és már eldöntöttük, hogy a usernek sikerült-e bejelentkeznie, vagy sem, akkor azt valahogy vissza kell adnunk a többi middleware-nek, hogy a sessionökkel és a cookiekkal már ne nekünk legyen bajunk. Erre való a done függvény. A done függvényt a következőképp kell használni:

* ha hiba történik a futás során\(pl. az adatbázis lekérdezésekor\), akkor a return `done(err)`-t kell hívni
* ha sikertelen a bejelentkezés, akkor a return `done(null, false)`-ot kell hívni
* ha sikeres a bejelentkezés, akkor a return `done(null, user)` hívandó

### A user változó



### Példa SQL-el:

```js
var express = require('express');
var app = express();

// require
var passport = require('passport');
var LocalStrategy = require('passport-local').Strategy;
var cookieParser = require('cookie-parser');
var bodyParser = require('body-parser');
var session = require('express-session')

// middleware config
app.use(express.static('public'));
app.use(cookieParser());
app.use(bodyParser());
app.use(session({ secret: 'KEK LOL ROFL HAHA LUL WOW OMG LMAO' }));
app.use(passport.initialize());
app.use(passport.session());

// mysql init
var mysql = require('mysql')
var connection = mysql.createConnection({
    host:         'localhost',
    user:         'root',
    password:     'root',
    database:     'node_db'
});

// mysql connect
connection.connect();

// itt írjuk meg a saját stratégiánkat, ami szerint eldöntjük, hogy beléphet-e a
// user vagy sem
passport.use( new LocalStrategy(
    function(username, password, done){
        // az adatbazisbol olvassuk ki a userhez tartozo adatokat
        connection.query('SELECT * FROM users WHERE username="' + username + '"',
            function(err, rows, fields){
                if(err) return done(err);

                var user = rows[0];

                if( password != user.password ) { // ha rossz a jelszó
                    console.log('Bad password');
                    return done(null, false); // ezt a függvényt kell hívni a dokumentáció szerint
                }

                if( password == user.password ){ // ha jó a jelszó, akkor minden OK
                    console.log("New login");
                    return done(null, user); // továbbküldjük a user változót
                }
            }
        );
    }
));

// elmentjük a user-t a sessionbe
passport.serializeUser(function(user, done) {
    done(null, user.id); // ebben a példában csak az id-t mentjük el
});

// ha pl. kijelentkezik, akkor nincs már szükség arra, hogy
// az adatai továbbra is a sessionben legyenek tárolva
passport.deserializeUser(function(id, done) { 
    connection.query("SELECT * FROM users where id="+id, function(err, rows, fields){
        var user = rows[0];
        done(err, user);
    });
});

function checkLogin(req, res, next){ // a saját checkLogin middleware függvényünk
    if( req.user ){ // a user be van jelentkezve, van joga látni a titkos oldalt
        console.log('user is logged in'); 
        res.redirect('/secret_page/'+req.user.id); // átirányítjuk a titkos oldalra
    } else { // a user nincs bejelentkezve
        console.log('user is not logged in');
        res.redirect('/login'); // átirányítjuk a bejelentkezéshez
    }

    next();
}

app.get('/', checkLogin); // használjuk a middlewaret, ha a /-re jön egy request

app.get('/login', function(req, res){
    console.log('GET on /login');

    // nagyon minimal login form
    res.send('<form action="/login" method="post"><input type="text" name="username"><input type="password" name="password"><input type="submit"></form>');
});

app.post('/login', 
    // bejelentkeztetjuk a usert - ha ez sikeres, akkor a /-re iranyitjuk, amugy a /login-re
    passport.authenticate('local', { successRedirect: '/', failureRedirect: '/login'})
);

app.listen(3000);
```



