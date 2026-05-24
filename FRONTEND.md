# MAPUMA Lakáscentrum — Frontend

> React alapú felhasználói felület | Záródolgozat 2026
> Urbanics Pál · Márki András · Martonfalvai Manassé Antal

---

## Magyar

1. A MAPUMA Lakáscentrum frontendje React 19 és TypeScript technológiák segítségével készült, biztosítva a típusbiztos, karbantartható kódbázist.
2. A felhasználói felület Tailwind CSS stílusrendszert és Radix UI komponenseket használ, amelyek modern, reszponzív megjelenést nyújtanak minden eszközön.
3. Az alkalmazás a háttérrendszerrel Axios HTTP kliens segítségével kommunikál a `http://localhost:8000/api` végponton keresztül, amelyet a Laravel backend szolgál ki.
4. A főoldalon a felhasználók dinamikusan szűrhetnek város, megye, ár, alapterület, szobaszám és elérhetőségi állapot alapján, a szűrők azonnal frissítik a találati listát.
5. A bejelentkezés és regisztráció oldalain a Sanctum-alapú token autentikáció révén biztonságos hozzáférés valósul meg, a token localStorage-ban kerül tárolásra.
6. A lakás részletoldalán képgaléria, felszereltségi lista és felhasználói értékelések jelennek meg csillagos értékeléssel együtt.
7. A profiloldalon a bejelentkezett felhasználó módosíthatja nevét, jelszavát és profilképét, amelyet Base64 formátumban küld el a backendnek.
8. Az adminisztrátori panel négy szekciója lehetővé teszi a hirdetések, felhasználók, bérlések és értékelések teljes körű kezelését táblázatos nézetben.
9. A React Router DOM v7 biztosítja az oldalak közötti navigációt egyoldalas alkalmazásként, a React Hot Toast pedig visszajelzést nyújt a felhasználói műveletekről.
10. A frontend Docker Compose környezetben a 3000-as porton fut, és közvetlenül kapcsolódik a Laravel backenddel és a MySQL adatbázissal.

---

## English

1. The MAPUMA Lakáscentrum frontend is built with React 19 and TypeScript, ensuring a type-safe and maintainable codebase throughout the application.
2. The user interface leverages Tailwind CSS and Radix UI components to deliver a responsive, accessible design that works across all screen sizes.
3. All HTTP communication with the backend is handled by Axios, targeting the Laravel REST API at `http://localhost:8000/api`.
4. The home page offers dynamic filtering by city, county, price range, area, bedroom count, and availability status, with results updating instantly on every filter change.
5. Authentication is powered by Laravel Sanctum tokens: upon login, the token is stored in localStorage and attached to every subsequent authenticated request.
6. The apartment detail page displays a full image gallery, a list of available utilities and amenities, and user reviews with star ratings.
7. The profile page allows logged-in users to update their display name, password, and avatar image, which is sent to the backend as a Base64-encoded string.
8. The admin panel is divided into four sections for managing listings, users, rentings, and reviews, all presented in sortable, editable table views.
9. Client-side routing is handled by React Router DOM v7 for a smooth single-page experience, while React Hot Toast provides instant feedback on user actions.
10. In the Docker Compose setup, the frontend runs on port 3000 and is fully integrated with the Laravel backend on port 8000 and the MySQL database on port 3306.
