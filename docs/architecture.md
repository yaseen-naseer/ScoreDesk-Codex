# System Architecture

The ScoreDesk application is a web-based platform built with a modular, component-driven architecture.

## Overview
- **Client**: React/Next.js frontend using shadcn/ui for theming and reusable components. Communicates with Supabase via its JavaScript SDK.
- **Backend**: Supabase provides authentication, Postgres database, edge functions and real-time channels.
- **Real-time Layer**: Match data (clock, score, statistics) is synced across clients using Supabase's real-time channels so multiple operators and the public scoreboard stay in sync.

## Modules
1. **Tenant Management**
   - Isolates data per sports organization.
   - Tenants own tournaments, teams, players and matches.
2. **Tournament Module**
   - Supports league, group stage and knockout structures.
   - Generates fixtures and standings.
3. **Team & Player Module**
   - CRUD operations for teams and player rosters.
   - Assign starting lineup and substitutes.
4. **Match Control Module**
   - Handles game clock, format (football or futsal) and stoppages.
   - Produces synchronized scoreboard output for arenas/stadiums.
5. **Statistics Module**
   - Records live metrics and aggregates match summaries.
6. **User Roles & Collaboration**
   - Role-based permissions (timekeeper, statistician, admin, viewer).
   - Concurrent editing supported via real-time updates.

## API Layer
- Supabase edge functions expose server-side logic for complex operations (e.g. generating tournaments or computing standings).
- All database interactions go through Supabase security policies enforcing tenant isolation and role-based access.

## Deployment
- Frontend deployed as static/SSR app (e.g. Vercel).
- Supabase project hosts database, authentication and edge functions.

## Dependencies
- Package management via **npm**.
- UI and theming through **shadcn/ui**.
