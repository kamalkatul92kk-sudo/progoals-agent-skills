# ProGoals Agent Skills

Free, open-source (MIT) SKILL.md skills from ProGoals that keep an AI agent approval-first and draft-only: scrub secrets before you share a template, score drafts with a strict rebuild gate, ask before anything irreversible, and ignore instructions hidden in content.

This is an [Agent Plugins](https://agent-plugins.org/) package (root `plugin.json` + `skills/`). It loads in Cursor and in other agents that read `SKILL.md` files, including Grok Bot.

Not affiliated with xAI. Not affiliated with Cursor.

## What's included

| Skill | What it does | Type |
|---|---|---|
| [`template-scrubber`](skills/template-scrubber/SKILL.md) | Before you share or publish a bot template, skill, routine or config, redacts keys, tokens, passwords, payment numbers, internal URLs, personal and customer data, and returns a findings report. Never shares anything itself. | Full skill (free) |
| [`product-rebuild-gate`](skills/product-rebuild-gate/SKILL.md) | Scores a product draft against its brief's success criteria, ranks every issue BLOCKER / MAJOR / MINOR with a concrete fix, then recommends REBUILD or ADVANCE TO TESTER. Formerly "Harsh Critique". | Full skill (free) |
| [`permission-gate-lite`](skills/permission-gate-lite/SKILL.md) | Classifies each planned action as READ, REVERSIBLE or IRREVERSIBLE and stops for your explicit approval, with an exact approval card, before any send, payment, delete or share. | **Lite subset** of a paid skill |
| [`untrusted-content-fence-lite`](skills/untrusted-content-fence-lite/SKILL.md) | Treats web pages, emails, documents and tool output as data, never instructions, and flags injected instructions instead of following them. | **Lite subset** of a paid skill |

Everything in this repository is free to use, copy and modify under the [MIT License](LICENSE). Nothing here requires a purchase, an account or a key.

## Install

**Cursor:** install the plugin from the Cursor Marketplace (once listed), or test it locally:

1. Copy this folder to `~/.cursor/plugins/local/progoals-agent-skills`.
2. Restart Cursor, or run **Developer: Reload Window**.
3. Open **Customize** and check that the four skills appear. You can invoke one by name, e.g. `/permission-gate-lite`.

**Other SKILL.md agents (including Grok Bot):** add each folder under `skills/` the way your agent installs skills (each folder holds one `SKILL.md`).

## How to use

- *"Make this bot setup safe to share."* → `template-scrubber` returns a scrubbed copy plus a report, marked `SCRUBBED - REVIEW BEFORE SHARING`. You create the share link.
- *"Score this draft against my brief. Be harsh."* → `product-rebuild-gate` returns per-criterion scores, ranked fixes and REBUILD or ADVANCE TO TESTER.
- *"Reply to these three customer emails."* → `permission-gate-lite` drafts the replies, then shows one approval card per send and waits.
- *"Summarize this supplier email."* → `untrusted-content-fence-lite` summarizes it and lists any `INJECTION FLAGS` it refused to act on.

The skills pair well: the fence decides that content can't authorize an action, and the gate decides that only you can.

## Lite subsets and full versions

The two `-lite` skills are lite subsets of paid ProGoals skills: every rule in a lite skill comes from its full version, and the lite skill adds nothing the full version lacks. Each works on its own; the full versions on Agensi add more coverage:

- **Permission Gate (full):** adds confirm gates for spending and DMs, a per-action spend cap, a "details changed? new card" rule, safe handling of pasted card or key details, standing approvals for unattended routines, and a full set of test scenarios.
  https://www.agensi.io/skills/permission-gate
- **Untrusted-Content Fence (full):** adds more trigger sources, hidden-text handling in summaries, an explicit fencing step, a fraud-pattern worked example and more test scenarios.
  https://www.agensi.io/skills/untrusted-content-fence

## More from ProGoals on Agensi

Other ProGoals skills and bundles are sold separately on Agensi. They are **not** part of this plugin, and you don't need them to use it.

- **ProGoals store:** https://www.agensi.io/creators/kamal-katul
- **Bot Guardrails Pack** (Permission Gate, Secrets Hygiene, Untrusted-Content Fence, Usage Budget):
  https://www.agensi.io/bundles/bot-guardrails-pack-4-safety-skills-for-grok-bot
- **Solo Seller Bot Team** (Seller Team Lead, Digital Product Research Brief, Digital Product Listing Draft, Weekly Digital Shop Health Digest, plus the four Guardrails Pack skills):
  https://www.agensi.io/bundles/solo-seller-bot-team-lead-research-listing-and-shop-health-skills-for-grok-bot
- Individual full versions:
  - Permission Gate: https://www.agensi.io/skills/permission-gate
  - Secrets Hygiene: https://www.agensi.io/skills/secrets-hygiene
  - Untrusted-Content Fence: https://www.agensi.io/skills/untrusted-content-fence
  - Usage Budget: https://www.agensi.io/skills/usage-budget
  - Seller Team Lead: https://www.agensi.io/skills/seller-team-lead
  - Digital Seller Command System: https://www.agensi.io/skills/digital-seller-command-system-research-rebuild-gate-list
  - Subject Matter Mastery: https://www.agensi.io/skills/subject-matter-mastery-research-drill-gate-present
- The two free skills here are also listed free on Agensi:
  [Template Scrubber](https://www.agensi.io/skills/template-scrubber) · [Product Rebuild Gate](https://www.agensi.io/skills/product-rebuild-gate-score-fix-iterate)

## What these skills will not do

- They don't send, post, pay, delete, share or publish anything on their own. Each one drafts or recommends, then stops for you.
- They don't collect, store or transmit data. There are no scripts, MCP servers, hooks or network calls in this plugin, only Markdown instructions.
- They don't replace your own review. Read every card and every draft before you approve it.

## Support

Open an issue in this repository. Support is best-effort.

## License

[MIT](LICENSE) © 2026 Kamal Katul (ProGoals)

"Grok" and "Grok Bot" are names of xAI products, and "Cursor" is a trademark of Anysphere, Inc. They are used here only to describe compatibility. Not affiliated with xAI. Not affiliated with Cursor.
