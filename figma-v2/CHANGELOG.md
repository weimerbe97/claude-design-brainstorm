# SVG Update — v2

Updated SVG set responding to SVP feedback on the original design.

## What changed

### Typography simplification (7 styles → 3)

The earlier set used 7 different font-size/weight combinations across the card. The new set uses just three:
- **Hero**: 26px / 500 weight (savings amount only)
- **Body**: 13px / 400 weight (everything textual)
- **Button**: 13px / 500 weight

Visual hierarchy now comes from the size jump between hero and body, not from layering more weight variants. Easier to maintain, less visual noise.

### Monotone icons

All decorative icons now use the same color as the adjacent text (`#5A5A55` for body, `#1A1A1A` for emphasized). The earlier set had colored icons in colored containers (e.g., a navy tag in a white circle on a beige card) which created attention contention with the actual value content.

### Social proof simplified

The "1,842 shoppers saved here today" treatment was previously inside a nested card with a circular icon container. Now it's a single inline line with a small monotone icon, matching the visual weight of the disclosure link. Same message, dramatically less footprint.

### Spinner toned down

In the earlier set, the loading spinner was framed by a horizontal rule and sized at 16px — it read as its own section of the notification. The new spinner is 10px with a 1.5px stroke, sits inline without a divider, and the copy reads "Also checking for codes" (was "Checking for codes…"). Reframes the loading state as ambient/supplemental rather than blocking.

### Rewards amount: rate-only framing

**This is the most important change.** The earlier set showed "$3.64 back" as the hero number, calculated from the cart total. This created an expectation problem: rewards apply only to eligible items, and the actual payout could be lower than the displayed number.

The new default shows **"Up to 30% back on eligible items"** — the rate is concrete, the constraint is explicit, and no specific dollar amount is promised until eligibility is determined.

A second variant (`state-1b-first-paint-with-ceiling.svg`) shows the rate-plus-ceiling alternative — **"Up to $54.60 back, 30% on eligible items, $182 cart"**. This frames a dollar number as a ceiling (the maximum if every item is eligible) rather than a promise. Worth testing against the rate-only version.

## Files

```
figma/svg/
├── state-1-first-paint.svg                    Rate-only framing (default)
├── state-1b-first-paint-with-ceiling.svg      Rate + ceiling variant
├── state-2a-rewards-only.svg                  Inline social proof, no card
├── state-2b-codes-ready.svg                   Codes + proof as parallel inline lines
├── state-3a-3b-rewards-activated.svg          Inline exclusions, simplified support text
├── state-3c-testing-codes.svg                 Monotone code list, lighter spinner
├── state-4a-code-rewards-win.svg              Flat receipt, no card wrapper
├── state-4b-codes-failed.svg                  Reframed copy, monotone treatment
├── state-5-checkout-pin.svg                   Refined pin copy
└── state-6-post-purchase.svg                  Flat receipt structure
```

## What stayed the same

- The state flow itself (1 → 2a/2b → 3 → 4 → 5 → 6) is unchanged
- The notification triggers on the same URLs at the same time
- The lifetime savings header pattern is preserved (still ticks up on activation)
- The codes-testing live list pattern is preserved (just visually simpler)
- The exclusions tooltip + inline disclosure pattern is preserved

## For Adam (SVP) review

The two open questions worth Adam's input:

1. **Rate-only vs rate-plus-ceiling**: which framing better balances persuasiveness against expectation-setting? Both are legally defensible. State 1 (rate-only) is the safer pitch; State 1b (rate + ceiling) is more compelling but exposes a specific dollar number.

2. **"Up to 30% back" vs alternative rate copy**: the placeholder uses 30% as the example. For lower-rate merchants (e.g., 2% back), does "Up to 2% back" still feel motivating, or do we need a different framing for low-rate cases?
