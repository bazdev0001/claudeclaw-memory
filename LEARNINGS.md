# LEARNINGS — Running Session Log

Format: date | agent | lesson | action taken

---

## 2026-05-29

- Ada | Barry said "you frequently forget what I told you" | Set up Obsidian vault for persistent memory. Must check INDEX.md at every session start.
- Ada | Expo Go broken (port 8081) — decision was to skip local testing and go to TestFlight directly | Do not attempt local testing for makemerich. Go to TestFlight.
- Ada | Voice messages arrive prefixed with [Voice transcribed]: — treat as normal commands | Already documented in CLAUDE.md but must be treated as priority commands.
- Ada | Build 37 EAS TestFlight submission failed 3 times | Root cause: Apple-side rejection, exact reason unknown. Build 24 is stable in TestFlight.
- Ada | /insight and /goal commands do NOT exist in Claude Code | Do not reference these. Real available commands: /loop, /schedule, skills.
- Ada | All times must be shown in Pacific (UTC-7) | UTC-7 for all user-facing timestamps.
- Ada | Barry confirmed: no emoji/icons like tick/cross — use text (YES/NO/PASS/FAIL) | Hard rule, applies to ALL agents.
- Ada | "No em dashes. Ever." | Hard rule in CLAUDE.md.
- Ada | Hard requirement: all tasks must be GitHub issues (BUG-XXX/FEAT-XXX) | Every piece of work tracked in GitHub.

---

## Template for future entries:

- [Agent] | [What happened / what Barry said] | [What to do differently]

---

**Rule:** Every agent reads this at session start. Every agent adds entries when lessons are learned.
