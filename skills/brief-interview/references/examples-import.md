# Importing past content into examples

The `examples` section is the strongest voice signal in the brief: real pieces the user wrote, plus a bank of openings that worked. Importing in bulk saves the user from pasting them one by one. The section is replaced whole on every save, so the import is one merge and one confirmed write.

## Limits (the tool rejects anything over them)

- Items: 1 to 50. Each has `title` (up to 200 characters), `body` (up to 3,000), `channel` (a tag), optional `whyItWorks` (up to 1,000).
- Hooks: up to 50. Each has `text` (up to 300), `channel`, optional `whyItWorks` (up to 300).
- Channel tags: `youtube`, `linkedin`, `newsletter`, `instagram`, `x`, `tiktok`, `blog`, `podcast`, `other`.

## Steps

1. **Gather candidates.** Read every file or page the user named. One piece per item. For a transcript, the item is the spoken script; for a thread, the whole thread.
2. **Load what exists.** Call `get_section` with key `examples`. If `content` is present, its items and hooks are the base; you add to them.
3. **Tag the channel** from the source, and say how you decided:

   | Source looks like | Tag |
   | --- | --- |
   | Video transcript, `.srt`, `.vtt`, a script with spoken cues | `youtube` |
   | Short professional post, LinkedIn export | `linkedin` |
   | Email, issue, Substack or newsletter export | `newsletter` |
   | Caption, carousel text | `instagram` |
   | Tweet, thread | `x` |
   | Short vertical video script | `tiktok` |
   | Article, long-form page | `blog` |
   | Episode notes, show transcript | `podcast` |
   | Anything else | `other` |

4. **Title and trim.** Title: the piece's own title, else its first line, cut to 200 characters. Body: cut at 3,000 characters, keep the opening, end the cut with an ellipsis. Say which items were trimmed.
5. **Dedupe.** Drop an item whose title matches an existing one (case-insensitive) or whose first 100 characters of body match. Count the drops.
6. **Hooks, only with a yes.** Offer to take the first one or two lines of each strong post as a hook entry (up to 300 characters), tagged with the same channel. Do it only if the user agrees; they can also name specific pieces.
7. **`whyItWorks`** comes from the user. Ask once: "Any of these you know performed well, and why?" Fill only what they say.
8. **Caps.** If the merged list exceeds 50 items or 50 hooks, show the overflow and ask which to leave out. Suggest dropping the oldest or the ones the user calls weakest; do not choose for them.
9. **Count table.** Before saving, show:

   | Channel | Existing | New | Total |
   | --- | --- | --- | --- |

   plus trimmed, deduped and left out, as counts.
10. **One save.** Ask the save gate question. On yes, call `update_examples` with the full merged list (existing plus new). Report the result in one line.

## After the import

List what was left out and why, in one short block. Then offer to continue with `nextStep`, or, if tone of voice is still empty, suggest doing it next: the examples are the evidence it needs.
