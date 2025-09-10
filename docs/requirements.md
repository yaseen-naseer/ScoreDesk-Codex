# Functional Requirements

## Game Modes
- Support both **football** and **futsal** formats.
- Game rules, pitch dimensions and timers adapt to the selected format.

## Match Management
- Operate in **standalone** mode for a single match or as part of a **tournament**.
- Tournament formats: **league**, **group stage**, and **knockout** brackets.

## Team & Player Management
- Create teams and register players for each team.
- Mark players as **starters** or **substitutes** before or during a match.

## Scoreboard & Timing
- Provide a stadium/arena scoreboard view that mirrors the referee's official time.
- Pause/Resume controls support frequent stoppages (e.g. futsal fouls or timeouts).

## Live Statistics
Track the following metrics per match:
- Ball possession percentages.
- Goals.
- Fouls.
- Shots **on** and **off** target.
- Corner kicks.
- Yellow and red cards.

## Match Summary
- Generate a shareable match summary containing all recorded statistics for broadcasters (e.g. YouTube or other platforms).

## Theming
- Support **dark** and **light** themes using [shadcn/ui](https://ui.shadcn.com/).

## Multi-user Operation
- Multiple operators can interact with the same match simultaneously:
  - Timekeeper controls the game clock.
  - Statistician updates live metrics.

## Multi-tenancy
- System serves multiple sports organizations. Each tenant manages its own tournaments, teams and matches.

## Persistence & Authentication
- All data and authentication handled through **Supabase**.
- Every statistic must be stored in the database.

## Development Guidelines
- Build reusable components; avoid hardcoded values.
- Use **npm** as the package manager.
