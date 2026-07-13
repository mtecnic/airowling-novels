# The Weight of Salt

**29,954 words / 13 chapters.** Literary novel set in a Sicilian
fishing village, 1963. AI-generated end-to-end by
[AIRowling](https://github.com/mtecnic/AIRowling). No sentence was
written or edited by a human.

**Read it here**: [`novel.md`](novel.md)

## What this is

Concetta Ricci, 43, works the postal exchange in a small coastal
village west of Trapani. Her fiancé Andrea vanished in 1942 during a
naval action off Malta. His family received the standard Regia
Marina notification. Concetta waited three years, then in 1945
married Andrea's cousin Enzo — a widowed fisherman with two young
children — and has since borne two more of her own. Her life is
small: the boat, the nets, the four children, the mother-in-law who
remembers everything Concetta ever did, the postal window that opens
at seven and closes at noon.

Then, in the spring of 1963, letters begin arriving at the exchange
addressed to Andrea Marino. First one postmarked from Marseille.
Then one from Palermo. And eventually a hand-delivered envelope with
no postmark at all.

Someone knows Andrea is alive. Someone knows where he was for
eighteen years. And now someone wants Concetta to know.

## How it was made

- **Pipeline**: [AIRowling](https://github.com/mtecnic/AIRowling)
- **Model**: Qwen3.6-35B-A3B-AWQ, hosted locally on RTX 4090
- **Style source**: none — voice established from scratch
- **Wall clock**: ~65 min on the local GPU
- **No cloud LLM calls, no human edits**

The prose voice specified in the prompt — Elena Ferrante-adjacent,
texture-heavy, small stakes revealed as large — is what emerged. The
opening image sets it:

> *"The post office breathed in sighs. Not the clean exhalation of a
> bell tower or the sharp crack of a cannon — though Concetta knew
> both sounds well enough, having heard the bell every Sunday for
> forty-three years and the cannon once, from the harbour wall, when
> she was a girl and the men had gone to fight."*

## What worked

- **Ferrante-adjacent texture**: the post office as a physical
  presence with dust that "accumulated in thick, grey felt along the
  edges of the counter and inside the cracks of the floorboards"
- **Concetta's characterisation**: 43, brown eyes, scar above the
  left eyebrow, "habit, deep-set and rigid as the grain in a
  workbench" — matches prompt spec
- **The Sicilian geography rendered without pastiche**: the bell, the
  harbour wall, the sea air carrying kelp-rot, the mail truck at
  eight
- **The letters-as-object motif**: each letter shifts the story's
  physical centre from the postal window to Concetta's kitchen table
  to a hillside in the interior

## Naming curiosity

This is the third of three non-fantasy novels generated in one
AIRowling session (see companion repos below). The second was titled
*The Weight of Paper*; the pipeline named this one *The Weight of
Salt* without human intervention, picking up thematic naming from
the same session's persisted memory. Both titles happen to fit their
books.

## Repository contents

- [`novel.md`](novel.md) — the manuscript
- [`architecture.md`](architecture.md) — the planning-phase output
- [`bible.json`](bible.json) — canonical character/setting record
- [`chief_editor_letter.md`](chief_editor_letter.md) — the pipeline's
  final editorial critique of its own work

## License

[CC BY 4.0](LICENSE).

## Related AIRowling outputs (this session's non-fantasy triptych)

- [ash-between-names](https://github.com/mtecnic/ash-between-names) —
  Southern Gothic literary novel (Wren Halloway's funeral home
  fraud)
- [weight-of-paper](https://github.com/mtecnic/weight-of-paper) —
  Prague 1968 literary espionage (Vera Novakova and the dissident
  manuscript)
- **The Weight of Salt** — this repo

Plus the other AI-authored fiction from the same tooling:

- [silence-of-lolth](https://github.com/mtecnic/silence-of-lolth) —
  drow priestess crisis of faith (Salvatore-styled fantasy)
- [pearl-casey-files](https://github.com/mtecnic/pearl-casey-files) —
  three-book Gilded Age NYC detective trilogy
- [stone-path-of-harrows-end](https://github.com/mtecnic/stone-path-of-harrows-end) —
  Tolkien-styled original pastoral fantasy
