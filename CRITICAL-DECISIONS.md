# Critical Decisions — Must Not Forget

## Obsidian Vault Setup (2026-05-28)
- Barry: "you frequently forget what i told you"
- Decision: Set up Obsidian vault to persist memory across sessions
- Vault: /home/apex/.obsidian/claudeclaw
- OBSIDIAN_VAULT_PATH added to .env
- Files are git-tracked for reproducibility

## MakeMeRich TestFlight (2026-05-28)
- Decision: Skip local testing (Expo Go broken - port 8081 conflict)
- Go straight to TestFlight for testing
- Build 24 is currently in TestFlight (stable)
- Build 37 failed TestFlight submission (SDK 55 changes may have broken it)

## Architecture Refactor (2026-05-28)
- Phase 1-2 Complete: Athena → Ada rename, 9-agent directory structure created
- Phase 3-6 Pending: Fill in documentation, hard/soft wake-up scripts
- Commit: 80e7f02

## No Local Testing Decision
- Cannot test locally due to Expo Go port/interactive mode issues
- Decided to skip local testing and submit directly to TestFlight
- This is why Build 37 failed — untested code submitted

---
Last updated: 2026-05-28 21:53 UTC
