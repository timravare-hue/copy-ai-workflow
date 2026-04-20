---
name: copy-ai-workflow
description: Use this skill when Tim wants to copy a Claude tip, AI workflow, or prompt technique he saw on TikTok, Instagram Reels, YouTube Shorts, X, or any short-form video. Triggers include pasting a video URL or transcript, or saying "copy this workflow," "turn this into a skill," "build this as a skill," "can I do this with my setup," or "verify this and build it." The skill pulls the transcript, checks if the workflow is actually possible with current tools and Tim's stack, and generates a new Claude Code skill that captures the workflow so Tim can run it anytime.
---

# Copy AI Workflow

## What this skill does

Tim saves a lot of AI workflow videos. Most never get built because the gap between watching and running is too big. This skill closes it.

Drop a video or transcript in. The skill pulls the workflow, checks the docs to confirm it's possible, and builds a new Claude Code skill that executes the workflow when Tim invokes it later.

**Input**: a video URL or transcript.
**Output**: a new SKILL.md saved to Tim's skills directory.

The skill follows Tim's style guide: plain English, short sentences, no hype, no em dashes, direct recommendations.

## When to run

Run this skill when:
- Tim pastes a TikTok, Reel, Short, or X video URL
- Tim pastes a raw transcript or script from an AI creator
- Tim says "copy this workflow," "turn this into a skill," or "build this as a skill"

## The workflow

### Step 1: Get the transcript

If Tim pasted a URL:
1. Try `web_fetch` on the URL first. Captions are often in the page HTML.
2. If that fails, tell Tim: "I need the transcript. Either paste the script, or run the URL through your Apify TikTok or Instagram actor and paste the output."

If Tim pasted a transcript directly, skip to Step 2.

Do not guess what the video says. Do not fabricate claims.

### Step 2: Pull out the workflow

Read the transcript and extract the actual workflow. Ignore the hype. Pull the signal.

Identify:
- **Tool stack**: every tool, app, model, or service named
- **Connections**: what connects to what
- **Trigger**: what kicks the workflow off (manual, scheduled, webhook, etc.)
- **Output**: what the workflow produces
- **Cost claimed**: what the creator said, or "not mentioned"

Show Tim a quick summary of what you pulled out before running verification.

### Step 3: Check feasibility

Use `web_search` and `web_fetch` to confirm the workflow is actually possible. See `references/feasibility-check.md` for the full list.

You're checking four things:
1. **Tools exist and have the features claimed** — not a deprecated beta, not a "coming soon"
2. **Tim has access** — right plan, needed API keys, required MCP servers
3. **Cost is reasonable** — real pricing from the pricing page, not what the creator said
4. **It's automatable as a skill** — Claude Code can execute this with Tim's existing tools, or can clearly instruct him on any manual parts

**Tim's existing stack (from memory):**
- Claude Code with MCP servers: Wix (x2), Vercel, Supabase/Neon, GitHub, Apify, Gmail, Google Drive, Google Calendar, n8n
- n8n at timothyravare.app.n8n.cloud
- Remotion project with sub-agents, hooks, slash commands
- Railway (Social Inbox app)
- Wix (Hope4Families and Clearwater accounts)

If a workflow uses tools Tim already has, the skill is faster to build. If it needs something new, name it clearly.

### Step 4: Give Tim the verdict

Format:
```
VERDICT: [Ready to build as a skill / Works with these changes / Not a fit]

The workflow:
[1-2 sentences. What it actually does, in plain English.]

What it'll cost:
[Real monthly cost based on actual pricing. Free path first if it exists.]

What you need:
[Accounts, API keys, MCPs — bullet list]

How it fits your setup:
[Call out tools Tim already has running. Name anything new he'd need.]
```

### Step 5: Build the skill

Only run this step if the verdict is "Ready to build" or "Works with these changes" AND Tim confirms.

Generate a new SKILL.md using `references/skill-template.md`. The generated skill captures:
- Clear trigger phrases so Tim can invoke it later
- The verified steps based on real docs
- Tool calls Claude will make when executing
- Any manual prep (get API key, connect MCP, etc.)

Show Tim the full SKILL.md in chat first. Wait for approval.

After approval, save to a new folder at the same directory level as this skill. Name the folder in kebab-case based on what it does, not the creator who posted it.

Good names: `gmail-lead-auto-reply`, `carousel-from-blog-post`, `youtube-competitor-digest`
Bad names: `cool-ai-tiktok`, `pauls-workflow`

### Step 6: Tell Tim where it's saved

After saving:
1. Path where the skill was saved
2. Two or three trigger phrases that will invoke it
3. One sentence on how to test it

Keep it short. He'll know if it works when he uses it.

## What NOT to do

- Do not trash the creator. Focus on speed of copying, not calling anyone out.
- Do not verify based on vibes. Every claim gets checked against real docs.
- Do not skip the cost check.
- Do not generate the new skill without verification and Tim's approval.
- Do not write the new skill using language from the video. Use Tim's voice.
- Do not use em dashes. Use periods or commas.
- Do not pad with "essentially," "basically," or "in order to."

## References

See `references/feasibility-check.md` for the full verification list.
See `references/skill-template.md` for the format of the new skill that gets generated.
