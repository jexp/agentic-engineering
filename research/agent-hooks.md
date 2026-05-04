  ---
  Hooks Comparison: Claude Code vs Cursor vs Kiro vs Cline

  TL;DR

  Claude Code and Cursor are nearly identical in architecture — same event
  names, same exit-code semantics, same JSON protocol. Kiro is a simplified
  UI-first take. Cline is a middle ground — structured protocol but far fewer
   events and no advanced types.

  ---
  Where All Four Converge

  All four share these fundamentals:
  - stdin JSON in, stdout JSON out as the wire protocol
  - Exit 2 = block/cancel semantics (Kiro uses a JSON field instead)
  - Pre/post tool use events
  - Shell commands as the universal hook primitive
  - Project-level config that can be version-controlled

  ---
  Claude Code vs Cursor (Strikingly Similar)

  These two share the same architecture and even identical field names
  (preToolUse, postToolUse, sessionStart, subagentStart, stop, etc.). They
  were clearly influenced by each other or a common design.

  Claude Code-only capabilities:
  - HTTP hooks — POST to remote endpoints
  - MCP tool hooks — call connected MCP servers directly from a hook
  - Agent hooks — subagent-based verification with full tool access (Cursor's
   prompt hooks are single-turn LLM only)
  - updatedInput — hooks can modify tool inputs mid-flight before execution
  - async + asyncRewake — background hooks that can re-wake Claude on
  completion
  - defer permission — pause for external UI handling
  - More events (~20+ vs ~18): FileChanged, WorktreeCreate/Remove,
  PermissionRequest/Denied, Elicitation, Compaction, StopFailure,
  TaskStart/Stop

  Cursor-only capabilities:
  - Tab vs Agent separation — distinct hook policies for inline completions
  vs chat agent
  - Enterprise team distribution — cloud-push hooks to all team members
  - failClosed flag — explicit per-hook fail-closed (vs relying on exit code)
  - loop_limit — cap on auto-continue iterations
  - Pre-built partner integrations — vendor-provided security/governance
  hooks

  ---
  Kiro (Most Different — Product Feature, Not Developer API)

  Kiro takes a fundamentally different philosophy. Hooks are an automation
  UX, not an extension protocol:

  - You create hooks via a UI panel or by asking the agent in natural
  language
  - Only two action types: agent prompt or shell command
  - No structured output protocol beyond cancel
  - No input modification, no permission decisions, no regex matchers
  - Target: convenience automation for any user, not tooling for power users

  ---
  Cline (Middle Ground — Structured but Simpler)

  Cline uses the same JSON stdin/stdout philosophy as Claude/Cursor but is
  much narrower:

  - 8 events vs Claude's 20+ — covers basics, misses file watching, MCP
  events, worktrees, compaction
  - Scripts only — no HTTP, no MCP tool calls, no LLM-as-hook
  - No input modification — can cancel or inject context, cannot mutate tool
  parameters
  - Hooks are files on disk — enabling = file exists, disabling = file
  removed (unusual; Windows can't even toggle)
  - Sequential execution: global hooks run before workspace hooks

  ---
  Summary Matrix

  ┌──────────────────┬────────────────┬───────────┬────────────┬─────────┐
  │    Dimension     │  Claude Code   │  Cursor   │    Kiro    │  Cline  │
  ├──────────────────┼────────────────┼───────────┼────────────┼─────────┤
  │ Event count      │ ~20+           │ ~18       │ ~5         │ 8       │
  ├──────────────────┼────────────────┼───────────┼────────────┼─────────┤
  │                  │ command,      │            │ agent     │        │
  │ Hook types       │ http,         │ command,   │ prompt,   │ shell  │
  │                  │ mcp_tool,     │ prompt     │ shell     │ script │
  │                  │ prompt, agent │            │           │        │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ Input mutation   │ yes           │ no         │ no        │ no      │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ Async/background │ yes           │ no         │ no        │ no      │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ Permission       │ yes           │ yes        │ no        │ no      │
  │ system           │               │            │           │         │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ LLM-as-hook      │ yes           │ yes        │ yes       │ no      │
  │                  │               │            │ (native)  │         │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ Team             │ no            │ enterprise │ no        │ no      │
  │ distribution     │               │  only      │           │         │
  ├──────────────────┼───────────────┼────────────┼───────────┼─────────┤
  │ Config UX        │ JSON files    │ JSON files │ UI-first  │ files   │
  │                  │               │            │           │ on disk │
  └──────────────────┴───────────────┴────────────┴───────────┴─────────┘

  The biggest differentiator across all four: Claude Code has the highest
  extensibility ceiling (HTTP, MCP, agent hooks, input mutation, async).
  Cursor has the strongest enterprise/team story. Kiro optimizes for
  approachability. Cline optimizes for guardrails and compliance.

  Sources

https://code.claude.com/docs/en/hooks
https://cursor.com/docs/hooks
https://kiro.dev/docs/hooks/
https://docs.cline.bot/customization/hooks