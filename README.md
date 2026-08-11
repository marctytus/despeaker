# despeaker

A Claude Code skill that turns a badly diarized meeting transcript into a clean record with no speaker names.

You record a meeting in a conference room. One mic, five people, and the transcript comes back with every single line attributed to whoever owned the laptop:

```
[Marc Tytus] 00:14:02 So the budget is approved?
[Marc Tytus] 00:14:05 Yes, approved on Friday.
[Marc Tytus] 00:14:09 Great, I'll tell the team.
```

Guessing who actually said what is worse than useless, because now you have confident misquotes attached to real people. This skill takes the other road: it removes attribution entirely and rewrites the meeting as one readable account of what was discussed, with the questions, answers, and disagreements intact but nobody's name on any of it. The original file is never touched.

## Install

```
git clone https://github.com/marctytus/despeaker ~/.claude/skills/despeaker
```

Then hand Claude Code a transcript and ask it to despeaker it, or just mention the speaker labels are wrong.
