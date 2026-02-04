# AGENTS.md — daily-mews

## Core behavior requirements

### Daily meme must change every day
- The site should **not** reuse the same featured meme on consecutive days.
- Current implementation pulls the **#1 entry** from `r/Catmemes/top/.rss?t=day`, which can remain the same across multiple days.
- When selecting a meme, choose from a pool (e.g., top 10–25 RSS entries) and pick deterministically per LA-local date (or track the last-used permalink in `site/data.json` and avoid repeats).

### Update cadence / idempotency
- The build script should publish **at most once per America/Los_Angeles local day**, but it must still ensure the chosen meme differs from yesterday’s.
