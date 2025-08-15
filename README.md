# Bus Code — Starter turned into Mini Bus App (Ionic + Angular)

This repo started as the default **Ionic Angular** template. The included add‑on converts it into a tiny **bus routes / live positions / tickets** demo with mock data — good for prototyping and teaching.

## What was added
- **Routes** page: list all bus routes, search by name/code
- **Route Detail** page: view stops for a route
- **Live** page: mock live bus positions (auto-refresh every 3s)
- **Tickets** page: simple booking form (no backend)

All features use **mock data**; you can later connect real APIs or a database.

## Quick Start

```bash
npm install
ionic serve
```

### Add the new pages to routing
Edit `src/app/app-routing.module.ts` and add these routes:

```ts
{ path: 'routes', loadChildren: () => import('./pages/routes/routes.module').then(m => m.RoutesPageModule) },
{ path: 'route/:id', loadChildren: () => import('./pages/route-detail/route-detail.module').then(m => m.RouteDetailPageModule) },
{ path: 'live', loadChildren: () => import('./pages/live/live.module').then(m => m.LivePageModule) },
{ path: 'tickets', loadChildren: () => import('./pages/tickets/tickets.module').then(m => m.TicketsPageModule) },
```

> If your file already contains a `routes` array, just paste these into it.

### Add navigation links (optional)
In `src/app/app.component.html`, add links in the menu:

```html
<ion-item routerLink="/routes">Routes</ion-item>
<ion-item routerLink="/live">Live</ion-item>
<ion-item routerLink="/tickets">Tickets</ion-item>
```

## Project Structure (new bits)
```
src/app/
  models/
    bus.models.ts
  services/
    bus.service.ts
  pages/
    routes/
      routes.page.{ts,html,scss}
      routes.module.ts
    route-detail/
      route-detail.page.{ts,html,scss}
      route-detail.module.ts
    live/
      live.page.{ts,html,scss}
      live.module.ts
    tickets/
      tickets.page.{ts,html,scss}
      tickets.module.ts
```

## Tech
- Ionic + Angular
- Capacitor (for native builds)
- TypeScript, SCSS

## Notes
- Live positions are randomized mock data; replace `BusService.getLivePositions()` with real GPS/map data later.
- To deploy natively:
  ```bash
  ionic build
  npx cap add android   # or ios
  npx cap copy
  npx cap open android  # or ios
  ```


