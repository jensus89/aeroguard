# AEROGUARD – UAS Operations

Webapplicatie (één pagina, geen installatie of buildstap) voor het voorbereiden van droneoperaties. Werkt op pc, gsm en tablet.

## Bestanden
- `index.html` : de volledige applicatie, inclusief toegangsscherm
- `sw.js`, `manifest.webmanifest`, `icon.svg` : offline-cache en "toevoegen aan startscherm"
- `.nojekyll` : zorgt dat GitHub Pages de bestanden ongewijzigd publiceert

## Online zetten met GitHub Pages (via de website, zonder programmeerkennis)
1. Maak een gratis account op https://github.com en meld je aan.
2. Klik rechtsboven op **+** en kies **New repository**.
3. Geef een naam (bv. `aeroguard`), kies **Public** (gratis Pages vereist een publieke repository) en klik **Create repository**.
4. Klik op **uploading an existing file** (of **Add file > Upload files**).
5. Open de map op je pc en sleep de **inhoud** van de map naar het venster: `index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg` en `.nojekyll`. `index.html` moet in de hoofdmap staan, niet in een submap. (`.nojekyll` is op sommige systemen verborgen; lukt het niet, dan werkt de site meestal ook zonder.)
6. Klik onderaan op **Commit changes**.
7. Ga naar **Settings > Pages**. Kies bij *Source* **Deploy from a branch**, bij *Branch* **main** en map **/ (root)**, en klik **Save**.
8. Wacht 1 tot 2 minuten. Bovenaan de Pages-instellingen verschijnt je adres: `https://JOUWNAAM.github.io/aeroguard/`.
9. Open dat adres, geef het paswoord in (**VA070**) en gebruik de app.

## Updaten
Open de repository, klik **Add file > Upload files**, sleep het nieuwe `index.html` erin en kies **Commit changes**. Na een minuut is de nieuwe versie online. Bij een hardnekkig oude versie: vernieuw de pagina met Ctrl+F5.

## Op gsm of tablet als app
Open het adres in Chrome (Android) en kies menu > **Toevoegen aan startscherm** (of **App installeren**). Op iPhone: Safari > Delen > **Zet op beginscherm**.

## Paswoord wijzigen
Het paswoord staat niet leesbaar in de code, enkel als SHA-256-hash in `index.html` (zoek `const PH=`). Pas in dat geval `PASSWORD` aan in `build.py` en voer `python3 build.py` opnieuw uit, of bereken de hash manueel:
- Linux/Mac: `printf 'aeroguard:NIEUWPASWOORD' | sha256sum`
Vervang de waarde bij `PH` in `index.html` en upload het bestand opnieuw.

## Kaart en obstakellagen
Het tabblad Kaart toont hoogspanningsmasten, zendmasten/antennes, windturbines, watertorens, schoorstenen, overige constructies én luchtvaartterreinen (luchthavens, vliegvelden, helihavens, start- en landingsstroken) als afzonderlijke lagen die je rechtsboven op de kaart kunt aan- of uitvinken. Obstakels worden gezocht binnen 8 km, luchtvaartterreinen binnen 50 km (een ruimere zone, omdat ook kleine vliegvelden operationeel relevant zijn). Klik op een punt voor coördinaten, type en, indien gekend, hoogte of ICAO/IATA-code.

## Belangrijk over beveiliging
Het toegangsscherm is een eenvoudige drempel in de browser, geen echte beveiliging. Alles wat de browser kan lezen, kan ook een bezoeker lezen: wie handig is met de ontwikkelaarstools kan het scherm omzeilen, en een kort paswoord is via de hash te kraken. Gebruik het dus als afscherming tegen toevallige bezoekers.
- Zet geen vertrouwelijke politiegegevens in de repository of in de code.
- Gegevens die je in de app invult (piloten, drones, rapporten, documenten) blijven enkel in de browser van dat toestel en worden niet gedeeld of gesynchroniseerd.
- Voor echte toegangscontrole en gedeelde gegevens is een backend met aanmelding nodig (bv. Microsoft Entra ID), af te stemmen met de ICT-verantwoordelijke van de politiezone.

## Databronnen
Open-Meteo (weer), NOAA SWPC (Kp-index), OpenStreetMap/Overpass (obstakels en luchtvaartterreinen, niet volledig of officieel), Nominatim (gemeente), DroneGuide, skeyes (AIP, NOTAM) en ADS-B Exchange via snelkoppelingen. Respecteer de gebruiksvoorwaarden van deze diensten.
