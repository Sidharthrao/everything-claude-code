# Study and Research Guide — Everything Claude Code (ECC)

> **Repository**: [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)
> **Version**: v1.8.0 (Mar 2026) | **License**: MIT
> **Stats**: 50K+ stars | 6K+ forks | 30+ contributors | 5 languages supported

---

## 1. What This Repository Is

**Everything Claude Code (ECC)** is a **production-ready performance optimization system for AI agent harnesses**. It is **not** just a collection of config files — it is a comprehensive system providing:

- **18 Specialized Agents** — Subagents for delegation (planning, reviewing, testing, security, etc.)
- **94 Skills** — Workflow definitions and domain knowledge across 15+ languages/frameworks
- **48 Commands** — Slash commands for quick task execution
- **Automated Hooks** — Trigger-based automations on tool and lifecycle events
- **Rules** — Always-follow guidelines (common + 8 language-specific rule sets)
- **MCP Configurations** — 14 pre-configured Model Context Protocol server setups
- **Cross-Platform Support** — Claude Code, Cursor, Codex (app + CLI), OpenCode, and Antigravity

It was born from an **Anthropic hackathon win** and refined over **10+ months of daily production use** building real products.

---

## 2. Repository Structure — High-Level Map

```
everything-claude-code/
│
├── 📄 README.md                    # Main documentation (1295 lines, the starting point)
├── 📄 AGENTS.md                    # Universal cross-tool agent instructions
├── 📄 CLAUDE.md                    # Claude Code project config
├── 📄 the-shortform-guide.md       # ⭐ START HERE — Setup, foundations, philosophy
├── 📄 the-longform-guide.md        # Advanced: token optimization, memory, evals, parallelization
├── 📄 the-security-guide.md        # Agent security: sandboxing, sanitization, attack vectors
├── 📄 the-openclaw-guide.md        # Security case study: OpenClaw risks
│
├── 📁 agents/          (18 files)  # Specialized subagent definitions
├── 📁 skills/          (94 dirs)   # Workflow skills and domain knowledge
├── 📁 commands/        (48 files)  # Slash commands
├── 📁 hooks/                       # Trigger-based automations (hooks.json + README)
├── 📁 rules/           (8 langs)   # Always-follow guidelines
├── 📁 scripts/                     # Cross-platform Node.js utilities
├── 📁 tests/                       # Test suite
├── 📁 mcp-configs/                 # MCP server configurations
├── 📁 contexts/        (3 files)   # Dynamic system prompt injection contexts
├── 📁 examples/        (7 files)   # Example CLAUDE.md configs for various stacks
├── 📁 docs/                        # Architecture docs, translations (5 languages)
├── 📁 schemas/         (8 files)   # JSON schemas for configs
├── 📁 manifests/       (3 files)   # Install profiles and modules
├── 📁 plugins/                     # Plugin documentation
├── 📁 assets/                      # Images for guides
│
├── 📁 .claude-plugin/              # Plugin and marketplace manifests
├── 📁 .claude/                     # Claude Code config
├── 📁 .cursor/                     # Cursor IDE support
├── 📁 .codex/                      # Codex app + CLI support
├── 📁 .opencode/                   # OpenCode support
├── 📁 .agents/                     # Cross-tool agent skills (contains .agents/skills/)
└── 📁 .github/                     # GitHub Actions, templates
```

---

## 3. Core Components — Deep Dive

### 3.1 Agents (`agents/`)

Agents are **specialized subprocesses** your main Claude instance can delegate tasks to, each with limited scope and specific tools.

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| `planner.md` | Feature implementation planning | Complex features, refactoring |
| `architect.md` | System design and scalability | Architectural decisions |
| `tdd-guide.md` | Test-driven development | New features, bug fixes |
| `code-reviewer.md` | Code quality review | After writing/modifying code |
| `security-reviewer.md` | Vulnerability detection | Before commits, sensitive code |
| `build-error-resolver.md` | Fix build/type errors | When builds fail |
| `e2e-runner.md` | Playwright E2E testing | Critical user flows |
| `refactor-cleaner.md` | Dead code cleanup | Code maintenance |
| `doc-updater.md` | Documentation sync | Updating docs |
| `go-reviewer.md` | Go code review | Go projects |
| `go-build-resolver.md` | Go build error resolution | Go build failures |
| `python-reviewer.md` | Python code review | Python projects |
| `database-reviewer.md` | PostgreSQL/Supabase specialist | Schema design, query optimization |
| `chief-of-staff.md` | Communication triage | Multi-channel comms |
| `loop-operator.md` | Autonomous loop execution | Safe loop monitoring |
| `harness-optimizer.md` | Harness config tuning | Reliability, cost, throughput |
| `kotlin-reviewer.md` | Kotlin code review | Kotlin projects |
| `kotlin-build-resolver.md` | Kotlin build errors | Kotlin build failures |

**Format**: Markdown with YAML frontmatter (name, description, tools, model).

### 3.2 Skills (`skills/`)

Skills are **detailed workflow definitions** — broader than commands, containing step-by-step procedures, best practices, and domain knowledge. There are **94 skill directories** grouped by category:

| Category | Skills | Examples |
|----------|--------|----------|
| **Core Development** | 8 | `coding-standards`, `tdd-workflow`, `verification-loop`, `eval-harness` |
| **Frontend** | 3 | `frontend-patterns`, `frontend-slides`, `liquid-glass-design` |
| **Backend/API** | 4 | `backend-patterns`, `api-design`, `postgres-patterns`, `database-migrations` |
| **Python** | 5 | `python-patterns`, `python-testing`, `django-*` (4 skills) |
| **Java/Kotlin** | 9 | `springboot-*` (4), `java-coding-standards`, `jpa-patterns`, `kotlin-*` (3) |
| **Go** | 2 | `golang-patterns`, `golang-testing` |
| **C++** | 2 | `cpp-coding-standards`, `cpp-testing` |
| **Perl** | 3 | `perl-patterns`, `perl-security`, `perl-testing` |
| **Swift/iOS** | 4 | `swift-actor-persistence`, `swift-protocol-di-testing`, `swift-concurrency-6-2`, `swiftui-patterns` |
| **DevOps** | 2 | `deployment-patterns`, `docker-patterns` |
| **Security** | 3 | `security-review`, `security-scan`, `plankton-code-quality` |
| **AI/LLM** | 4 | `claude-api`, `cost-aware-llm-pipeline`, `foundation-models-on-device`, `prompt-optimizer` |
| **Business/Content** | 7 | `article-writing`, `content-engine`, `market-research`, `investor-*` (2), `crosspost`, `x-api` |
| **Learning Systems** | 5 | `continuous-learning`, `continuous-learning-v2`, `iterative-retrieval`, `strategic-compact`, `search-first` |
| **Media** | 3 | `fal-ai-media`, `video-editing`, `videodb` |
| **Orchestration** | 4 | `autonomous-loops`, `dmux-workflows`, `continuous-agent-loop`, `nanoclaw-repl` |
| **Research** | 2 | `deep-research`, `exa-search` |
| **Industry-Specific** | 7 | `carrier-relationship-management`, `customs-trade-compliance`, `energy-procurement`, etc. |

### 3.3 Commands (`commands/`)

Commands are **slash commands** — quick executable prompts invoked via `/command-name`. There are **48 commands**:

**Key Commands to Know First**:
- `/plan` — Create implementation plan (uses planner agent)
- `/tdd` — Test-driven development workflow
- `/code-review` — Quality review of code
- `/build-fix` — Fix build errors
- `/e2e` — Generate E2E tests
- `/learn` — Extract patterns from current session
- `/verify` — Run verification loop
- `/skill-create` — Generate skills from git history

### 3.4 Hooks (`hooks/`)

Hooks are **trigger-based automations** that fire on specific events:

| Hook Type | When It Fires | Example Use |
|-----------|--------------|-------------|
| `PreToolUse` | Before a tool executes | tmux reminder, block dangerous writes |
| `PostToolUse` | After a tool finishes | Auto-format code, typecheck, lint |
| `UserPromptSubmit` | When you send a message | Detect secrets in prompts |
| `Stop` | When Claude finishes responding | Check for console.log in modified files |
| `PreCompact` | Before context compaction | Save important state |
| `SessionStart` | When session begins | Load previous context |
| `SessionEnd` | When session ends | Persist session learnings |
| `Notification` | Permission requests | Custom notification handling |

Configuration lives in `hooks/hooks.json`.

### 3.5 Rules (`rules/`)

Rules are **always-follow guidelines** that Claude loads every session:

```
rules/
├── common/          # 9 language-agnostic principles (always install)
│   ├── coding-style.md, git-workflow.md, testing.md
│   ├── performance.md, patterns.md, hooks.md
│   ├── agents.md, security.md
├── typescript/      # TypeScript/JavaScript specific
├── python/          # Python specific
├── golang/          # Go specific
├── kotlin/          # Kotlin specific
├── swift/           # Swift specific
├── perl/            # Perl specific
└── php/             # PHP specific
```

### 3.6 MCP Configurations (`mcp-configs/`)

Pre-configured **Model Context Protocol** servers for external integrations:
- GitHub, Supabase, Vercel, Railway, Firecrawl, Memory, Sequential Thinking, etc.

### 3.7 Cross-Platform Support

The repo ships ready-to-use configs for **4 major AI coding tools**:

| Tool | Config Location | Key Feature |
|------|----------------|-------------|
| **Claude Code** | Native (primary target) | Full plugin support |
| **Cursor** | `.cursor/` | DRY adapter pattern for hooks |
| **Codex** | `.codex/` | AGENTS.md + config.toml + agent roles |
| **OpenCode** | `.opencode/` | Full plugin + 6 native tools |

---

## 4. The Four Guides — Your Reading Order

The repo includes **4 comprehensive guides** that are essential reading:

### Guide 1: The Shorthand Guide ⭐ **(Read First)**
**File**: `the-shortform-guide.md` (432 lines)

**Covers**:
- Skills and Commands — what they are, how to use them
- Hooks — types, examples, creating your own
- Subagents — delegation, scoping, sandboxing
- Rules and Memory — configuration approaches
- MCPs — what they are, context window management
- Plugins — installation, LSP integration
- Tips & Tricks — keyboard shortcuts, parallel workflows, tmux, mgrep
- Editor setup (Zed, VSCode/Cursor)
- The author's personal setup (plugins, MCPs, hooks, rules, agents)

### Guide 2: The Longform Guide
**File**: `the-longform-guide.md` (355 lines)

**Covers**:
- Context and Memory Management — session persistence, dynamic prompt injection
- Continuous Learning — auto-extracting patterns into skills
- Token Optimization — model selection (Haiku vs Sonnet vs Opus), cost strategies
- Verification Loops and Evals — pass@k vs pass^k metrics
- Parallelization — forking, git worktrees, the cascade method
- Groundwork — the two-instance kickoff pattern, llms.txt
- Sub-Agent best practices — the context problem, iterative retrieval pattern

### Guide 3: The Security Guide
**File**: `the-security-guide.md` (596 lines)

**Covers**:
- Attack vectors and surfaces (WhatsApp example, transitive prompt injection)
- Sandboxing (tool-level → Docker → VMs)
- Sanitization (link auditing, hidden text detection, AgentShield)
- Common attacks: prompt injection, supply chain, credential theft, lateral movement, MCP tool poisoning, memory poisoning
- OWASP Top 10 for Agentic Applications
- Observability and logging
- AgentShield — automated security scanning tool

### Guide 4: The OpenClaw Guide
**File**: `the-openclaw-guide.md` (471 lines)

**Covers**: A detailed security case study analyzing the OpenClaw recursive agent platform — attack surface analysis, real-world breaches (Moltbook, ClawHavoc, CVE-2026-25253), the "MiniClaw" philosophy, and what a secure agent architecture looks like.

---

## 5. Study Roadmap — How to Learn This Repo

### Phase 1: Foundations (Day 1-2)

1. **Read `the-shortform-guide.md`** — This is the essential starting point. Understand skills, hooks, agents, rules, MCPs, and plugins.
2. **Read `AGENTS.md`** — Understand core principles (agent-first, TDD, security-first, immutability, plan-before-execute).
3. **Read `CLAUDE.md`** — Understand how the project itself is configured.
4. **Browse `README.md`** — Quick Start, installation options, FAQ.

### Phase 2: Core Components (Day 3-5)

5. **Study 3-4 agents** — Start with `planner.md`, `code-reviewer.md`, `tdd-guide.md`, `security-reviewer.md`. Understand the YAML frontmatter format.
6. **Study 5-6 skills** — Start with `coding-standards`, `tdd-workflow`, `security-review`, `backend-patterns`, `frontend-patterns`. Read each `SKILL.md`.
7. **Study 5-6 commands** — Start with `plan.md`, `tdd.md`, `code-review.md`, `build-fix.md`, `e2e.md`. Understand the command → agent → skill chain.
8. **Study `hooks/hooks.json`** — Understand hook matchers, types, and the event lifecycle.
9. **Study `rules/common/`** — Read all 8-9 common rules files to understand coding standards enforced.

### Phase 3: Advanced Patterns (Day 6-8)

10. **Read `the-longform-guide.md`** — Token optimization, memory persistence hooks, verification loops, parallelization.
11. **Study `contexts/`** — Understand dynamic system prompt injection (dev.md, review.md, research.md).
12. **Study `examples/`** — Real-world CLAUDE.md configs for Next.js SaaS, Go microservice, Django API, Rust API.
13. **Study `scripts/`** — Cross-platform Node.js hook implementations (session-start.js, session-end.js, etc.).
14. **Study `mcp-configs/mcp-servers.json`** — Understand MCP server configurations.

### Phase 4: Security (Day 9-10)

15. **Read `the-security-guide.md`** — Essential for understanding agent risks.
16. **Read `the-openclaw-guide.md`** — Real-world security case study.
17. **Study `skills/security-review/SKILL.md`** and `skills/security-scan/SKILL.md`.

### Phase 5: Specialization (Day 11+)

18. **Pick your stack** and deep-dive into relevant skills:
    - **TypeScript/React**: `frontend-patterns`, `e2e-testing`, `rules/typescript/`
    - **Python/Django**: `python-patterns`, `django-patterns`, `rules/python/`
    - **Go**: `golang-patterns`, `golang-testing`, `rules/golang/`
    - **AI/LLM**: `claude-api`, `cost-aware-llm-pipeline`, `deep-research`
    - **DevOps**: `deployment-patterns`, `docker-patterns`, `database-migrations`
19. **Study continuous learning**: `continuous-learning/`, `continuous-learning-v2/`
20. **Study cross-platform configs**: `.cursor/`, `.codex/`, `.opencode/`

---

## 6. How to Leverage This Repo to the Fullest

### 6.1 Installation Strategies

| Strategy | Best For | How |
|----------|----------|-----|
| **Plugin Install** | Quick start, everything at once | `/plugin marketplace add affaan-m/everything-claude-code` |
| **Manual Selective** | Cherry-picking components | Copy only what you need from specific directories |
| **Installer Script** | Language-specific setup | `./install.sh typescript python` |

### 6.2 Immediate High-Value Practices

1. **Token Optimization Settings** — Add to `~/.claude/settings.json`:
   ```json
   {
     "model": "sonnet",
     "env": {
       "MAX_THINKING_TOKENS": "10000",
       "CLAUDE_AUTOCOMPACT_PCT_OVERRIDE": "50"
     }
   }
   ```

2. **Use `/plan` before any complex feature** — This engages the planner agent to create a proper implementation blueprint before writing code.

3. **Use `/tdd` for all new features** — Enforces test-first development with 80%+ coverage.

4. **Use `/code-review` after every significant change** — Catches quality and security issues immediately.

5. **Keep MCP count low** — Under 10 enabled, under 80 tools active. Each MCP eats context tokens.

6. **Use `/compact` at logical breakpoints** — After research, after milestones, after debugging. Not mid-implementation.

### 6.3 Workflows to Master First

**New Feature Workflow**:
```
/plan "Add user authentication"    → planner creates blueprint
/tdd                                → write tests first, then implement
/code-review                        → quality check
/e2e                                → E2E tests for critical flows
```

**Bug Fix Workflow**:
```
/tdd                                → write failing test reproducing bug
                                    → implement fix, verify test passes
/code-review                        → check for regressions
```

**Production Prep Workflow**:
```
npx ecc-agentshield scan            → security audit
/e2e                                → critical user flow tests
/test-coverage                      → verify 80%+ coverage
```

### 6.4 Customization Path

1. **Start with core rules**: Install `rules/common/` + your language-specific rules
2. **Add agents you'll use**: Start with planner, code-reviewer, tdd-guide
3. **Add skills for your stack**: Pick 5-10 relevant skills
4. **Set up key hooks**: Auto-format, typecheck, console.log warnings
5. **Create your own skills**: Use `/skill-create` to extract patterns from your Git history
6. **Build continuous learning**: Set up `continuous-learning-v2` to auto-learn from sessions

### 6.5 Advanced Usage

- **Instinct System**: Use `/instinct-status`, `/instinct-import`, `/instinct-export`, `/evolve` to build personalized AI instincts
- **Multi-Agent Orchestration**: Use `/multi-plan`, `/multi-execute`, `/orchestrate` for complex parallel work
- **Session Management**: Use `/sessions`, `/save-session`, `/resume-session` for long-running projects
- **Dynamic Contexts**: Create aliases for different modes:
  ```bash
  alias claude-dev='claude --system-prompt "$(cat ~/.claude/contexts/dev.md)"'
  alias claude-review='claude --system-prompt "$(cat ~/.claude/contexts/review.md)"'
  ```

---

## 7. Key Concepts to Understand

| Concept | What | Why It Matters |
|---------|------|----------------|
| **Context Window** | 200k tokens, but MCPs/tools reduce effective capacity | Must manage carefully to avoid degraded performance |
| **Token Optimization** | Choose right model per task (Haiku→cheap, Sonnet→balanced, Opus→deep) | 60-70% cost reduction possible |
| **Immutability** | Never mutate objects; always create new copies | Core coding principle enforced across all rules |
| **TDD** | Write test first (RED→GREEN→REFACTOR) | Mandatory 80%+ coverage |
| **Strategic Compaction** | Compact at logical breakpoints, not automatically | Preserves crucial context during complex work |
| **Subagent Scoping** | Give subagents limited tools and permissions | Focused execution, lower cost, security isolation |
| **OWASP Agentic Top 10** | Security risks specific to AI agents | Essential knowledge for secure agent deployment |
| **Least Agency** | Grant minimum autonomy needed for a task | Central security principle |

---

## 8. Testing the Repo

```bash
# Run all tests
node tests/run-all.js

# Run individual test files
node tests/lib/utils.test.js
node tests/lib/package-manager.test.js
node tests/hooks/hooks.test.js
```

---

## 9. Key Files for Quick Reference

| Need | File |
|------|------|
| What the repo does | `README.md` |
| Core principles | `AGENTS.md` |
| Getting started | `the-shortform-guide.md` |
| Advanced techniques | `the-longform-guide.md` |
| Security practices | `the-security-guide.md` |
| How to contribute | `CONTRIBUTING.md` |
| Troubleshooting | `TROUBLESHOOTING.md` |
| Changelog | `CHANGELOG.md` |
| Hook configuration | `hooks/hooks.json` |
| MCP setup | `mcp-configs/mcp-servers.json` |
| Rules README | `rules/README.md` |
| Example configs | `examples/` directory |
| Token optimization | `docs/token-optimization.md` |

---

## 10. Community and Ecosystem

- **AgentShield** — Security scanner (`npx ecc-agentshield scan`) — 102 rules, 1282 tests
- **Plankton** — Write-time code quality enforcement via hooks
- **GitHub App** — Install at [github.com/marketplace/ecc-tools](https://github.com/marketplace/ecc-tools)
- **Skill Creator** — Generate skills from git history (`/skill-create`)
- **npm packages** — `ecc-universal` (OpenCode plugin), `ecc-agentshield` (security)
- **Contributing** — See `CONTRIBUTING.md` for PR templates per contribution type

---

*Document generated on 2026-03-15 by studying the entire everything-claude-code repository structure, all four guides, agent definitions, skills catalog, command list, hooks configuration, rules architecture, cross-platform configs, scripts, schemas, and documentation.*
