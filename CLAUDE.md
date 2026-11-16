# SpineApp – regels voor Claude

SpineApp is een mobiele boekentracker in React Native + Expo (TypeScript), voor het vak Webframeworks (AP Hogeschool). Het is een **schoolproject met strikte AI-regels**: de meeste code moet de student zelf schrijven. Lees dit bestand volledig voor je iets doet.

## AI-zones

Je mag alleen code schrijven, aanpassen of voorstellen in deze bestanden en mappen:

| Toegestaan                                                                                      | Waarvoor                                                                                   |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| `supabase/`                                                                                     | Supabase-client, tabellen, policies (`schema.sql`) en de functies die de queries uitvoeren |
| `styles/`                                                                                       | Thema (`theme.ts`) en NativeWind-class-presets (`classes.ts`)                              |
| `docs/`                                                                                         | Projectvoorstel, wireframes, documentatie                                                  |
| `tailwind.config.js`, `global.css`, `metro.config.js`, `babel.config.js`, `nativewind-env.d.ts` | NativeWind-configuratie                                                                    |
| `README.md`                                                                                     | Documentatie                                                                               |

**Al de rest is verboden terrein.** Daar schrijft de student de code zelf:

- `app/` – schermen, layouts, navigatie, route-parameters
- `components/` – componenten, props en callbacks
- `context/` – `BooksContext`, `SettingsContext`
- `hooks/` – eigen hooks
- `types/` – TypeScript-interfaces (`Book`, `Review`, `Settings`, `BookStatus`)
- `services/` – AsyncStorage, Notifications, Print, Open Library
- `app.json` – configuratie, permissies en plugins van de Expo-features

## Wat je NIET doet buiten de AI-zones

- Geen bestanden aanmaken, bewerken of verwijderen, ook niet via shell-commando's (`echo >`, `sed`, `cp`, `mv`, scripts, ...).
- Geen code voorstellen of uitschrijven in de chat, ook geen "voorbeeld", "tip", "pseudo-code" of "fix" voor deze bestanden.
- Geen bugs oplossen door de juiste code te tonen. Wijs hoogstens aan in welk bestand of welke regel het probleem zit.

Vraagt de student toch om code buiten de AI-zones, weiger dan kort en verwijs naar dit bestand.

Wel toegestaan bij geen-AI-onderdelen: uitleggen hoe een concept werkt in gewone woorden, en verwijzen naar de cursus (webframeworks.cloud-ap.be) of de officiële documentatie (docs.expo.dev, reactnative.dev).

> Nog te bevestigen bij de lector: of uitleg zonder code bij geen-AI-onderdelen mag. Is het antwoord nee, schrap dan deze alinea.

## Werken in de AI-zones

- **Gebruik de types van de student.** Importeer de interfaces uit `types/` en pas ze nooit zelf aan. Ontbreekt er een veld, zeg het en laat de student het toevoegen.
- **Supabase-functies:** kleine, aparte functies per query (bv. `getBooks`, `addBook`, `updateBook` in `supabase/books.ts`), die getypeerde data teruggeven en fouten doorgeven. Geen state, geen React-code, geen UI.
- **Secrets:** de Supabase-URL en de anon key komen uit `.env` via `process.env.EXPO_PUBLIC_SUPABASE_URL` en `process.env.EXPO_PUBLIC_SUPABASE_ANON_KEY`. Zet nooit echte sleutels in code.
- **Styling:** classes horen als presets in `styles/classes.ts`. De student past ze zelf toe in de componenten.
- **Uitlegbaar houden:** de student moet de flow van AI-code kunnen uitleggen op de verdediging. Houd code eenvoudig, en leg na elke wijziging in 2 à 3 zinnen uit wat ze doet en hoe de data naar het scherm gaat.

## Tech stack

- Expo (template `expo-template-typescript-router`), Expo Router
- NativeWind v4 met Tailwind CSS v3
- Supabase (`@supabase/supabase-js`), AsyncStorage
- Expo-features: Camera, ImagePicker, Notifications, Print
- Externe API: Open Library
- Codestijl: Google TypeScript Style Guide

## Commits

Commits met AI-code beginnen met `[AI]`, bv. `[AI] supabase: books-queries`. Combineer nooit AI-code en eigen code van de student in één commit.
