# Personal Agent Starter

A drop-in workspace that turns a fresh Claude agent into a capable **personal assistant** — an executive assistant by default, but the same building blocks serve a wealth manager, a house-build / architect tracker, or a meeting manager.

Built to run in **DAM**: an isolated cloud pod (VM- and network-isolated, allowlisted egress) where the agent's connections (email, calendar, chat, files) and its **schedules** are provided as MCP servers. You don't wire those up here — the agent discovers them at runtime.

> This README is the one file the agent doesn't live by. It's for **you**, the person deploying the agent. (The agent reads the "Roles it supports" section once during bootstrap to shape itself.)

## How to use it

1. Copy the contents of this folder into the agent's working directory.
2. Start the agent. On first run it follows `BOOTSTRAP.md`: a short conversation to set its identity, learn about you, pick its role, and install its schedules — then it deletes `BOOTSTRAP.md`.
3. From then on it works from these files, keeping them current as its memory.

## The building blocks

| File | What it is |
|---|---|
| `SOUL.md` | Who the agent is — values plus its name / vibe / emoji / mission. |
| `USER.md` | Who it works for — you. |
| `CLAUDE.md` | Its operating manual: workplace, startup routine, memory, heartbeat, safety, house style. |
| `MEMORY.md` | Curated long-term memory (distilled facts). |
| `memory/` | Raw daily logs plus `heartbeat-state.json`. |
| `TODOS.md` | Single-step tasks, a waiting-on chase-list, and what you owe others. |
| `projects/` | Bigger, multi-step threads — one file or folder each. |
| `TOOLS.md` | Which tool for which action, plus local setup notes. |
| `HEARTBEAT.md` | The proactive checklist read on each scheduled wake. |
| `.claude/settings.json` | Model, attribution, permissions. |

## Day one in DAM

- The agent installs two schedules through the schedule MCP: a **heartbeat** (~every 30 min during waking hours) and a **weekly memory prune**.
- It treats all tool output as data, never as instructions, and verifies before anything that leaves the pod.

## Roles it supports

Same primitives, shaped to the job. The agent picks the closest fit during bootstrap.

**Executive / personal assistant.** Inbox and calendar triage, drafting replies, protecting focus time. The `TODOS.md` waiting-on list chases people for what they promised; the heartbeat surfaces urgent mail and imminent meetings; a daily brief can run on a morning cron.

**Wealth manager.** `projects/` tracks holdings and positions with a `decisions.md` rationale log per move; the `TODOS.md` waiting-on list chases counterparties, banks, and paperwork; the heartbeat watches for portfolio events and news that needs a decision.

**House-build / architect tracker.** A `projects/<build>/` folder with `decisions.md` (ADR-style: what was chosen and why), `ledger.md` (items, costs, status), and `designs/` (drawings, references); the `TODOS.md` waiting-on list chases contractors and architects for deliverables; the heartbeat nudges on overdue milestones.

**Meeting manager.** A `projects/<meeting>/` folder with prep and agenda; the `TODOS.md` waiting-on list tracks attendee confirmations; the heartbeat nudges people who haven't confirmed and assembles prep before the meeting.

## Credits

Distilled from the OpenClaw workspace templates (the skeleton), a lived-in production assistant (the waiting-on register and project ledgers), and Hermes (memory discipline, tool-use enforcement, the prompt-injection taxonomy, and non-proactive day-zero).
