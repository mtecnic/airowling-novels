# The Load-Bearing Wall

> A comic-literary novel in fourteen chapters about a hardware chain owner who has been counting screws while the roof caves in.

Steve Roberts, 47, runs a nine-store hardware chain in central Ohio that his father built and his mother staffed. He is three years into a spectacular midlife crisis he refuses to name. Then, in a single week, the flagship store's roof collapses on a Tuesday morning, his fifteen-year-old son posts a nine-second video of him crying in the parking lot that gets 1.4 million views, a private-equity-backed rival announces a new store across the street from Roberts #3, and his wife slides a proposed separation agreement across the kitchen counter and tells him, quietly, that it isn't a threat — it's a request for space. Steve decides to rebuild the ruined store himself, alone, with the son who filmed him. It goes about as well as could be expected.

---

## Read it

**[novel.md](./novel.md)** — the full 32,008-word manuscript, fourteen chapters.

If you only have five minutes, read Chapter 1. It opens with a man counting toggle bolts, and it ends with him counting nothing at all.

---

## A passage

The book opens in aisle seven of a big-box hardware store in Toledo, Ohio, on the kind of Tuesday morning that hasn't quite decided yet whether to matter:

> The fluorescent lights hummed at a frequency Steve had learned to ignore, the same way he'd learned to ignore the pile of unpaid vendor invoices sitting on his desk, the same way he ignored the fact that it was barely Tuesday and he'd already checked his email fourteen times. He stood in aisle seven of the Flagship Store, clipboard pressed against his ribs like a shield, and counted boxes of drywall anchors.
>
> One. Two. Three. Four.
>
> He liked counting. Counting was honest. A number either matched or it didn't. There was no ambiguity in arithmetic, unlike the silent treatment from his son, who hadn't spoken to him directly in three weeks except to demand the charger or complain about the Wi-Fi, or the look Marla gave him — sharp, assessing, as if he were a spreadsheet she couldn't reconcile.

And later, in the parking lot, after the roof has come down and Steve has run:

> He put his forehead against the warm asphalt and breathed. He breathed in the smell of hot tar and gasoline and cut grass, and he thought of Doug's hand in his, and he thought of the roof, and he thought of the twelve work orders in the PRIORITY_LOW queue, and he understood, with a clarity that felt like violence, that he had been counting screws while the building fell apart above his head.

---

## What it's about

*The Load-Bearing Wall* is a comic-literary novel about a man who has spent twenty years mistaking maintenance for love, and a family that has learned to speak in Wi-Fi signals and closed doors. The premise is simple and midwestern: the physical building of Steve's family business collapses, and the reconstruction — hammer by hammer, drywall panel by drywall panel — becomes the only thing slow enough to hold him still long enough to notice his son, his wife, his employees, and himself.

The store, Roberts & Sons, sits at the intersection of two failures. Structurally, the roof has been failing since about 2003 and Steve has been filing the work orders into a queue labeled PRIORITY_LOW that no one in corporate ever opens. Emotionally, the marriage has been failing since about November, when Marla started writing something called *Proposed Separation Agreement — Draft for Discussion* in longhand at the kitchen counter while Steve was checking his email in the driveway. The book's central conceit is that Steve, a man fluent in the load ratings of toggle bolts, cannot read the load ratings of the people directly in front of him — until the roof comes down and forces him to.

What follows is not a redemption story. It is a shrinking story. Steve does not save his empire; he saves the core of it. He does not win his wife back; he learns to occupy the same room without lying to her. He does not become the father he wishes he had been; he becomes a fifteen-year-old boy's competent apprentice on a drywall crew of two. The victory, when it arrives, is that the sign over the door reads Roberts & Co. instead of Roberts & Sons, and Steve is standing behind the counter tired and present, watching Owen help a customer find the right size of galvanized screw.

The book is a comedy in the older sense — the marriage does not end, the business does not die, the boy does not disappear into his phone forever — but it is a comedy with dust in its teeth. Nobody in it is a fool. Everybody in it is trying.

---

## Cast

**Steve Roberts**, 47. Blue eyes, greying hair, the defensive jargon-laced speech of a man who reaches for optimization the way other men reach for a beer. He has been running his father's hardware chain for twenty years and thinks he has been doing a good job, largely because he has never stopped moving long enough to check. He counts things. He is very good at counting things. He is about to discover the limits of that skill.

**Marla Roberts**, 45. Green eyes, dark hair, the dry precise voice of someone who has been rehearsing a difficult sentence for months. She is writing a novel that Steve has never asked to read, on paper he does not understand why she prefers to a screen. She loves him. She has run out of ways to say so that he will hear.

**Owen Roberts**, 15. Brown eyes, black hair, a hoodie with a hole where his thumb has worn through the cuff. He communicates with his father primarily through the household router, films Steve crying in the parking lot mostly to see what will happen if he does, and turns out — nobody more surprised than him — to have very steady hands.

**Doug Miller**, 62. White hair, hazel eyes, hired in 1981 by Steve's mother because she said he had good hands. He remembers the foreman who built the store, and the foreman's daughter, and why the trusses are cedar. He is the load-bearing wall of the store in a way corporate has never priced into anything.

**Piper Bellamy**, 29. Blonde hair, brown eyes, MBA. A cheerful algorithmic consultant sent by Torrid Home, the private-equity-backed rival, to talk to Steve about liquidation, micro-fulfillment hubs, and the humane retirement of Class-B big-box structures. Her PowerPoints are, unfortunately, mostly correct. The book is generous to her anyway.

**Mei-Lin Chen**, 34. Dark eyes, black hair, the stock manager. She organizes the salvage yard into a supply chain because if she doesn't organize it she will have to feel it, and feeling it would break her. Steve has worked twenty feet from her for six years and is about to notice her for the first time.

---

## Voice

Close third, past tense, Ohio-specific. The register is Richard Russo crossed with Nick Hornby — tender rather than cruel toward its characters, funny because Steve is genuinely trying and failing rather than because he is a fool. The prose likes hardware-store nouns (toggle bolts, galvanized straps, drywall anchors, cedar trusses) and uses them to measure emotional distance. Interior monologue leans on counting and lists when Steve is losing his grip, which is often. If you like the domestic-comic register of *Straight Man* or *About a Boy*, and don't mind if the comedy occasionally has to sit down and catch its breath, this is aimed at you.

---

## How this was made

*The Load-Bearing Wall* was drafted end-to-end by **AIRowling**, a private novel-generation pipeline. The pipeline handles the whole stack: premise expansion, story bible, chapter architecture, per-chapter drafting with continuity checks against a running world state, and a multi-editor pass at the end (developmental, copy, proofreader, chief). The chief editor's letter from that final pass is preserved in this repo as [chief_editor_letter.md](./chief_editor_letter.md) — it is candid about the manuscript's weaknesses and worth reading if you care about the seams.

The source-of-truth planning artifacts are also checked in:

- [architecture.md](./architecture.md) — premise, themes, plot beats, chapter outlines
- [bible.json](./bible.json) — structured world state (characters, settings, plot points)

The manuscript in this repo is the first pass. It has not been rewritten by a human. The seams are visible if you look for them — most notably a fifteen-chapter outline that arrives as fourteen chapters in the manuscript, some day-of-the-week continuity drift in the early chapters, and a climactic inspection scene that resolves more neatly than it should. The prose voice, the toggle-bolt-and-fluorescent-hum texture, the parking-lot moment on the asphalt — those are all pipeline output.

*Caption: 32,008 words · 14 chapters · one drafting run.*

---

## See also

Other manuscripts drafted by the same pipeline live in sibling repos under [github.com/mtecnic](https://github.com/mtecnic):

- **[vacuum-variable](https://github.com/mtecnic/vacuum-variable)** — near-future hard SF. Captain Jack Rogers and an orbital data center that has already decided he will investigate.
- **[ash-between-names](https://github.com/mtecnic/ash-between-names)** — Southern Gothic literary. Wren Halloway and the funeral home her family cannot quite bury.
- **[weight-of-paper](https://github.com/mtecnic/weight-of-paper)** — Prague 1968 literary espionage. Vera Novakova, translator, dissident, unreliable narrator of her own courage.
- **[weight-of-salt](https://github.com/mtecnic/weight-of-salt)** — Sicilian 1963 literary. Concetta Ricci and a marriage that has to be undone in a village that will not permit it.
- **[pearl-casey-files](https://github.com/mtecnic/pearl-casey-files)** — Gilded Age NYC detective trilogy.
- **[silence-of-lolth](https://github.com/mtecnic/silence-of-lolth)** — Salvatore-styled fantasy, with a v2 pass in the repo.
- **[stone-path-of-harrows-end](https://github.com/mtecnic/stone-path-of-harrows-end)** — Tolkien-styled pastoral fantasy.

A western (William Buck) and a second AI thriller (Nic Charles) are still in progress. When they are ready they will land in sibling repos on the same account.

---

## License

The manuscript and planning artifacts in this repository are published for reading and research. If you want to quote a passage, adapt the premise, or study the pipeline output, open an issue and say so.
