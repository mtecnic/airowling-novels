# The Stone Path of Harrow's End

**36,690 words / 16 chapters. AI-generated. Zero Tolkien IP.**

A pastoral fantasy about Ilse Vane, a 26-year-old farmer in a
slowly-emptying northern countryside, who inherits from an uncle she
barely knew the wardship of an ancient pilgrimage road that runs from
her father's farm down through the hills to a shore no ship has
visited in seventy years. The road is dying. The Baron's foreman is
taking its waystones for foundations. Then a traveler arrives at dusk
with a bruised staff and asks the way. Then more. Then a family with
three children who say something is following behind them that they
cannot describe. Ilse's road is the only way north.

**Read it here**: [`novel.md`](novel.md)

## How it was made

Generated end-to-end by [AIRowling](https://github.com/mtecnic/AIRowling),
an autonomous novel-writing pipeline, using stylistic analysis of
J.R.R. Tolkien's *Lord of the Rings* trilogy as its voice reference.

- **Style source**: `AIRowling/samples/lotr` (Fellowship, Two Towers,
  Return of the King — 2.58 MB of text ingested as voice fingerprint,
  motif catalogue, signature-phrase set, and structural techniques)
- **Model**: Qwen3.6-35B-A3B-AWQ hosted locally on RTX 4090
- **IP anchoring**: `--allow-source-names` NOT set. AIRowling's
  Q1 fix (`765956c`) extracts the corpus's proper nouns during
  ingest and forbids them from the new work. Frodo, Gandalf, Aragorn,
  Sauron, Mordor, Rivendell, Shire, Bilbo, Elrond, Legolas, Gimli,
  Boromir, Merry, Pippin, Isildur, Númenor — all zero occurrences in
  the manuscript.
- **Wall clock**: ~75 minutes on the local GPU
- **No cloud LLM calls, no human edits**

CLI invocation:

```bash
python3 -m AIRowling \
  --api-url http://192.168.86.42:8000/v1 \
  --plain \
  --style-source AIRowling/samples/lotr \
  auto "A 15-18 chapter fantasy novel set in a slowly-emptying
        northern countryside..."
```

## What the pipeline preserved from Tolkien

**Voice**: measured cadence, aphoristic sentences, landscape rendered
as moral geography. Specific patterns lifted from the corpus:

- Compressed-history-in-single-sentences (Tolkien would write
  a paragraph, then drop a proper noun that implies a whole
  institutional history you're expected to grasp)
- Pastoral opening turning grave — chapter 1 opens with flour, bread,
  a copper coin, a goat, and ends with a bloodied stranger collapsing
  against a waystone
- Landscape doing character work: *"the moss that grew only on its
  northern face, as though the stone itself were afraid of the sun"*
- Aphoristic tails: *"Appurtenances. A word that meant nothing and
  everything."* • *"The Baron always heard about things that belonged
  to him."*

**Motifs**: the waystone, the road as vigil, the hollow, the pilgrim,
snow-and-cold as ambient presence. Tolkien wrote about these things
constantly; nothing here is *his* handling of them — only the
disposition to write about them.

## What the pipeline invented

Everything else. The setting has no name. Harrow's End is not a place
that appears in any established mythology. The Baron Kaelen and his
foreman Torvin are the pipeline's inventions. Uncle Eamon, Jaren the
traveler, Elara the child, the ledger with its silent list of
pilgrims — original.

The mythology around the waystones — that they hum with cold, that
they hold a "phantom imprint of the thousands who had passed before,
pressed into the cold rock like breath on glass" — is a mystical
mechanism the pipeline built to fit its own premise. No Silmaril, no
Ring, no palantír. A cracked stone road that was once holy, and a
woman who inherited it.

## Post-generation edits

Two intra-chapter paragraph duplicates were caught by manual review
and removed:

1. **Chapter 1**, a paragraph beginning "Where the valley dipped, the
   path constricted" that repeated verbatim the middle sentence of an
   earlier paragraph beginning "At the first hollow, the road
   narrowed." Deleted.
2. **Chapter 2**, a paragraph beginning "Ilse felt the hair on her
   arms rise" that repeated after another paragraph with the same
   opening. Deleted (the retained version reads as a stronger
   antecedent for Ilse's line "It follows no one," she said).

Both were **shared-middle duplicates** — different openings and
endings, but shared 20-30 word verbatim substrings. The prior
`find_duplicate_paragraphs` cosine+opening-shingle detector missed
them. AIRowling commit
[`48fdb7d`](https://github.com/mtecnic/AIRowling/commit/48fdb7d)
adds a third detection mode (12-word shingle intersection) that will
catch this class in future builds.

Total edit: 98 words removed from a 36,788-word manuscript. ~0.27%
by word count. No prose was rewritten — only deletions of redundant
paragraphs.

## Signals fired during the build

- **PLAN_REPAIR**: 9 fires — plot beat endpoints defaulted per the
  Q1-Q5 plan-hardening tier
- **CROSS-CHAPTER SCENE DUPLICATE**: 4 fires — scenes between
  chapters flagged for revision (Q5 fix)
- **CHIEF_EDITOR**: 6 fires — final editorial passes (v6 macro edit
  + copy-edit specialist passes)
- **IP anchoring**: 0 leaks across a 17-name check

## Repository contents

- [`novel.md`](novel.md) — the manuscript (post-dupe fix)
- [`architecture.md`](architecture.md) — the pipeline's planning-phase
  output (title, premise, themes, voice, characters, settings, plot
  points, chapters, pacing, irrevocable loss)
- [`bible.json`](bible.json) — the canonical character/setting record
  the pipeline enforced during drafting
- [`chief_editor_letter.md`](chief_editor_letter.md) — the pipeline's
  final editorial critique of its own work

## License

[CC BY 4.0](LICENSE). Attribution should read: "The Stone Path of
Harrow's End (2026), generated by AIRowling, based on stylistic
analysis of J.R.R. Tolkien's Lord of the Rings trilogy."

## Related AIRowling outputs

- [silence-of-lolth](https://github.com/mtecnic/silence-of-lolth) —
  Salvatore Dark Elf-style novel, with a v2 companion demonstrating
  the same Q1 IP-anchoring fix used here
- [pearl-casey-files](https://github.com/mtecnic/pearl-casey-files) —
  a three-book Gilded Age NYC detective trilogy with cross-book
  character continuity via the Q6 canonical-bible companion loader
