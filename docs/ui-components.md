# UI Components & Theming

The interface is built with React/Next.js and shadcn/ui. Components should be reusable and configurable; no hardcoded values.

## Theming
- Provide global **light** and **dark** themes.
- Themes controlled via shadcn/ui with ability for tenants to customize accent colors.

## Core Components
- **ScoreboardDisplay**: Full-screen view for arena/stadium screens showing clock, score, period, and possession. Receives real-time updates.
- **MatchControlPanel**: Used by officials to start/pause time, record goals, cards, and substitutions.
- **StatsPanel**: Interface for statisticians to update metrics such as shots, fouls, and possession.
- **TournamentManager**: CRUD screens for tournaments, teams and fixtures.
- **PlayerRoster**: Manage team rosters and assign starters/substitutes.

All components must:
- Be written as standalone React components.
- Accept data and callbacks via props (no internal hardcoding).
- Include basic accessibility attributes.
