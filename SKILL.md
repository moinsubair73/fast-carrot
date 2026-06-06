---
name: content-repurposer
description: Turn one input (a blog post, a case note, a transcript, a caption) into a week of LinkedIn posts written in your own voice, with every claim checked before you see it. Use when someone wants to repurpose existing content into a sequenced week of voice-matched LinkedIn posts, build a reusable personal-brand content loop, or set up an interview-then-ingest onboarding so the output sounds like them and not like AI. Runs an angles to drafts to week pipeline with a self-scoring step and a hard grounding gate, and can optionally generate a standalone HTML version of the engine.
---

# Content Repurposer

Turn one input into a week of LinkedIn posts in your voice, scored before you ever read them, with a human gate you never remove.

This is the loop a good ghostwriter runs, made repeatable. The model drafts and judges; you approve. Nothing posts unattended.

## The one-paragraph version

You give the engine your voice (how you sound) and your positioning (what you want to be known for), kept as two separate files. Then you drop in one input. The engine finds the angles worth saying, assigns each to the part of your positioning it serves, drafts each post in your voice, scores it on voice / positioning / grounding, revises once if it falls short, kills anything that fails grounding, and lays the week out on a calendar tuned to LinkedIn reach, with a first comment and a warm-lead reply per post. You approve, edit, or kill. Approved posts and your edits feed back so next week is better.

## Before anything: run the interview (once per person)

Do not draft until you have these. Ask the user, conversationally, and write the answers to two files.

**`voice.md` — how they sound.** Ask for, and then capture:
- 3 to 8 samples of their real writing (past posts, captions, emails, a voice transcript). This is the single most important input. Without real samples the output will sound like generic AI.
- Their hard style rules (sentence length, formality, words they never use, emoji yes/no, em dashes yes/no).
- Their platform: if their samples are from Instagram or a blog and the target is LinkedIn, note the register shift (strip emoji walls and hashtag stacks, expand the "why", keep disclaimers).

**`positioning.md` — what they want to be known for.** Ask:
- The one thing they want a smart reader to think after reading them.
- 2 to 4 content pillars (the recurring themes). Mark which is the lead pillar.
- For regulated fields (medical, legal, financial): the claims they are NOT allowed to make, and their source of truth for facts.
- A 0-to-5 scoring guide: what a 5 looks like for them, what a 1 looks like.

Keep both files plain markdown. They are living documents; every approved post and edit sharpens them.

## The loop

Run these stages in order. Keep each visible to the user.

**1. Ingest.** Take the one input. Reduce to clean text. Keep any links (a guide, a booking page, a demo); they get reused in the first comment, never the post body.

**2. Extract angles.** Read the input and return 3 to 6 distinct angles. Assign each to the pillar it serves. Show them to the user and let them deselect the weak ones. This curation is the highest-leverage human moment; do not skip it.

**3. Draft + self-score.** For each selected angle, in one pass:
- Write the post in their voice, using `voice.md` as the reference and their hard rules as constraints.
- Score it 0 to 5 on three axes:
  - **voice** — does it sound like them, not like AI or a brochure?
  - **positioning** — does it reinforce a pillar, or just fill the calendar?
  - **grounding** — is every claim supported by the input or their source of truth?
- If any axis is below 4, revise once and keep the better version.
- Return the post, the three scores, and any flags.

**4. The grounding gate (hard).** This is not a quality score, it is a safety boundary. Kill, and never surface, any draft that:
- states a statistic, result, or outcome not present in the source,
- invents a patient, client, testimonial, or quote,
- makes a claim the user listed as not-allowed (regulated fields).
Show the user a one-line reason for each kill. The post that scores voice 5 / grounding 1 (sounds great, says something untrue) is exactly what this catches. For medical, legal, and financial content, treat the gate as absolute: when unsure, kill.

**5. Continuity.** De-dupe across the week so it reads as a sequence, not five rewordings of one headline.

**6. Assemble the week.** Space the posts across the week (steady cadence, not all in one day). For each: generate the user's first comment with the relevant link (LinkedIn suppresses reach on posts with links in the body, so the link lives in the comment). Draft a short, non-salesy warm-lead reply they can send to someone who engages. Human-sent, never automated.

**7. Human gate + learn.** Show every post with its scores and flags. The user approves, edits, or kills. Append approved posts and edits to `voice.md` so the corpus grows and review gets faster over time. Never auto-post.

## Output

Give the user a clean, copyable week: each post with its day/time slot, pillar, first comment, and (where relevant) a warm-lead reply. Plus a short note of anything the gate killed and why.

## Hard rules (anti-slop, always on)

- No em dashes unless the user's `voice.md` allows them. Use commas, periods, or "to" for ranges.
- No hype vocabulary (game-changer, revolutionary, cutting-edge, unlock, delve, leverage as filler).
- Numbers and specifics over adjectives.
- Never invent a fact, a result, or a person.
- Never post on the user's behalf. The engine drafts; a human approves; a human posts.

## Going the distance: generate your own HTML engine (optional)

If the user wants a shareable, clickable version of their engine (a "try it" page like the demo this skill came from), generate a single self-contained HTML file:
- Reuse the four-step structure: Source → Angles (you curate) → Drafts (scored, you approve) → The week.
- Bake in 1 to 2 of the user's real inputs, fully wired end to end, so anyone can click through.
- Show the 0-to-5 scores and include one draft that the grounding gate visibly kills, so the gate is part of the story.
- Keep it client-side only (no API key in the browser), so it is safe to host and link publicly.
- Use their brand fonts and colours if they have them.
Hand them the file to host on GitHub Pages, Netlify, or any static host, and link from their first comment.

Keep this optional. The core deliverable is the week of posts. Ship that reliably before offering the HTML.

## Setup note

This skill needs no special tools to draft. If you want it to fetch a live blog URL as the input, enable web access. Everything else runs from the files the user gives you in the interview.
