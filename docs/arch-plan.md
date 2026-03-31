# Architecture Plan: gstack

> Generated 2026-03-30 via /codebase-mapping

## 1. System Overview

**Purpose:** gstack turns Claude Code into a virtual engineering team — 31 slash-command
skills covering CEO strategy, eng review, design audit, QA testing, security audit,
headless browser automation, deploy pipelines, and retrospectives. Created by Garry Tan
(YC President/CEO) as an open-source software factory.

**Version:** 0.14.1.0 | **License:** MIT | **Runtime:** Bun 1.0+ | **Language:** TypeScript

**Tech Stack:**
- Bun (runtime + bundler + test runner)
- Playwright (headless Chromium)
- OpenAI GPT-4 Image API (design CLI)
- Anthropic SDK (LLM-judge evals)
- Supabase (telemetry backend)

```
┌─────────────────────────────────────────────────────────────────────┐
│                          gstack                                     │
│                                                                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │
│  │  31 Skills   │  │  Browse CLI  │  │  Design CLI  │              │
│  │  (SKILL.md)  │  │  (Playwright)│  │  (GPT Image) │              │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘              │
│         │                 │                  │                       │
│  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────┴───────┐              │
│  │  Template    │  │  HTTP Server │  │  Stateless   │              │
│  │  Pipeline    │  │  + Chromium  │  │  Commands    │              │
│  │ (resolvers)  │  │  + SSE Feed  │  │  + Sessions  │              │
│  └──────┬───────┘  └──────┬───────┘  └──────────────┘              │
│         │                 │                                         │
│  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────────┐              │
│  │  3-Host Gen  │  │  Chrome Ext  │  │  Test/Eval   │              │
│  │  Claude      │  │  Side Panel  │  │  3-Tier      │              │
│  │  Codex       │  │  Activity    │  │  Diff-Based  │              │
│  │  Factory     │  │  Chat        │  │  12 CI Jobs  │              │
│  └──────────────┘  └──────────────┘  └──────────────┘              │
│                                                                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │
│  │  bin/        │  │  lib/        │  │  Supabase    │              │
│  │  Utilities   │  │  Worktree    │  │  Telemetry   │              │
│  └──────────────┘  └──────────────┘  └──────────────┘              │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2. Directory Structure Map

```
gstack/
├── browse/                    # Headless browser CLI (Playwright + Bun)
│   ├── src/                   # 16 TypeScript modules
│   │   ├── cli.ts             # CLI entry point (persistent server model)
│   │   ├── server.ts          # Bun.serve HTTP daemon (1221 lines)
│   │   ├── commands.ts        # Command registry: READ(13) + WRITE(24) + META(18)
│   │   ├── snapshot.ts        # ARIA accessibility tree + @ref system
│   │   ├── browser-manager.ts # Chromium lifecycle, tabs, refs, dialogs
│   │   ├── read-commands.ts   # text, html, links, forms, js, eval, css, etc.
│   │   ├── write-commands.ts  # goto, click, fill, scroll, upload, cookies, etc.
│   │   ├── meta-commands.ts   # tabs, screenshot, pdf, snapshot, handoff, chain, etc.
│   │   ├── activity.ts        # SSE activity streaming to Chrome extension
│   │   ├── buffers.ts         # Circular ring buffer for console/network/dialog
│   │   ├── sidebar-agent.ts   # Claude subprocess for sidebar chat
│   │   ├── config.ts          # State/config resolution (.gstack/)
│   │   ├── url-validation.ts  # SSRF protection (metadata IP blocklist)
│   │   ├── platform.ts        # Cross-platform (Windows/macOS/Linux)
│   │   ├── find-browse.ts     # Binary discovery (workspace → global)
│   │   └── cookie-import-*.ts # Browser profile cookie import
│   ├── test/                  # 25+ integration tests (real Chromium, no mocks)
│   ├── dist/                  # Compiled binaries (browse, find-browse)
│   └── scripts/               # build-node-server.sh (Windows fallback)
│
├── design/                    # AI design mockup CLI (GPT-4 Image API)
│   ├── src/                   # 16 modules (generate, variants, compare, serve, etc.)
│   ├── test/                  # Server, feedback, gallery tests
│   └── dist/                  # Compiled binary
│
├── extension/                 # Chrome extension (side panel + activity feed)
│   ├── background.js          # Server discovery, auth, badge status
│   ├── sidepanel.js           # Chat + activity feed + refs (663 lines)
│   ├── content.js             # @ref overlay badges on pages
│   └── manifest.json          # sidePanel + serviceWorker + contentScript
│
├── scripts/                   # Build + DX tooling
│   ├── gen-skill-docs.ts      # Template → SKILL.md generator (475 lines)
│   ├── discover-skills.ts     # Template file scanner
│   ├── resolvers/             # 13 resolver modules (preamble, browse, design, etc.)
│   ├── skill-check.ts         # Health dashboard
│   ├── dev-skill.ts           # Watch mode (auto-regen + validate on change)
│   └── eval-*.ts              # Eval management (list, compare, summary, watch, select)
│
├── test/                      # Skill validation + eval tests
│   ├── helpers/               # session-runner, llm-judge, eval-store, touchfiles, etc.
│   ├── fixtures/              # Ground truth JSON, planted-bug pages, vulnerable code
│   ├── skill-validation.test.ts    # Tier 1: static validation (free)
│   ├── gen-skill-docs.test.ts      # Tier 1: generator quality (free)
│   ├── audit-compliance.test.ts    # Tier 1: security/compliance (free)
│   ├── skill-llm-eval.test.ts     # Tier 2: LLM-as-judge (~$0.15)
│   ├── skill-e2e-*.test.ts        # Tier 3: E2E via claude -p (~$3.85 total)
│   ├── skill-routing-e2e.test.ts   # Tier 3: skill routing by intent
│   ├── codex-e2e.test.ts          # Tier 3: Codex CLI integration
│   └── gemini-e2e.test.ts         # Tier 3: Gemini CLI integration
│
├── bin/                       # CLI utilities (bash + compiled TS)
│   ├── gstack-slug            # Project slug from git remote
│   ├── gstack-config          # Read/write ~/.gstack/config.yaml
│   ├── gstack-repo-mode       # Solo vs collaborative detection
│   ├── gstack-global-discover # Cross-AI session discovery
│   ├── gstack-update-check    # Version update notifications
│   ├── gstack-learnings-*     # Learning journal log/search
│   ├── gstack-telemetry-*     # Telemetry log/sync
│   ├── gstack-review-*        # PR review tracking
│   ├── gstack-relink          # Re-symlink skills after prefix change
│   └── gstack-uninstall       # Deregister skills from all hosts
│
├── lib/                       # Shared libraries
│   └── worktree.ts            # Git worktree isolation + change harvesting
│
├── supabase/                  # Cloud backend
│   ├── functions/             # Edge functions (telemetry-ingest, community-pulse, update-check)
│   └── migrations/            # Database schema + RLS policies
│
├── agents/                    # OpenAI agent interface (openai.yaml)
│
├── .github/                   # CI/CD
│   ├── workflows/             # evals.yml, skill-docs.yml, actionlint.yml, etc.
│   └── docker/                # Dockerfile.ci (pre-baked toolchain)
│
│── [31 skill directories]     # Each with SKILL.md.tmpl → SKILL.md
│
├── setup                      # One-time install (684 lines bash)
├── SKILL.md.tmpl              # Root skill template
├── ETHOS.md                   # Builder philosophy (Boil the Lake)
├── CLAUDE.md                  # Project instructions
├── CONTRIBUTING.md            # Contributor guide
├── CHANGELOG.md               # Release notes
├── VERSION                    # Current version (0.14.1.0)
├── conductor.json             # Orchestration config
└── package.json               # Build scripts + dependencies
```

---

## 3. Feature-to-Code Mapping

### Feature: Headless Browser Automation (`/browse`)

- **User-facing capability:** AI agents can navigate, read, interact with, and screenshot
  web pages via a headless Chromium instance — no mcp\_\_chrome tools needed
- **Entry point:** `$B <command>` (compiled binary at `browse/dist/browse`)
- **Code path:** `cli.ts` → `ensureServer()` → `server.ts /command` → command handler →
  `browser-manager.ts` → Playwright
- **Key files:**
  - `browse/src/cli.ts` — CLI launcher, server lifecycle
  - `browse/src/server.ts` — HTTP daemon, route dispatch (1221 lines)
  - `browse/src/commands.ts` — 55 command definitions (READ 13 + WRITE 24 + META 18)
  - `browse/src/snapshot.ts` — ARIA tree extraction, @e/@c ref assignment
  - `browse/src/browser-manager.ts` — Chromium lifecycle, tab management
- **Dependencies:** Playwright, `diff` library
- **Architecture notes:**
  - Persistent server model (30-min idle timeout, auto-restart on crash)
  - Token-based auth (UUID per server instance in `.gstack/browse.json`)
  - Refs persist in refMap until next snapshot (enables multi-step workflows)
  - No DOM mutation — uses Playwright's `ariaSnapshot()` for ARIA tree

### Feature: Skill Template Pipeline

- **User-facing capability:** 31 slash-command skills auto-generated from templates,
  compiled for Claude Code, Codex, and Factory hosts
- **Entry point:** `bun run gen:skill-docs [--host claude|codex|factory|all]`
- **Code path:** `gen-skill-docs.ts` → `discoverTemplates()` → for each `.tmpl`:
  parse frontmatter → resolve `{{PLACEHOLDER}}` → transform for host → write SKILL.md
- **Key files:**
  - `scripts/gen-skill-docs.ts` — Main engine (475 lines)
  - `scripts/discover-skills.ts` — Template scanner
  - `scripts/resolvers/*.ts` — 13 resolver modules
  - `*/SKILL.md.tmpl` — 32 template files (source of truth)
- **Resolver categories:**
  | Category | Resolvers | Purpose |
  |----------|-----------|---------|
  | Preamble | PREAMBLE, TEST_FAILURE_TRIAGE | Initialization, voice, preferences |
  | Browse | BROWSE_SETUP, COMMAND_REFERENCE, SNAPSHOT_FLAGS | Auto-generated from command registry |
  | Design | DESIGN_METHODOLOGY, DESIGN_HARD_RULES, DESIGN_MOCKUP, etc. | 8 design resolvers |
  | Review | REVIEW_DASHBOARD, ADVERSARIAL_STEP, CODEX_SECOND_OPINION, etc. | 12 review resolvers |
  | Testing | TEST_BOOTSTRAP, TEST_COVERAGE_AUDIT_* | Framework detection, coverage audit |
  | Utility | BASE_BRANCH_DETECT, QA_METHODOLOGY, CHANGELOG_WORKFLOW, etc. | Platform detection, git |
  | Learning | LEARNINGS_SEARCH, LEARNINGS_LOG | Cross-project learning recall |
  | Composition | INVOKE_SKILL | Multi-skill chaining |

### Feature: AI Design Mockup Generation (`/design-*`)

- **User-facing capability:** Generate, iterate, compare, and verify UI mockups using
  GPT-4 Image API — feedback loop with comparison boards
- **Entry point:** `design/dist/design <command>`
- **Code path:** `cli.ts` → command handler → OpenAI API → image generation → local output
- **Key files:**
  - `design/src/cli.ts` — 13 commands (generate, variants, iterate, check, compare, etc.)
  - `design/src/generate.ts` — OpenAI Responses API with `image_generation` tool
  - `design/src/compare.ts` — HTML comparison board (628 lines)
  - `design/src/serve.ts` — HTTP feedback server (state machine: SERVING → DONE)
  - `design/src/memory.ts` — Extract design language to DESIGN.md
- **Dependencies:** OpenAI API (key in `~/.gstack/openai.json` or env)
- **Architecture notes:** Fully stateless — session state in `/tmp/` JSON files

### Feature: E2E Test & Eval System

- **User-facing capability:** Diff-based test selection, three-tier system (free/LLM-judge/E2E),
  cost tracking, auto-comparison with previous runs
- **Entry point:** `bun run test:evals` or `bun run test:gate`
- **Code path:** `touchfiles.ts selectTests()` → `e2e-helpers.ts describeIfSelected()` →
  `session-runner.ts runSkillTest()` → `claude -p` subprocess → `eval-store.ts` persistence
- **Key files:**
  - `test/helpers/touchfiles.ts` — Diff-based selection engine (GLOBAL_TOUCHFILES, E2E_TIERS)
  - `test/helpers/session-runner.ts` — Spawns `claude -p`, streams NDJSON
  - `test/helpers/llm-judge.ts` — Quality scoring via claude-sonnet-4-6
  - `test/helpers/eval-store.ts` — Result persistence + comparison
  - `test/helpers/skill-parser.ts` — SKILL.md validation parser
- **Storage:** `~/.gstack/projects/$SLUG/evals/{version}-{branch}-{tier}-{timestamp}.json`

### Feature: Chrome Extension (Side Panel)

- **User-facing capability:** Live activity feed, chat with Claude via sidebar,
  @ref overlay badges on web pages
- **Entry point:** `$B connect` → headed Chromium + extension
- **Code path:** `sidepanel.js` polls `/sidebar-chat` + SSE from `/activity/stream`;
  `content.js` renders ref overlays; `background.js` manages connection
- **Key files:**
  - `extension/sidepanel.js` — Chat UI + activity feed (663 lines)
  - `extension/background.js` — Server discovery, auth relay
  - `extension/content.js` — @ref badge overlays
- **Connection:** HTTP to browse server (localhost, bearer token auth)

### Feature: Multi-Host Skill Compilation

- **User-facing capability:** Skills work identically on Claude Code, Codex (OpenAI), and Factory
- **Code path:** `gen-skill-docs.ts processExternalHost()` → path rewriting → frontmatter
  transformation → tool name translation (Factory) → OpenAI YAML generation (Codex)
- **Host differences:**
  | Aspect | Claude | Codex | Factory |
  |--------|--------|-------|---------|
  | Paths | `~/.claude/skills/gstack` | `$GSTACK_ROOT` | `$GSTACK_ROOT` |
  | Local | `.claude/skills/gstack` | `.agents/skills/gstack` | `.factory/skills/gstack` |
  | Metadata | None | `openai.yaml` | None |
  | Tool names | Native (Bash, Read, Write) | Native | Translated ("run this command") |
  | Frontmatter | Strip `sensitive:` | Name + desc only (1024 char limit) | Full + `disable-model-invocation` |

---

## 4. Database Schema

gstack has no traditional database. State is file-based:

```
┌───────────────────────────────────────────────┐
│  ~/.gstack/                                    │
│  ├── config.yaml          (global settings)    │
│  ├── openai.json          (design API key)     │
│  ├── sidebar-agent-queue.jsonl (chat queue)    │
│  └── projects/                                 │
│      └── {slug}/                               │
│          ├── repo-mode.json   (solo/collab)    │
│          ├── learnings.jsonl  (learning log)   │
│          ├── evals/           (test results)   │
│          │   └── {ver}-{branch}-{tier}-{ts}.json│
│          └── e2e-runs/        (run artifacts)  │
│              └── {runId}/                      │
│                  ├── progress.log              │
│                  └── {testName}.ndjson          │
├───────────────────────────────────────────────┤
│  {project}/.gstack/                            │
│  ├── browse.json          (server state)       │
│  │   ├── pid, port, token, startedAt           │
│  │   └── serverPath, binaryVersion, mode       │
│  ├── browse-console.log   (console buffer)     │
│  ├── browse-network.log   (network buffer)     │
│  └── browse-dialog.log    (dialog buffer)      │
├───────────────────────────────────────────────┤
│  Supabase (cloud)                              │
│  ├── telemetry events    (telemetry-ingest)    │
│  ├── community pulse     (community-pulse)     │
│  └── version registry    (update-check)        │
└───────────────────────────────────────────────┘
```

---

## 5. API Endpoints Reference

### Browse Server (localhost, random port 10000-60000)

| Method | Endpoint | Purpose | Auth |
|--------|----------|---------|------|
| POST | `/command` | Execute browse command | Token |
| GET | `/health` | Server health check | No |
| GET | `/activity/stream?after=ID` | SSE activity feed | Token |
| GET | `/activity/history?limit=N` | Activity history (REST) | Token |
| GET | `/sidebar-chat?after=N` | Poll chat messages | Token |
| POST | `/sidebar-chat` | Send chat message | Token |
| POST | `/sidebar-chat/clear` | Clear chat history | Token |
| POST | `/sidebar-agent/event` | Agent event relay | Token |
| GET | `/refs` | Current snapshot refs | Token |

### Design Server (localhost, created by `design serve`)

| Method | Endpoint | Purpose | Auth |
|--------|----------|---------|------|
| GET | `/` | Comparison board HTML | No |
| POST | `/feedback` | Submit design feedback | No |
| POST | `/regenerate` | Trigger regeneration | No |
| GET | `/status` | Server state (SERVING/REGENERATING/DONE) | No |

### Supabase Edge Functions

| Method | Endpoint | Purpose | Auth |
|--------|----------|---------|------|
| POST | `/telemetry-ingest` | Batch telemetry events (100 max, 50KB) | API key |
| GET | `/community-pulse` | Aggregated community metrics | API key |
| GET | `/update-check` | Version update detection | None |

---

## 6. Core Architecture Diagrams

### Browse CLI Architecture

```
┌──────────────────┐
│  $B <command>     │   CLI (cli.ts)
│  (compiled bin)   │
└────────┬─────────┘
         │ HTTP POST /command
         ▼
┌──────────────────────────────────────────────────┐
│  Bun.serve HTTP Server (server.ts)                │
│  Port: random 10000-60000 | Auth: UUID token      │
│                                                    │
│  ┌────────────┐ ┌──────────────┐ ┌─────────────┐ │
│  │ READ (13)  │ │ WRITE (24)   │ │ META (18)   │ │
│  │ text, html │ │ goto, click  │ │ snapshot    │ │
│  │ links,forms│ │ fill, scroll │ │ screenshot  │ │
│  │ js, eval   │ │ upload, wait │ │ tabs, chain │ │
│  │ css, attrs │ │ cookie, type │ │ handoff     │ │
│  │ console    │ │ press, hover │ │ connect     │ │
│  └─────┬──────┘ └──────┬───────┘ └──────┬──────┘ │
│        └───────────┬────┘               │         │
│                    ▼                    │         │
│  ┌─────────────────────────────┐        │         │
│  │  BrowserManager             │◄───────┘         │
│  │  • Chromium via Playwright  │                  │
│  │  • Tab map (page IDs)       │                  │
│  │  • Ref map (@e1, @c1)      │                  │
│  │  • Dialog auto-accept       │                  │
│  │  • Frame context            │                  │
│  └─────────────┬───────────────┘                  │
│                │                                   │
│  ┌─────────────▼───────────────┐                  │
│  │  Snapshot Engine            │                  │
│  │  page.ariaSnapshot()       │                  │
│  │  ──► parse YAML tree       │                  │
│  │  ──► assign @e1..@eN refs  │                  │
│  │  ──► build Locator map     │                  │
│  │  ──► cursor-interactive    │                  │
│  │       (@c1..@cN)           │                  │
│  └─────────────────────────────┘                  │
│                                                    │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────┐│
│  │ Activity │  │ Buffers  │  │ Sidebar Agent    ││
│  │ SSE Feed │  │ Console  │  │ claude -p queue  ││
│  │ (ext)    │  │ Network  │  │ (headed mode)    ││
│  │          │  │ Dialog   │  │                  ││
│  └──────────┘  └──────────┘  └──────────────────┘│
└──────────────────────────────────────────────────┘
```

### Skill Template Pipeline

```
┌────────────────────────────────────────────────────────────────┐
│  SKILL.md.tmpl files (32 total, source of truth)               │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │  ---                                                      │  │
│  │  name: ship                                               │  │
│  │  preamble-tier: 4                                         │  │
│  │  ---                                                      │  │
│  │  {{PREAMBLE}}                                             │  │
│  │  {{BASE_BRANCH_DETECT}}                                   │  │
│  │  ## Step 1: ...                                           │  │
│  │  {{REVIEW_DASHBOARD}}                                     │  │
│  │  {{INVOKE_SKILL:plan-eng-review}}                         │  │
│  └──────────────────────────────────────────────────────────┘  │
└───────────────────────┬────────────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────────┐
│  gen-skill-docs.ts (475 lines)                                 │
│                                                                │
│  1. discoverTemplates() ──► find all SKILL.md.tmpl             │
│  2. Parse YAML frontmatter (name, tier, hooks, benefits-from)  │
│  3. For each {{PLACEHOLDER}}:                                  │
│     ┌─────────────────────────────────────────────────────┐    │
│     │  RESOLVERS[name](ctx, args)                         │    │
│     │                                                     │    │
│     │  preamble.ts ──► PREAMBLE (tier 1-4), TEST_FAILURE  │    │
│     │  browse.ts   ──► COMMAND_REFERENCE, SNAPSHOT_FLAGS   │    │
│     │  design.ts   ──► DESIGN_METHODOLOGY, HARD_RULES     │    │
│     │  review.ts   ──► REVIEW_DASHBOARD, ADVERSARIAL      │    │
│     │  testing.ts  ──► TEST_BOOTSTRAP, COVERAGE_AUDIT     │    │
│     │  utility.ts  ──► BASE_BRANCH_DETECT, QA_METHODOLOGY │    │
│     │  learnings.ts──► LEARNINGS_SEARCH, LEARNINGS_LOG    │    │
│     │  confidence.ts─► CONFIDENCE_CALIBRATION              │    │
│     │  composition.ts► INVOKE_SKILL (chain skills)        │    │
│     └─────────────────────────────────────────────────────┘    │
│  4. Host-aware transformation (paths, frontmatter, tool names) │
│  5. Write output + optional openai.yaml                        │
└───────────┬───────────────────┬──────────────────┬─────────────┘
            │                   │                  │
            ▼                   ▼                  ▼
     ┌────────────┐     ┌────────────┐     ┌────────────┐
     │ SKILL.md   │     │ .agents/   │     │ .factory/  │
     │ (Claude)   │     │ (Codex)    │     │ (Factory)  │
     │            │     │ +yaml      │     │            │
     └────────────┘     └────────────┘     └────────────┘
```

### Test & Eval Architecture

```
┌──────────────────────────────────────────────────────────────┐
│  Test Tiers                                                   │
│                                                               │
│  Tier 1: FREE (<2s) ──► bun test                             │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ skill-validation.test.ts  (command + flag validation)  │  │
│  │ gen-skill-docs.test.ts    (freshness + quality)        │  │
│  │ audit-compliance.test.ts  (security checks)            │  │
│  │ browse/test/*.test.ts     (25+ integration tests)      │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  Tier 2: LLM-JUDGE (~$0.15) ──► bun run test:evals          │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ skill-llm-eval.test.ts                                 │  │
│  │ Scores: clarity, completeness, actionability (1-5)     │  │
│  │ Uses: claude-sonnet-4-6 via callJudge()                │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  Tier 3: E2E (~$3.85) ──► bun run test:evals                │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ skill-e2e-*.test.ts (8 files, 100+ tests)             │  │
│  │ skill-routing-e2e.test.ts (intent routing)            │  │
│  │ codex-e2e.test.ts (Codex CLI)                         │  │
│  │ gemini-e2e.test.ts (Gemini CLI)                       │  │
│  │                                                        │  │
│  │ Each test: runSkillTest() ──► claude -p subprocess     │  │
│  │            ──► stream NDJSON ──► capture tool calls    │  │
│  │            ──► recordE2E() ──► EvalCollector           │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  Diff-Based Selection:                                        │
│  git diff ──► touchfiles.ts selectTests() ──► skip unaffected│
│  EVALS_ALL=1 to force all | EVALS_TIER=gate|periodic         │
│                                                               │
│  Two-Tier Gating:                                             │
│  gate (35+ tests) ──► CI blocks merge                        │
│  periodic (60+ tests) ──► weekly cron, non-blocking          │
└──────────────────────────────────────────────────────────────┘
```

### Installation & Multi-Host Setup

```
┌─────────────────────────────────────────────────────────┐
│  ./setup (684 lines bash)                                │
│                                                          │
│  1. bun install + bun run build                         │
│     ├── browse/dist/browse (Mach-O arm64)               │
│     ├── browse/dist/find-browse                          │
│     ├── design/dist/design                               │
│     └── gen:skill-docs (all hosts)                       │
│                                                          │
│  2. Ensure Playwright Chromium                           │
│                                                          │
│  3. Install for Claude Code                              │
│     ~/.claude/skills/ ◄── symlinks per skill             │
│     ├── [prefix-]qa -> gstack/qa/                        │
│     ├── [prefix-]ship -> gstack/ship/                    │
│     └── ... (31 skills)                                  │
│                                                          │
│  4. Install for Codex                                    │
│     ~/.codex/skills/gstack/ ◄── symlinks to runtime      │
│     ├── bin/ -> gstack/bin/                              │
│     ├── browse/dist/ -> gstack/browse/dist/              │
│     └── ETHOS.md -> gstack/ETHOS.md                      │
│                                                          │
│  5. Install for Kiro (copy from .agents/, sed rewrite)   │
│  6. Install for Factory (copy from .factory/)            │
└─────────────────────────────────────────────────────────┘
```

---

## 7. Key Classes & Functions

### BrowserManager (`browse/src/browser-manager.ts`)
- **Purpose:** Manages Chromium lifecycle, tab state, ref resolution, dialog handling
- **Key methods:** `getPage()`, `resolveRef(selector)`, `newTab(url)`, `switchTab(id)`,
  `recreateContext()` (for useragent/header changes)
- **Used by:** All command handlers via server.ts

### EvalCollector (`test/helpers/eval-store.ts`)
- **Purpose:** Accumulates test results during a run, writes JSON, prints summary, auto-compares
- **Key methods:** `add(entry)`, `finalize()`, `compareWith(previous)`
- **Used by:** All E2E test files via `recordE2E()`

### WorktreeManager (`lib/worktree.ts`)
- **Purpose:** Git worktree isolation for E2E tests that modify code
- **Key methods:** `create(testName)`, `harvest(testName)`, `cleanup(testName)`, `pruneStale()`
- **Used by:** E2E tests that need isolated repos

### Template Resolvers (`scripts/resolvers/*.ts`)
- **Purpose:** Generate dynamic content for SKILL.md templates
- **Pattern:** Each exports functions matching `(ctx: TemplateContext, args: string[]) => string`
- **13 modules:** preamble, browse, design, review, testing, utility, learnings, confidence, composition

---

## 8. Configuration & Environment

### Required Environment Variables

| Variable | Purpose | Required For |
|----------|---------|-------------|
| `ANTHROPIC_API_KEY` | Claude API access | LLM-judge evals, E2E tests |
| `OPENAI_API_KEY` | Design CLI, Codex E2E | Design features, Codex tests |
| `GEMINI_API_KEY` | Gemini CLI E2E | Gemini tests |

### Optional Environment Variables

| Variable | Purpose | Default |
|----------|---------|---------|
| `EVALS` | Enable eval tests | unset (disabled) |
| `EVALS_ALL` | Force all tests (skip diff selection) | unset |
| `EVALS_TIER` | Filter by tier (gate/periodic) | unset (all) |
| `EVALS_MODEL` | Override test model | claude-sonnet-4-6 |
| `EVALS_CONCURRENCY` | Parallel test limit | 15 |
| `BROWSE_PORT` | Fixed browse server port | random 10000-60000 |
| `BROWSE_HEADED` | Launch headed Chromium | unset (headless) |
| `BROWSE_IDLE_TIMEOUT` | Server idle timeout (ms) | 1800000 (30 min) |

### Config Files

| File | Purpose |
|------|---------|
| `~/.gstack/config.yaml` | Global settings (proactive, telemetry, skill_prefix, etc.) |
| `~/.gstack/openai.json` | OpenAI API key for design CLI |
| `{project}/.gstack/browse.json` | Browse server state (pid, port, token) |
| `~/.gstack/projects/{slug}/` | Per-project data (learnings, evals, repo-mode) |

---

## 9. Change Guidance

### Adding a New Skill

1. Create `my-skill/SKILL.md.tmpl` with frontmatter (name, preamble-tier, description)
2. Use `{{PREAMBLE}}` and other resolvers as needed
3. Run `bun run gen:skill-docs` → generates `my-skill/SKILL.md`
4. Add touchfile entries in `test/helpers/touchfiles.ts` (E2E_TOUCHFILES + E2E_TIERS)
5. Add validation entry in `test/skill-validation.test.ts` if it uses browse commands
6. Run `bun test` to verify
7. Run `./setup` to register the skill

### Adding a New Browse Command

1. Add to `browse/src/commands.ts` (READ_COMMANDS, WRITE_COMMANDS, or META_COMMANDS)
2. Add description in COMMAND_DESCRIPTIONS (same file)
3. Implement handler in appropriate file (read-commands.ts, write-commands.ts, meta-commands.ts)
4. Add test in `browse/test/commands.test.ts`
5. Run `bun run build` (regenerates SKILL.md command reference)
6. Run `bun test` to verify

### Adding a New Resolver

1. Create or edit `scripts/resolvers/my-resolver.ts`
2. Export function matching `(ctx: TemplateContext, args?: string[]) => string`
3. Register in `scripts/resolvers/index.ts`
4. Use `{{MY_RESOLVER}}` in templates
5. Run `bun run gen:skill-docs` and verify output

### Modifying the Preamble

1. Edit `scripts/resolvers/preamble.ts`
2. Consider preamble tier (1-4) — changes cascade to all skills at that tier and above
3. Run `bun run gen:skill-docs` → regenerates all affected SKILL.md files
4. Run `bun test` (freshness check will catch missed regeneration)
5. Commit both `.tmpl` and `.md` files

### Running Tests Before Shipping

```bash
bun test                  # Always (free, <2s)
bun run eval:select       # Preview which evals would run
bun run test:evals        # Diff-based evals (~$4 max)
```

### Modifying CI

- Workflows: `.github/workflows/evals.yml` (main CI gate)
- Docker image: `.github/docker/Dockerfile.ci` (toolchain)
- Test matrix: `evals.yml` → `strategy.matrix.suite` (12 parallel jobs)

---

## 10. Technical Debt & Notes

### Known Issues

- **Tracked binaries:** `browse/dist/` and `design/dist/` are tracked by git due to
  historical mistake. They show as modified in `git status` — ignore them. Never stage
  with `git add .` or `git add -A`.
- **Mach-O only binaries:** Compiled binaries are arm64 macOS only. `./setup` rebuilds
  from source for each platform, making the checked-in binaries redundant.
- **Windows Bun bug:** `posix_spawn` broken on Windows — browse server falls back to
  Node.js (`server-node.mjs`). Workaround is stable but adds maintenance surface.

### Architecture Observations

- **No spec system yet:** Commit 1878713 mentions "spec frontmatter and rebuild spec
  registry" but no spec.json/spec.yaml files exist on disk. Planned but not implemented.
- **Supabase integration:** Edge functions exist for telemetry/community/update-check
  but the integration path (when telemetry syncs, what community-pulse shows) is
  infrastructure-level, not user-facing yet.
- **Token budget awareness:** `gen-skill-docs.ts` prints line/token counts per skill
  after generation. Some skills (ship, review, qa) are 1500-2000 lines — context
  window pressure for smaller models.
- **Symlink danger:** When `.claude/skills/gstack` is a symlink to the working directory,
  template changes are live immediately across all concurrent Claude Code sessions.
  Large refactors should `rm` the symlink first.

### Strengths

- **Comprehensive test infrastructure:** 3-tier, diff-based, cost-tracked, auto-comparing
  eval system is best-in-class for an open source tool
- **Multi-host strategy:** Skills compile for 3 AI platforms from a single template source
- **Self-documenting:** SKILL.md files are auto-generated from templates + command registries,
  so documentation stays in sync with implementation
- **Real browser testing:** No mocks — Playwright drives real Chromium in both browse tests
  and E2E skill evals
