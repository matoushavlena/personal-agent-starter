# PRUNE.md — Weekly Maintenance

<!--
Read by the weekly prune cron (a fresh, isolated session). The steps live here so the
schedule's task can just say "read PRUNE.md and run it" - edit the procedure here, not
the schedule. It runs weekly, so it can be fuller than HEARTBEAT.md.
-->

Work through this each week:

1. **Distill the daily logs.** Read the recent `memory/YYYY-MM-DD.md` logs and route anything durable to its home (see CLAUDE.md, "Where things live"): commitments to `TODOS.md`, multi-step work and decisions to `projects/`, lasting facts to `MEMORY.md`.
2. **Drop old logs.** Delete `memory/` daily logs older than ~2 weeks; their signal now lives in its home.
3. **Trim memory.** Bring `MEMORY.md` back under its ~2200-char guardrail (and `USER.md` under ~1375): tighten, merge, drop what's stale.
4. **Clear done items.** Remove `TODOS.md` "Recently done" entries older than ~2 weeks.

Quiet job: only message the principal if something surprising turns up.
