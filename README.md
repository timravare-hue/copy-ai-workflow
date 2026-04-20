# copy-ai-workflow

A Claude Code skill that turns any AI workflow video into a working skill you can actually run.

Saw a cool AI tip on TikTok or Instagram? Drop the transcript in. This skill pulls out the workflow, checks the docs to confirm it's possible, and generates a new Claude Code skill that executes the workflow when you invoke it later.

**Input:** a transcript from a short-form video about an AI workflow.
**Output:** a brand new skill saved to your skills directory.

## Why this exists

Most AI workflow videos are 30 seconds of hype and leave you Googling for an hour to figure out how to build it. By then you've lost interest.

This skill closes the gap. Transcript in, verified working skill out.

## How it works

1. You paste a transcript 
2. The skill extracts the tools, connections, and output the video describes
3. It checks every claim against the real docs (does this tool exist, is the feature current, what does it actually cost, what do you need to have set up)
4. You get a verdict: ready to build, works with small changes, or not a fit
5. If it's good, the skill writes a new SKILL.md and saves it to your skills directory
6. You invoke the new skill any time with a natural phrase

## Install

```
git clone https://github.com/timravare-hue/copy-ai-workflow.git ~/.claude/skills/copy-ai-workflow
```

Restart Claude Code. That's it.

## Test it

Open a Claude Code session. Paste any AI workflow transcript and say:

```
turn this into a skill
```

Or:

```
copy this workflow
```

The skill should fire, pull out the workflow, run verification, and ask you to approve before saving the new skill.

## Requirements

- Claude Code installed and working
- Internet connection (the skill uses web_search and web_fetch to verify claims)
- A transcript. Claude Code can't pull video transcripts on its own. TikTok's share menu has a copy-transcript option, or you can use an Apify actor if you've got one connected.

## Who built this

Built by Tim Ravare, a regular guy using AI. Follow @regularguyusingai on TikTok and Instagram for short-form videos on how to actually use AI tools without being a developer.

## License

MIT.
