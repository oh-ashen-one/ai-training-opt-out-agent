# Verification and rollback

Use this after the owner has authorized the exact change. It is not proof that a provider has excluded content from a training dataset.

## Acceptance checklist

- [ ] Site, owner permission, origin scope, and selected controls recorded.
- [ ] Current official source status and relevant tradeoffs explained.
- [ ] Original live file and source-of-truth configuration saved privately.
- [ ] Minimal diff reviewed; unrelated rules, comments, and sitemaps preserved.
- [ ] No accidental shared group, duplicate policy group, or unreviewed Allow exception.
- [ ] Real source edited, not disposable generated build output.
- [ ] Normal project checks passed, or exact limitations reported.
- [ ] Authorized deployment completed, or clearly labeled not deployed.
- [ ] Public root file fetched successfully after deployment.
- [ ] Actual body is robots text, not HTML or an authentication challenge.
- [ ] Effective groups inspected, not only searched for matching strings.
- [ ] Each authorized origin checked separately.
- [ ] Repeating the workflow would make no unnecessary change.
- [ ] Rollback instructions and evidence-based completion report delivered.

## A read-only HTTP check

Replace the example origin with the site you are authorized to inspect. These commands fetch a public file; they do not modify a website:

```sh
curl --silent --show-error --location --max-redirs 5 \
  --dump-header /tmp/robots-headers.txt \
  --output /tmp/robots-live.txt \
  --write-out 'status=%{http_code}\ncontent_type=%{content_type}\nfinal_url=%{url_effective}\n' \
  'https://example.com/robots.txt'

cat /tmp/robots-headers.txt
cat /tmp/robots-live.txt
```

Choose fresh local output paths if those files already hold anything valuable. Inspect the redirect chain and the final body. A `200` status is not enough if the response is an error page. A file visible in a repository is not enough if a CDN or generated route serves different content.

Do not treat a generic robots parser, a spoofed User-Agent request, or a substring match as proof of shared-policy support or provider compliance. If a parser does not implement the proposal, use it only for the established syntax it actually supports and label that limit.

## Edge cases to review

| Case | Expected handling |
| --- | --- |
| Missing file | Verify that it is genuinely absent; create only through the real source of truth. |
| Network error / login / HTML response | Diagnose or report the blocker; do not overwrite based on an assumed empty file. |
| Existing correct policy group | No-op, then verify. |
| Existing policy group with path exceptions | Explain the conflict; do not silently erase the owner's exception. |
| Duplicate matching groups | Inspect effective combined behavior; no last-line-wins assumption. |
| Trailing User-Agent-only group | Avoid appending rules that accidentally apply to that group. |
| Generated robots route | Edit the generator or supported setting, then check built/deployed output. |
| Platform-managed section | Preserve its ownership; use documented customization mechanisms. |
| Explicit Google-Extended rule | Explain precedence and training/grounding implications before changing it. |
| Production still serves the old file | Check the deployment and relevant cache; report not live-verified until observed. |
| New subdomain discovered | Ask before expanding scope; don't assume the parent domain covers it. |

## Rollback

Revert only this change using the recorded source/configuration or commit. Follow the same deployment process, then fetch the live root file again and compare it with the saved baseline. Do not restore an old full-file backup over unrelated newer edits.

## Suggested completion report

```text
Site / origin:
Platform and source of truth:
Selected preferences:
Change / commit / PR:
Deployment status:
Live robots.txt URL:
HTTP status / content type / final URL:
Checked at (UTC):
Preservation and effective-group checks:
Tests passed / failed / not run:
Provider rollout caveats:
Remaining blockers:
Rollback:
```
