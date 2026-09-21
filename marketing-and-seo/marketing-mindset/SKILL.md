---
name: marketing-mindset
description: Apply a working marketer's operating mindset to acquisition decisions — sizing a test before judging it, choosing what to do with zero paying clients, benchmarking against competitors with live motion, and deciding when to kill a channel. Use when the user asks where their first customers will come from, whether doing X will produce Y, how to write an ad or landing page, how many sends a cold email test needs, or whether a channel should be stopped. Distinct from content-strategy and keyword-research, which produce artifacts; this skill produces a verdict with the reasoning attached.
license: MIT
metadata:
  author: awesome-ai-agent-skills
  version: 1.0.0
---

# Marketing Mindset

This skill gives an agent the decision layer under acquisition work: what to do, how much volume a result needs before it means anything, and when to stop. It is deliberately not a tactic library — the neighbouring skills in this category produce artifacts (a content plan, a keyword set, an SEO report), while this one produces a decision and states the number that settles it.

It is most useful for early-stage B2B and SaaS work, where the honest answer is often "not enough data yet" or "stop doing this", and where a confident-sounding tactic list actively costs the user money.

## Required Inputs

- What is being sold, to whom, and at what price. A missing audience or offer blocks a verdict on positioning.
- The number of paying clients today and the channel that produced them. Unknown counts get treated as zero until stated.
- The budget and the target cost per acquisition, when paid channels are in question. Without a target CPA the skill cannot evaluate ad spend.
- Any test results already collected, together with the volume behind them. Results without their sample size are not evidence.
- Which missing inputs permit a documented assumption (channel choice, wording) and which block work (offer, price, audience).

## Output Contract

- A single verdict: run it, change one variable and rerun at a stated volume, or stop and do something else.
- The reasoning behind the verdict, naming the specific number, threshold or competitor observation it rests on.
- When the answer is "not enough data yet", the exact volume required before the question can be answered, and the cost of reaching it.
- Assumptions separated from verified facts, with anything the user supplied labelled as their report rather than as checked data.
- Deliverables for the current stage only: client #1 and the first ten are in scope; scaling past ten is not.

## Workflow

1. **Check the exchange.** Marketing is an exchange, and every action must trade for money, qualified prospects, or something applicable immediately. State what the proposed action trades for. If the exchange is zero, say so and name the missing half before discussing tactics.

2. **Establish the business state.** Ask for the paying-client count and the channel that produced them. With zero clients, the only honest advice is hand-won outreach plus the founder using their own product; money in this state buys noise rather than learning. Money is a scaling instrument, so treat paid channels as out of scope until a channel is already converting.

3. **Ground the hypothesis in live competitors.** Benchmark against companies reaching the same audience right now and making money from it, especially recently founded ones whose moves are short and copyable. Treat launch sites, ranking lists and influencer endorsements as advertising rather than as evidence, and treat any report older than six months as history.

4. **Size the test before judging it.** Below a floor the result measures randomness, not the market. Declare the floor before the test starts and refuse a conclusion below it:

   | Channel | Minimum volume before a verdict |
   |---|---|
   | Cold email, deliverability or wording smoke test | 50–100 sends |
   | Cold email, reply-rate comparison | ~1,500–2,000 sends per variant |
   | Subject-line or open-rate test | 100–500 sends per version |
   | Landing page smoke test | 100–200 targeted visitors |
   | Paid ad | 1–3x target CPA over 48–72 hours |
   | Strict A/B test | ~10,000 visitors and 300+ conversions per variation |

5. **Apply a kill rule, not a feeling.** Decide in advance what keep, re-hook and stop look like, then hold that decision at the declared volume. Stopping a channel that cannot pay back within the stated budget is a result, not a failure — it returns the capacity a weak channel consumes quietly.

6. **Write for attention, then for proof.** Attention divides into a part reachable with numbers and a part that answers only to feeling; both need addressing. In visuals the eye resolves sharply only in a small focal area, so a creative needs a background, a scene, one hero subject and implied movement. In copy the reader is thinking about themselves, so content that lets them keep doing that outperforms content about the product.

7. **Return the verdict with its evidence.** State the decision, the number that settles it, and what would change your mind. When the obvious options have already been tried and failed, say that plainly instead of producing another reasonable variant — the reasonable variant is what everyone already tested.

## Safety and Permissions

- Do not fabricate testimonials, case studies, logos, user counts or results. Framing an offer around intended value is legitimate; inventing proof is not.
- Require explicit approval before spending money, sending outbound messages at volume, or publishing under the user's brand, and confirm the sending domain and warmup state before any cold email volume is planned.
- Preserve the user's original claims and numbers; correct them openly rather than adjusting them silently.
- Do not advise scraping or contacting people through channels that the user has no lawful basis to use.

## Verification

- Every verdict is tied to a number: a client count, a spend figure, a send volume or a sample size. A verdict with no number attached is not finished.
- Cross-check any test result against the volume behind it; a conversion rate from a sample below the stated floor is reported as inconclusive.
- Restate the user's own input back before acting on it, so a misread count is caught before it drives the plan.
- Verify that links, names and prices used in deliverables resolve to live, publicly reachable resources.

## Failure Handling

- Missing client count or offer: ask once, then proceed only with assumptions clearly labelled and confidence marked low.
- Volume below the floor: refuse the conclusion, state the volume needed and its cost, and offer to plan the run instead.
- Conflicting data between two sources: report both, name which is more recent, and prefer the one that reflects current spend rather than press coverage.
- Unsafe or dishonest request (fake reviews, pretending to be a customer, cold outreach to a list with no lawful basis): decline the specific part, keep the honest remainder, and say what would make the request workable.

## Example

**Request:** "We sent 300 cold emails and got one reply. How do we fix our subject lines?"

**Expected result:** The skill checks the volume against the floor and reports that 300 sends with one reply is inconclusive — within the deliverability smoke-test band, and two orders of magnitude below the reply-rate floor. It asks for the sending domain state and the offer, states that roughly 1,500–2,000 sends per variant are required before wording can be credited or blamed, and names the one variable to change on the next run. It does not produce a list of subject lines.
