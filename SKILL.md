---
name: copy-ai-workflow
description: Use this skill when the user wants to copy a Claude tip, AI workflow, or prompt technique they saw on TikTok, Instagram Reels, YouTube Shorts, X, or any short-form video. Triggers include pasting a transcript, or saying "copy this workflow," "turn this into a skill," "build this as a skill," "can I do this with my setup," or "verify this and build it." The skill pulls the workflow from the transcript, checks if it's actually possible with current tools, and generates a new Claude Code skill that captures the workflow so the user can run it anytime.
---

# Copy AI Workflow

## What this skill does

People save a lot of AI workflow videos. Most never get built because the gap between watching and running is too big. This skill closes it.

Paste the transcript. The skill pulls the workflow, checks the docs to confirm it's possible, and builds a new Claude Code skill that executes the workflow when the user invokes it later.

**Input**: a transcript from a short-form video about an AI workflow.
**Output**: a new SKILL.md saved to the user's skills directory.

Style: plain English, short sentences, no hype, no em dashes, direct recommendations.

## When to run

Run this skill when:
- The user pastes a raw transcript or script from an AI creator
- The user says "copy this workflow," "turn this into a skill," or "build this as a skill"

## The workflow

### Step 1: Confirm you have the transcript

The user should paste the transcript directly. If they paste a URL instead, tell them: "I can't pull transcripts from video URLs directly. Grab the transcript from TikTok's share menu, or use an Apify actor, and paste the text here."

Do not guess what the video says. Do not fabricate claims.

### Step 2: Pull out the workflow

Read the transcript and extract the actual workflow. Ignore the hype. Pull the signal.

Identify:
- **Tool stack**: every tool, app, model, or service named
- **Connections**: what connects to what
- **Trigger**: what kicks the workflow off (manual, scheduled, webhook, etc.)
- **Output**: what the workflow produces
- **Cost claimed**: what the creator said, or "not mentioned"

Show the user a quick summary of what you pulled out before running verification.

### Step 3: Check feasibility

Use `web_search` and `web_fetch` to confirm the workflow is actually possible. See `references/feasibility-check.md` for the full list.

You're checking four things:
1. Tools exist and have the features claimed, not a deprecated beta, not a "coming soon"
2. The user has access, right plan, needed API keys, required MCP servers
3. Cost is reasonable, real pricing from the pricing page, not what the creator said
4. It's automatable as a skill, Claude Code can execute this with the user's existing tools, or can clearly instruct them on any manual parts

If the workflow uses tools the user already has connected, the skill is faster to build. If it needs something new, name it clearly.

### Step 4: Give the user the verdict

Use this format:

**VERDICT:** Ready to build as a skill / Works with these changes / Not a fit

**The workflow:** 1-2 sentences. What it actually does, in plain English.

**What it'll cost:** Real monthly cost based on actual pricing. Free path first if it exists.

**What you need:** Accounts, API keys, MCPs, bullet list.

**How it fits your setup:** Call out tools the user already has running. Name anything new they'd need.

### Step 5: Build the skill

Only run this step if the verdict is "Ready to build" or "Works with these changes" AND the user confirms.

Generate a new SKILL.md using `references/skill-template.md`. The generated skill captures:
- Clear trigger phrases so the user can invoke it later
- The verified steps based on real docs
- Tool calls Claude will make when executing
- Any manual prep (get API key, connect MCP, etc.)

Show the user the full SKILL.md in chat first. Wait for approval.

After approval, save to a new folder at the same directory level as this skill. Name the folder in kebab-case based on what it does, not the creator who posted it.

Good names: `gmail-lead-auto-reply`, `carousel-from-blog-post`, `youtube-competitor-digest`
Bad names: `cool-ai-tiktok`, `pauls-workflow`

### Step 6: Tell the user where it's saved

After saving:
1. Path where the skill was saved
2. Two or three trigger phrases that will invoke it
3. One sentence on how to test it

Keep it short.

## What NOT to do

- Do not trash the creator. Focus on speed of copying, not calling anyone out.
- Do not verify based on vibes. Every claim gets checked against real docs.
- Do not skip the cost check.
- Do not generate the new skill without verification and the user's approval.
- Do not write the new skill using language from the video. Use the user's voice.
- Do not use em dashes. Use periods or commas.
- Do not pad with "essentially," "basically," or "in order to."

## References

See `references/feasibility-check.md` for the full verification list.
See `references/skill-template.md` for the format of the new skill that gets generated.
