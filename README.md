Try AI directly in your favorite apps … Use Gemini to generate drafts and refine content, plus get Gemini Pro with access to Google's next-gen AI
# Content Engine + Repurposer

Turn one input, a blog, a case note, or a podcast transcript, into a week of LinkedIn posts in your own voice, scored before you ever see them, with a hard grounding gate that kills any unsupported claim.

This repo has two things:

1. **The engine** (`index.html`) — a self-contained page that walks the loop: Source → Angles (you curate) → Drafts (scored, you approve) → The week. Runs the real pipeline on Claude.
2. **The skill** (`skills/content-repurposer/SKILL.md`) — the same loop as a reusable Agent Skill you can run in Claude.

> **Live demo:** https://fast-carrot.vercel.app/  ·  built by Moin Subair

---

## The idea

Most "AI content" is one prompt and a wall of generic text. This is the loop a good ghostwriter actually runs, made repeatable:

- **Voice and positioning are separate inputs.** One file says how you sound; one says what you want to be known for. Keeping them apart stops on-voice posts from being strategically empty.
- **Every draft is scored 0 to 5** on voice, positioning, and grounding, and revised once if it falls short.
- **The grounding gate is hard.** Any draft that invents a statistic, a result, a person, or a testimonial is killed before it reaches you. For regulated work (medical, legal, financial), this is the only check that matters.
- **A human approves. Nothing posts unattended.**

---

## Try the engine

Open `index.html` in any browser, or visit the live link above. Pick a sample source and walk the four steps. The baked samples run instantly and need no API key.

**Live mode (your own content):** open the Live mode panel, paste your Anthropic API key and any blog or transcript, and the engine extracts angles and drafts for real. Your key stays in your browser and is sent only to `api.anthropic.com`. Get a key at https://console.anthropic.com/settings/keys (pay-as-you-go, set a small spend limit).

> Never hardcode an API key into a hosted copy of this page. The public demo is meant to run on the baked samples only.

---

## Use the skill (three ways)

**1. Claude.ai (paid plans).** Download `content-repurposer.skill`, then in Claude go to Settings → Capabilities → Skills → upload it. Then just ask Claude to "use the content-repurposer skill."

**2. Claude Code (one command).** Register this repo as a plugin marketplace, then install:

```
/plugin marketplace add moinsubair73/fast-carrot
/plugin install content-repurposer@moin-gtm-skills
```

**3. Copy-paste (works anywhere).** Copy `skills/content-repurposer/SKILL.md` into a file named `SKILL.md` and hand it to Claude.

---

## What's in here

```
.
├── index.html                          the live content engine (open or host this)
├── skills/
│   └── content-repurposer/
│       └── SKILL.md                    the reusable Agent Skill
└── .claude-plugin/
    └── marketplace.json                lets Claude Code install the skill in one command
```

## Notes

- The engine is a single static file. Host it free on Vercel (`vercel.com/new`, drag the folder) or GitHub Pages (Settings → Pages → deploy from `main`, root).
- Not medical, legal, or financial advice. The skill drafts from material you give it; it never invents claims.

Built by Moin Subair.
