# Status and primary sources

**Last checked: October 31, 2026 (UTC).** This is a dated documentation snapshot, not a continuously monitored compatibility database. Recheck official pages before applying it later.

## Shared signal: announced, not universally deployed

| Source | What the source establishes at this check |
| --- | --- |
| [IETF Datatracker](https://datatracker.ietf.org/doc/draft-kelley-aipref-training-preference-signal/) | Version 00, dated October 30, 2026; an individual Internet-Draft, not IETF endorsement or a completed standard. |
| [OpenAI announcement, October 30, 2026](https://openai.com/index/helping-websites-express-ai-training-preferences/) | Plans implementation in the coming months; promises another implementation update. Existing crawler controls continue. No exact launch date is supplied. |
| [Google announcement, October 30, 2026](https://developers.google.com/search/blog/2026/10/ai-training-control) and [crawler documentation](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers#google-extended) | Announced 2027 support; crawler documentation says early 2027. This is a target, not evidence it is already live. |
| [Anthropic statement to the IETF list, October 30, 2026](https://mailarchive.ietf.org/arch/msg/ai-control/mddjatOxSR0h6GmLRBWlc839c7w/) | Says implementation work has started and complements existing controls. Does not establish completed rollout or a completion date. |
| [Microsoft announcement, October 30, 2026](https://blogs.bing.com/search/2026/10/your-content-your-choice-clearer-preferences-for-training-and-grounding/) | Says honoring begins February 1, 2027 as crawling occurs. Page-level training preferences override robots.txt preferences. Grounding is a separate control. |

Do not infer that all providers will implement the same policy, at the same time, or that announcing support proves production enforcement.

## Current provider-specific documentation

- [OpenAI crawler documentation](https://developers.openai.com/api/docs/bots): GPTBot is distinct from OAI-SearchBot and ChatGPT-User.
- [Anthropic crawler documentation](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler): ClaudeBot is distinct from Claude-SearchBot and Claude-User. Use this for existing controls; this repository does not claim a verified shared-signal deployment date for Anthropic.
- [Google-Extended documentation](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers#google-extended): a product token with training and certain grounding scope, not a separate HTTP user agent. See the README for the important shared-signal interaction.

## Protocol and interpretation references

- [RFC 9309](https://www.rfc-editor.org/rfc/rfc9309.html): established robots.txt syntax, matching, retrieval, and caching behavior.
- [Version 00 of the proposal](https://datatracker.ietf.org/doc/html/draft-kelley-aipref-training-preference-signal-00): work-in-progress semantics for the shared policy token. Keep this separate from the finalized robots protocol itself.

The prompts and examples are this project's practical workflow, not copied official implementation instructions or an assertion of legal effect. Live-file checks verify what a website publishes; they do not audit a provider's internal data pipeline.
