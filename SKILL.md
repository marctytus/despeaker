---
name: transcript-deattribute
description: >-
  Rewrite a meeting transcript with failed diarization (a shared-room mic
  collapsed every speaker into one label) into a clean, unattributed record of
  the discussion. Use when the user shares a transcript where the speaker
  labels are wrong, or asks to strip attribution from a transcript and produce
  a documentation-style writeup.
---

# De-attribute a mislabeled meeting transcript

## When to use

A meeting was recorded in a **conference room** (one mic, several people), so the
platform's diarization collapsed everyone into a **single speaker label**
(e.g. every line reads `[Marc Tytus] HH:MM:SS`). Guessing who actually said each
line is unreliable and risks misattributing quotes to real people. The right move
is to **remove** attribution entirely and render the meeting as one continuous,
readable account of what was discussed.

## The core principle

**Remove speakers; never guess them.** The output has no speaker names at all;
it reads as a single flowing narrative of the discussion, preserving the
back-and-forth (questions answered, points debated) without tagging anyone.

## Procedure

1. **Read the whole transcript.** These files are long — often 1000+ lines.
   Read every page (paginate with `offset`/`limit`) before writing anything.
   The substance is spread throughout, and later sections change the meaning of
   earlier ones. Done means: every line of the source has been read.

2. **Write a new Markdown file next to the original**, same folder, named
   `<original basename> - unattributed.md`. The source file stays untouched.

3. **Header block.** Start the file with a title, the meeting date (from the
   folder/file name), and this exact note so the reader knows what they're
   looking at:

   > **Note:** This was recorded in a conference room with several people speaking.
   > The original transcript attributed every line to a single speaker, which was
   > incorrect. It has been rewritten below as an unattributed record of the
   > discussion — the words as spoken, without assigning them to individual
   > people. Light cleanup has been applied where the automatic transcription was
   > garbled, but no content has been added.

4. **Rewrite the body as continuous prose:**
   - Strip **all** `[Name] HH:MM:SS` labels and timestamps.
   - Merge the choppy ASR fragments into complete, readable sentences.
   - Keep the natural conversational flow — it will still shift between
     "I think we should…" and "he's asking whether you want to…" because it's a
     discussion. That's correct; it preserves the deliberation without pretending
     to know who's who.
   - **Lightly** de-garble obvious ASR errors (repeated "yeah yeah yeah", false
     starts, mangled homophones) **only** where the intended meaning is clear.
     Preserve proper nouns, dollar figures, and technical terms exactly.
   - Every idea in the output must trace to the source. Transitions connect what
     was said; they never assert new facts.
   - Fix obvious mis-transcriptions of entities you know from context — product
     names, project codenames, acronyms the ASR mangled into homophones
     ("Lone Star" → the project actually named Lodestar). When unsure, leave
     the text as transcribed.

5. **Section headings for long transcripts.** If the meeting covers several
   distinct topics (a budget walkthrough, a vendor-pricing debate, etc.), add
   `##` headings so it reads as documentation. For a short/single-topic meeting,
   a single flowing narrative is fine.

6. **Report back** with the file link and a 1–2 line summary of the approach.
   Offer optional variants only if useful:
   - **Topic-organized notes** (regrouped under headings, spec/requirements style).
   - **Short decisions summary** (one page of just the decisions).

## Guardrails

- Never identify or label speakers, even partially, even when context makes a
  line's author seem obvious.
- This is a *record of the words*, not meeting minutes — keep the substance at
  full length unless the user asks for a summary variant.
