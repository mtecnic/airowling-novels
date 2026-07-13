# The Ash Between Names

**29,677 words / 13 chapters.** Southern Gothic literary novel,
AI-generated end-to-end by
[AIRowling](https://github.com/mtecnic/AIRowling). No sentence was
written or edited by a human.

**Read it here**: [`novel.md`](novel.md)

## What this is

Wren Halloway, 38, returns to her small Southern hometown after her
father's death to take over the family funeral home. Going through his
office ledgers, she discovers a coded pattern of adjustments spanning
three decades — bodies received for cremation but never cremated, the
mahogany urns delivered to grieving families filled instead with mill
ash. Some of the missing bodies were quietly interred in unmarked
graves behind the crematory. Others were sold to a medical school in
Birmingham.

As Wren works to understand what her father did, and why, and what to
do with widows who came to him with grief and left with wood ash, she
must decide whether to expose the fraud — which will ruin the
surviving family members who depended on the funeral home — or bury
it deeper.

## How it was made

- **Pipeline**: [AIRowling](https://github.com/mtecnic/AIRowling)
- **Model**: Qwen3.6-35B-A3B-AWQ, hosted locally on RTX 4090
- **Style source**: none — voice established from scratch
- **Wall clock**: ~65 min on the local GPU
- **No cloud LLM calls, no human edits**

The voice that emerged:

> "Third-person limited on Wren, spare and weighted, with a Southern
> cadence that favors concrete physical details over sentimental
> abstraction."

The pipeline's own architecture describes it as Ron Rash / Bonnie Jo
Campbell-adjacent, and the prose bears that out — grief as a
discipline, ash as an actual physical substance, hands that carry
generations.

## What worked

- **Voice**: consistently spare, present-tense-flavored past-tense,
  concrete detail forward
- **Wren's characterisation**: precise, guarded, speaks in short
  measured sentences. Her father's presence carries even in his
  absence via his ledger and her memory
- **Physical setting**: the funeral home, the timber mill riverbank,
  the unmarked grave site behind the crematory, the Birmingham
  medical archive — each rendered as a specific place with a smell
  and a weight

## Period drift note

The prompt specified rural Alabama, 2007. The manuscript's period
signals (train arrival at a wooden platform with a "corrugated iron
roof", elderly woman knitting, farmer in a worn cap) drift toward an
unspecified earlier decade. AIRowling's `_extract_period_anchor`
matched "Victorian house" in the funeral home's setting description
(architectural style, not historical period) and locked to `victorian`
as the period — which then influenced the drafting cadence.

The story reads consistently as Southern Gothic in an unspecified
past era. It doesn't hurt the book — it just isn't the 2007
specifically requested. Worth fixing the `_extract_period_anchor` to
distinguish "Victorian" as an architectural style from Victorian as
a period.

## Repository contents

- [`novel.md`](novel.md) — the manuscript (post-dupe check; zero
  duplicates found)
- [`architecture.md`](architecture.md) — the planning-phase output
- [`bible.json`](bible.json) — canonical character/setting record
- [`chief_editor_letter.md`](chief_editor_letter.md) — the pipeline's
  final editorial critique of its own work

## License

[CC BY 4.0](LICENSE).

## Related AIRowling outputs

- [silence-of-lolth](https://github.com/mtecnic/silence-of-lolth) —
  drow priestess crisis of faith (Salvatore style)
- [pearl-casey-files](https://github.com/mtecnic/pearl-casey-files) —
  three-book Gilded Age NYC detective trilogy
- [stone-path-of-harrows-end](https://github.com/mtecnic/stone-path-of-harrows-end) —
  Tolkien-styled original pastoral fantasy
