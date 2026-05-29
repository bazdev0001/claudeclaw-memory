# FRICTION LOG — Mistakes That Must Not Repeat

Format: date | agent | what went wrong | root cause | fix applied | prevention rule

---

## 2026-05-29

### F-001 | Ada | Forgot Expo Go skip decision
- What: Ada asked "what needs testing?" when Barry already decided to skip local testing
- Root cause: Memory not checked at session start
- Fix: Set up Obsidian vault, added LEARNINGS.md
- Prevention: Check LEARNINGS.md AND FRICTION-LOG.md at every session start

### F-002 | Ada | Build 37 submission retried 3 times without diagnosing root cause
- What: Retried same failing submission without getting actual Apple error
- Root cause: EAS CLI doesn't surface Apple's specific rejection reason
- Fix: Need to check App Store Connect web UI for actual error
- Prevention: After 2 failed submissions, check ASC web UI before retrying

### F-003 | Ada | Used emoji tick/cross in responses
- What: Barry said "all agents, please do not use pic/icon with cross and tick, its confusing"
- Root cause: Default behavior
- Fix: Hard rule added to CLAUDE.md
- Prevention: Use YES/NO/PASS/FAIL/CRITICAL in text. No emoji status indicators.

### F-004 | Ada | Repeated status format wrong before SYSTEM-STATUS-REPORT-FORMAT.md
- What: Used trading hourly format for system status
- Root cause: No format documented at time
- Fix: Created SYSTEM-STATUS-REPORT-FORMAT.md
- Prevention: Always use 3-section format (Projects / Departments / COO) for system status

### F-005 | Ada | Narrated plans instead of executing
- What: Said "I'll now proceed to..." instead of just doing it
- Root cause: Default AI behavior
- Fix: "Don't narrate what you're about to do. Just do it." in CLAUDE.md
- Prevention: Execute immediately. Explain only if asked.

### F-006 | Ada | Athena → Ada rename — didn't commit before starting new work
- What: Phase 1-2 complete but not committed until prompted
- Root cause: No checkpoint cadence
- Fix: Commit after every phase
- Prevention: Commit after each discrete phase of work

---

**Rule:** All agents must add to this log when they make a mistake. This is a shared cross-agent log.

### F-007 | Ada | Reported "done" without verifying implementation worked
- What: Queued hard-wake tasks, said done. "spawn_refused: main is always_on" error was in hive mind. Barry had to find it.
- Root cause: Treated "task queued" as "task done." Never checked hive mind after implementation.
- Fix: Removed main from hard-wake cron
- Prevention: After any implementation, wait 60s and check hive mind for errors. Only say "done" after confirming success. Never make Barry chase down my mistakes.
