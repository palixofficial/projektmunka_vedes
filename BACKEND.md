# MAPUMA Lakáscentrum — Backend

> Laravel 12 alapú REST API | Záródolgozat 2026
> Urbanics Pál · Márki András · Martonfalvai Manassé Antal

---

## Magyar

1. A MAPUMA Lakáscentrum háttérrendszere Laravel 12 keretrendszerrel, PHP 8.2 futtatókörnyezetben valósult meg, RESTful API architektúrát követve.
2. Az összes végpont a `http://localhost:8000/api` alap URL-en keresztül érhető el, és ezeket a React frontend fogyasztja Axios segítségével.
3. A felhasználói autentikációt Laravel Sanctum biztosítja, amely bejelentkezéskor tokent állít ki, majd ezt a frontend minden védett kéréshez csatolja.
4. A bérlési hirdetések szűréséhez dinamikus Eloquent lekérdezések épülnek fel, amelyek több JOIN táblát, where feltételt és rendezési lehetőséget kombinálnak.
5. Az adminisztrátori szerepkörű felhasználók (role === 0) teljes CRUD-műveletet végezhetnek hirdetéseken, bérléseken, értékeléseken és felhasználókon külön admin végpontokon.
6. A képek a `/upload` végponton keresztül tölthetők fel, és Base64 kódolású karakterláncként kerülnek mentésre az adatbázis `rent_images` táblájába.
7. A kiemelt hirdetések automatikusan a találati lista elején jelennek meg; az admin egy dedikált `PATCH` végponton keresztül állíthatja be a kiemelést.
8. Az értékelési rendszer a bérlési rekordokhoz kötött, így csak az adott tranzakcióban részt vevő felhasználók küldhetnek visszajelzést.
9. A backend Docker konténerben fut Supervisor felügyelete alatt, amely kezeli a queue worker folyamatot és az alkalmazás naplózását.
10. Az adatbázis-migrációk és seederek automatikusan lefutnak a konténer indításakor, feltöltve az alaptáblák referenciaadatait és az alapértelmezett admin felhasználót.

---

## English

1. The MAPUMA Lakáscentrum backend is built on Laravel 12 with PHP 8.2, following a clean RESTful API architecture that serves the React frontend.
2. All API endpoints are available under the `http://localhost:8000/api` base URL and are consumed by the frontend using Axios HTTP client.
3. Authentication is handled by Laravel Sanctum, which issues a token on login that the frontend stores and attaches to every subsequent protected request.
4. Rental listing queries are built dynamically using Eloquent ORM, combining multiple JOINs, where clauses, and sorting options based on incoming filter parameters.
5. Admin users (role === 0) have access to dedicated endpoints for full CRUD operations on all listings, rentings, users, and reviews in the system.
6. Images are uploaded via the `/upload` endpoint and stored as Base64-encoded strings in the database `rent_images` table, linked to their parent listing.
7. Highlighted listings are automatically prioritized in query results, and admins can toggle a listing's highlight status via a dedicated `PATCH` endpoint.
8. The review system is tied directly to renting records stored in the database, ensuring only participants of a specific transaction can submit feedback.
9. The backend runs inside a Docker container supervised by Supervisor, which manages the queue worker process and the application logging pipeline.
10. Database migrations and seeders run automatically on container startup, populating reference tables and creating the default admin account for immediate use.
