# Smart Neighbourhood Intelligence System (SNIS)

SNIS is an academic web application for exploring and comparing London neighbourhoods. It brings together an interactive map, venue and socio-economic profiles, K-Means clustering, crime-based safety scores, and a community survey in one place.

> **Data note:** The current app uses a bundled example dataset for 12 London boroughs and 62 venues. Its venue, population, income, and crime values are sample project data, not a live feed or official, current safety guidance. Treat the rankings as a demonstration of the analysis workflow, not as a basis for real-world relocation or safety decisions. Map tiles are served by OpenStreetMap and require an internet connection.

## Features

- **Neighbourhood analysis:** Build feature vectors from venue-category proportions, safety index, median income, and population; standardize them; then explore configurable K-Means clusters and an elbow curve.
- **Interactive map:** View borough and venue markers on a Leaflet map, color boroughs by cluster or safety score, toggle venue markers, and inspect neighbourhood details.
- **Safety ranking:** Compare boroughs using the sample monthly theft, assault, burglary, and vandalism records.
- **Community survey:** Rate safety, amenities, transport, and overall experience, say whether you would live in an area, and leave an optional comment. Survey storage can use Supabase; sample ratings are shown when no survey records are available.
- **Responsive interface:** Browse the home, analysis, safety, map, and survey pages on desktop or mobile.

## Technology

- React , TypeScript, and Vite
- Tailwind CSS and Lucide icons
- Leaflet with OpenStreetMap tiles
- Supabase JavaScript client for optional survey storage

## Getting started

### Requirements

- Node.js and npm
- Internet access for OpenStreetMap map tiles
- A Supabase project only if you want survey responses stored remotely

### Install and run

```bash
npm install
npm run dev
```

Vite prints the local development URL after startup.

### Optional Supabase setup

1. Create a Supabase project.
2. Apply the SQL migration in `supabase/migrations/` to create the `survey_responses` table and its policies.
3. Create a `.env` file in the project root with your project URL and public anon key:

   ```dotenv
   VITE_SUPABASE_URL=https://your-project.supabase.co
   VITE_SUPABASE_ANON_KEY=your-public-anon-key
   ```

Without these variables, the app uses placeholder Supabase settings and survey interactions remain available in the current page session. Never put a service-role key or other private credentials in a `VITE_` variable; Vite exposes these values to the browser.

## Useful scripts

```bash
npm run dev        # Start the development server
npm run build      # Create a production build
npm run preview    # Preview the production build
npm run lint       # Run ESLint
npm run typecheck  # Check application TypeScript types
```

## Project structure

```text
src/
  components/   Shared navigation and footer
  data/         Bundled neighbourhood, venue, and crime example data
  lib/          K-Means, feature preparation, and safety score calculations
  pages/        Home, analysis, safety, map, and survey views
supabase/
  migrations/   Survey response table and access policies
```

## License

No license has been added yet. All rights remain with the project authors unless a license is added.
