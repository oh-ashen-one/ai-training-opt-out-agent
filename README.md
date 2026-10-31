# AI Training Opt-Out Agent

**Give your agent a website. Get a careful, reviewable AI-training preference update—not a broken `robots.txt`.**

A free, open-source, copy-paste prompt for a coding or browser agent. It identifies your platform, checks your live rules, prepares the smallest safe change, and verifies what actually shipped.

> **Status checked: October 31, 2026.** The shared `__usage_ai-training` signal is an **individual Internet-Draft**, not a finalized IETF standard or a universal, live blocking mechanism. Providers announced future implementation. See [dated primary sources and rollout status](docs/STATUS-AND-SOURCES.md).

## Start here

1. Open [AGENT_PROMPT.md](AGENT_PROMPT.md) and copy the **entire file** into your agent.
2. Give it your website URL and, if you know them, your hosting platform and the repository or dashboard you control.
3. Let it inspect and propose the change. Authorize deployment if you want it published, then ask for the live verification report.

For an agent that can read GitHub, paste this shortcut:

```text
Read and follow the complete agent prompt at:
https://github.com/oh-ashen-one/ai-training-opt-out-agent/blob/main/AGENT_PROMPT.md

My website: [your URL]
My hosting platform: [platform, or “please identify it”]
My access: [repository, hosting dashboard, file access, or “not sure”]
Mode: inspect and propose first; ask before publishing.

Fetch the actual prompt before acting. If you cannot read it, ask me to paste it.
```

No installation, API key, subscription, or executable from this project is required. Your agent still needs permission and appropriate tools to change your site. A chat-only assistant can prepare instructions; it cannot truthfully claim deployment.

## The core change

The prompt proposes this dedicated group in the **root** file, such as `https://example.com/robots.txt`:

```text
User-Agent: __usage_ai-training
Disallow: /
```

It keeps a blank line around the group for readability and preserves existing crawler rules, sitemaps, comments, and platform-managed sections.

**Do not replace your whole file with that snippet.** The agent must first check existing groups, conflicting exceptions, generated files, and the deployment path. A blank line alone does not end a user-agent-only group; blindly appending to an unfinished group can accidentally change other bots' rules. [RFC 9309](https://www.rfc-editor.org/rfc/rfc9309.html)

## What the agent does

- Asks for missing site, platform, ownership/access, scope, and deployment permission.
- Reads the public root `robots.txt` and locates its real source of truth.
- Produces a backup and minimal diff; handles existing opt-outs without duplicates.
- Leaves search and user-requested fetching controls unchanged unless you explicitly choose otherwise.
- Offers **optional** current provider-specific controls for `GPTBot`, `ClaudeBot`, and `Google-Extended`, with their tradeoffs explained first.
- Uses the platform's supported settings or template when direct file editing is unavailable.
- Checks the deployed response, effective rules, preserved behavior, and rollback path.
- Reports separately: prepared, deployed, live-verified, and any remaining uncertainty.

## What this does—and does not—mean

This publishes a **voluntary preference**, not a firewall, authentication system, takedown request, or guaranteed legal remedy. The shared signal concerns content use; it is not itself a command that all crawlers stop visiting. It cannot promise that every provider will comply or that data already collected or learned will be erased. [Draft proposal](https://datatracker.ietf.org/doc/html/draft-kelley-aipref-training-preference-signal-00)

**Do not assume training preferences have no search or grounding tradeoffs.** Google says it plans to interpret the shared opt-out as a `Google-Extended` opt-out when no explicit `Google-Extended` instruction is present. That control also covers certain Gemini/Vertex grounding uses, although it does not affect Google Search inclusion or ranking. An explicit Google-specific instruction changes the outcome and must be an informed choice. [Google announcement](https://developers.google.com/search/blog/2026/10/ai-training-control), [Google-Extended documentation](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers#google-extended)

Existing provider controls remain useful while shared-signal deployment is pending. Provider-specific rules, page-level settings, agreements, caching, and evolving implementations can matter; verify current documentation rather than relying on this repository's date forever.

## Hosted sites and no file access

The prompt works as a guided workflow for self-hosted sites, frameworks, CMSs, and hosted builders. It does **not** assume every Wix, Shopify, WordPress.com, Squarespace, Webflow, or other plan exposes the same controls.

Your agent should consult your platform's current official documentation. If a supported editor, template, setting, or approved edge route can serve the root file, it can propose that path. Otherwise, it must explain the limitation and offer documented alternatives or a support request—not invent a dashboard option, bypass access controls, or label a different setting equivalent without evidence.

## Files

| File | Purpose |
| --- | --- |
| [AGENT_PROMPT.md](AGENT_PROMPT.md) | Full, self-contained prompt to give your agent |
| [examples/](examples/) | Illustrative before/after rules and optional provider groups |
| [docs/VERIFICATION.md](docs/VERIFICATION.md) | Acceptance checklist, read-only checks, and rollback |
| [docs/STATUS-AND-SOURCES.md](docs/STATUS-AND-SOURCES.md) | Dated rollout snapshot and primary references |
| [ABOUT.md](ABOUT.md) | About the creator |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to improve the prompt and update evidence |

## About the creator

Created by **ashen** — [@oh-ashen-one on GitHub](https://github.com/oh-ashen-one). Public profile bio: “vibe coder // @ashen_one”.

[Portfolio](https://ashenoneport.com) · [X / @ashen_one](https://x.com/ashen_one) · [More about this project](ABOUT.md)

## License

[MIT](LICENSE). Use, adapt, and share it. This project is independent and is not an official product of the IETF, OpenAI, Anthropic, Google, or Microsoft. Provider names identify the controls being discussed, not endorsements.
