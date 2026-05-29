# CONTEXT — Brand and Business Reference

Last updated: 2026-05-29
Purpose: Shared context for all agents. Read at session start. Do not re-debate decisions marked as final.

---

## BARRY AU YEUNG

Barry is the CEO and owner of this entire system. Ada (main) is his COO.

Background (confirmed):
- Yoga teacher for 11+ years
- E-RYT 500 certified (Yoga Alliance's highest teaching credential)
- Entrepreneur running multiple parallel projects
- Engineer background (unconfirmed by Barry directly -- do not state unless confirmed)
- Built selfLove.Yoga in 2024
- Email: barry@selflove.yoga
- Personal brand: Barry Auyeung

Communication style:
- Wants execution, not explanations
- Makes decisions fast
- No emoji in responses
- All times in Pacific (UTC-7)
- Does not respond = has not seen it (resend)
- Work is not done until Barry says "pass" or "fail"

Approval protocol:
- Never assume approval
- For real-money trades: explicit "approved" or "execute" required
- For financial decisions over $1,000: ask before acting
- Ask for approval on one item at a time, wait, then next

---

## SELFLOVE.YOGA

Website: selflove.yoga
Platform: Wix LMS
Email list: practiceyogawithbarry

What it is:
Online yoga membership platform Barry built because the online yoga market had a structure problem. Content existed; curriculum and real teacher presence did not.

Target audience:
- Serious yoga practitioners (not casual fitness app users)
- People wanting structured progression, not just videos to browse
- Aspiring yoga teachers (YTT program)
- Anyone who tried group classes but wanted something deeper

Three tiers:
- Free: 30+ practice library, new class weekly, Barry's 7-day morning reset email, community forum
- Deep Practice Membership: $888/year -- full Season 2 curriculum (6 modules), monthly live sessions with Barry, philosophy masterclasses, private community
- Teacher Training: $2,888/year -- 200-hour YTT (Yoga Alliance certified), anatomy modules, 6 practicum assignments with Barry's feedback, bi-monthly 1:1 video calls, small cohort (max 20)

Current status:
- Revenue target: $30k/month growing to $200k/month
- Season 2: 6 modules, 64 videos each (in production)
- KPIs: teacher training enrolments, website conversion, email list growth, social reach, content shipped/week
- Barry's Instagram: @practiceyogawithbarry
- Weekly newsletter: every Monday

Brand voice for selfLove.Yoga:
- Warm but not soft
- Conviction-based (yoga changes things, not just fitness)
- Anti-fluff: no "wellness" jargon, no toxic positivity
- Barry teaches from direct experience, speaks to real practitioners
- Tone: the teacher who actually knows what they're talking about

Key brand message: "Yoga is not a fitness practice with philosophical window dressing. It's a system for living honestly in your body."

---

## MAKEMERICH

App name: Make Me Rich Now
App Store ID: 6762598615
GitHub: bazdev0001/Make-me-rich (private)
Bundle ID: com.makemerich.app

What it does:
AI-powered mobile app. User answers a 5-question profile. App generates a personalized wealth strategy with: income plan, named-mentor perspective, 90-day action plan, adaptive mindset coaching. Uses Claude API (claude-sonnet-4-6) as the AI engine.

Target user:
People who want a personalized wealth roadmap but cannot afford a real financial advisor or coach. Mobile-first, international (10 languages).

Tech stack:
- React Native + Expo SDK 55 + TypeScript
- Firebase Firestore (project: makemerich-bc564)
- Node.js + Express backend (port 3001)
- Anthropic Claude API
- EAS Build + TestFlight + App Store
- react-native-iap (StoreKit 2 for iOS IAP)

Current state (as of 2026-05-29):
- Build 24: last known-good TestFlight build
- Build 37: failed TestFlight submission (SDK 55 breaking changes)
- Critical bug: MainTabNavigator not registered in App.tsx (breaks revenue loop)
- iOS IAP: implemented (StoreKit 2, receipt validation server-side)
- Android billing: ready for implementation
- Expo Go broken locally: port 8081 conflict -- skip local testing, go straight to TestFlight

Pricing (credits system):
- Starter: 100 credits / $4.99
- Popular: 550 credits / $19.99
- Pro: 1,500 credits / $49.99
- Elite: 3,500 credits / $99.99
Revenue: 70% to apex (Apple takes 30%)
MRR target: $5k-$15k

IAP product IDs:
- com.makemerich.credits.starter
- com.makemerich.credits.popular
- com.makemerich.credits.pro
- com.makemerich.credits.elite

Key links:
- App Store Connect: https://appstoreconnect.apple.com/apps/6762598615
- TestFlight: https://appstoreconnect.apple.com/apps/6762598615/testflight/ios
- EAS Dashboard: https://expo.dev/accounts/bazdev0001/projects/makemerich
- Firebase: https://console.firebase.google.com/project/makemerich-bc564

Submission credentials:
- ASC API Key: W74H858V9H (use this -- Apple ID auth causes lockouts)
- Apple Team ID: 36M5AD7X5C
- EAS owner: bazdev0001 / slug: makemerich
- EAS project ID: a68d50cc-1504-4d84-a80a-ea5291370399

Build decision (FINAL -- do not re-debate):
- Skip local testing (Expo Go broken)
- Build via EAS, test in TestFlight

---

## APEX SYSTEM

What it is:
ClaudeClaw is apex's personal AI operating system. It runs as a persistent service on a VPS at 2.24.214.147. Barry accesses it primarily through Telegram and a web dashboard.

Purpose:
Remote-control of all business operations from Barry's phone or laptop. Every department runs as an on-demand AI agent. Ada (main) is always on as COO.

Architecture:
- Main (Ada): always-on COO, handles Telegram/Slack/email directly
- All other departments: spawned on demand when work appears in agent_tasks table
- Tasks queue via: node /home/apex/claudeclaw/dist/mission-cli.js queue AGENT_ID CHAT_ID "prompt"
- Scheduled tasks: node /home/apex/claudeclaw/dist/schedule-cli.js create "PROMPT" "CRON" CHAT_ID
- Results to: Discord channels by default

Key infrastructure:
- VPS: 2.24.214.147 (Ubuntu, bash/zsh)
- Obsidian vault: /home/apex/.obsidian/claudeclaw (git-tracked)
- Claudeclaw project: /home/apex/claudeclaw
- Projects: /home/apex/projects/ (makemerich, selflove-website, trading, aiassistance)
- Gemini API: for memory v2, video analysis (GOOGLE_API_KEY in .env)
- Memory v2: Gemini extracts facts after significant turns, stored with embeddings
- Hive mind: cross-agent activity log, visible to all agents

Web dashboard:
- https://apex.socialtokens.site (public URL, not localhost)
- Reports: /reports, Tasks: /tasks, Schedule: /schedule, Vault: /vault

War Room (voice):
- Browser-based voice interface at localhost:7860 (SSH tunnel required from laptop)
- Start: cd ~/claudeclaw/warroom && ./start_with_monitor.sh
- Not accessible from iPhone -- use Telegram voice messages instead
- Auto-stops after 30 min idle

---

## BRAND VOICE ACROSS ALL APEX PRODUCTS

Shared rules for all agents writing copy or communications:

Direct and specific:
- No vague "actionable insights" or "holistic approaches"
- Say what it does. Say who it's for. Name the outcome.

Plain language:
- Avoid jargon unless the audience is expert
- Short sentences over compound ones

Conviction over enthusiasm:
- Don't hype. State facts with confidence.
- Let the product speak. Don't oversell.

No AI cliches in copy:
- Not just agent behavior -- applies to content created for social, email, apps
- Real voice, not corporate wellness speak

---

## KEY DECISIONS MADE (do not re-debate)

These decisions are final. Bring new data to change them, not just opinions.

| Decision | Status | Date |
|----------|--------|------|
| MakeMeRich local testing skipped -- go straight to TestFlight | FINAL | 2026-05-28 |
| Build 37 abandoned -- rebuild from Build 24 state | FINAL | 2026-05-28 |
| All tasks must be GitHub issues (BUG-XXX/FEAT-XXX) | FINAL | 2026-05-23 |
| No em dashes in any agent output | FINAL | 2026-05-23 |
| No emoji tick/cross -- use YES/NO/PASS/FAIL in text | FINAL | 2026-05-29 |
| All times shown in Pacific (UTC-7) | FINAL | 2026-05-23 |
| Ada is COO -- does not execute software/engineering tasks | FINAL | 2026-05-29 |
| TestFlight status verified only via ASC web UI or Barry's device | FINAL | 2026-05-29 |
| selfLove.Yoga revenue target: $30k growing to $200k/month | FINAL | -- |
| MakeMeRich credits pricing: $4.99/$19.99/$49.99/$99.99 | FINAL | 2026-05-24 |
| ASC submission uses API Key W74H858V9H (not Apple ID auth) | FINAL | -- |

---

## WHAT NEEDS BARRY INPUT

[NEEDS BARRY INPUT] -- items where agent work is blocked pending a decision or fact from Barry.

| Item | Agent Waiting | Why Needed |
|------|--------------|------------|
| Barry's engineering background (exact field and timeline) | yoga | Bio accuracy for About page and YTT sales page |
| Q2 2026 financial model approval (yoga spend scenarios) | yoga | Whether to proceed with $3k-$8k marketing spend in June |
| Alpaca API key | trading | Enables live paper trading vs. manual entry |
| GITHUB_PAT for bazdev0001/Make-me-rich | makemerich | Required for git push to private repo |
| EAS_TOKEN | makemerich | Required for EAS build submissions |
| Firebase credentials for backend deploys | makemerich | Required for production backend pushes |
| selfLove.Yoga Season 2 filming schedule | yoga | Production planning and content calendar depend on it |
| Android release priority | software | Whether to build Android version of MakeMeRich this sprint |
