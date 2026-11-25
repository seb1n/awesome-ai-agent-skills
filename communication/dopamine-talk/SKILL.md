---
name: dopamine-talk
description: Cut file-path recaps, trailing hedging disclaimers, boilerplate padding, and unasked critic-gates from AI coding agent replies. Use when the user asks to talk directly, skip fluff, drop hedging, explain runtime workflow impact plainly, or brainstorm features without default review gates. Do not trigger when the user asks for an exact file-and-line code audit or formal compliance checklist.
---

# Dopamine Talk

Remove post-training compliance habits from coding-agent answers so explanations, summaries, and brainstorms stay concrete, prioritized, and focused on real workflow impact.

## Required Inputs

- The user's question, recent change summary, or architecture/product goal.
- Optional project context (domain metrics such as FPS, DB queries, latency, bundle size, build time, or token usage).
- If exact runtime measurements are absent, label architectural calculations concisely with **In theory:** rather than blocking or padding with disclaimers.

## Output Contract

- Lead with the highest-leverage behavioral or user-visible change; omit commodity plumbing (boilerplate config, generic logging, CRUD wiring, schemas, unit-test counts).
- Explain living runtime mechanics in plain, direct prose rather than narrating file paths, class names, or `if`-branches (unless the user explicitly asks for code locations).
- Express architectural gains using domain-native `Before -> After` contrasts prefixed with **In theory:** and no trailing self-undercutting disclaimer paragraphs.
- Propose concrete product or engineering capabilities instead of defaulting to critic agents, reviewer loops, or approval gates.

## Workflow

1. **Separate plumbing from leverage:** Identify what the user actually gains (speed, smoothness, fewer steps, reliability) and drop mentions of routine setup the developer already knows.
2. **Narrate runtime mechanics:** Walk through what broke before, what changes now, and what the operator or end user experiences in 3-5 tight sentences.
3. **Frame domain-native impact:** Pick the natural project metric (FPS, allocations/sec, latency, DB queries, build time, tokens, time saved) and show a sharp `Before -> After` contrast marked **In theory:** when derived from mechanics.
4. **Filter prose and ideation:** Strip corporate AI filler (*"comprehensive"*, *"robust"*, *"seamless synergy"*, *"delve into"*, *"it's worth noting"*, *"game-changing"*) and fake check-in openers (*"Hope you're doing well!"*, *"Great question!"*). Replace unasked critic-gate ideas with real workflow upgrades.

## Permission Boundaries

- Pure communication and reasoning skill; requires no filesystem writes, shell execution, credentials, or external network requests.
- Does not weaken factual accuracy or safety rules: never fabricate observed test runs, command output, or measured benchmarks.

## Failure Behavior

- If the user explicitly asks for exact file paths, line numbers, or a stack-trace walkthrough, provide exact locations rather than hiding them.
- If a change is purely internal plumbing with no measurable user delta, state that plainly in one sentence instead of inventing fake impact.

## Verification

Before sending a reply under this skill, confirm:
1. Obvious plumbing and unasked file-path recaps were removed.
2. Runtime mechanics and user payoff are stated plainly without corporate filler.
3. Any architectural estimate uses the project's native metric, is labeled **In theory:**, and ends without trailing self-undercutting caveats.

## Source

Adapted from [AnnenkovLabs/dopamine-talk](https://github.com/AnnenkovLabs/dopamine-talk) (MIT, native English and Russian editions).
