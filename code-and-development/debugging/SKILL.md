---
name: debugging
description: "Systematically diagnose and fix software bugs by analyzing error messages, stack traces, logs, and runtime behavior across multiple languages. Follows a structured reproduce-isolate-diagnose-fix-verify process to find root causes and produce reliable corrections. Use when investigating error messages, analyzing stack traces, diagnosing runtime failures, fixing race conditions, or resolving memory leaks."
license: MIT
metadata:
  author: awesome-ai-agent-skills contributors
  version: 1.0.0
---

# Debugging

This skill equips an AI agent with a systematic methodology for diagnosing and resolving software bugs. Rather than guessing at fixes, the agent follows a structured process — reproduce, isolate, diagnose, fix, verify — to find root causes and produce reliable corrections. It handles a wide range of bug categories including logic errors, runtime exceptions, race conditions, memory leaks, and performance regressions across multiple languages and runtime environments.

## Workflow

1. **Reproduce the problem.** Gather the exact error message, stack trace, and logs. Identify the minimum input or steps that trigger the issue. Note environmental conditions for intermittent bugs.

2. **Isolate the fault location.** Use the stack trace to narrow down the responsible code region. Trace data flow backward from the failure point. For large codebases, use binary search — disable half the system and check if the bug persists.

3. **Diagnose the root cause.** Distinguish symptoms from causes — a NullPointerException is a symptom; a missing validation upstream is the cause. Common roots: incorrect input assumptions, concurrent state mutation, stale caches, missing `await`, dependency version mismatches.

4. **Develop and apply the fix.** Write the smallest change addressing the root cause. Trace all callers if changing a shared interface. Prefer defensive fixes that handle the error class broadly over narrow patches.

5. **Verify and prevent regression.** Re-run reproduction steps, write a regression test encoding the failure, and confirm existing tests still pass.

## Supported Technologies

| Category          | Tools and Techniques                                              |
|-------------------|-------------------------------------------------------------------|
| Stack traces      | Python tracebacks, Java/JS stack traces, Go panic output, Rust backtraces |
| Logging           | Python `logging`, JavaScript `console`, structured JSON logs      |
| Debuggers         | `pdb` / `ipdb`, Chrome DevTools, `gdb` / `lldb`, `dlv` (Go)     |
| Profiling         | `cProfile`, `py-spy`, Chrome Performance tab, `pprof`            |
| Memory analysis   | `tracemalloc`, `heapq`, Valgrind, Chrome Heap Snapshots          |
| Concurrency       | Thread dumps, `asyncio` debug mode, Go race detector (`-race`)   |

## Examples

### Example 1 — Debugging a race condition in Python async code

**Bug report:** "Sometimes the response is missing the `user_profile` field, but only under load."

Buggy code in `src/api/handler.py`:

```python
import asyncio
import aiohttp

user_cache = {}

async def fetch_user(session, user_id):
    if user_id in user_cache:
        return user_cache[user_id]
    async with session.get(f"https://api.example.com/users/{user_id}") as resp:
        data = await resp.json()
    user_cache[user_id] = data
    return data

async def build_response(user_id):
    async with aiohttp.ClientSession() as session:
        profile, orders = await asyncio.gather(
            fetch_user(session, user_id),
            fetch_orders(session, user_id),
        )
    return {"user_profile": profile, "orders": orders}
```

**Agent diagnosis:**

The `user_cache` dictionary is shared mutable state accessed by concurrent coroutines without synchronization. When two requests for the same `user_id` arrive simultaneously, both see a cache miss, both issue HTTP requests, and the second write may overwrite the first with a partially different object. More critically, dictionary mutation during concurrent iteration can produce `RuntimeError` on Python 3.

**Root cause:** Unsynchronized shared mutable state in a concurrent context.

**Fix:**

```python
import asyncio
import aiohttp

user_cache = {}
cache_locks = {}
global_lock = asyncio.Lock()

async def fetch_user(session, user_id):
    async with global_lock:
        if user_id not in cache_locks:
            cache_locks[user_id] = asyncio.Lock()
        lock = cache_locks[user_id]

    async with lock:
        if user_id in user_cache:
            return user_cache[user_id]
        async with session.get(f"https://api.example.com/users/{user_id}") as resp:
            data = await resp.json()
        user_cache[user_id] = data
        return data
```

The per-key lock ensures only one coroutine fetches a given user at a time. Others wait and then read from the cache.

### Example 2 — Debugging a memory leak in a Node.js server

**Bug report:** "Server memory usage grows from 150 MB to 2 GB over 24 hours, then crashes with OOM."

Buggy code in `src/server.js`:

```javascript
const express = require("express");
const app = express();

const requestLog = [];

app.use((req, res, next) => {
  requestLog.push({
    method: req.method,
    url: req.url,
    headers: { ...req.headers },
    timestamp: new Date(),
  });
  next();
});

app.get("/health", (req, res) => {
  res.json({ status: "ok", requestCount: requestLog.length });
});

app.listen(3000);
```

**Agent diagnosis:**

The `requestLog` array is a module-level variable that grows without bound. Every incoming request appends an object containing a full copy of the request headers. At 1000 requests per minute with an average header size of 2 KB, this accumulates roughly 2.8 GB per day — matching the reported OOM timeline.

**Root cause:** Unbounded in-memory array that is never pruned or rotated.

**Fix:**

```javascript
const express = require("express");
const app = express();

const MAX_LOG_SIZE = 10000;
const requestLog = [];

app.use((req, res, next) => {
  if (requestLog.length >= MAX_LOG_SIZE) {
    requestLog.shift();
  }
  requestLog.push({
    method: req.method,
    url: req.url,
    timestamp: new Date(),
  });
  next();
});
```

Key changes: (1) cap the array at a fixed size and evict the oldest entry, (2) stop storing full headers — log only what is needed, (3) for production use, replace the in-memory array with a proper logging pipeline (e.g., write to a log file or send to an external service).

**Verification:** Run a load test with `autocannon -d 60 http://localhost:3000/health` and monitor memory via `process.memoryUsage()`. Memory should plateau at the cap size rather than climbing linearly.

## Best Practices

- **Check recent changes first.** If the bug appeared after a specific deployment or commit, `git bisect` or reviewing the recent diff is often the fastest path to the root cause.
- **Change one thing at a time.** When testing a hypothesis, make a single modification and re-run to isolate which change had the effect.
- **Write a regression test.** Every fixed bug should produce a test case that fails before the fix and passes after.

## Edge Cases

- **Heisenbugs:** Use logging instead of interactive debuggers when bugs disappear under observation. Run with the language's race detector if available.
- **Environment-specific bugs:** Reproduce with matching constraints (Docker with memory limits, same OS version) when bugs only appear in production.
- **Third-party library bugs:** Check changelogs and issue trackers before recommending upgrades, workarounds, or version pins.
- **Corrupted state:** Examine data alongside code when bugs involve half-written records or inconsistent state.
