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

### F-008 | Ada | Attempted software task instead of delegating to @software
- What: Barry asked to submit makemerich to TestFlight. Ada spent 30+ min trying to run EAS CLI instead of delegating to @software immediately.
- Root cause: Ada acted as engineer instead of COO. COO coordinates; does not execute software tasks.
- Fix: Queued to @software. Added delegation rules to CLAUDE.md.
- Prevention: Any app build, EAS, TestFlight, code change = immediate delegate to @software or @makemerich. No exceptions.

### F-009 | Ada | Confirmed Build 37 in TestFlight without verifying — Barry found it was still Build 24
- What: Reported Build 37 was in TestFlight based on @software's claim. Barry checked and saw Build 24 only.
- Root cause: Trusted agent output without independent verification. Same pattern as F-007.
- Fix: Queued @makemerich to actually fix and submit.
- Prevention: For TestFlight status, the only reliable check is: (1) App Store Connect web UI, or (2) Barry checking TestFlight on device. Never trust EAS CLI output or agent reports as confirmation.

### F-010 | Ada | Recurring pattern: misinterprets instructions, produces post-mortem instead of preventing
- What: Barry asked to run agents for 2.5 hours. Ada set up HOURLY RECURRING cron. Barry never asked for recurring. Ada then wrote post-mortem explaining the error. This pattern repeats across sessions.
- Root cause: Ada acts on assumed intent, does not clarify scope/duration/recurring vs one-time. Does not state side effects before committing.
- Fix: GitHub issue #60 — SI-002 self-improvement task
- Prevention rule (effective immediately):
  1. Before any automation with side effects: state what it does, how long, how to stop
  2. Ambiguous duration/scope = ask ONE question before acting
  3. Never set up recurring automation without explicit "this will keep running" warning
  4. Distinguish one-time vs recurring in every response

### F-011 | Ada | Plain text responses bypass Telegram when MCP tool disconnects
- What: Telegram MCP tool disconnects frequently. When Barry sends a message and the tool is reconnecting, Ada responds with plain text in the Claude Code session. Barry sees these as "thoughts in the app" not Telegram messages.
- Root cause: Responded immediately instead of waiting for Telegram tool to reconnect.
- Fix: Always use ToolSearch to wait for mcp__plugin_telegram_telegram__reply before responding.
- Prevention: If Telegram tool is not available, call ToolSearch first. Never output plain text as a substitute for a Telegram reply.
