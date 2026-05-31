# Current Blockers — 2026-05-31 03:55 UTC

## CRITICAL

**NEW: Bot Token Lifecycle Management — Weekly Routing Conflicts**
- Multiple active tokens for hours causing message routing to wrong channels
- Manual intervention required each time (disable integrations, rebuild dist/)
- Root cause: No automated token management, old tokens not revoked on upgrade
- Prevention needed: Automated monitoring (hourly), pre-deploy verification, token rotation playbook
- Assign to: @operations
- Task: INFRA-001 (create as GitHub issue)

## CRITICAL (Existing)
1. **MakeMeRich EAS Build Broken — Cannot Rebuild Build 24**
   - Error: `Failed to resolve plugin for module` (react-native-iap, expo-font)
   - Cause: app.json has plugin configs but EAS build system can't resolve them
   - Impact: Cannot submit updated builds to TestFlight
   - Current state: Build 24 is in TestFlight, stable
   - Attempted fixes:
     * Reverted to Build 24 commit (6f49c1b)
     * Cleaned node_modules multiple times
     * Cleared npm cache
     * Tried building with --legacy-peer-deps
   - All attempts fail with same plugin resolution error
   - Need to either: fix plugin config OR use existing Build 24 in TestFlight

2. **Build 37 Failed TestFlight Submission (Twice)**
   - Reason: Code changes after Build 25 broke the app
   - Reverted to Build 24 to fix
   - But can't rebuild Build 24 due to above blocker

## HIGH
3. **Expo Go Port Conflict**
   - Cannot run local testing
   - Task #3 pending (fix port 8081 + interactive mode)

4. **Discord Communication Stalled**
   - Initialized but zero agent messages

## MEDIUM  
5. **26 Uncommitted Changes Across Projects**
   - Git state dirty

---
Last updated: 2026-05-29 00:15 UTC
