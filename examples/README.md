# Illustrative examples—not drop-in replacements

Read the real website's file and the full [agent prompt](../AGENT_PROMPT.md) before editing. The examples show a narrow change to a fictional site; never copy their whole contents over your configuration.

- [before.robots.txt](before.robots.txt): existing crawl rules and sitemap.
- [after-shared-signal.robots.txt](after-shared-signal.robots.txt): the same content plus a dedicated shared-preference group.
- [optional-provider-groups.txt](optional-provider-groups.txt): separate opt-in additions, not a mandatory blocklist.

The before/after example assumes no existing shared-token group or unfinished User-Agent-only group. Real files need inspection for conflicts and effective behavior.

Google's announced handling of the shared signal can also affect certain grounding uses; review the [README warning](../README.md) and current official documentation before adopting it. Existing explicit provider preferences must be checked rather than overwritten.
