---
name: obsidian-knowledge-brain
description: An AI agent skill that remembers every technical decision and bug fix across sessions, builds a searchable knowledge base, and evolves project rules automatically.
license: MIT
---

# Obsidian Knowledge Brain v4.0 / Obsidian 知识大脑 v4.0

**Schema**: 4.0 | **Lines**: ≤200 | **Load**: Always (if skill active)
**Platforms**: **Claude Code** — full auto (hooks + cron). **Cursor / Gemini CLI / Codex** — manual trigger (type "收尾" to save, "诊断" to bootstrap). Requires an AI Agent with file read/write. Not designed for plain-terminal or Agent-free use. / CC 全自动，其他平台需手动输入口令触发。

**Upgrade from v2.0**: zero vault dependency (无 vault 依赖), project-local `.claude/` storage. Obsidian is now optional — open your project folder as a vault for knowledge graph visualization. / Obsidian 现为可选——将项目文件夹作为 vault 打开即可获得知识图谱可视化。

**What this does / 它做什么**: Every time you debug an error or make a technical decision with an AI agent, that knowledge vanishes when the session ends. This skill **remembers** — it captures your decisions and error fixes across sessions, builds a searchable knowledge base, and evolves project rules automatically. A personal project librarian that learns from every conversation. / 每次和 AI 编程解决了 bug、做了技术决策，下次对话就忘了。这个 Skill 帮你**记住**——自动捕获每次会话的决策和错误，构建可检索的知识库，持续进化项目规则。一个从每次对话中学习的项目图书管理员。

**Obsidian?** Not required. v4.0 stores knowledge as `.md` files in your agent directory. Open your project as an Obsidian vault to browse the knowledge graph — purely optional. See §0a. / 非必需。用 Obsidian 打开项目文件夹即可浏览知识图谱——完全可选。

→ **First time?** See `references/quickstart.md` (5-minute walkthrough / 5分钟上手).

## 0. Critical Rules / 关键规则 (Priority 0)

**v4.0 dual rule / 双规则**:

1. **[ERROR:] stubs — IMMEDIATE after fix / 修复后立即记录。** After resolving ANY error, BEFORE writing the permanent fix, append a one-line stub to `memory/_phase1_inbox.md`:
   `[ERROR: type=<from-taxonomy> | resolution=<fix> | project: <slug>]`
   This is the FINAL step of every error fix. NOT deferred to session end. Skipping this and hitting the same error again → `[ERROR: type=missed-record | error_type=<type>]`.

2. **[DECISION:] annotations — session end only / 仅会话结束时。** Do NOT interrupt work to annotate decisions mid-session. Work normally. At session end (T2 "收尾"), extract ALL technical decisions from the session transcript into `[DECISION:]` format. This is a memory system — it learns from completed experiences, not live interruptions.

Format: `[DECISION: <summary> | context: <why> | project: <slug> | scope: project|cross-project]` and `[ERROR: type=<from-taxonomy> | resolution=<fix> | project: <slug>]`. Missing required fields → mark `# MVA_FAIL:<field>` and leave in inbox.

## 0a. Prerequisites / 环境要求

**Required / 必需**: An AI Agent platform (Claude Code, Cursor, Gemini CLI, Codex) with file read/write capability + a project directory. / 一个有文件读写能力的 AI Agent 平台 + 一个项目目录。

**Recommended / 推荐**: Python 3.x (for hook scripts; all protocols work manually without it) + Git (version-control your knowledge base). / Python 3.x（钩子脚本）+ Git（版本控制）。

**Obsidian?** Not required. v4.0 stores knowledge as plain `.md` in your agent directory. Open your project folder as an Obsidian vault to browse the knowledge graph — purely optional. v2.0 users: old vault data preserved in `archive/`. / 非必需。v4.0 用纯 `.md` 存储，用 Obsidian 打开项目文件夹即可浏览知识图谱——完全可选。

## 0b. Sandbox Boundary / 沙箱边界

**Project scope / 项目范围**: This skill reads and writes within `<project>/{AGENT_DIR}/` and `<project>/archive/`. No other project directories are modified. / 仅触碰项目内的 Agent 目录和 archive/。

**Global store / 全局存储 (v4.0)**: `~/.obsidian-knowledge-brain/` — a single, well-known directory outside the project. Contains `atoms.json` (global atom pointer table, ≤20 active atoms), `atoms.json.bak` (write-backup), and `atoms.json.lock` (concurrent write guard). Written ONLY during install/uninstall/promotion. During normal Agent sessions, atoms.json receives ONLY `last_triggered` timestamp updates when atoms are matched (metadata, not knowledge modification). All other writes are promotion-only. Read during Pre-action sync. No other paths outside the project are touched. / 全局存储目录，仅在安装/卸载/晋升时写入，正常会话只更新 last_triggered 时间戳。

**Uninstall / 卸载**: `--uninstall` flag creates `.uninstalled` marker → Pre-action instruction removed from always-loaded file → `_global_atoms` removed from keyword index → atoms.json preserved (user may reinstall). / 卸载时保留 atoms.json 以备重新安装。

## 0c. Known Limitations / 已知局限 (Agent: read before acting)

**L1 — Pre-action is MUST, not hook.** You are responsible for executing Pre/During/Post steps from the injected instruction. Skip Pre + hit documented pitfall → `[ERROR: type=missed-atom | atom_id=<id>]`. Skip Post error recording → `[ERROR: type=missed-record | error_type=<type>]`.

**L2 — Gemini CLI / Codex always-loaded files unverified.** `.gemini/extensions.json` and `.codex/codex.yaml` are listed but NOT tested. On these platforms, verify the file is actually loaded by your platform. If not → read `~/.obsidian-knowledge-brain/atoms.json` directly.

**L3 — JSON array-top-level not supported for injection.** `pre_action.py` assumes `{` object-top-level. Unreachable in practice (all known platforms use Markdown/YAML/plain). If encountered → skip injection, note it.

**L4 — install.py version mismatch warns but doesn't exit.** If SKILL.md schema ≠ install.py version → stop, ask user to resolve.

**L5 — Cross-machine atoms.json is manual.** Each machine has its own `~/` atoms.json. Machines converge: same root_cause_id → same content-hash atom ID. To sync manually, copy `~/.obsidian-knowledge-brain/atoms.json`.

**L6 — Dual-platform: shared atoms.json, independent keyword indexes.** If `.claude/` + `.cursor/` coexist → run install.py for each. Pre-action does NOT auto-appear in both.

**L7 — Non-CC platforms: T1/T2/T3 are manual.** Pre-action still auto (in always-loaded file). But session-start, "收尾", "健康检查" require user trigger words. Remind user at appropriate moments.

**L8 — Pointer drift.** Atom pointers (`rules/foo.md#L6-L8`) may go stale. Pre-action: lines mismatch topic → load entire file. T3: file missing → flag `pointer_broken: true`. Not auto-repaired — note drift for next T2/T3.

**L9 — Recovery from `_global_atoms` loses metadata.** Both atoms.json + .bak corrupt → rebuild from `_global_atoms`. Recovers IDs/types/phases/pointers/triggers. Loses `project_origin` (→`[current]`), `promoted` (→now), `demoted` (→false). T3 flags as "recovered, needs review."

### Platform Matrix / 平台矩阵

| | Claude Code | Cursor / Gemini CLI / Codex |
|---|------------|---------------------------|
| Pre-action | ✅ Auto | ✅ Auto (if always-loaded file exists) |
| T1/T2/T3 | ✅ Hook/Cron auto | ○ Manual: user trigger words |
| Promotion | ✅ T2 auto | ○ Manual: Agent prompts during T2 |
| install.py | ✅ `python scripts/install.py` | ✅ `--platform <X>` |

○ = remind user.

## 1. Phase Detection / 相位检测 (Execute FIRST)

Check `.claude/PHASE_A_COMPLETE`:
- Exists + `status: complete` + `bootstrap_date` ≤90 days → Phase B (skip bootstrap)
- Exists + `status: complete` + >90 days → re-validate 6 checklist items; pass→refresh date; fail→re-diagnose
- Exists + `status: in_progress` → re-run all 6 checks (marker only stores overall result, no per-item state)
- Corrupt YAML / missing fields → re-diagnose

3-axis check: `.claude/rules/` (≥8 valid-frontmatter files?) + `.claude/projects/` (≥1?) + `.claude/memory/` (pitfalls/ decisions/ preferences/ reference/ subdirs?). 3 green → Phase B. Any yellow/red → Phase A incremental. 2+ red → Phase A full bootstrap.

## 2. Phase A · Framework Bootstrap / 框架播种

→ Full instructions: `references/phase-a-bootstrap.md`

Summary: Diagnose chaos score (混沌度 0-12) → legacy automation audit (遗留自动化审计, reduced if chaos≤3) → classify raw content (parallel 3-tag labeling: IS_RULE/IS_PROJECT/IS_MEMORY) → build skeleton (CLAUDE.md + rules/ + projects/ + memory/) → migrate originals to archive/ → validate 6-item checklist → create `PHASE_A_COMPLETE` marker.

## 3. T1-T4 Trigger Contracts / 触发契约

### T1 · Session Start / 会话启动 (Required)
→ `references/t1-session-start.md`

5-step protocol: crash detection → T2 completion guard → inbox drain (MECE classify ALL annotations, always; pattern extraction gated by cold-start counter) → health summary → project briefing (≤30 lines, bilingual). Writes `.session_active` new marker.

### T2 · Session End / 会话结束 (Required)
→ `references/t2-session-end.md`

Safety net: F2 PRIMARY (user says "收尾" — the ONLY guarantee on all platforms). F1 auto on CC only. F4 catches crashes from inbox residue. No F3 (auto-checkpoint has no implementation — LLMs cannot count their own tool calls). Phase 1 quick close (① decisions ② errors ③ status ④ rule trigger update ⑤ ceiling check). Phase 2 deferred (⑥ rules created ⑦ rules outdated). MVA check before write. Anti-pollution. Delete `.session_active`. Emit `[SESSION_SUMMARY]`.

### T3 · Periodic Health Check / 定期健康检查 (Recommended)
→ `references/t3-periodic-check.md`

Trigger: L1 cron / L2 T1 detects >7 days / L3 user口令. Concurrent guard: skip if `.session_active` present. 7-dim scan (hard ceiling, contradiction, orphan, GC, pattern extraction Tier 1→2→3, index rebuild, legacy back-pressure). Tier 2 default OFF. ROI tracking: `hit_rate = 0` × 30 days → auto-degrade to cold-start.

### T4 · Manual Invoke / 手动调用 (On-demand)

| 中文 / English | Agent Action |
|---|---|
| "诊断" / "diagnose" | Phase A Pass 1 (READ-ONLY): scan project → chaos score + plan. No files modified. |
| "整理项目" / "bootstrap" | Phase A full: diagnose → plan → [confirm] → build → migrate → validate |
| "继续播种" / "resume bootstrap" | Resume interrupted Phase A from last checkpoint |
| "收尾" / "wrap up" | T2 F2: Phase 1 quick close (3-step) → write memory → [SESSION_SUMMARY] |
| "健康检查" / "health check" | T3 full 7-dim scan → HEALTH_REPORT.md |
| "规则审计" / "rule audit" | Rules-only: contradiction, staleness, ceiling, GC |
| "记忆整理" / "memory cleanup" | MECE re-classify inbox → memory/ + dedup merge |
| "重建索引" / "rebuild index" | Rebuild _keyword_index.json + CLAUDE.md index tables |
| "Skill 状态" / "skill status" | Output: Phase A/B state, inbox backlog, last health check, cold-start progress |

## 4. Annotation MVA Standards / 标注最低可行标准

| Annotation | Required Fields | Missing → |
|-----------|----------------|-----------|
| `[DECISION:]` | summary + context + project | `# MVA_FAIL:<field>`, stay in inbox |
| `[ERROR:]` | type (from error-taxonomy) + resolution + project | same |
| `[SESSION_SUMMARY]` | decisions + errors + rules_triggered | same |

Quality target: ≥90% field completeness. 3 consecutive sessions <90% → T3 warns.

**Anti-pollution (反污染)**: ① [DECISION:] store only FINAL adopted solutions, never dead-end explorations. ② [ERROR:] only FIXED errors; UNRESOLVED → inbox. ③ No intermediate states (不存中间态): temporary judgments, unverified hypotheses → do NOT annotate. ④ No duplicates: same type+root_cause_id → increment `sessions_observed` counter, no new file.

## 5. Cold Start Protocol / 冷启动协议

`memory/` empty or `mode: cold_start`: classify+store only, no pattern extraction. Counter in `_phase1_inbox.md` YAML frontmatter (`cold_start: {total_annotations, sessions_observed, threshold: 20, mode}`). ≥20 annotations AND ≥3 sessions → switch `mode: active`, announce transition.

## 6. File Manifest / 文件清单

```
<templates/> 4 files     → Agent uses these to create rules/projects/pitfalls/decisions
<references/> 10 files   → Agent loads on-demand per trigger/phase (each ≤80 lines)
  ├── Seed data:    error-taxonomy.md, root-cause-kb.md, domain-registry.md
  ├── Protocols:    t1-session-start.md, t2-session-end.md, t3-periodic-check.md
  ├── Bootstrap:    phase-a-bootstrap.md
  ├── User guides:  quickstart.md, platform-guide.md, troubleshooting.md
SKILL.md                 → Always loaded (≤200 lines)
```

## 7. Install & Config / 安装与配置

### Where to put files / 文件放哪里
Copy `obsidian-knowledge-brain/` into `<project>/.claude/skills/`. For non-Claude-Code platforms, run: `python scripts/install.py --platform cursor` (or `gemini`, `codex`). This replaces all `.claude/` paths with your platform's base directory. / 复制到 skill 目录后，非 CC 平台运行 `python scripts/install.py --platform cursor` 一键替换路径。

### Hook config (Claude Code only, optional) / 钩子配置
Claude Code `settings.json`:
- `SessionStart` → `session_start.py` (T1)
- `Stop` → `session_close.py --prompt` (T2)
- `CronCreate` weekly → `maintainer.py --health-check` (T3)

### No-hook / no-Agent fallback / 无钩子降级
If your platform has no hooks or no Agent: T1 via manually reading SKILL.md §0. T2 via typing "收尾" / "wrap up". T3 via typing "健康检查" / "health check". F3 auto-checkpoints still work if your Agent supports them. Core knowledge capture works even without hooks. / 即使没有钩子，核心知识捕获仍可通过口令手动触发。

### English-only users / 纯英语用户
All labels and headings are bilingual (Chinese + English). If you read only English, the `/ 中文` suffix is a term annotation — you can ignore it. The body text is English-primary. See §8 for term translations if curious. / 所有标签中英双语，纯英语读者可忽略 `/ 中文` 后缀，正文以英语为主。

### v4.0 Global Atom Table / 全局原子表
The global atom table lives at `~/.obsidian-knowledge-brain/atoms.json`. It is created automatically by `install.py` or Phase A bootstrap. Cross-project knowledge is promoted here when the same error occurs in ≥2 independent projects. See `references/t2-session-end.md` §②b for promotion protocol. / 全局原子表位于 `~/.obsidian-knowledge-brain/atoms.json`，同一错误在 ≥2 个独立项目中复现时晋升到此。

## 8. FAQ / 常见问题

**Q: Nothing happens when I install. / 安装后没反应。** A: Agent auto-loads and runs §1. No Agent → manually follow §0 and §3. The skill is a protocol, not a daemon. More recovery scenarios: `references/troubleshooting.md`.

**Q: Why `.claude/`? I use Cursor. / 为什么是 `.claude/`？** A: Replace with `.cursor/` (see `references/platform-guide.md`). The folder name is convention — structure works on any platform.

**Q: How long until useful? / 多久见效？** A: ~3 sessions × ~7 annotations → 20 total → pattern extraction activates. Before that, everything is still stored — just no auto-detection yet.

**Q: Can I use this without any Agent? / 没 Agent 能用？** A: No. This skill requires an AI Agent to execute MECE classification, cold-start counting, and pattern extraction. Without an Agent, you have empty directories and unused templates — not a functioning knowledge system. See `references/platform-guide.md` for supported platforms. / 不行，此 Skill 需要 AI Agent 执行协议。

## 9. Bilingual Terminology / 中英术语对照

| English | 中文 | English | 中文 |
|---------|------|---------|------|
| Framework Skeleton | 框架骨架 | Memory Engine | 记忆引擎 |
| Trigger Contract | 触发契约 | Annotation | 标注 |
| Chaos Score | 混沌度 | Cold Start | 冷启动 |
| MECE Classification | 互斥穷尽分类 | Pattern Extraction | 模式提取 |
| Root Cause KB | 根因知识库 | Error Taxonomy | 错误分类法 |
| Pitfall | 陷阱 | Decision | 决策 |
| Health Check | 健康检查 | Bootstrap | 播种/减负 |
| Deferred Audit | 延迟审计 | Safety Net | 兜底/安全网 |
