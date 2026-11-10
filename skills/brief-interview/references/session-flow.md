# Session flow

## The three levels

Sections fill in three levels. A level counts as reached when every section in it and in the levels below is saved. The connector reports the level in `level`, `levelName` and `levels[]`.

| Level | Name | Sections, in interview order | What it gives an AI |
| --- | --- | --- | --- |
| 1 | Foundations | personal, business, positioning, icp, opinions, content_pillars, offers | Who you are, who you serve, what you think, what you offer. Enough to write the right things to the right person, with a next step. It does not sound like you yet. |
| 2 | Growth | tone_of_voice, examples, channel_rules, do_not_say | How you sound and where you publish. |
| 3 | Scale | proof_points, testimonials | Proof, once there are clients to draw on. |

Say these in the user's language and in your own words; the table is the content, not a script.

## Where to start

- No argument: follow `nextStep` from `get_onboarding_status`. It always names the next missing section of the lowest unfinished level.
- A level argument: take that level's `missing` list from `levels[]` in order. If a lower level is unfinished, say so in one line and ask whether to finish it first; respect the answer.
- A section key: that section only, then stop.
- `import <source>`: the examples import first; afterwards offer to continue with `nextStep`.

Resuming mid-level needs nothing special: the status call tells you what is missing.

## When a level is reached

Say it plainly, in one or two sentences, then what the next level adds. When Foundations is reached, also say that the brief now has its baseline and that Growth is where it starts to sound like the user. When Scale is reached, say the brief is complete and that it only needs to be kept current.

## The save gate

Show the draft in full, in the shape the tool takes, then ask exactly:

> Save this? yes / edit / skip

- **yes**: call `update_<key>`, report the result in one line (what changed, the level name).
- **edit**: change only what the user says, show the draft again, ask again.
- **skip**: move on; list the section under "skipped" at the stop point.

Never save without the yes. Never save a suggested default the user has not seen in full.

## The question counter

Count every question you ask, including follow-ups, excluding the save gate. Around 15 to 20, finish the current section and stop. If a level completes before that, stop there. Stopping is normal, say so; the user continues with the skill name and a level or section key.

## The stop-point summary

Print, in this order:

1. Level reached, with the counts (for example "Foundations: 6 of 7").
2. Saved this sitting: section titles.
3. Skipped: section titles, with the reason if the user gave one.
4. Still missing for the next level: section titles.
5. How to continue: `/content-brain:brief-interview`, optionally with a level or a section key.

## Scripts for the two failure paths

**No profile.** "There is no Content Brain profile yet. What is the name of the person or business the brief is for, and the website if there is one?" Then infer the content language from how they write, confirm it, and call `update_business_profile`.

**Read-only connection.** "This connection can read your brief but not write to it. To save sections, reconnect Content Brain with write access, or create a read and write token in your dashboard under Settings › MCP tokens. Until then I can walk through the questions and give you the drafts to paste in yourself." Do not retry the write.
