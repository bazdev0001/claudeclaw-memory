# Current Blockers

## Critical
1. **MakeMeRich Build 37 TestFlight Submission Failed**
   - Cause: Unknown (Apple rejected during processing)
   - Blocker: Cannot submit untested code due to Expo Go issues
   - Barry input needed: Retry Build 37 or revert to Build 24?

2. **MakeMeRich Navigation Bug**
   - MainTabNavigator not registered in App.tsx
   - Must be fixed before App Store submission
   - @software identified this as biggest technical debt

## High
3. **Expo Go Port Conflict**
   - Cannot run local testing due to port 8081 conflict + non-interactive mode
   - Blocks verification of SDK 55 changes
   - Task #3 created but not yet started

4. **Discord Communication Stalled**
   - Discord sender initialized but zero agent messages since setup
   - Agents spawning/failing (e.g., makemerich task-5ac spawn_failed)
   - Impact: Cannot see agent activity in Discord

## Medium
5. **26 Uncommitted Changes Across Projects**
   - Git state dirty, reproducibility broken
   - Recommend: Commit or revert everything to establish clean baseline

6. **Agent Documentation Incomplete**
   - Directories created but all 13 docs per agent are empty templates
   - Phase 3-6 of architecture refactor pending

---
Last updated: 2026-05-28 21:53 UTC
