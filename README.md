# Challenge 14: Magazijn App

## Over dit project

In het magazijn liggen een heleboel materialen die gebruikt kunnen worden door studenten en docenten. Een magazijnuitleenapplicatie zou superhandig zijn om de zaken georganiseerd te krijgen. Het maakt het gemakkelijker om bij te houden wie wat leent, wanneer het terug moet worden gebracht en voorkomt het eeuwige mysterie van "waar is dat ding gebleven?". Het bespaart tijd, vermindert verwarring en maakt het beheer van magazijnvoorraden veel efficiënter.

## Functionaliteiten

Naar aanleiding van de behoefteanalyse is er een overzicht van de gewenste functionaliteiten:
*   Gebruikersbeheer (beheerders, medewerkers, gebruikers).
*   Beheer van de itemcatalogus.
*   Een systeem voor het uitlenen en terugbrengen van items.
*   Bijhouden van de uitleenstatus (uitgeleend, geretourneerd, te laat).
*   Notificaties voor gebruikers (bijv. herinneringen voor het terugbrengen).
*   Een systeem voor het afhandelen van boetes voor te laat ingeleverde items.

## Database Schema (ERD)

Hieronder staat een voorbeeld van de entiteiten, attributen en relaties voor de database.

### Entiteiten en Attributen

**1. Gebruiker**
*   `gebruiker_id` (PK)
*   `gebruikersnaam`
*   `wachtwoord`
*   `e-mail`
*   `rol` (beheerder, medewerker, gebruiker)
*   `registratiedatum`

**2. Item**
*   `item_id` (PK)
*   `naam`
*   `beschrijving`
*   `categorie`
*   `beschikbaarheid` (boolean)
*   `locatie`

**3. Uitleen**
*   `uitleen_id` (PK)
*   `gebruiker_id` (FK)
*   `item_id` (FK)
*   `uitleendatum`
*   `retourdatum`
*   `status` (uitgeleend, geretourneerd, te laat)

**4. Notificatie**
*   `notificatie_id` (PK)
*   `gebruiker_id` (FK)
*   `bericht`
*   `datum`
*   `gelezen` (boolean)

**5. Boete**
*   `boete_id` (PK)
*   `uitleen_id` (FK)
*   `bedrag`
*   `betaald` (boolean)

### Relaties

*   Een **Gebruiker** kan meerdere **Uitleen** hebben.
*   Een **Item** kan meerdere **Uitleen** hebben.
*   Een **Uitleen** hoort bij één **Gebruiker** en één **Item**.
*   Een **Gebruiker** kan meerdere **Notificaties** ontvangen.
*   Een **Notificatie** hoort bij één **Gebruiker**.
*   Een **Uitleen** kan één of geen **Boete** hebben.