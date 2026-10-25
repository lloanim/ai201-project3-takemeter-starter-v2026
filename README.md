# TakeMeter

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->
TakeMeter classifies r/gaming posts into four categories: `argued`, `reaction`, `hot_take`, and `question`. I labeled 200 real r/gaming posts with these categories and trained a small model on them. The goal is to separate posts worth reading from noise in a way that matches how regulars judge them. 

---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `argued`

**Definition:**
Makes a claim about a game or industry topic and backs it with at least one concrete reason: specific gameplay details, comparisons, stats, sources, or personal experience explained in enough detail to show why.

**Example 1:**
> I'm genuinely surprised Rewindead isn't getting more attention. It is a brilliant concept. I don't normally post but I feel compelled since the concept of this game is genuinely quite cool. It's like a speed runners dream. (The fella at the top of the leader board posts all his stuff online and it freaks me out how it is even possible) Lad you're a hitman who is looping in time. You start by killing a VIP, which sends you back in time. Now you need to take out yourself and the VIP. This repeats until you've finished every loop on the level. It's pretty simple at first, but the more loop they add, the wilder it gets. It's basically a puzzle shooter game at the end of the day.There is a whole ranking system, which forces you to actually play fast. It's pretty sneaky on how it baits you into optimising everything. You start thinking...."NO I can't settle for a C! I am beyond a mere C! I will become number 1" but the faster you play, the harder the game gets (The past versions of you turn into a bit of a menace) I spent way too long trying to find the perfect run, just to find out some guy online to show me something I couldn't even imagine. TLDR: Gud Gam, Fun Gam, Try Demo

**Example 2:**
> Genuinely bad or mediocre games don't tend to get the kind of massive overhaul mods that transform them into a suddenly amazing game. However, there are a ton of games that either aged horribly, or we're just down right unplayable on Modern Hardware that got mods that ranged from making them playable to completely overhauling them. One of the first examples that come to mind is Daggerfall, that game may have been revolutionary when it came out but it did not age very well and it's barely playable on Modern hardware, but the unity mod completely changed that while adding a bunch of modern qol. There's still one guy working on an Ultima 7 Unity port

### `hot_take`

**Definition:**
States a confident opinion or verdict with no reason given, or only a vague one. Naming specific games does not count as support. 

**Example 1:**
> Graveyard Keeper is honestly a really solid game with funny writing and some decent expansions. They just announced a sequel with a free demo as well.

**Example 2:**
> Kind of incredible that Sony can get away with their awful refund policy. Even Microsoft’s is better

### `reaction`

**Definition:**
Expresses an emotion or personal feeling without making a claim others could agree or disagree with.

**Example 1:**
> I'm the same way. And I'm honestly not sure why. Something about Minecraft doesn't appeal to me even though I love building crafting and survival games. I adore Vintage Story. And I really love some of the more robust mod packs. Legendary, Fear Nightfall, and DawnCraft are super fun to me

**Example 2:**
> I am a big fan of game soundtracks. My all time favorite has got to be from Arcanum of Steamworks and Magick Obscura followed by Zeliard and Homeworld. Honorable mention goes to Xenon II by the Bitmap Brothers.

### `question`

**Definition:**
Primary purpose is to ask for information, help, opinions, or recommendations. Rhetorical questions that really make a point are labeled by the point instead.

**Example 1:**
> Can I play old COD games on PC with a PS5 controller (or any controller)? Hey so, admittedly, I’m not very tech savvy and don’t know whether or not this will work. But I’ve been wanting to play the older COD games on PC for some time now. By older COD games, I’m talking about those in the WW2 era, including World at War and others before it. Can I play those on PC with a PS5 controller? Or am I stuck with mouse and keyboard?

**Example 2:**
> I just bought a seagate HHD game drive for Xbox and I’m having regrets. I have an Xbox series s 500gb and was trying to expand the storage with hopes of being able to handle the 300gb+ that the new fable game will take up but the seagate game drive won’t let you play series s games from the drive. It’s not properly advertised and they sell it with a 1 month game pass. I don’t know if this is actually a good way to use the system. The price between a 2tb HDD for $139 to an inserted drive at 199 for 1tb I don’t know if I should return the game drive and I’m looking for suggestions.

### The hardest boundary

**Which two labels:**
`argued` and `hot_take`
**The decision rule I used every time:**
If the post makes a claim and explains why using a specific gameplay detail, comparison, source, or sufficiently explained personal experience, its `argued`, even if the tone is heated or the opinion is controversial. If it gives a verdit with no supporting reason, or only vauge praise or criticism, its `hot_take`. Simply naming a game or listing examples does not count as sufficient support. 



---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**
The posts come from the subreddit r/gaming

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->
I labelled 80 posts myself and then had Claude help me label the rest. I looked through each to make sure it fit my label definitions.

**Counts per label:**

| Label | Count | Share |
|---|---|---|
| argued | 54 | 27.0% |
| hot_take | 42 | 21.0% |
| reaction | 55 | 27.5% |
| question | 49 | 24.5% |
| **Total** | 200 | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
> Not necessarily an ""older"" game, but playing Stardew Valley without any tools requires a special kind of strategy and more thought than you'd think.
> *Could have been:*
> reaction
> *I chose hot_take, because:*
> Although this post sounds more like a reaction to how the game could be played based on my rule for reaction it should be "an emotion or personal feeling without making a claim others could agree or disagree with". So this leans more towards hot_take because it states a claim on how the game can be played but does do vaguely so it also can't be argued. 

**2.**
> *The post:*
> I’ve tried fromsoft games, not really for me. I do have a mate that loves their games so I’ll take his word for the fact if you like that style, they make the best games
> *Could have been:*
> hot_take
> *I chose reaction, because:*
> The post initially makes a claim that the game is not great but then claims that they make the best games under the impression of their friend. The statement is vauge in explaining what make the game either great or bad. But does express an emotion that explains their choice and is not actually trying to prove their claim.

**3.**
> *The post:*
> If I never encounter another pack of wild wolves in an RPG it’ll still be too soon. Seriously, can we be done with this trope? Can no one think of something a little more original?
> *Could have been:*
> question
> *I chose hot_take, because:*
> Even though they are asking questions, their main point is to claim this gameplay is overused in this genre. It invited people to opinate differently to what they claim. It also fits my hot_take definition of "states a confident opinion". 

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**
"distilbert-base-uncased"

**Settings:** <!-- epochs, learning rate, batch size, seed -->
- Epochs: 3
- Learning rate: 2e-5
- Batch size: 16
- Seed: 42

**Anything I changed from the defaults, and why:**
I did not change the default settings.

**Split sizes:** <!-- train / val / test, and per-label counts in the test split. If a label had fewer than about 8 in test, say so — it explains a lot of next unit's variance. -->
train 139  ·  val 31  ·  test 30

| label | train | val | test |
|---|---|---|---|                
| argued | 38 | 8 | 8 |
| hot_take | 29 | 7 | 6 |
| reaction | 38 | 9 | 8 |
| question | 34 | 7 | 8 |
| **Total** | **139** | **31** | **30** |

Note: 'hot_take' has only 6 examples in the test split.


---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:*
     I had writen my notes on possible labels for the gaming posts.
- *What came back:*
     It told me to focus more on the structure of the post rather than its content topic. 
- *What I changed:*
     I focused more on look through the posts on the four labels which allowed me to create definitions for each. 

**Moment 2**

- *What I asked for:*
     I asked Claude to review the criteria I had originally had
- *What came back:*
     Gave feedback on what was good and what I had issues with giving an explaination
- *What I changed:*
     I changed my criteria to each have a number for what I was stating in the criteria. 

**Pre-labelling disclosure:**
I had Claude label some of the posts and while reading through them I had encountered some where I had difficulty deciding if it was right. For example a post had claimed "In Xmen on Sega genises there is a part to needed to restart a computer..." and then have a specific gameplay detail of "To solve this you literally needed to reset your console.". It was labelled by Claude to be argued but I had originally thought it was more of a reaction. I stayed with argued because it gives a claim with an explaination and not an emotion or personal feeling about the game. It is also something someone could disagree with which does not fit my reaction definition. 

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy | 0.300 | 0.500 | +0.200 |
| Macro F1 | 0.164 | 0.393 | +0.229 |
| F1 — `argued` | 0.432 | 0.571 | +0.139 |
| F1 — `hot_take` | 0.000 | 0.000 | +0.000 |
| F1 — `question` | 0.000 | 0.333 | +0.333 |
| F1 — `reaction` | 0.222 | 0.667 | +0.444 |

`note`: ran with definitions

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->
I predict that my model will be able to distinguish `argued` posts from `hot_take` because it can learn to reconize when a post provides concrete reason from specific evidence or reasoning to support an opinion rather than simply expressing a strong opinion.

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->
Compared to the baseline with definitions, training improved overall accuracy by +0.20 and macro F1 by +0.229, which suggests the model learned something from my labeled examples. The biggest gains were `reaction` (+0.444), `question` (+0.333), and `agrued` (+0.139). `hot_take` did not improve and stayed at 0.0 for both models, so neither one predicted it correctly. My prediction that the model would separate `argured` from `hot_take` did not hold up. This may be because the line between the two is hard to judge. However, when I ran the baseline with bare label names, it scored 0.600 accuracy and 0.537 macro F1, so it did better than both the definitions baseline and my trained model. So my definitions actually hurt the zero-shot model, possibly because of how long they are and the negations in the definition. 


---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1. Overall accuracy | ≥ 0.60 | 0.50 | 0.27 | 0.63 | MISSED |
| 2. `argued` / `hot_take` F1  | each ≥ 0.50 | 0.57 / 0.00 | 0.43 / 0.00 | 0.82 / 0.00 | MISSED |
| 3. `question` F1 | ≥ 0.75 | 0.33 | 0.00 | 0.67 | MISSED |
| 4. Label balance (share of 200 posts) | every label 15-40% | 21-27.5% | 21-27.5% | 21-27.5% | MET |
| 5. Confidence ≥0.70 right ≥10pts more often | gap ≥10pts | +20 pts | +60 pts | +10 pts | MISSED (not measurable as written) |

`Note`: The notebook reports accuracy by confidence third, not at a 0.70 cutoff. Mean confidence was ~0.28, so almost no predictions reached 0.70. I used the top-third vs. bottom-third gap instead. It clears 10 points on every seed, but seed 2024 is exactly at the line and each third is only 10 posts, so this is weak evidence that confidence is meaningful. 

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted | argued | hot_take | reaction | question |
|---|---|---|---|---|
| **argued** | 6 | 0 | 1 | 1 |
| **hot_take** | 2 | 0 | 4 | 0 |
| **reaction** | 0 | 0 | 7 | 1 |
| **question** | 5 | 0 | 1 | 2 |

Biggest confusion: 5 real `question` posts called `argued`.
The other direction: 1 real `argued` posts called `question`.

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->

5 real `question` posts were called `argued` and only 1 went the other way. This means that the model did not learn the boundary between `question` and `argued`. 

---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 | The held out accuracy is at least 0.60 on every on of the three seeds | ≥ 0.60 | MISSED | Seed 42 and 7 scored below 0.60 |
| 2 | `argued` and `hot_take` each have an F1 of at least 0.50 on all three seeds | each ≥ 0.50 | MISSED | `hot_take` had an F1 of 0.00 on all three seeds, and `argued` fell below 0.50 on seedd 7 (0.43) |
| 3 | `question` has an F1 of at least 0.75 on all three seeds | ≥ 0.75 | MISSED | Across all three seeds the F1 of `question` was below 0.75 |
| 4 | Every label makes up at least 15% (30 posts) and at most 40% (80 posts) of my 200 labelled posts | every label 15-40% | MET | All four labels are between 30 to 80 posts |
| 5 | Predictions with confidence of 0.70 or higher are right at least 10 points more often than predicitons below 0.70 on every seed | gap ≥10pts | MISSED | Average confidence was only about 0.27-0.29 on every seed, so no predictions reach 0.70 and the comparison couldn't be made as written.  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->

Criterion 1 (accuracy): 
**Cause: a task the model can't reach from this much data, not a labelling problem**
My agreement report shows 30/30 agreement with the staff labels, so I applied the labelling rules consistently. I did mention that I found the staff labelling easy but it does not rule out inconsistency in my own 200 labels, especially on `argued` vs `hot_take` borderline posts. The model is barely confident in anything, average confidence was ~0.28, close to random guessing over 4 labels (0.25). Accuracy also swung from 0.27 (seed 7) to 0.63 (seed 2024) just by changing the seed, which shows that ~160 training posts are not enough to learn stable boundaries. The bare label baseline (0.60) beat my trained model, which also points to too little training data rather than bad label.


Criterion 2 (`argued` / `hot_take`):
**Cause: a genuinely hard label pair plus too few examples, not inconsistent labelling**
`hot_take` is my smallest label pair (42 of 200 posts, only 6 in the test set), and the model never predicted it once on any seed. In the confusion matrix, the 6 real `hot_take` posts went to `reaction` (4) and `argued` (2). Even through I was able to label the staff posts correctly this may be because the of the model, where it finds it hard to differentiate a strong opinion without reasons from an emotional reaction or arguement. The labels differ by whether reasons are given, which is subtle for a small model with few examples.

Criterion 3 (`question`):
**Cause: a hard boundary between `question` and `argued`**
5 of the 8 real `question` posts were predicted as `argued`, but only 1 `argued` post went the other way. Many of my question posts include background or an opinion before asking, and those explanation sentences look like the reasoning in `argued` posts. This suggests that the confusion comes from the model focusing on the explanation instead of the question being asked. 

Criterion 5 (confidence):
**Cause: the criterion couldn't be measured as written, and the model is uncertain overall**
The notebook reports accuracy by confidence thrid, no at a 0.70 cut-off. With average confidence of ~0.28, almost no predictions reach 0.70. The top vs bottom thrid gap (+20, +60, +10 points) suggests confidence means something, but with 10 posts per thrid tells this is weak evidence. This is a measurement/model issue, not a labelling one.  

---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** __30_ / 30 = _100%__

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**
None. I matched the staff label on all 30 posts, so there was nothing to sort into (a) consistency problems, (b) gaps or (c) defensible readings.

**Easy set or tight rule?**
I think it the set was easy to label because after reading a couple of the posts I understood the difference between the analysis and hot_take definitions. The reaction posts had a certain format that fit the definition and allowed me to label it as reaction. 


---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
