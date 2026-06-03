# gald3r Readiness Report — Kimi Code CLI

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** Kimi Code CLI (Moonshot AI) exposes a native host for
nearly the entire gald3r primitive set — commands, rules, agents, skills, hooks, and MCP all
map onto first-class mechanisms. Its Agent Skills engine even reads `.claude/skills` and
`.codex/skills` directly, so gald3r's `SKILL.md` library installs without translation.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | User-authored Agent Skills invoke as `/skill:<name>` and `/flow:<name>`; Custom Plugins declare executable tools via `plugin.json` | No standalone top-level slash-command file — gald3r's `@g-*` commands install as Skills, not a dedicated command system |
| **R** | Rules | ✅ | `AGENTS.md` (via `/init`) injected into the system prompt through `KIMI_AGENTS_MD` as always-on session context | None — gald3r rules load here as a first-class project instruction file |
| **A** | Agents | ✅ | Built-in `coder` / `explore` / `plan` subagents; custom agent/subagent YAML specs via `--agent-file`, with `extend`, tools, and a `subagents` block | None of substance — gald3r's `g-agnt-*` roles map to native custom agent specs |
| **S** | Skills | ✅ | Native `SKILL.md` (YAML frontmatter + Markdown); discovery reads `.kimi/skills`, **`.claude/skills`**, **`.codex/skills`**, `.agents/skills` | None — directly compatible with the gald3r Agent Skills standard, no port required |
| **H** | Hooks | ✅ | 13 lifecycle events (SessionStart, PreToolUse, PostToolUse, Stop, PreCompact, …) in `~/.kimi/config.toml` via `[[hooks]]`; JSON on stdin, exit 2 = block | Hooks are Beta — config schema may change; gald3r's `g-hk-*` wiring fits but rides a moving target |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native Model Context Protocol support via the `kimi mcp`
sub-command group and the AI-native `/mcp-config` flow (add / edit / authenticate servers
conversationally, no hand-edited JSON) — gald3r's MCP backend connects directly.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Flow skills / Agent Flow (`type: flow`, Mermaid/D2, `/flow:<name>`) | ⚙️ needs customization | Authoring `type: flow` skills could express gald3r `g-go-*` multi-step pipelines as native diagrams |
| Custom Plugins (Beta) — `plugin.json` executable tools (Python/TS/shell) | ⚙️ needs customization | A real automation entry point; gald3r tooling could ship as invokable plugin tools (Beta caveat) |
| Cross-tool skill dirs (`.claude/skills` + `.codex/skills` honored) | ✅ present | gald3r skill library is read as-is with zero per-platform copies |
| OpenAI- / Anthropic-compatible endpoints + ACP integration (JetBrains, Zed) | ✅ present | Extra surfaces for gald3r model orchestration; no gald3r work required |

## The ceiling, and what's beyond it

gald3r runs at full strength on this platform — commands, rules, agents, skills, and hooks all map onto native mechanisms, so the framework installs without compromise. As third-party adaptation goes, this is the high end: nothing here has to be approximated.

But adaptation, however clean, is still gald3r living as a guest inside someone else's tool. The native build goes further — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where these primitives aren't mapped onto a host, they *are* the substrate. Same framework, no host in between.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
