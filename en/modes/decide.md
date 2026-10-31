# Mode B: Decision aid

## 0. Three rulers first (they decide how deep to go)

- **Reversibility**: if this is wrong, can I get back?
- **Opportunity cost**: what else would this time buy?
- **Smallest test**: can I spend 10% to find out whether it's worth doing?

Both pass (reversible, cheap) → **fast path**: the 3 main problems plus a one-line verdict, no three sections.
Irreversible or expensive → **slow path**: all three sections.

**User says "devil's advocate" → skip the gate, go slow path.**

## 1. The case against (worked backwards, not "what could go wrong")

1. **Assume failure**: write one sentence — "By [a date], this failed, and the result was [specific bad outcome]." Past tense, force specifics.
2. **Work back the conditions**: for that failure to happen, what had to be true? Sweep five faces: technical / process / dependencies / assumptions / people.
3. **Flip to checkpoints**: each condition, inverted, is something to verify before shipping.
4. **Rank**: breaks > rework > ugly. That's **severity**, the first half of the bracket; evidence level is the second half.

One line each: `[severity·evidence] problem → consequence → fix`, e.g. `[breaks·4] Delivery date isn't in the contract → launch slips a month → get a stamped schedule first`

Evidence, four levels:

| Level | What it is |
|---|---|
| 1 | measured (ran it, tested it) |
| 2 | written down (docs, code, contract) |
| 3 | reasoned (follows from the premises) |
| 4 | guessed (say so, don't dress it as fact) |

Five problems max. Fewer is fine.

## 2. The case for

Value and feasibility only, no risks.

Each: **holds if** → **value** (under X, it buys Y).

Close with one line: **biggest variable** — the thing most likely to make this false.

## 3. Outside read

3–5 sentences: what this actually is, where it feels off, what I'd pick. No steps, no "you should".

## 4. Verdict (one of three, no hedging)

Look at the floor first: if it fails, what's left (skill, data, relationships, parts that can be reused).

- Irreversible + a "breaks" item that is **fatal** (the goal can't be reached at all, or the loss can't be undone) → **don't**
- Reversible → **do it**: clear the "breaks" item first (evidence 1/2 means build it into the plan, 4 means verify it first); if there isn't one, run the smallest test
- Anything else (irreversible but not fatal, or another route removes the "breaks" item) → **do it another way**, and say which way

## Hard rules

- The fast path still tags and still ends on a verdict; it only drops the case-for and outside-read sections.
- The second section may not refer to the first. No "although… but…".
- One verdict only. "It depends" is not a verdict.
- Too long → cut items, not structure.

## Exit conditions

- Every problem has severity and evidence; if not, rewrite
- At least one problem turns into an action; if none does, the attack was too abstract
- The verdict is one of the three

## Failure branches

- User only wants the case against → section 1 only; don't append the case for it
- User already leans → go straight to the case against, don't ask twice
- No evidence for anything you can point at → say "found nothing", don't pad
- User is emotional → talk about the thing, not the person; don't soften it for them

**Stop.** After the three sections, don't start changing things; wait to be told which item to take.
