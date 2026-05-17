# SuggestHub

A modern Angular application to capture, browse and manage suggestions, with full CRUD operations, likes, favorites and a JSON-server backend.

Built with **Angular 18.2.21** and a clean indigo/violet design system using Inter + Plus Jakarta Sans typography.

## Features

- **List suggestions** — grid view with category and status pills, real-time search by title or category.
- **Add / Edit suggestion** — reactive form with validations (title pattern, min lengths, required category) and edit mode via route parameter.
- **View details** — dedicated details page with banner, info tiles and status badge.
- **Delete suggestion** — with confirmation prompt.
- **Like suggestion** — increments like counter and persists via API.
- **Favorites** — local favorites section displayed when at least one item is bookmarked.
- **User sign-up form** — reactive form with name, email and password validation.
- **Lazy-loaded suggestion module** — `/suggestions` route is code-split.
- **404 page** — animated not-found page for unknown routes.

## Tech stack

| Layer | Tech |
|------|------|
| Framework | Angular 18.2.21 |
| Forms | Angular Reactive Forms |
| HTTP | `HttpClient` (`SuggestionService`) |
| Routing | `RouterModule` with lazy modules |
| Backend (dev) | `json-server` reading `db.json` |
| Styling | Plain CSS with CSS custom properties, Google Fonts (Inter, Plus Jakarta Sans) |

## Project structure

```
src/
├── app/
│   ├── app.component.*           # Shell (header + router-outlet + footer)
│   ├── app-routing.module.ts     # Top-level routes
│   ├── app.module.ts
│   ├── header/                   # Sticky glassmorphic navbar
│   ├── footer/                   # Brand footer with dynamic year
│   ├── home/                     # Landing page with hero + feature cards
│   ├── services/
│   │   └── suggestion.service.ts # CRUD against json-server
│   ├── suggestions/
│   │   ├── suggestion.ts         # Suggestion interface
│   │   ├── suggestion-list/      # Grid + search + actions + favorites
│   │   ├── suggestion-form/      # Create / edit form
│   │   ├── suggestion-details/   # Details view
│   │   ├── sug-nf/               # 404 page
│   │   └── suggestion-m/         # Lazy-loaded feature module + routing
│   └── users/
│       └── user-form/            # Sign-up form
├── index.html
├── main.ts
└── styles.css                    # Global theme, fonts, CSS variables
```

## Prerequisites

- **Node.js** 18+ (tested with Node 22.22.3)
- **npm** 10+
- **Angular CLI** 18.2.21 (already pinned in `devDependencies`)

## Getting started

### 1. Install dependencies

```bash
npm install
```

### 2. Start the JSON backend (optional, for full CRUD)

The app reads/writes suggestions from a `json-server` instance. From the project root:

```bash
npx json-server --watch db.json --port 3000
```

The Angular service points to `http://localhost:3000` by default.

### 3. Start the Angular dev server

```bash
npm start
# or
ng serve
```

Open [http://localhost:4200/](http://localhost:4200/). The app auto-reloads on file changes.

## Available scripts

| Script | What it does |
|------|------|
| `npm start` | Run dev server on port 4200 |
| `npm run build` | Production build into `dist/3sleam1-m` |
| `npm run watch` | Build in watch mode (dev configuration) |
| `npm test` | Run unit tests via Karma + Jasmine |

## Routes

| Path | Component |
|------|------|
| `/home` | `HomeComponent` |
| `/suggestions` | `SuggestionListComponent` (lazy module) |
| `/suggestions/details/:id` | `SuggestionDetailsComponent` (lazy module) |
| `/suggestionForm` | `SuggestionFormComponent` (create) |
| `/suggestionForm/edit/:id` | `SuggestionFormComponent` (edit) |
| `/userForm` | `UserFormComponent` |
| `**` | `SugNFComponent` (404) |

## Design system

CSS custom properties defined in `src/styles.css` :

- **Primary**: `#6366f1` (indigo)
- **Accent**: `#8b5cf6` (violet) and `#ec4899` (pink)
- **Surface / Background**: soft white on a multi-radial gradient
- **Typography**: Inter (body) + Plus Jakarta Sans (headings)
- **Radii**: `8px`, `14px`, `20px`
- **Shadows**: layered indigo-tinted soft shadows

All components share the same gradient brand bar (`primary → accent → pink`) used on cards, buttons and accents.

## Build

```bash
npm run build
```

Build artifacts are produced in `dist/3sleam1-m/`.

## Further help

Run `ng help` or visit [angular.dev/tools/cli](https://angular.dev/tools/cli).
