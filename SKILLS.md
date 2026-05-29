# SKILLS — Available Skills Catalog

Last updated: 2026-05-29
Two locations: project skills at ~/claudeclaw/skills/ and global skills at ~/.claude/skills/

---

## PROJECT SKILLS
Location: /home/apex/claudeclaw/skills/

### gmail
- Path: /home/apex/claudeclaw/skills/gmail/SKILL.md
- What: Read, draft, and send email via Gmail API
- Triggers: "check my email", "reply to X", "send email to X", "any unread from X"
- Setup: Stub. Wire to ~/.claude/skills/gmail/ or configure Google OAuth
- Status: Stub (not fully wired)

### google-calendar
- Path: /home/apex/claudeclaw/skills/google-calendar/SKILL.md
- What: Read and modify Google Calendar events, create Meet links
- Triggers: "what's on my calendar today", "schedule a meeting with X at time", "send me a Meet link"
- Setup: Same OAuth as gmail. Both share credentials.
- Status: Stub (not fully wired)

### slack
- Path: /home/apex/claudeclaw/skills/slack/SKILL.md
- What: Read channels and DMs, send messages, search history
- Triggers: "any unread on slack", "post in #channel", "what did X say in slack"
- Setup: Set SLACK_BOT_TOKEN (xoxb-...) in .env. Uses src/slack.ts + @slack/web-api
- Status: Token required

### timezone
- Path: /home/apex/claudeclaw/skills/timezone/SKILL.md
- What: Multi-timezone helper. "What time is it in X" and overlap calculator.
- Triggers: "what time is it in city", "when is 3pm PT in CET", "find overlap between people in different timezones"
- How: Pure Node, no external API. Uses Intl.DateTimeFormat + city-to-IANA TZ table.
- Command: No special command -- Ada handles inline

### pikastream-video-meeting
- Path: /home/apex/claudeclaw/skills/pikastream-video-meeting/SKILL.md
- What: Join Google Meet or Zoom calls with video avatar (Pika) or voice-only bot (Recall.ai). Pre-flight brief from Calendar + Gmail + Memory 75s before meeting.
- Triggers: "join my next meeting", "send my avatar to the call", "summarize the meeting at URL"
- Command: node dist/meet-cli.js MEETING_URL --provider pika --chat-id CHAT_ID
- Setup: PIKA_API_KEY or RECALL_API_KEY in .env

### restart-conversation
- Path: /home/apex/claudeclaw/skills/restart-conversation/SKILL.md
- What: Loads system context to bring a new session up to speed without fresh-session amnesia
- Triggers: "restart conversation", "load context", "what do you know about the system"
- What it reads: docs/RESTART-CONTEXT.md, docs/CONVERSATION-KNOWLEDGE-BASE.md, CLAUDE.md, memory/ dir
- Command: Invoke via Skill tool as "restart-conversation"

### memory-check (script)
- Path: /home/apex/claudeclaw/skills/memory-check.sh
- What: Prints LEARNINGS.md, FRICTION-LOG.md, and BLOCKERS.md for agent to read at session start
- Command: bash ~/claudeclaw/skills/memory-check.sh AGENT_ID
- When: Run at every session start

### session-end-maintenance (script)
- Path: /home/apex/claudeclaw/skills/session-end-maintenance.sh
- What: Appends to LEARNINGS.md, commits Obsidian vault, commits claudeclaw repo
- Command: bash ~/claudeclaw/skills/session-end-maintenance.sh AGENT_ID "one-line lesson"
- When: Run at end of every significant session

---

## GLOBAL SKILLS
Location: /home/apex/.claude/skills/

### status-report
- Path: /home/apex/.claude/skills/status-report.sh
- What: Consolidates status from all 7 departments. Scans agent output dirs, finds recent status/report files, extracts achievements/issues/blockers, outputs unified report.
- Output: Saves to /tmp/status-report-YYYY-MM-DD.md and stdout
- Command: bash /home/apex/.claude/skills/status-report.sh
- Format: 3 sections -- Department Updates, Projects table, COO Updates

### coo-status-report
- Path: /home/apex/.claude/skills/coo-status-report.js
- What: Node version of status consolidator. Parses markdown output files from yoga, software, social, marketing, content, trading, operations. Returns structured report with achievements, issues, blockers.
- Command: node /home/apex/.claude/skills/coo-status-report.js

### trade-status-report
- Path: /home/apex/.claude/skills/trade-status-report.js
- What: Pulls latest trading status from @trading output. Formats portfolio position, P&L, allocation, next targets.
- Command: node /home/apex/.claude/skills/trade-status-report.js

### telegram-recovery
- Path: /home/apex/.claude/skills/telegram-recovery.sh
- What: Auto-attempts recovery on Telegram bot failures. Checks .env, validates token, tests API, restarts bot, verifies startup, checks logs.
- Command: bash /home/apex/.claude/skills/telegram-recovery.sh
- When: Use when Telegram bot is unresponsive or throwing errors

### telegram-health-check
- Path: /home/apex/.claude/skills/telegram-health-check.js
- What: Monitors Telegram bot connection and token validity. Auto-alerts and attempts recovery on failure.
- Command: node /home/apex/.claude/skills/telegram-health-check.js
- When: Runs every 5 minutes via ops audit (or call manually)

### barry-file-intake
- Path: /home/apex/.claude/skills/barry-file-intake.sh
- What: Stores and git-commits files sent by Barry to categorized storage at ~/claudeclaw/agents/coo/barry-files/
- Command: bash ~/claudeclaw/skills/barry-file-intake.sh FILE_PATH CATEGORY "description"
- Categories: notebooks, videos, documents, instructions, resources

### check-barry-files
- Path: /home/apex/.claude/skills/check-barry-files.sh
- What: Lists all files in Barry's file storage, optionally by category
- Command: bash /home/apex/.claude/skills/check-barry-files.sh [category] [search_term]

### build-report-template
- Path: /home/apex/.claude/skills/build-report-template.sh
- What: Outputs the standard build submission report format. Use this for all build reports to maintain consistency.
- Command: bash /home/apex/.claude/skills/build-report-template.sh
- Format: Build Details table, Key Fixes list, Next Steps, Monitoring Notes

---

## SCRIPTS (not skills but frequently used)

### gh-issue.sh
- Path: /home/apex/claudeclaw/scripts/gh-issue.sh
- What: Creates GitHub issue in bazdev0001/claudeclaw
- Command: bash ~/claudeclaw/scripts/gh-issue.sh "title" "body" "label1,label2" "agent_id"
- Labels: bug, task, self-improvement, research, blocker, trading, operations, software, yoga, social, content, marketing

### notify.sh
- Path: /home/apex/claudeclaw/scripts/notify.sh
- What: Sends a progress message to Barry's Telegram chat from inside an agent run
- Command: bash /home/apex/claudeclaw/scripts/notify.sh "message text"
- When: Use for heavy multi-step tasks only. Do not spam. Use judgment.
- Requires: TELEGRAM_BOT_TOKEN and ALLOWED_CHAT_ID in .env

### session-end-maintenance.sh (also in project skills)
- Path: /home/apex/claudeclaw/scripts/session-end-maintenance.sh
- Same as project skills version above

---

## MCP SERVERS (available via tool calls)

These are wired as deferred tools in the Claude Code harness. Load via ToolSearch before calling.

- Gmail: mcp__claude_ai_Gmail__ prefix (search_threads, get_thread, create_draft, label_message, etc.)
- Google Calendar: mcp__claude_ai_Google_Calendar__ prefix (list_events, create_event, update_event, etc.)
- Google Drive: mcp__claude_ai_Google_Drive__ prefix (read_file_content, search_files, create_file, etc.)
- Telegram: mcp__plugin_telegram_telegram__ prefix (reply, react, edit_message, download_attachment)

---

## SKILL CREATION RULE

If you do the same task twice, make it a skill.
Save to ~/claudeclaw/skills/ (project-scoped) or ~/.claude/skills/ (global).
Document it in this file before the session ends.
