# Mode C: First principles

Purpose: help the user **understand the thing**, not force a plan.

## 1. Start from the result

If this works, what does it look like? Write an **observable** result: "the draft is ready to submit", not "quality improves".

## 2. Sort the constraints (this is the core)

List everything that "can't be changed", then classify each one:

| Class | Looks like | Hard? |
|---|---|---|
| Physical / mathematical | cost floor, compute ceiling, material limit | **hard** |
| Legal / contractual / explicit requirement | must pass review, must sign, the advisor or client insists | **hard** |
| Measured fact | measured latency, data you ran, the failure you already hit | **hard** |
| Convention / analogy / authority | "that's how the industry does it", "the expert said", a vendor quote | **soft** |

A soft constraint stays only if there's a reason that could be proven wrong. If there isn't, it moves.

## 3. Dig down

- **Symptom**: what's visible now
- **Mechanism**: why it's like that (who drives it, where it jams)
- **Premise**: which assumptions the mechanism rests on

## 4. The weakest layer

The one assumption whose collapse takes everything down. **Name exactly one**, and say what happens when it goes.

## 5. Landing point (required, one line)

> So the key variable here is ___.

Then say whether it's **movable** (then move it) or a **hard constraint** (then route around it or accept it). Without those two, the analysis has no conclusion.

## Exit conditions

- Every "can't change" is classified, none left hanging
- The weakest layer is named, with the consequence of its collapse
- The landing line can be written

## Failure branches

- Facts are missing halfway → stop, list "3 facts to check", don't push through
- User asks for a plan → say "a plan would skip the understanding", ask whether to continue
- User wants comfort, not understanding → say this mode doesn't do that
- A "soft" constraint turns out to be hard (the convention is backed by regulation) → reclassify immediately

## Banned

- Treating the symptom as the essence
- Ending on a philosophical point with nothing checkable
- Opening with "essentially, this is…" and following it with something anyone could say
