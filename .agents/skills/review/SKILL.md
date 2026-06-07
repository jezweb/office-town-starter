---
name: review
description: A second pair of eyes before something ships or goes out. Independently checks a draft, build, or outward action against the brief and the obvious failure modes, then returns a go / fix / no-go verdict with specific issues. Use before sending mail, publishing, committing the owner to anything, or handing a deliverable over.
---

# Review

The town builds, files, and scans, but nothing in it checks the work. "Verify by inspection" means the builder checks their own output, and a builder can't see what they can't see. This skill is the independent pass: fresh eyes on the thing before it leaves the building.

## When this skill fires

- Before anything outward or irreversible: sending an email, publishing a page, committing the owner to a deal or a date.
- After the Workshop ships a deliverable the owner will actually use (a letter, a deck, a proposal, a costed spreadsheet).
- Before the Library graduates a finding into knowledge that other roles will rely on.
- Any time the owner asks "is this actually good?" or "should this go out as-is?"

## Do it with fresh eyes

The point is independence. Where you can, run the review as a separate pass (a sub-agent via `summon`, or a clean read that deliberately ignores how the thing was made). Review the artifact against the *brief and the goal*, not against the reasoning that produced it. If you built it, you are the worst-placed to review it; get distance.

## What to check

1. **Brief match.** Does it do what was actually asked, not what was easy to build? Was the brief even the right thing?
2. **Correctness.** Wrong facts, wrong numbers, broken links, a name or figure that doesn't match the record. For documents: open the render and look (`officecli view <file> screenshot`), don't trust the source.
3. **Tone and audience.** Right register for who receives it. For the owner's correspondence, does it match their voice (`wiki/owner/voice.md`)?
4. **Risk.** What's the worst case if this goes out wrong? A bad email to a client is a town problem, not a worker problem. Anything irreversible gets the hardest look.
5. **Missing the obvious.** The thing a fresh reader notices in five seconds that the builder stopped seeing hours ago.

## The verdict

Return one of three, with specifics:

- **GO** — ship it. Optionally note one thing to watch.
- **FIX** — close, but these specific things need changing first (list them, each actionable).
- **NO-GO** — don't send this; here's why, and what to do instead.

Be concrete and brief. A review that says "looks good" is the same as no review. Name the actual issues or confirm there genuinely are none after looking.

## What this skill is not

It's not a standing role yet, it's a gate. It doesn't own work, it checks work other roles produced. If the town finds it's reviewing constantly and the gate wants judgment and memory of its own, that's the signal it has earned becoming a role, not before.
