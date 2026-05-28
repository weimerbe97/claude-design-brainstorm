# Microcopy Test Agenda

A parallel track of small, low-risk copy experiments that can run continuously throughout the major redesign rollout. Each test is scoped to a single phrase or label change — engineering lift is minimal, and the tests fit comfortably on a 5–10% traffic slice without interfering with the main roadmap.

## How to use this agenda

Each test is structured the same way:

- **Element**: which UI piece is being tested
- **Variants**: the copy options to compare (one of which is always the current production wording)
- **Hypothesis**: what we expect to move and why
- **Primary metric**: the one number we're optimizing for
- **Notes**: any constraints, sequencing dependencies, or things to watch

Run on a dedicated 5–10% slice of traffic. With 5–8M daily impressions, expect statistically significant reads in 3–7 days for the lifts we'd typically see (1–3% on activation, 0.5–1.5% on completion). Run for the full week regardless to capture weekend behavior.

Tests are roughly ordered by expected impact — start with #1.

---

## Pre-decision states (notification visible, user hasn't engaged)

### Test M1 — Primary CTA verb on rewards-only

**Element**: The primary button on the rewards activation notification.

**Variants**:
- A (control): `Activate rewards`
- B: `Get 2% back`
- C: `Start earning rewards`

**Hypothesis**: "Get 2% back" leads with the outcome (the dollar value) rather than the mechanism (activating), which should lift click-through. "Start earning" frames it as ongoing rather than transactional.

**Primary metric**: Click-through rate on the primary CTA.

**Notes**: Once a winner is identified, lock that pattern in for downstream tests — the rest of the agenda assumes the activate verb is settled.

---

### Test M2 — Cart-specific dollar framing

**Element**: The subline below the hero savings amount.

**Variants**:
- A (control): `2% on your $182 Sephora cart`
- B: `That's $3.64 back on this order`
- C: `You'll get $3.64 back from Sephora`

**Hypothesis**: Restating the dollar amount in the subline (vs the percentage and cart total) reinforces the concrete benefit. Variant C personalizes ("you'll get") which should outperform the more neutral framings.

**Primary metric**: Activation rate.

**Notes**: Skip this test if the savings amount is already in the hero element above it — redundancy might tank the variant.

---

### Test M3 — Social proof framing

**Element**: The trust signal line on the rewards card.

**Variants**:
- A (control): `1,842 shoppers activated at Sephora today`
- B: `1,842 people saved at Sephora today`
- C: `Sephora shoppers saved an average of $14 this week`
- D: `Joined by 1,842 shoppers at Sephora today`

**Hypothesis**: "Saved" is more outcome-focused than "activated" but may be harder to defend legally. The average framing avoids count fragility on small merchants. The "joined by" framing leans on social belonging rather than pure proof.

**Primary metric**: Activation rate.

**Notes**: Confirm each variant with legal before launching. "Saved" implies an outcome we may not be able to verify per-user.

---

### Test M4 — Secondary dismiss copy

**Element**: The "soft dismiss" link/button below the primary CTA.

**Variants**:
- A (control): `No thanks`
- B: `Not this time`
- C: `Maybe later`
- D: `Skip for now`

**Hypothesis**: "No thanks" is psychologically harder to click than softer alternatives — it requires the user to declare a stronger preference. Softer phrasings should *increase* the dismissal rate, which is good (it means users who dismiss are doing so deliberately rather than ignoring the notification).

**Primary metric**: Order completion rate for users who dismiss (not the dismissal rate itself). The goal is to see whether dismissers complete orders at a higher rate when dismissal feels low-friction.

**Notes**: This is a counterintuitive test — leadership might worry about dismissal rate going up. Frame the metric carefully.

---

### Test M5 — Codes-available CTA

**Element**: The combined primary CTA when codes are present.

**Variants**:
- A (control): `Try codes + activate rewards`
- B: `Apply codes + activate rewards`
- C: `Save with codes + 2% back`
- D: `Find savings`

**Hypothesis**: "Try" implies uncertainty; "Apply" implies confidence. "Save" leads with outcome. "Find savings" is the most aggressive shortening — risks losing clarity but maximizes urgency.

**Primary metric**: Click-through rate on the primary CTA, segmented by whether the codes ultimately succeeded.

**Notes**: Watch the secondary metric carefully — if "Apply" lifts CTR but codes often fail, user trust may erode in subsequent sessions.

---

### Test M6 — Codes loading state copy

**Element**: The "Checking for codes…" footer during progressive load.

**Variants**:
- A (control): `Checking for codes…`
- B: `Looking for savings…`
- C: `Scanning for deals…`
- D: `Finding codes that work…`

**Hypothesis**: "Codes" is jargon — "savings" or "deals" is more universally understood. "That work" hints at the testing process and may build trust.

**Primary metric**: Activation rate among users who arrive when codes are still loading (a session-level segment).

**Notes**: Variant D may set expectations that *get* violated when codes don't work — watch the post-failure activation rate carefully.

---

## Post-decision states (user has engaged)

### Test M7 — Success state headline

**Element**: The headline on the rewards activation success state.

**Variants**:
- A (control): `Rewards activated`
- B: `You're earning 2% back`
- C: `2% back is on its way`
- D: `Done — 2% back unlocked`

**Hypothesis**: Active progressive ("you're earning") feels more rewarding than the past-tense system message. The "unlocked" framing borrows gaming language and may resonate, but could feel out of brand.

**Primary metric**: Time-to-checkout-completion (does the user feel "done" enough to proceed quickly?).

---

### Test M8 — Code-success line item label

**Element**: The line item label in the receipt when a code applied successfully.

**Variants**:
- A (control): `Code applied`
- B: `Saved with code`
- C: `Discount applied`
- D: `Code: BROWSHADE`

**Hypothesis**: "Saved" is the user's emotional frame, not "applied" (which is the system's frame). Variant D embeds the code name directly, removing the need for a separate code line — cleaner but loses the "we found this for you" narrative.

**Primary metric**: Order completion rate (does perceived value affect cart abandonment?).

---

### Test M9 — Codes-failed honesty framing

**Element**: The note explaining that no codes worked.

**Variants**:
- A (control): `We tested all 5 codes — none applied to your cart this time.`
- B: `No codes worked for this cart, but rewards still apply.`
- C: `Codes didn't apply this time. Your 2% back is still on.`
- D: `No discount codes for this cart today.`

**Hypothesis**: Variant A leads with the work done before delivering the news; variant B leads with the bad news but immediately pivots. Variant D is the most clipped and least apologetic — may actually outperform if users want the facts fast.

**Primary metric**: Activation rate from this state (does the user still activate rewards after the codes-failed message?).

**Notes**: This is the most emotionally loaded copy in the system. Worth running in two consecutive cycles to confirm the winner replicates.

---

### Test M10 — Disclosure prefix

**Element**: The "Exclusions apply:" prefix on the inline disclosure text.

**Variants**:
- A (control): `Exclusions apply:`
- B: `Important:`
- C: `Note:`
- D: No prefix, just the body text

**Hypothesis**: The current prefix is technical and may signal "fine print, skip this." Softer prefixes might actually *increase* the chance users read the disclosure — counterintuitively making the legal team happier.

**Primary metric**: Disclosure-read rate (measurable via tooltip hover or scroll-into-view events) AND order completion rate. Want to confirm we're not hurting trust.

**Notes**: Legal must approve all four variants before testing. Some jurisdictions require specific framing.

---

## Persistent / contextual elements

### Test M11 — Lifetime Savings label

**Element**: The label beside the lifetime savings amount in the header.

**Variants**:
- A (control): `Lifetime Savings`
- B: `Total saved`
- C: `Your savings`
- D: `Saved with us`

**Hypothesis**: "Lifetime" is a long, formal word. Shorter alternatives may feel more conversational and increase the chance users actually notice and value the number.

**Primary metric**: Session return rate (does noticing the lifetime number drive repeat engagement?).

**Notes**: This is a slow-read test — return rate impacts are best measured over 3–4 weeks.

---

### Test M12 — Exclusions tooltip text

**Element**: The body of the exclusions tooltip on pre-decision states.

**Variants**:
- A (control): `Not eligible for purchases of gift cards, or on orders deemed by Sephora to be for reseller activity.`
- B: `Some items don't qualify — including gift cards and bulk/reseller orders.`
- C: `Excludes gift cards and orders flagged as reseller activity by Sephora.`

**Hypothesis**: Plain-language variants are easier to parse quickly, which may *reduce* hesitation. Variant A is closer to legal-team original; B and C are progressively friendlier.

**Primary metric**: Activation rate among users who hovered/tapped the tooltip.

**Notes**: Must clear legal review. Per-merchant variations exist — this test only applies to merchants with this specific disclosure template.

---

### Test M13 — Checkout pin content

**Element**: The text on the slim corner pin during checkout.

**Variants**:
- A (control): `$3.64 back ready`
- B: `2% back applied`
- C: `Rewards locked in`
- D: `$3.64 saved`

**Hypothesis**: "Ready" implies pending action; "applied" implies done; "locked in" is the most reassuring. Variant D claims savings as a past-tense win, which may be the strongest framing but could be technically inaccurate at the pin stage.

**Primary metric**: Order completion rate (the pin's job is to not distract — measure whether different framings affect cart abandonment).

**Notes**: Variant D should be confirmed accurate before testing. If rewards are still pending at the pin stage, "saved" is misleading.

---

### Test M14 — Post-purchase total framing

**Element**: The bottom-line summary on the post-purchase confirmation.

**Variants**:
- A (control): `Saved on this order: $21.48`
- B: `You saved $21.48 today`
- C: `Total savings: $21.48`
- D: `$21.48 back in your pocket`

**Hypothesis**: "Back in your pocket" is the most emotional framing — risky on brand, but may resonate. Personal pronouns ("you saved") generally outperform impersonal phrasings in confirmation moments.

**Primary metric**: Click-through rate on the "See all my savings" CTA below.

---

### Test M15 — Post-purchase secondary CTA

**Element**: The CTA on the post-purchase confirmation that pulls users into the broader platform.

**Variants**:
- A (control): `See all my savings`
- B: `View savings history`
- C: `Track my rewards`
- D: `Open my account`

**Hypothesis**: "See all my savings" implies a comprehensive view but is vague about *what* the user will see. More specific framings ("history," "rewards") may pull better-qualified clicks.

**Primary metric**: Click-through rate, but track *bounce rate from the destination* as well — vague CTAs may inflate clicks while disappointing on arrival.

---

## Stretch / experimental

### Test M16 — Urgency framing on social proof

**Element**: Adding a recency qualifier to the social proof line.

**Variants**:
- A (control): `1,842 shoppers activated at Sephora today`
- B: `142 shoppers activated at Sephora in the last hour`
- C: `1,842 shoppers activated at Sephora today — join them`

**Hypothesis**: Hour-window numbers feel more urgent than day-window numbers. The "join them" addition is a direct call-to-action embedded in the proof.

**Primary metric**: Activation rate.

**Notes**: Requires merchant-level hourly activation counts to be queryable. Hourly numbers are smaller — make sure the floor logic doesn't kick in awkwardly.

---

### Test M17 — Personalized lifetime framing

**Element**: A new line on the rewards card for returning users.

**Variants**:
- A (control): No additional line
- B: `You've saved $792 with us at other stores`
- C: `Welcome back — $792 saved so far`

**Hypothesis**: Surfacing the user's existing relationship with the brand on a non-final state may increase trust and activation. The risk is increasing visual noise on a state we just simplified.

**Primary metric**: Activation rate, segmented by lifetime savings tier (does this work for high-lifetime users but not new ones?).

**Notes**: Only run on users with lifetime savings > $50. Below that, the number isn't motivating.

---

### Test M18 — Reframe rewards as a setting

**Element**: The activation CTA on the rewards-only state.

**Variants**:
- A (control): `Activate rewards`
- B: `Turn on 2% back`
- C: `Enable rewards for Sephora`
- D: `Add 2% back to Sephora`

**Hypothesis**: Framing rewards as a setting ("turn on," "enable," "add") instead of an action ("activate") may feel lower-commitment, which lifts conversion. Setting language also implies ongoing benefit.

**Primary metric**: Activation rate AND deactivation rate over the following 30 days (does setting language reduce later regret?).

---

### Test M19 — Cart value contextualizing

**Element**: The cart subline on activations with low cart values.

**Variants**:
- A (control): `2% on your $12 cart`
- B: `2% on this order — and every Sephora order`
- C: `Earn on this cart and your next one`
- D: `Every cent counts — 2% back, every time`

**Hypothesis**: When the immediate dollar amount is small (e.g., $0.24 on a $12 cart), pivoting to ongoing-value framing should outperform leading with the unimpressive number.

**Primary metric**: Activation rate on low-cart-value sessions specifically.

**Notes**: Define "low" as below $25. Only triggers on that segment.

---

### Test M20 — Brand voice exploration

**Element**: The hero eyebrow text on the rewards-only state.

**Variants**:
- A (control): `Earn rewards on this order`
- B: `Cash back available`
- C: `Money's on the table`
- D: `Quick savings`

**Hypothesis**: Casual brand voice ("money's on the table") may outperform formal phrasings in capturing attention — or may feel off-brand. Worth testing in a controlled slice to learn what voice register works for the audience.

**Primary metric**: Activation rate.

**Notes**: Run only after brand team alignment. Variant C is deliberately provocative — drop it if it doesn't pass internal review.

---

## Operational notes

**Sequencing**: Run no more than three tests simultaneously to keep attribution clean. Track which test won at each slot so cumulative copy improvements compound.

**Holdout cohort**: Reserve 5% of users to see the original production copy throughout — this lets you measure the cumulative lift of all microcopy wins at the end of each quarter.

**Segment cuts**: Run each test's primary read across at least: logged-in vs guest, mobile vs desktop, returning vs new user, and top 5 merchants by volume. With your traffic, all of these are statistically tractable.

**Loser archive**: Document every losing variant with the data — these archives are valuable for arguing against future "let's just retry this" suggestions.

**Winner application**: When a microcopy test wins, the new copy ships globally within one week. Don't let winners sit in the experiments tool.
