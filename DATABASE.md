# MAPUMA Lakáscentrum — Adatbázis

> MySQL 8.0 séma | Záródolgozat 2026
> Urbanics Pál · Márki András · Martonfalvai Manassé Antal

---

## Magyar

1. A MAPUMA Lakáscentrum adatbázisa MySQL 8.0 rendszeren alapul, amelyet a Laravel Eloquent ORM kezel a backend oldalán, verziókövetett migration fájlokon keresztül.
2. A központi `rents` tábla tartalmazza a hirdetések összes adatát: cím, ár, deviza, alapterület, szobaszám, fürdőszobaszám, elérhetőségi állapot és kiemelési dátum.
3. A `rent_images` tábla tárolja a hirdetésekhez feltöltött képeket Base64 kódolású longText mezőkben, és kaszkád törléssel kapcsolódik a `rents` táblához.
4. A `rentings` tábla rögzíti a bérlési tranzakciókat, és egyidejűleg hivatkozik a bérlőre és a tulajdonosra is a `users` táblán keresztül, megőrizve a bérlési időszakot.
5. Az értékelések a `reviews` táblában tárolódnak, és mindig egy konkrét `rentings` rekordhoz kötődnek, így csak valódi bérlési tranzakcióhoz lehet értékelést írni.
6. A `utilities` és `utility_options` táblák egy kapcsolótáblás many-to-many kapcsolatot valósítanak meg a hirdetések és az elérhető felszereltségi opciók között.
7. A `counties` és `cities` referenciatáblák konzisztens helyszínadatokat biztosítanak, amelyeket mind a backend szűrőlogikája, mind a frontend legördülő listái felhasználnak.
8. A `rent_types` tábla kategorizálja a hirdetéseket típusonként (pl. lakás, ház, garzon), amelyek szintén megjelennek a frontend szűrőiben.
9. Az adatbázis Docker Compose környezetben fut, és a phpMyAdmin felület a 8080-as porton keresztül érhető el vizuális felügyelethez és karbantartáshoz.
10. Az adatbázis seederek alapértelmezett admin felhasználót, demó hirdetéseket, városokat, megyéket és felszereltségi opciókat hoznak létre az alkalmazás első indításakor.

---

## English

1. The MAPUMA Lakáscentrum database runs on MySQL 8.0 and is managed entirely through Laravel's Eloquent ORM and versioned migration files on the backend.
2. The central `rents` table holds all listing data: title, price, currency, area, bedroom count, bathroom count, availability status, and highlight timestamp.
3. The `rent_images` table stores uploaded listing photos as Base64-encoded longText values and is linked to `rents` with cascading delete to keep data consistent.
4. The `rentings` table records rental transactions and references both the renter and the listing owner from the `users` table, preserving the full rental period.
5. Reviews are stored in the `reviews` table and are always tied to a specific `rentings` record, ensuring that only participants of a real transaction can leave feedback.
6. The `utilities` and `utility_options` tables implement a many-to-many relationship via a pivot table, connecting listings to available amenity options such as parking or balcony.
7. The `counties` and `cities` reference tables supply consistent geodata used by both the backend's filter logic and the frontend's dropdown selectors.
8. The `rent_types` table categorizes listings by property type (e.g. apartment, house, studio), which also feeds into the frontend's filter options.
9. The database runs in a Docker container with phpMyAdmin accessible at port 8080 for visual inspection and administrative management of all tables.
10. Database seeders automatically create a default admin account, demo listings, counties, cities, and utility options when the application is launched for the first time.
