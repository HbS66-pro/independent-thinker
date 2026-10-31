# Roadmap

What is still missing, in rough order of how much it matters. Nothing here is a promise.

## 1. No evidence it changes anything

The sample in the README is hand-written to show the shape. It is not a before/after.

The cheapest honest test: take two or three real tasks, run each twice (skill installed, then removed), publish both transcripts under `examples/`, and label it as one person's comparison rather than a benchmark. That will not prove causation, but it will show what the output looks like on real work, which the README cannot do today.

## 2. No real transcripts

Every mode should have one real output in `examples/`, not a mock. At the moment the only example is the compressed one in the README.

## 3. The two builds can drift

`en/` and `zh/` are translations, and nothing checks that they stay aligned. A rule added to one and forgotten in the other is the most likely failure mode.

A small CI job would catch most of it: parse both frontmatters, compare heading counts, check that every mode named in `SKILL.md` has a file, and that the budget numbers agree.

## 4. The layout needs a copy step

The repo is a distribution wrapper: `en/` and `zh/`, with no `SKILL.md` at the root. A plain `git clone` into a skills folder therefore produces a folder the agent ignores. The release zips remove most of that pain. A real fix would be one repo per language, at the cost of two places to maintain.

## 5. Compatibility is under-documented

Agent Skills is a shared format. The README says any agent that reads `SKILL.md` can load the files, then shows a single skills path. Two or three paths would cover most readers for one line each.

## 6. Nothing is tested

No check that the frontmatter parses, that the files referenced from `SKILL.md` exist, or that the two builds agree. Same job as in 3.

## 7. The name does not carry the search terms

`independent-thinker` is not what anyone types when looking for a thinking skill. Topics and the description do that work now. Renaming would break links and existing installs, so it is not worth it until the project has another reason to move.

## Not planned

- More modes, or a library of mental models. The bet is on output discipline, not depth.
- Copying text from other skill repos. Methods are fair game; sentences are not.
