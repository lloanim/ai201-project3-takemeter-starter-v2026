# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## 1. The held out accuracy is at least 0.60 on every one of the three seeds

**Why this target:**
There is a hard case between the lables `argued` and `hot_take` where its determined if its one over the other through the reason of "having concrete explaination" and its a point the model may miss. I set it at 0.60 because the test split is of 30 posts, so the score can shift several points between the three seeds and the target has to hold on all of them.


---

## 2. `argued` and `hot_take` each have an F1 of at least 0.50 on all three seeds

**Why this target:**
These two labels are the hardest case where I mention in my rule that naming a game or listing examples does not count as support, but the model could use the listing of games as `argued`. I set the bar lower than others because I think its a distinction it could take longer to learn.

---

## 3. `question` has an F1 of at least 0.75 on all three seeds


**Why this target:**
It is easier to determine the format of a question with key words of "can I", "should I", etc. It also has a punctuation of "?" that allows the model determine the post as question. 


---

## 4. Every label makes up at least 15% (30 posts) and at most 40% (80 posts) of my 200 labelled posts


**Why this target:**
I set 30 posts as minimum because the test split is 15% so a label with 30 posts gets only about 5 test posts, which is barely enough for the F1 score to mean something. Over 80 posts would make the model over predict that label. 

---

## 5. Predictions with confidence of 0.70 or higher are right at least 10 points more often than predictions below 0.70 on every seed

**Why this target:**
Both `reaction` and `argued` include personal experience but the difference is if that experience is used as a reason for a claim. I expect the model to be unsure on posts like that, so its confidence should drop there. I choose 10 point difference because with about 30 test posts, one or two posts can swing a group's accuracy by 5-10 points, so a smaller gap would not tell me much.  


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
