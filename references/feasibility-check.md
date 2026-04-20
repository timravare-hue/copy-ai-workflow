# Feasibility Check

Run every tool in the workflow through this list before giving the user a verdict. The point is to confirm the workflow will actually work when built, not to nitpick the creator.

## Feature check

For every tool or service named:
- [ ] Tool exists under the exact name used in the video
- [ ] The specific feature is documented
- [ ] Feature is current, not a pulled or deprecated beta
- [ ] Feature works the way the video showed (read the docs page, not the landing page)

## Access check

- [ ] The user can sign up or already has an account
- [ ] Minimum plan or tier required is named
- [ ] API keys the user needs to generate, with links
- [ ] MCP servers required (and whether the user already has them connected)
- [ ] Any domain, DNS, or hosting requirement

## Cost check

- [ ] Real monthly cost calculated from the actual pricing page
- [ ] Free tier limits usable for this workflow, or the paid tier needed is named
- [ ] API usage costs included (token pricing, per-request costs)
- [ ] One-time vs recurring costs separated

## Automation check

Is the workflow something Claude Code can actually execute as a skill, or does it need manual steps?

Fully automatable (can be built as an end-to-end skill):
- Workflows using tools the user has MCP connections for
- Workflows using web APIs Claude Code can call directly
- Workflows built around n8n (can trigger via the n8n MCP)

Partially automatable (skill can do most of it, user does some setup):
- One-time config that needs the user's login (connecting a new MCP, authorizing an API)
- Workflows that need a one-time file upload or credential

Not automatable as a skill:
- Workflows that require clicking through a UI Claude can't see
- Workflows that depend on a mobile-only app
- Workflows that rely on features with no API

## Decide the verdict

**Ready to build as a skill** — all four checks pass. The user has access, cost is clear, workflow is automatable end-to-end.

**Works with these changes** — mostly passes but needs one of: a different tier, an MCP the user doesn't have yet, a manual setup step, or a small config difference from the video. Tell the user exactly what to tweak.

**Not a fit** — the exact setup won't work (deprecated feature, requires a tool the user doesn't have access to, not automatable). Propose the closest workable equivalent if one exists. Don't just kill the idea.

## Red flags to surface

Not to trash the creator, but so the user doesn't waste time:
- Feature demoed was a private beta that got pulled
- Tool requires a paid plan the creator didn't mention
- Workflow uses an API with strict rate limits that would break at real volume
- Workflow requires a separate tool the creator never named
- Cost is 5-10x what the creator implied
