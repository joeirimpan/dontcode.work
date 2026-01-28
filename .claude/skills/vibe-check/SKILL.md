---
name: vibe-check
description: Decide whether Claude should code a feature or the user should write it themselves
user-invocable: true
argument-hint: [feature description]
---

# Vibe Check - Should I Code This?

When the user describes a feature or task, evaluate it against these 7 criteria and decide whether Claude should code it ("vibe it") or the user should write it themselves.

## Evaluation Criteria

Rate each from 1-10 mentally, then apply the weights:

| Criteria | Weight | Higher value means... |
|----------|--------|----------------------|
| **Boilerplate level** | 20% | More boilerplate → Claude codes |
| **Learning value** | 20% | More learning → User codes |
| **Code commonality** | 15% | More common pattern → Claude codes |
| **Joy factor** | 15% | More enjoyment → User codes |
| **Urgency** | 15% | More urgent → Claude codes |
| **Complexity** | 10% | More complex/interconnected → User codes (needs control) |
| **Ego check** | 5% | Avoiding AI feels like "cheating" → Claude codes (get over it) |

## Scoring

Calculate: `score = Σ(weight × adjusted_value)`
- For "Claude codes" criteria: use value directly
- For "User codes" criteria: use (10 - value)

## Verdicts

Based on the final percentage:
- **>65%**: "Just vibe it. Your ancestors debugged assembly so you wouldn't have to."
- **55-65%**: "Vibe it. Life's too short for boilerplate."
- **50-54%**: "Vibe it, but maybe skim the output."
- **50%**: "Flip a coin. Or just ask Claude—same energy."
- **46-49%**: "Write it yourself... if you must."
- **35-45%**: "Okay, write it by hand. This one's worth it."
- **<35%**: "Go full artisan. We respect the craft."

## Your Task

When invoked with `/vibe-check [feature]`:

1. Briefly evaluate the feature against each criterion
2. Show your scoring reasoning in a compact table
3. Calculate the weighted score
4. Deliver the verdict
5. Then either:
   - If "vibe it": Offer to implement it
   - If "write it yourself": Explain what concepts the user would learn by doing it manually

## Example Output Format

```
## Vibe Check: [Feature Name]

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Boilerplate | 8 | Standard CRUD pattern |
| Learning | 3 | Nothing new here |
| ... | ... | ... |

**Score: 62%**
**Verdict: Vibe it. Life's too short for boilerplate.**

Want me to implement this?
```

Feature to evaluate: $ARGUMENTS
