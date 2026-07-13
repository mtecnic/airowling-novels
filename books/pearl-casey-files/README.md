# The Pearl Casey Files

A three-book historical detective series set in Gilded Age New York
(1897–1899), generated end-to-end by
[AIRowling](https://github.com/mtecnic/AIRowling) — an autonomous
novel-writing pipeline. No sentence in these books was written or
edited by a human.

**Total: ~101,000 words / 41 chapters across three novels.**

## The books

| # | Title | Words | Chapters | Setting | Read |
|---|---|---|---|---|---|
| 1 | *The Stitched Key* | 32,307 | 13 | New York, 1897 | [`1. The Stitched Key/`](1.%20The%20Stitched%20Key) |
| 2 | *The Silk Knot* | 37,565 | 15 | New York, 1898 | [`2. The Silk Knot/`](2.%20The%20Silk%20Knot) |
| 3 | *The Silk Knot: Resurrection* | 31,014 | 13 | New York, 1899 | [`3. The Silk Knot - Resurrection/`](3.%20The%20Silk%20Knot%20-%20Resurrection) |

## The detective

**Pearl Casey**, 29, auburn-haired daughter of a retired Bowery beat
cop. Green eyes, sharp tongue, quicker eye. Works cases the NYPD
won't take. Attractive enough to weaponize it; wit sharp enough to
prefer not to. Voice: "sharp, clipped, uses humor as armor."

Her cast — Sergeant Michael Doyle (grey eyes, weary Irish sergeant),
Silas Vane (Fifth Avenue industrialist antagonist), Lao Wei (Chinatown
apothecary), Elena Rossi (Italian immigrant seamstress) — carries
across all three books with structurally-preserved attributes.
Between books, the pipeline's Q6 fix (see "How the trilogy was made"
below) prevents attribute drift.

## The arc

A shadow syndicate — the Blackwell organization — has been sabotaging
New York's industrial infrastructure since before Pearl was born. Book
1 fights a syndicate arm and doesn't know it. Book 2 dismantles its
public face and pays a personal cost. Book 3 confronts its head, a
Fifth Avenue widow named Astrid Blackwell, who has been reading Pearl
her whole life from a distance.

Pearl's father's death opens Book 3 and closes the trilogy: he was
hunting Blackwell his whole retirement without ever knowing her name.
Pearl must decide whether to finish his work by his method (the badge,
the paperwork, the courts) or hers (the truth, whatever it costs).

## How the trilogy was made

Sequential AIRowling builds with cross-book character and voice
transfer. Each book uses the previous book(s) as `--style-source`.
Book 2 and Book 3 also use `--reuse-characters` so Pearl and her
supporting cast return.

### Chain of commands

**Book 1** (from scratch — establishes voice, characters, world):

```bash
python3 -m AIRowling --api-url http://192.168.86.42:8000/v1 --plain \
  auto "A 15-20 chapter historical detective novel set in New York
        City in 1897. Detective Pearl Casey — 29, auburn-haired..."
```

**Book 2** (uses Book 1's novel as voice source, characters return):

```bash
python3 -m AIRowling --api-url http://192.168.86.42:8000/v1 --plain \
  --style-source /tmp/pearl-trilogy/book1.txt \
  --reuse-characters \
  auto "A 15-20 chapter historical detective novel set in New York
        City in 1898, six months after the events of Book 1..."
```

**Book 3** (uses combined Book 1 + Book 2 corpus):

```bash
python3 -m AIRowling --api-url http://192.168.86.42:8000/v1 --plain \
  --style-source /tmp/pearl-trilogy/books12 \
  --reuse-characters \
  auto "A 15-20 chapter historical detective capstone set in New York
        City in 1899, six months after The Silk Knot..."
```

### Q6: canonical character preservation

The obvious problem with `--reuse-characters` across books was
attribute drift. Between Book 1 and Book 2's first draft, Pearl's
canonical green eyes and auburn hair became grey eyes and dark hair —
the LLM's chunked extraction of Book 1's prose picked up inconsistent
descriptions and the architecture LLM invented new attributes.

Q6, added mid-trilogy, fixed this. When a `bible.json` sits alongside
the style source, AIRowling uses it as authoritative — overrides the
LLM extraction, emits structured attributes explicitly
(`— eyes: green — hair: auburn — age: 29`) in the architecture prompt,
tells the model NOT to change them.

Book 2 v2 and Book 3 built with Q6 in place produce zero attribute
drift across the trilogy. Verified: Pearl's green eyes / auburn hair /
age 29 appear identically in all three bibles.

### The pipeline in one line

Each book runs the same 8-phase AIRowling pipeline:

```
PLAN (arch + bible + manifest) → BIBLE_LOCK → ZERO_DRAFT
    → STRUCTURAL_REVIEW → STRUCTURAL_REVISION
    → DEVELOPMENTAL_REVIEW → DEVELOPMENTAL_REVISION
    → LINE_REVISION → CONTINUITY → COPY_EDIT
    → CHIEF_EDITOR (4 specialist passes)
    → PACKAGE
```

Every chapter passes through mechanical critics (POV leaks, said-
bookisms, stylistic tics, duplicate paragraphs, cross-chapter scene
overlap, chapter-ending cadence, motif overuse, sentence-pattern
repetition, workshop-tell dialogue) and gets targeted rewrites when a
critic flags a specific paragraph.

Wall clock per book on a single RTX 4090 running
Qwen3.6-35B-A3B-AWQ locally: ~50-90 minutes. Total trilogy:
about 4 hours of GPU time. No cloud LLM calls.

## Provenance

- **Model**: Qwen3.6-35B-A3B-AWQ, hosted locally
- **Pipeline**: AIRowling
  ([mtecnic/AIRowling](https://github.com/mtecnic/AIRowling)) —
  private repo but the commit hashes referenced in this README are
  verifiable
- **Author**: no human authored any sentence in these three books

## License & terms

The prose is offered under [CC BY 4.0](LICENSE).

Attribution should read: "The Pearl Casey Files (2026), generated by
AIRowling."

## Bibles

Each book's `bible.json` in this repo is the authoritative canon for
that book — character attributes, plot beats, setting descriptions.
Read in order: [1. The Stitched Key/bible.json](1.%20The%20Stitched%20Key/bible.json) →
[2. The Silk Knot/bible.json](2.%20The%20Silk%20Knot/bible.json) →
[3. The Silk Knot - Resurrection/bible.json](3.%20The%20Silk%20Knot%20-%20Resurrection/bible.json).
Pearl's attributes are byte-identical across all three.
