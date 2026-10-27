# Spine 📖

Een mobiele boekentracker in React Native met Expo. Hou bij wat je leest, wat je gelezen hebt en wat je nog wil lezen, schrijf reviews en exporteer je leeslijst als PDF.

Individueel project voor het vak **Webframeworks** (Graduaat Programmeren, AP Hogeschool, 2026–2027).

## Functionaliteit

- Boeken zoeken via de [Open Library API](https://openlibrary.org/developers/api) of de barcode (ISBN) scannen met de camera
- Elk boek een status geven: *te lezen*, *aan het lezen* of *gelezen*
- Je voortgang bijhouden (huidige pagina) en een review met score (1–5) schrijven
- Een eigen cover kiezen uit je galerij
- Een dagelijkse leesherinnering op een tijdstip naar keuze
- Een gefilterde boekenlijst exporteren als PDF
- Een jaarlijks leesdoel met statistieken

## Tech stack

| Onderdeel | Technologie |
| --- | --- |
| Framework | React Native + Expo (TypeScript) |
| Navigatie | Expo Router (tabs + stack + modal) |
| Styling | NativeWind (Tailwind CSS) |
| Backend | Supabase (`@supabase/supabase-js`) |
| Lokale opslag | AsyncStorage |
| Externe API | Open Library |

### Expo-features

| Feature | Package | Gebruik in de app |
| --- | --- | --- |
| Camera | `expo-camera` | Barcode (ISBN) van een boek scannen |
| ImagePicker | `expo-image-picker` | Eigen boekcover kiezen |
| Notifications | `expo-notifications` | Dagelijkse leesherinnering, melding bij het halen van je leesdoel |
| Print | `expo-print` | PDF van je boekenlijst, gefilterd op status |

Voor elke feature vraagt de app de nodige permissie aan. Weigert de gebruiker die, dan blijft de app bruikbaar en verschijnt er uitleg.

## Schermen

| Scherm | Route |
| --- | --- |
| Bibliotheek | `app/(tabs)/index.tsx` |
| Zoeken & toevoegen | `app/(tabs)/search.tsx` |
| Profiel & instellingen | `app/(tabs)/profile.tsx` |
| Scanner (modal) | `app/scan.tsx` |
| Boekdetail | `app/books/[id].tsx` |
| Review schrijven | `app/books/[id]/review.tsx` |

## Projectstructuur

```
app/          Schermen en navigatie (Expo Router)
components/   Herbruikbare componenten (BookCard, StatusFilter, StarRating, ...)
context/      BooksContext en SettingsContext
hooks/        Eigen hooks
types/        TypeScript-interfaces (Book, Review, Settings)
services/     AsyncStorage, notificaties, PDF-export, Open Library
supabase/     Supabase-client, queries en databankschema
styles/       Thema en class-presets voor NativeWind
docs/         Projectvoorstel en wireframes
```

## Aan de slag

### Vereisten

- [Node.js](https://nodejs.org/) (LTS)
- De app **Expo Go** op je smartphone ([Android](https://play.google.com/store/apps/details?id=host.exp.exponent) / [iOS](https://apps.apple.com/app/expo-go/id982107779))
- Een (gratis) [Supabase](https://supabase.com/)-project

### Installatie

```bash
git clone <url-van-deze-repo>
cd spineapp
npm install
```

### Omgevingsvariabelen

Maak een bestand `.env` in de root van het project:

```
EXPO_PUBLIC_SUPABASE_URL=https://<jouw-project>.supabase.co
EXPO_PUBLIC_SUPABASE_ANON_KEY=<jouw-anon-key>
```

Je vindt beide waarden in het Supabase-dashboard onder **Project Settings → API**. Het bestand `.env` staat in `.gitignore` en wordt niet mee gecommit.

### Databank

Voer `supabase/schema.sql` uit in de SQL-editor van Supabase. Dat maakt de tabellen `books` en `reviews` aan, samen met hun policies.

### Starten

```bash
npx expo start
```

Scan de QR-code met Expo Go (Android) of met de camera-app (iOS). Je gsm en computer moeten op hetzelfde netwerk zitten.

## Gebruik van AI

Volgens de projectopdracht mag AI alleen voor bepaalde onderdelen gebruikt worden. In deze repo:

| Met AI | Zonder AI |
| --- | --- |
| Projectvoorstel en wireframes (`docs/`) | Routing en schermen (`app/`) |
| Supabase-verbinding en queries (`supabase/`) | Componenten, state en context |
| Styling en NativeWind-config (`styles/`, configbestanden) | AsyncStorage en Expo-features |
| | TypeScript-interfaces en de rest van de code |

Commits met AI-gegenereerde code beginnen met `[AI]`.

## Auteur

**Dimitrije Ivanovic** · [GitHub](https://github.com/DimitrijeIvanovic) · [Portfolio](https://dimitrije-portfolio.mooo.com)
