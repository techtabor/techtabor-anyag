# Bevezetés

Egészen nagyszabású projekteken dolgoztok egyénileg vagy párban. Ilyen méretű projekteknél majd látjátok, hogy sokfajta probléma lép fel: összekuszálódik a cél, elakad a projekt, nem fér bele annyi az időbe mint amit az ember elképzel, elfelejti, hogy miket tervezett csinálni, és eközben folyamatosan koordinálnia kell a partnerével is. Sokfajta technika létezik ezeknek a problémáknak a kezelésére. Az alábbiakban ezekről olvashatsz. Habár nem lesz rögtön szükséged mindre, illetve sok elsőre akár értelmetlennek is tűnhet, mégis érdemes tudni róluk, hogy amikor a problémák beköszöntenek, majd tudd őket kezelni.

# Tervezés \(“Planning”\)

Ha nem is tudatosan, te is mindenképpen terveztél már: a kisebb projekteknél, például a játéknál, eldöntötted, hogy milyen legyen a végeredmény, majd azt, hogy milyen sorrendben programozod le a részeit. A terv alapján megbecsülted, hogy belefér-e a határidőig elkészíteni a játékot. Eközben persze a terved változott is.

A nagyobb projekteknél ez már sokszor nem megy fejben. Explicit terv nélkül nem lehet csapatban megbeszélni a teendőket, sokszor pedig elakadnak a projektek, nem érik el a céljaikat, vagy sokkal kevesebbet érnek el mint amit eredetileg elgondoltak.

Sokan a tervről azt hiszik, hogy az egy pontos útmutató arról, hogy mikor mit kell csinálni, és amit szó szerint követni kell a projekt végéig. Ez azonban nincs így. A terv elsősorban egy eszköz számodra azért, hogy jobban megértsd a projekted komponenseid, illetve azt, hogy hogy haladsz vele.

1. A terv segít egy mentális modellt építeni a projektedről, mert rákényszerülsz arra, hogy kigondold a részleteket.
2. A leírt terv segítségével megbeszélheted a csapattársaiddal és mentorokkal, hogy hogyan képzeled el a projektet, és közösen gondolkodhattok a megvalósításon.
3. Egy nagy projektnek sok komponense van, és nem csak napokra, hanem hetekre, hónapokra, és évekre is előre kell gondolkodni. Ennyi mindent képtelenség fejben tartani. Ezért a terv arra is jó, hogy felidézd a projekted megvalósításának a részleteit.
4. A terv arra is jó, hogy ütemezd a feladataidat. Ezáltal lesz fogalmad arról, hogy 1\) belefér-e az adott időtartamba a projekted 2\) mikor min kell dolgoznod 3\) megfelelő ütemben haladsz-e a megvalósítással, vagy esetleg újra kell-e gondolnod a tervet és a projektet.

# Sarkcsillag \(“North Star”\)

Az [északi sarkcsillag](https://en.wikipedia.org/wiki/Pole_star) egy fix pont az égen: míg az éjszaka során a csillagok elmozdulni látszanak a Föld forgása miatt, a sarkcsillag látszólag egy pontban áll, minden egyéb mozgás ellenére. Ezért \(volt\) olyan hasznos a tengeri navigációban: akármerre is sodort a tenger vagy fújt éppen a szél, bátran választhattál irányt a sarkcsillag alapján.

A projekttervek definiálásakor a sarkcsillagon a projekted távlati célját értjük. Mi a probléma amit megcélzol? Miért fontos megoldani? Mi a megoldási javaslatod? Miért fog működni? Kik fogják használni? Mikor tekinthető a projekt sikeresnek?

A sarkcsillag megfogalmazása segít letisztázni, hogy mit szeretnél elérni:

1. magadnak \(néha csak egy katyvasz van az ember fejében\);
2. a csapattársaidnak, hogy biztosan szinkronban legyetek a céllal kapcsolatban;
3. külső szemlélőknek, hogy mások is értsék, mit akarsz elérni;
4. de még a jövőbeli énednek is: ugyanis az ember hosszabb projektek során könnyen szem elől tudja téveszteni a távlati célt.

Mindenképpen fogalmazd meg ezeket a célokat a projektedhez, és írd is le őket.

> Hogyan fogalmaznád meg a Wikipedia sarkcsillagját? És a kedvenc cégedét/projektedét?

# Mérföldkövek \(“Milestones”\)

Amikor egy projektet tervezel, lehetetlen pontosan belőni, hogy mire lesz időd. Éppen ezért hasznos úgynevezett _mérföldköveket_ megfogalmazni.

Tegyük fel, hogy egy olyan amőba játékot akarsz írni egy hónap alatt, ahol a számítógép játszik veled. Ez egy nagy cél, és mivel sok ismeretlen része van, nehéz megmondani, hogy vajon teljesen kifutnál-e az időből, vagy ellenkezőleg, egy csomó időd marad még a hónap végén.

Ezért egyetlen cél megfogalmazása helyett érdemes több mérföldkövet definiálni. Például:

1. \[minimum\] 3x3-as amőba készítése két emberi játékossal
2. \[minimum\] NxM-es amőba két emberi játékossal
3. \[várható\] Nyerő stratégiás számítógépes játékos 3x3-ra
4. \[extra\] Egyszerű számítógépes játékos NxM-re
5. \[extra\] Fejlett, vagy ha lehetséges, nyerő stratégiás számítógépes játékos NxM-re

Ezek a példa mérföldkövek jók, mert:

* A minimum követelményeket relatíve könnyű teljesíteni, így valami működőt biztosan elérsz ebben az egy hónapban;
* a várható \(“expected”\) mérföldkövek már egy rendes, érdekes projektet alkotnak;
* az extra \(“stretch”\) mérföldkövek kiegészítések egy nagyon fejlett projekthez.

Mindenképpen bontsd fel a terved ilyen mérföldkövekre, és azt is próbáld meg megsaccolni, hogy mennyi időbe telik majd megvalósítani őket. Ne aggódj ha nem tudod pontosan megtippelni: senki sem tudja, és majd év közben frissítjük a becsléseket.

> Mik lehetnének egy Wikipedia projekt mérföldkövei?

# Minimum Viable Product \(MVP\)

A \`[Minimum Viable Product](https://en.wikipedia.org/wiki/Minimum_viable_product)\` szó szerint “minimális életképes terméket” jelent. Ez egy olyan termékverzióra utal, ami már nyújt valami új funkcionalitást, de éppen csak a minimálisat ami a működéshez szükséges.

Térjünk vissza az amőba programra. Az MVP lehet például egy 3x3-as amőba két emberi játékossal, egyebek nélkül. De az MVP-be nem tartozik bele az általános méret, a számítógépes játékos, de nincs benne mentés sem, high scores, regisztrált felhasználók, vagy akár fejlett grafika.

Mi ennek az értelme? Két nagyobb indoka is van.

## Az ötlet hatékony tesztelése

Sokszor az emberek, cégek, projektek “elkalandoznak”, és sok olyan dolgot kifejlesztenek, amik ugyan kényelmesebbé teszik a használatot, de nem tartoznak a projekt központi, új eleméhez \(a fenti példában ilyen az állás mentése vagy a high scores\). Azonban sokszor, főleg újszerű projektek fejlesztésénél, nem lehet előre megmondani, hogy tényleg működőképes-e a konstrukció, illetve hogy mennyire nehéz lefejleszteni. Ezért az MVP abban segít, hogy a lehető leghamarabb, a legkevesebb befektetett energia segítségével megállapítsd, hogy a programod lényege működik-e.

Nézzünk meg két esetet, mondjuk a Twitter esetében.

1. Az egyik esetben lehet szöveget írni, új felhasználót regisztrálni, illetve egymást követni. Ezt mondjuk 3 hónap elkészíteni.
2. A másik esetben lehet szöveget írni, de képet és videót is fel lehet tölteni. Lehet új felhasználót regisztrálni, de Google és Facebook accounttal is be lehet lépni. Lehet egymást követni, de privát felhasználói fiókokat is létre lehet hozni. Ezt mondjuk 9 hónap elkészíteni.

Ha nem tudjuk előre, hogy a Twitter népszerű lesz-e, akkor melyiket érdemes először elkészíteni? Az 1-es esetben 3 hónapot töltöttünk el vele, és mondjuk 50 000 dollárt. A másik esetben 9 hónapot, és kb. 150 000 dollárt. Ha az ötlet nem működik, akkor a második esetben sokkal több pénzt dobtunk ki, és ráadásul később is tudunk csak változtatni az ötleten. Ha az ötlet működik, akkor még mindig ráérünk kifejleszteni a további feature-öket, ha valóban szükség van rájuk.

## Priorizálás és Feature Creep

A másik indok szorosan kapcsolódik az előbbihez: a priorizálás. Folyamatosan szem előtt kell tartani, hogy mik a legfontosabb, elengedhetetlen feature-ök. Ha az ember olyat fejleszt, ami nem nagyon fontos, akkor időt pazarol el.

Ezzel kapcsolatos a _Feature Creep _fogalma is. Ez azt a jelenséget takarja, amikor a fejlesztők elvesztik a lényegi elemeket szem elől, és olyan dolgokra is pazarolják az idejüket, amik nem létfontosságúak. Ilyenkor sokszor a projekt el sem készül időben, van túl bonyolult lesz.

Ezekben is sokat segít az MVP-re való koncentrálás.

> Mi lehetne a Wikipedia vagy a Facebook MVP-je?

## A tervezési csapda \(Planning Fallacy\)

Gondolj a legközelebbi beígért témazáró dolgozatodra. Mit gondolsz, hány napba telik majd felkészülnöd? \(Tényleg válaszolj erre a kérdésre.\) És mit gondolsz, a legeslegjobb esetben, ha minden jól alakul, hány napba telne felkészülnöd? És a legeslegrosszabb esetben?

Most gondolj arra, hogy a legutóbbi pár alkalommal mennyi idő volt felkészülni a nagydolgozatra. Több idő volt, mint amennyire most gondoltál? És úgy sikerült időben felkészülni?

Kutatásokból kiderült, hogy a legtöbb ember amikor megbecsli valaminek az idejét, igazából a legeslegjobb esetet becsli meg. Ezzel szemben a valóságban még a legrosszabb esetre tippelt időnél is többet töltenek el az adott teendővel. Ezt hívják a _tervezési csapdának _\(Planning Fallacy\).

Hogyan lehet ez ellen védekezni? Felejtsd el a részleteket, és gondolj hasonló projektekre. Pl. ha azt kell megbecsülni, hogy mennyi idő felkészülni a nagydolgozatra, gondolj a korábbi nagydolgozatok előtti időre.

Ennek a témának nagyon érdekesek a részletei és a mögötte álló kutatások; ha érdekel, ajánlom [ezt a Less Wrong cikket](http://lesswrong.com/lw/jg/planning_fallacy/).

# A tervek

A terveidet írd is le, majd oszd meg őket a csoporttal a [közös google drive mappánkban](https://drive.google.com/drive/folders/0B4CEjXzOjZEldlBZaUtORXh6dDg).

