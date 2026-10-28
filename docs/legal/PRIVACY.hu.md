# ChaosMC Launcher – adatkezelési tájékoztató

Változat: 1.5.0. Dátum: 2026. október 28.

## 1. Kihez tartozik a launcher?

A launcher üzemeltetője: Gajár Szabolcs. Márkanév: ChaosMC. Kapcsolat és adatkezelési megkeresések: elixifyhu@gmail.com. Weboldal: https://chaosmc.hu/.

Ez a tájékoztató a ChaosMC Launcher saját működését írja le. A Minecraft, a telepített modok, a játék közben felkeresett szerverek és a böngészőben megnyitott szolgáltatások külön is kezelhetnek adatokat.

## 2. Microsoft-fiók és tulajdonjog-ellenőrzés

A játékindításhoz előbb egy Minecraft: Java Editionre jogosult Microsoft-fiók sikeres ellenőrzése szükséges. Az egyszer használatos kódot a Microsoft adja ki. Jelszavadat a Microsoft böngészős oldalán adod meg; a launcher nem kér és nem tárol Microsoft-jelszót, és nem olvassa ki a rendszerböngésződ sütijeit.

A Microsoft, Xbox és Minecraft szolgáltatásain keresztül a launcher hozzáférési és frissítési tokeneket, Xbox-hitelesítési adatokat, a Java Edition jogosultságára adott választ, valamint a Minecraft-profil nevét és UUID-azonosítóját dolgozza fel. Ezek az ellenőrzéshez és a hitelesített játékindításhoz szükségesek.

A hozzáférési tokeneket a launcher a futás idején használja; nem menti őket tartós fájlba. A frissítési token – ha rendelkezésre áll – és a sikeres korábbi tulajdonjog-ellenőrzés feljegyzése az operációs rendszer által védett, titkosított `account.dat` fájlba kerül. Az igazolás tartalmazza az alkalmazáshoz és az ellenőrzött profilhoz tartozó kötést, a Java Edition megjelölését és az ellenőrzés időpontját. Biztonságos tároló nélkül csak az alkalmazás aktuális futására marad meg az ellenőrzés.

Az ellenőrzött Microsoft-tulajdonos és az általad választott offline játékosnév két külön adat. Az offline névből helyben képzett UUID nem a Microsoft-fiók azonosítója, és nem helyettesíti annak ellenőrzését.

## 3. A korábbi ellenőrzés offline használata

A védett helyi igazolással a már telepített játék offline profillal hálózat nélkül is indítható. Az igazolásnak nincs automatikus lejárata: korábbi sikeres ellenőrzést rögzít, nem bizonyítja az aktuális jogosultságot, és az offline indítás nem végez friss Microsoft-hitelesítést vagy tulajdonjog-lekérdezést.

A kijelentkezés törli vagy tartósan érvényteleníti a helyi hitelesítési mentést. Az ellenőrzött fiók frissítésekor ismertté váló licenc- vagy hitelesítési érvénytelenség szintén visszavonja az igazolást. A hálózati hiba önmagában nem vonja vissza a korábbi ellenőrzést. Másik fiók sikertelen vagy megszakított belépése megtartja a korábbi ellenőrzött tulajdonost.

Félbeszakadt újraellenőrzés vagy nem befejezhető érvénytelenítés után a launcher külön helyi jelöléseket is használhat, hogy ne állítsa vissza a bizonytalan igazolást. Tárolási hiba esetén figyelmeztetést mutathat, és új bejelentkezést kérhet.

## 4. Milyen további adat marad a gépeden?

- Beállítások és profilok: például a választott játékverzió, csomag, offline név, memóriakeret, Java-útvonal, grafikus preferencia és a kijelölt profil. Ezek külön helyi fájlokban vannak; nem mind titkosítottak.
- Játékfájlok: letöltött Java, Minecraft, modok, erőforrások, telepítési jegyzékek és gyorsítótárak. A külön játékprofilok világokat, képernyőképeket, játékbeállításokat és saját játék-/modnaplókat is tartalmazhatnak.
- Skin- és modikon-gyorsítótár: a profilképekhez letöltött nyilvános skinek, kapcsolódó azonosítók, valamint a Modrinth-projektek ikonjai. A 24 órás frissítési idő nem automatikus törlési határidő; a korábbi kép hálózati hiba esetén továbbra is használható.
- Naplók: működési üzenetek, hibák, telepítési események, játékosnevek és helyi fájlútvonalak is bekerülhetnek. A launcher az ismert tokenformátumokat kitakarja a saját naplójából. A launcher naplóját induláskor mérethatár felett forgatja; a játék és a modok naplói külön kezelődnek.
- Eltávolított saját modok: a modkezelő a profil `mod-trash` mappájába helyezi őket, ahonnan visszaállíthatók. Ez nem végleges fájltörlés.

A launcher saját kódjában nincs külön beépített analitikai vagy reklámkövető szolgáltatás. Ez nem írja le a telepített modok vagy a külső szolgáltatók saját működését.

## 5. Hálózati kapcsolatok és külső szolgáltatók

A hálózati kérések címzettjei a kapcsolat működéséhez szükséges adatokat – például a nyilvános IP-címet, az időpontot és a kért erőforrást – megismerhetik. Verzió-, frissítés- és szerverállapot-ellenőrzés az alkalmazás indításakor és futása közben automatikusan is történhet. A következő kapcsolatok a launcher jelenlegi működéséből erednek:

| Címzett | Mire használjuk, milyen adat érintett? |
| --- | --- |
| Microsoft, Xbox, Minecraft Services | Eszközkódos bejelentkezés, tokenváltás, jogosultság- és profil-ellenőrzés. A hitelesítési tokenek a megfelelő hitelesítési szolgáltatásokhoz kerülnek. |
| Mojang/Minecraft profil- és textúraszolgáltatások | Microsoft-profilnál UUID, offline névnél nyilvános név–profil keresés a skin megjelenítéséhez. A skinlekérés nem küld fióktokent. |
| Mojang/Minecraft letöltési szolgáltatások és könyvtártárai | Verziójegyzékek, játékfájlok, hangok, textúrák és futtatási könyvtárak letöltése. |
| Modrinth és hivatalos CDN-jei | Keresőkifejezés, választott verzió, kategória, rendezés, projekt-/gyűjteményazonosító, fájlhashek, modpackok, modok és ikonok lekérése. A launcher nem kér Modrinth-bejelentkezést. |
| Fabric és Maven-kiszolgálói | A megfelelő modbetöltő és könyvtárainak lekérése. |
| Eclipse Adoptium és a megadott hivatalos letöltési helyek | A megfelelő Java-futtatókörnyezet és verzióadatainak letöltése. |
| GitHub és kiadási letöltési szolgáltatásai | Launcherfrissítések jegyzékének, aláírásának és telepítőjének ellenőrzése/letöltése. A jogi dokumentumok GitHub-linkje böngészőben nyílhat meg. |
| OptiFine weboldala | Elérhetőségi/verzióinformáció ellenőrzése; a telepítőt a felhasználó szerzi be a hivatalos helyről. |
| DNS-szolgáltató és a kijelölt játékszerver | Névkiszolgálás és szerverállapot-lekérdezés. A szerverping nem Microsoft-bejelentkezés, és nem küld Microsoft-jelszót. |

A launcher a webes API-khoz és letöltésekhez HTTPS-t használ. A szerverállapot és a Minecraft játékforgalma a saját hálózati protokollját követi.

Amikor ténylegesen csatlakozol egy szerverhez, a játékkliens a kapcsolat és a játék működéséhez további adatokat, például játékosazonosítót és játékbeli eseményeket továbbíthat. Egyes modok saját hálózati szolgáltatást használnak. A külső szolgáltatók saját feltételei, megőrzési szabályai és fiókbeállításai is alkalmazandók; az ottani adatokat a launcher helyi kijelentkezése nem törli.

## 6. Megőrzés és törlés

A helyi profilok, beállítások, játékfájlok, világok és gyorsítótárak általában a launcher adatkönyvtárában maradnak, amíg felül nem írod vagy törlöd őket. Az ellenőrzött tulajdonjog helyi feljegyzésének nincs automatikus időbeli lejárata; a visszavonási szabályait a 3. pont ismerteti.

A kijelentkezés nem törli a korábbi offline nevet, világokat, modokat, skineket, ikonokat, beállításokat és naplókat. Nem törli a Microsoft-fiókot, és nem jelentkezik ki a rendszerböngésző Microsoft-munkamenetéből sem.

A jelenlegi Windows-eltávolító szándékosan megőrzi az alkalmazásadatokat. Teljes helyi törlés előtt zárd be a játékot és a launchert, és készíts biztonsági másolatot a megőrizni kívánt világokról, képernyőképekről és beállításokról. A launcher mappamegnyitó funkciójával ellenőrizheted a tényleges helyet; az alapértelmezett könyvtár `%APPDATA%/ChaosMC Launcher/`. Ezután az eltávolítás után külön törölheted a megmaradt adatkönyvtárat. Egyedi adatkönyvtár használatakor annak helyét is ellenőrizd. Frissítési telepítők a Windows külön helyi gyorsítótárában is maradhatnak.

Naplót vagy hibajelentést csak átnézés után küldj a támogatásnak: fájlútvonalak, játékosnevek vagy egy mod saját adatai is szerepelhetnek benne. A launcher nem tölti fel automatikusan a helyi világokat és naplókat támogatási célra.

## 7. Adataid és a rendelkezésedre álló lehetőségek

Módosíthatod a helyi beállításokat, másik offline nevet választhatsz igazolt tulajdonosként, kijelentkezhetsz, és biztonsági mentés után törölheted a helyi adatokat. A Microsoft-fiókodhoz adott alkalmazás-hozzáférést a Microsoft saját fiókbeállításaiban is kezelheted; egy későbbi hitelesítési ellenőrzés ezt figyelembe veheti.

Adatkezelési kérdéssel, hozzáférési, helyesbítési, törlési vagy egyéb, rád alkalmazandó jog gyakorlására irányuló kéréssel az elixifyhu@gmail.com címen keresheted a ChaosMC-t. A kizárólag a saját gépeden tárolt fájlokhoz az üzemeltetőnek nincs távoli hozzáférése pusztán attól, hogy a launchert használod. A külső szolgáltatóknál kezelt adatokkal kapcsolatban azok saját kapcsolattartási és fiókkezelési lehetőségei is rendelkezésre állnak.

## 8. A tájékoztató változásai

A tájékoztató a launcher működésének vagy adatkezelésének változásakor frissülhet. A szöveg elején találod a változatát és a dátumát. Az aktuális tájékoztató a launcher Adatvédelem hivatkozásán és ezen az oldalon érhető el: https://github.com/Szabolcs05/chaosmc-launcher/blob/main/docs/legal/PRIVACY.hu.md .

A változásokkal kapcsolatos kérdéseidet az elixifyhu@gmail.com címre küldheted.
