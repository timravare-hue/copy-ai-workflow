# Skill Template

Use this format when turning a verified workflow into a new Claude Code skill.

The goal: the user invokes the skill later with a natural phrase, and Claude Code executes the whole workflow.

## Where to save it

Create a new folder at the same directory level as `copy-ai-workflow/`. Name it in kebab-case based on what the workflow does.

Good names:
- `gmail-lead-auto-reply`
- `carousel-from-blog-post`
- `youtube-competitor-digest`
- `tiktok-comment-responder`

Bad names:
- `cool-ai-tiktok`
- `workflow-from-video`
- `pauls-trick`

Folder structure:

```
skill-name/
  SKILL.md
  references/    (only if the skill needs longer reference docs)
```

## SKILL.md format

Frontmatter with name and description. Description starts with "Use this skill when the user wants to..." and lists specific trigger phrases the user would actually say. Names the tools involved. Names the output. The description is the trigger, so it must be specific enough that Claude Code picks it up when the user says one of the phrases.

Then the body:

- **What this does**: 2-3 sentences. What goes in, what comes out, what problem it solves.
- **When to run**: Bullet list of specific triggers, including exact phrases the user might use.
- **Before first run**: Any one-time setup the user has to do (get an API key, connect an MCP, install a package). Skip this section if nothing is needed.
- **What you need in context**: Inputs the skill expects (a URL, a blog post, a brand guide, etc.).
- **The workflow**: Numbered steps. Each step names the tool or MCP Claude will call and the expected output.
- **Output format**: What the skill produces. File path, format, delivery method.
- **Rules**: Any voice or style rules, gotchas discovered during verification, places where the video's advice was wrong and should be ignored.
- **References**: Link any reference files the skill uses.

## Rules for generating the skill

1. **Description is the trigger.** Include three or four phrases the user would actually say. If the description is vague, the skill won't fire when needed.
2. **Use the user's voice.** Never copy the creator's language into the skill.
3. **Every step should be executable.** Name the tool Claude will call. If it's an MCP, name the MCP. If it's a web API, link the docs.
4. **Call out prerequisites at the top.** If the skill needs an API key the user doesn't have, the first thing they should see is how to get it.
5. **Don't over-engineer.** A skill with 12 steps and 4 reference files is worse than a clear one with 5 steps.
6. **Test the trigger.** Read the description and ask: would this fire if the user said what they'd naturally say? If not, rewrite.

## Before saving

Show the user the complete SKILL.md in chat. Get explicit approval. Then save to disk.

## After saving

Tell the user:
1. Where the skill was saved (full path)
2. Two or three trigger phrases that will invoke it
3. One sentence on how to test it

Keep it short. No overselling.
