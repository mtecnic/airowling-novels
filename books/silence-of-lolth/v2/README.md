# v2 — The Silence Beneath the Web

**Companion volume. 31,869 words / 15 chapters. Zero WotC IP names.**

Read it here: [`novel.md`](novel.md)

## What this is

A second novel generated end-to-end by
[AIRowling](https://github.com/mtecnic/AIRowling) using the same style
corpus (R.A. Salvatore's *Dark Elf Trilogy*), the same LLM
(Qwen3.6-35B-A3B-AWQ), and a prompt semantically identical to the one
that produced [the original *Silence of Lolth*](../novel.md) — the
difference is that the pipeline had been patched between runs to
address five specific weaknesses another Claude instance identified
after reviewing the first book.

The result: a novel of the same scale (31,869 vs 33,152 words; 15 vs
14 chapters) that uses **zero source-corpus IP names**, has visibly
better cross-chapter distinctness, and — in this reader's judgment —
tells a more inventive story precisely because the pipeline was
forbidden from leaning on Salvatore's mythology.

## The five fixes (Q1-Q5)

An external Claude reviewer read the published v1 *Silence of Lolth*
and produced a five-point critique of the AIRowling pipeline. Each was
audited against the code:

| # | Critique | Pre-fix state | Live-observed on v2 |
|---|---|---|---|
| **Q1** | IP anchoring — forbid source-corpus character names in output | MISSING | Zero leaks on 11-name check (Lolth, Menzoberranzan, Drizzt, Zaknafein, Do'Urden, Malice, Bruenor, Wulfgar, Baenre, Guenhwyvar, Belwar) |
| **Q2** | Chapter-ending cadence variation | MISSING | Detector + prompt directive in place; verified by lock test |
| **Q3** | Noun-phrase + sentence-pattern motif tracking | PARTIAL | New "temple breathing"-style detector + "not X, not Y, real Z" pattern detector |
| **Q4** | Mid-generation ledger enforcement | PARTIAL | Ledger block now injected into surgical revision prompts |
| **Q5** | Cross-chapter scene deduplication | MISSING | **4 live fires** during v2 build — ch02, ch03, ch09 each flagged for overlapping ch01 (cosine 0.80-0.85) |

Full commit: [`765956c`](https://github.com/mtecnic/AIRowling/commit/765956c)
(private repo; commit hash provided for reference).

## What Q1 (IP anchoring) actually did

Before this fix, when AIRowling ingested a copyrighted corpus, the
pipeline told the LLM "here are the signature phrases, the voice
metrics, the motif domains" — but never said "don't use the corpus's
named characters and places." So the LLM did what LLMs do with
confident material: reused it. The v1 *Silence of Lolth* uses Lolth,
Zaknafein, Menzoberranzan, House Do'Urden — Wizards of the Coast
trademarks — because the pipeline never asked it not to.

Q1 changed the ingest phase to also extract a **corpus IP list**:
proper nouns appearing ≥5 times in the source, minus a broad
allowlist (dates, honorifics, common English caps). For the Salvatore
Dark Elf Trilogy, this produces:

```
Drizzt, Malice, Belwar, Do'Urden, Dinin, Guenhwyvar, Zak,
Montolio, Briza, Roddy, Alton, Masoj, Zaknafein, Menzoberranzan,
Baenre, Clacker, Vierna, Spider, Dove, Underdark, Hun'ett,
Lloth, Bruenor, Catti-brie, Academy, Jarlaxle, Tephanis...
```

Every drafting round now sees a forbidden-names block:

> ## Forbidden names (from the reference corpus — DO NOT use)
> The reference corpus uses these named characters and places. You
> MUST NOT introduce them into the new work. Invent your own names
> for equivalent archetypes and settings.

The LLM complies. Where v1 named its priestess *K'liira* — a
Salvatore-adjacent drow-name pattern — v2 names her **Vespera**. Where
v1's temple sat in *Menzoberranzan*, v2's chamber is unnamed. Where
v1 invoked *Lolth* explicitly, v2 refers only to "the Spider Queen"
as a title.

An `--allow-source-names` CLI flag exists for intentional pastiche.
v1 was published *before* this flag existed; had it been available,
v1 would have used it. v2 is what the default (safer) mode produces.

## Why v2 is arguably the better book

The strongest evidence is what Q1's constraint *forced* into
existence. When the LLM couldn't reach for Lolth as a divine
abstraction, it had to invent a mystical mechanism for prayer-
reception. It came up with this:

> *The silk threads hummed. Not a sound exactly — the air here was
> too thin for ordinary acoustics to carry far — but a vibration
> that moved through bone and sinew. Each thread stretched from the
> cavern ceiling to the floor in radiating spokes, dozens of them,
> hundreds, each one tuned to a different frequency of Vespera's
> attention. When the chamber was empty, the threads sang in their
> slow, patient chorus. When a prayer arrived, one thread would
> tighten, and the song would shift.*

That is a *specific* mechanism for how a priestess hears her goddess.
It doesn't exist in Salvatore's canon. It doesn't exist in D&D. It's
an invention forced into existence by the constraint that the
Salvatore vocabulary was off-limits — and it's more concrete, more
sensory, and more originally imagined than v1's borrowed
Menzoberranzan-cavern framing.

The moral crisis (a young priestess hearing a prayer she cannot
answer) is the same. The character (drow priestess in a matriarchal
society questioning her doctrine) is the same. What differs is the
*rendering* — and rendering is where fiction lives.

## Q5 (scene deduplication) in the wild

The Q5 detector fired four times during v2's LINE_REVISION pass. The
LLM had drafted chapters 2, 3, and 9 with opening beats that
semantically overlapped chapter 1's opening (a common Qwen tendency —
hedging its bets on continuity by re-establishing the setup each
chapter). Excerpts from the live log:

```
[LINE_REVISION/ch02] CROSS-CHAPTER SCENE DUPLICATE (score 0.83):
  ch02 para 0 overlaps ch01 para 0 — both open with sleep/darkness/Vespera on cot

[LINE_REVISION/ch03] CROSS-CHAPTER SCENE DUPLICATE (score 0.82):
  ch03 para 0 overlaps ch01 para 0 — both open with Council Chamber summons

[LINE_REVISION/ch09] CROSS-CHAPTER SCENE DUPLICATE (score 0.83):
  ch09 para 0 overlaps ch01 para 0 — both dawn-summons scenes

[LINE_REVISION/ch09] CROSS-CHAPTER SCENE DUPLICATE (score 0.80):
  ch09 para 5 overlaps ch01 para 0 — bound-ritual-woman scene
```

Each finding routed back to the chapter as a chapter-wide LLM
revision instruction ("Recast this beat with different framing —
shift the POV moment, change the sensory register, or cut it"). The
rewrites reduced the openings' semantic overlap. This is exactly the
failure mode the reviewer's critique #2 called out — caught first
pass.

## How this reads against v1

**v1** opens in an underground temple with Lolth (named), K'liira
kneeling on obsidian, Menzoberranzan (named) implicit beneath.
**v2** opens in the same physical space, but named differently: the
Chamber (unnamed), Vespera on a "carved obsidian platform at the
chamber's center," the Spider Queen referenced only obliquely.

**v1** develops through prayer-goddess dialogue with Zaknafein's
Shadow (named, from Salvatore's canon) making the argument about
faith.

**v2** develops through a system of silk threads that transmit
prayers — an invented mechanism unique to this book. The doctrinal
crisis lands through Vespera failing to recognise a *type* of prayer
her training identifies as impossible.

Both are competent. Only one is invention-forward.

## The pipeline improvements are in AIRowling

- Q1-Q5 code changes are in [`AIRowling`
  commit 765956c](https://github.com/mtecnic/AIRowling/commit/765956c)
- 578 unit tests lock the new behaviour
- The Salvatore-Dark-Elf-Trilogy ingest cache remains identical
  between v1 and v2 (same hash `f6c20cd134f64001`)
- Only the pipeline changed. Not the model. Not the prompt. Not the
  style corpus.

## Attribution

Same as v1 — style source: R.A. Salvatore's *Dark Elf Trilogy*
(© TSR / Wizards of the Coast). Setting references transformative for
critical engagement. No human authored any sentence in this book.
Model: Qwen3.6-35B-A3B-AWQ hosted locally on RTX 4090.

License: [CC BY 4.0](../LICENSE) — same as v1.
