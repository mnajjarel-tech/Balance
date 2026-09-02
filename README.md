# Balance

Balance is een volledig offline voedings-, activiteits-, trainings- en gewichtstracker als vanilla PWA. Er is geen account, backend, cloud-database, npm, Node-buildstap of externe library nodig.

## Bestanden

- `index.html` – interface en alle CSS inline.
- `app.js` – applicatielogica plus de ingebouwde productbibliotheek.
- `manifest.json` – PWA-manifest.
- `sw.js` – offline service worker.
- `icons/` – 192, 512 en maskable PWA-iconen.
- `.nojekyll` – voorkomt Jekyll-verwerking op GitHub Pages.

## Functies

- Dagdashboard met kcal, macro's, water, stappen, actieve kcal en geschatte energiebalans.
- Maaltijd-builder volgens categorie/winkelmand-principe: maaltijdmoment → categorie → meerdere producten selecteren → gram/ml invoeren → toevoegen → eindcontrole → opslaan.
- 156 seed-productrecords verdeeld over groenten, fruit, zuivel, kaas, ei, vis, vlees, noten, pitten/zaden, granen, peulvruchten, proteïne, olie/vet en extra's.
- Droog/bereid-uitleg voor rijst, quinoa, bulgur, couscous en gedroogde peulvruchten.
- Favorieten en recente producten.
- Zelf samengestelde maaltijden optioneel bewaren als eigen recept.
- Trainingsagenda met CRUD.
- Gewicht met maximaal één meting per dag, 7-daags gemiddelde en trends.
- Trends over 7/30/90 dagen met inline SVG.
- Doelen voor kcal, macro's, water, stappen, rustverbranding, smartwatch-correctie en doelgewicht.
- Eigen producten toevoegen.
- Lokale JSON-back-up export/import.
- Volledig offline na eerste succesvolle laadbeurt via service worker.

## Lokaal testen

Een service worker werkt niet betrouwbaar wanneer je `index.html` rechtstreeks via `file://` opent. Start daarom een eenvoudige lokale statische server in deze map, bijvoorbeeld:

```bash
python -m http.server 8080
```

Open daarna `http://localhost:8080/` in Chrome, Edge of een andere moderne browser.

## GitHub Pages

1. Maak een nieuwe GitHub-repository.
2. Upload **de inhoud van deze map** naar de root van de repository.
3. Ga naar **Settings → Pages**.
4. Kies bij **Build and deployment** voor **Deploy from a branch**.
5. Selecteer de branch (bijvoorbeeld `main`) en map `/ (root)`.
6. Sla op en wacht tot GitHub Pages de publieke URL toont.
7. Open de URL één keer online zodat de service worker de statische bestanden kan cachen.
8. Daarna kan de PWA offline werken.

De app gebruikt hash-navigatie en relatieve paden, waardoor hij ook werkt wanneer GitHub Pages hem onder `https://gebruikersnaam.github.io/repositorynaam/` publiceert.

## Android / PWABuilder

Wanneer de GitHub Pages-URL live is, kun je deze in PWABuilder invoeren. Controleer daar eerst de PWA-audit. De app bevat een manifest, service worker en 192/512/maskable iconen.

## Dataprivacy

Alle gebruikersdata worden lokaal opgeslagen in `localStorage` van de browser. Er worden geen voedingslogs, gewicht, agenda-items of instellingen naar een server verstuurd. Verwijderen van browsergegevens kan de lokale data wissen; gebruik daarom regelmatig **Instellingen → Back-up exporteren**.

## Voedingsdata

De seed-dataset komt uit de aangeleverde Balance-productbibliotheek. Generieke waarden verwijzen naar RIVM/NEVO; specifieke merkproducten bevatten waar beschikbaar de bronstatus en bron-URL uit die bibliotheek. Bereidingsfactoren zijn richtwaarden en kunnen door kookmethode en wateropname variëren.

## Versie

Balance v1.0.0 – GitHub Pages ready.

## v1.1 productbewerking
Alle producten in de ingebouwde bibliotheek kunnen nu via **Meer → Producten → Bewerken** worden aangepast. Wijzigingen worden lokaal als override opgeslagen en blijven bestaan bij normale app-updates. Eerdere maaltijdregistraties blijven ongewijzigd omdat de voedingswaarden als snapshot zijn opgeslagen. Bij een aangepast standaardproduct verschijnt ook **Herstel standaard**.
