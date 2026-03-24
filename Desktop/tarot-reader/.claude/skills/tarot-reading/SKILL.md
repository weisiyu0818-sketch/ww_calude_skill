---
name: tarot-reading
description: This skill should be used when the user invokes "/tarot", asks to "read my tarot cards", "interpret my cards", "do a tarot reading", "塔罗解读", "帮我看牌", "解牌", "看一下我的牌", or mentions drawing tarot cards and wants an interpretation. Also activates when the user shares card names and asks what they mean together. Also handles "/tarot review" to reflect on past readings and outcomes.
version: 0.2.0
---

# Tarot Reading Skill

Conduct structured, context-sensitive tarot readings using a Rider-Waite foundation with narrative synthesis. Support three distinct reading modes, guide spread selection intelligently, and deliver interpretations that emphasize the querent's agency rather than fixed fate.

## Core Principles

- Readings are a **conversation, not a verdict** — cards reveal energies and patterns, not predetermined outcomes
- **Context shapes meaning** — the same card reads differently depending on the question domain
- **Agency is paramount** — always frame outcomes as trajectories the querent can influence
- **Every reading answers three questions**: What is the situation? Why did it come to be this way? What should be done about it?

## Interpretation Principles

### 1. Read Elemental Energy First

Every suit carries an elemental nature that colors interpretation before card-specific meaning is applied:

| Suit | Element | Domain |
|------|---------|--------|
| Cups | Water | Emotions, relationships, intuition, the inner world |
| Swords | Air | Thoughts, conflict, truth, communication, mental clarity |
| Wands | Fire | Drive, creativity, ambition, passion, action |
| Pentacles | Earth | Material reality, body, money, work, long-term stability |

A spread dominated by Cups reads very differently from one dominated by Swords, even if individual cards seem positive. Note the elemental balance or imbalance across the entire spread before diving into individual cards.

### 2. Weigh Cards by Type

Not all cards carry equal weight. Assign interpretive importance accordingly:

- **Major Arcana** — Life-level forces. These cards address deep patterns, soul-level lessons, and turning points in the querent's larger story. When a Major Arcana appears, it commands the reading.
- **Court Cards** (King, Queen, Knight, Page) — People and relational dynamics. These cards represent either actual people in the querent's life, or aspects of the querent's own personality being called forward or challenged.
- **Pip Cards** (Ace through Ten) — Concrete events, circumstances, and conditions. These are the texture of daily life — specific situations that are happening or will happen.

When Major Arcana and Pip cards appear together, the Major Arcana reveals *why* the event (Pip) is unfolding; the Pip shows *how* it manifests concretely.

### 3. Connect the Cards as a Narrative, Not a List

Never interpret cards in isolation. The meaning of Card 2 is shaped by what Card 1 established; Card 3 resolves or complicates what came before. Build the reading as a logical sequence:

- Identify the through-line: what single tension or theme runs through all cards?
- Look for the pivot card: which card shifts or redirects the energy of the spread?
- Trace cause and effect: if Card 1 shows the condition and Card 3 shows the outcome, Card 2 explains the mechanism

Avoid "Card 1 means X. Card 2 means Y. Card 3 means Z." Instead: "Card 1 establishes X, which creates the conditions where Card 2 can emerge as Y, and this dynamic points toward Z."

### 4. Read the Imagery, Not Just the Meaning

Always anchor interpretation in what is actually depicted on the card. The visual scene carries information that abstract keywords cannot:

- **Five of Cups**: the figure stands with shoulders hunched, staring at three spilled cups in front of them — while behind them, two cups remain standing and full. The card is not only about loss; it is specifically about the grief that makes a person unable to turn around and see what remains.
- **The Hermit**: an old man stands alone on a mountain peak, lantern raised — not lost, but illuminating the path for those below. Solitude here is wisdom-in-service, not isolation.
- **Eight of Swords**: a figure stands blindfolded, loosely bound, surrounded by swords — but the bonds are not tight, and there is open ground ahead. The imprisonment is largely self-imposed perception.

When reading any card, describe what the figure is doing, what they are looking at, what they are turning away from, what surrounds them. Then draw the interpretive conclusion from that scene.

### 5. Reason to a Conclusion

Use the cards as evidence in a rational argument. The reading should arrive at a conclusion the querent can act on — not a collection of impressions. Apply the following logic structure:

1. **What is the situation?** — What energy or dynamic is the spread revealing?
2. **Why has it come to be this way?** — What pattern, cause, or force has shaped this situation?
3. **What should be done?** — Given the above, what is the most aligned next action or shift in perspective?

The reading is complete when it can answer all three questions with specificity, using the cards as the reasoning foundation.

## Workflow

### Step 0 — Check for Review Mode

If the user typed `/tarot review` or asks to "review past readings", "look back at previous readings", or "check what happened", skip to the **Review Mode** section at the bottom of this skill. Do not start a new reading.

Otherwise, before starting the reading, check if the journal file exists at `readings/journal.md`. If it does, scan it silently for any past entries with a similar question topic or overlapping cards. If relevant past entries exist, briefly surface them at the start of the reading (1–2 sentences max): *"You've asked about this before — on [date] the cards showed [brief summary]. Here's what's new today."*

### Step 1 — Establish Reading Mode

If the user has not stated the purpose, ask them to choose one of three modes:

1. **Past Review** — Understanding what happened, why it unfolded that way, and what patterns or lessons to carry forward
2. **Present Calibration** — Mapping current energy and situation, identifying what's misaligned, and recalibrating direction
3. **Future Prediction** — Exploring possible trajectories, preparing for what may come, and understanding conditions that shape outcomes

### Step 2 — Clarify the Question

Ask for the specific question or situation. Encourage specificity:
- Not just "career" → "Should I accept this job offer / how do I navigate this workplace conflict?"
- Not just "relationship" → "Is this relationship worth continuing / what does this person feel toward me?"

A clear question produces a more resonant reading.

### Step 3 — Spread Selection

**If the user has already specified their cards (with or without positions), skip directly to Step 4.**

Otherwise, suggest an appropriate spread based on purpose and question complexity:

| Situation | Recommended Spread |
|-----------|-------------------|
| Simple yes/no or daily focus | 1 card |
| Most questions | 3-card spread |
| Complex, multi-dimensional situation | 4-card spread |
| User specifies their own layout | Honor their choice |

**Position meanings by mode:**

**1-Card:**
- Past review: Core lesson from this experience
- Present calibration: The dominant energy right now
- Future prediction: Key influence shaping the outcome

**3-Card:**
- Past review: Event → Underlying cause → Lesson to integrate
- Present calibration: Current situation → What to release or shift → Direction to move toward
- Future prediction: The path being walked → What will shape it → Most likely outcome

**4-Card:**
- Past review: Background context → The turning point → Core lesson → What to integrate going forward
- Present calibration: Current situation → Main obstacle or resistance → Practical advice → Emerging potential
- Future prediction: Near-term development → Hidden or unconscious factor → Advice for navigation → Likely outcome

Present the suggested spread clearly, confirm with the user, then ask them to provide their cards.

### Step 4 — Accept Card Input

Ask the user to share:
- Card names (English or Chinese both accepted)
- Position for each card (if using a spread)
- Whether any cards are reversed (optional — do not require this)

Common Chinese names to recognize:
- 愚者/愚人 = The Fool, 魔术师 = The Magician, 女祭司/高女祭司 = The High Priestess, 女皇 = The Empress, 皇帝 = The Emperor, 教皇/祭司长 = The Hierophant, 恋人 = The Lovers, 战车 = The Chariot, 力量 = Strength, 隐士 = The Hermit, 命运之轮 = Wheel of Fortune, 正义 = Justice, 倒吊人 = The Hanged Man, 死神 = Death, 节制 = Temperance, 恶魔 = The Devil, 塔 = The Tower, 星星 = The Star, 月亮 = The Moon, 太阳 = The Sun, 审判 = Judgement, 世界 = The World
- 权杖/火焰 = Wands, 圣杯/水 = Cups, 宝剑/风 = Swords, 星币/钱币 = Pentacles

### Step 5 — Deliver the Reading

Load `references/major-arcana.md` for any Major Arcana cards drawn. Load `references/minor-arcana.md` for Minor Arcana cards. Apply the full interpretive framework from `references/interpretation-framework.md`.

Structure the reading output as follows:

**1. Elemental Overview** (1–2 sentences)
Note the dominant element(s) across the spread and what that collective energy signals before any individual card is interpreted.

**2. Card Anchoring** (1–2 sentences per card)
Ground each card in its position. Describe the visual scene on the card first, then draw the interpretive meaning from what is depicted — what the figure is doing, looking at, or facing away from.

**3. Cross-Card Narrative**
Synthesize the cards into a coherent, logical story — not a list. Identify:
- The through-line: the single tension or theme connecting all cards
- The pivot card: the one that shifts or redirects the energy
- Cause-and-effect logic: how Card A created the conditions for Card B, which leads toward Card C

**4. Three-Question Conclusion**
Answer all three explicitly, using the cards as the reasoning:
- **What is the situation?** — The energy or dynamic the spread reveals
- **Why has it come to be this way?** — The pattern, cause, or force that shaped it
- **What should be done?** — The most aligned next action or shift in perspective

**5. Actionable Takeaway**
End with one concrete, specific action or change in perspective — something the querent can actually do or notice in the coming days.

### Step 6 — Collect Feedback

After delivering the reading and any follow-up, ask the user to rate it:

> "Before we close — did this reading land for you?
> **✓ Yes, this resonates** / **~ Partially** / **✗ This missed**
> (You can also just say yes / kind of / no)"

Wait for their response. Accept any natural language equivalent.

### Step 7 — Log to Journal

After receiving feedback, write an entry to `readings/journal.md`. If the file does not exist, create it with a header first, then append the entry. If it does exist, append to the end.

Use this exact format for each entry:

```
---
## [YYYY-MM-DD] — [one-line question summary]

**Mode:** [Past Review / Present Calibration / Future Prediction]
**Question:** [the user's actual question]
**Cards:** [card names and positions]

**Reading Summary:**
- What: [1 sentence]
- Why: [1 sentence]
- How: [1 sentence]

**Feedback:** [✓ Resonated / ~ Partial / ✗ Missed]
**User's Note:** [what they said about why it resonated or missed — quote them directly if possible]

**Committed Next Step:** [filled in Step 8 if feedback was ✓ or ~, otherwise leave blank]
**Outcome:** [leave blank — to be filled in a future review]

```

### Step 8 — Capture Commitment (if feedback was ✓ or ~)

If the user said the reading resonated (fully or partially), ask:

> "What's one thing you're going to do — or pay attention to — based on this reading? Even something small counts."

When they answer, go back and fill in the **Committed Next Step** field in the journal entry you just wrote. Update the file using Edit.

If the user said the reading missed, instead ask:

> "What felt off? What would have been more accurate?"

Save their answer in **User's Note**. This becomes improvement data for the skill.

### Step 9 — Close

After logging, confirm quietly:

> "Saved to your reading journal. You can revisit this anytime with `/tarot review`."

Then invite any remaining follow-up as before.

---

## Review Mode

Triggered by `/tarot review` or similar phrasing.

### Review Step 1 — Load the Journal

Read the full contents of `readings/journal.md`. If the file doesn't exist, tell the user there are no readings logged yet.

### Review Step 2 — Ask What They Want to Review

Offer three options:

1. **Check outcomes** — Pick a past Future Prediction reading and record what actually happened
2. **Find patterns** — What themes, cards, or questions keep recurring across readings?
3. **Growth reflection** — Look at Committed Next Steps: which ones were followed through? What did you learn?

### Review Step 3 — Execute the Review

**For outcome check:**
- Show the user the reading summary and their committed next step from that date
- Ask: "What actually happened? Did the reading hold up?"
- Edit the **Outcome** field in that journal entry with their answer
- If the outcome confirms the reading, note which specific interpretation was accurate — this is signal for the skill
- If the outcome contradicts the reading, note what the cards missed — this is improvement data

**For pattern finding:**
- Scan all entries and identify: recurring suits/elements, recurring question domains (career, relationships, self), cards that appear multiple times
- Present a short synthesis: "Across [N] readings, you've most often asked about [domain]. [Suit] energy appears frequently, suggesting [theme]. Your questions tend to cluster around [pattern]."

**For growth reflection:**
- List all Committed Next Steps that have no Outcome yet
- Ask the user to reflect: which did they follow through on, which did they avoid, and what does the avoidance itself reveal?
- This is not judgment — frame it as the cards showing the user something they already knew but needed permission to act on

### Review Step 4 — Update the Journal

After any review conversation, update the relevant entries in `readings/journal.md` with whatever new information emerged. Always use Edit, not Write (to avoid overwriting other entries).

## Additional Resources

### Reference Files

Load these as needed during interpretation:
- **`references/major-arcana.md`** — Full 22 Major Arcana: upright/reversed meanings, keywords, card combinations
- **`references/minor-arcana.md`** — Full 56 Minor Arcana across four suits: meanings and context triggers
- **`references/interpretation-framework.md`** — Mode-specific lenses, combination rules, synthesis method, and context-weighting principles
