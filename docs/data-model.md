# Data Model

The database is hosted on Supabase (Postgres). All tables include a `tenant_id` to support multi-tenancy.

## Tables

### tenants
- `id` (uuid, pk)
- `name`

### users
- Managed by Supabase Auth.
- Profile table extension:
  - `id` (uuid, references auth.users)
  - `tenant_id`
  - `role` (admin, timekeeper, statistician, viewer)

### tournaments
- `id` (uuid, pk)
- `tenant_id`
- `name`
- `format` (league | group | knockout)
- `start_date`
- `end_date`

### teams
- `id` (uuid, pk)
- `tenant_id`
- `tournament_id`
- `name`

### players
- `id` (uuid, pk)
- `team_id`
- `full_name`
- `number`

### matches
- `id` (uuid, pk)
- `tenant_id`
- `tournament_id` (nullable for standalone match)
- `home_team_id`
- `away_team_id`
- `format` (football | futsal)
- `status` (scheduled | live | finished)
- `kickoff_at`

### lineups
- `match_id`
- `player_id`
- `is_starting` (boolean)

### events
- `id` (uuid, pk)
- `match_id`
- `minute`
- `type` (goal | foul | shot_on | shot_off | corner | yellow | red | etc.)
- `player_id` (nullable)
- `team_id`

### stats
- `match_id`
- `team_id`
- `possession` (numeric)
- `shots_on` (int)
- `shots_off` (int)
- `corners` (int)
- `fouls` (int)
- `yellow_cards` (int)
- `red_cards` (int)
- `goals` (int)

Indexes and foreign keys enforce tenant isolation and referential integrity.
