

# TCS NQT SI/CI Pattern Notes (2022-2026)

> Focus: Simple Interest (SI) and Compound Interest (CI) patterns seen in TCS NQT Quant/Analytical preparation and recent practice sets.

## Ranked patterns

| Rank | Pattern name | How frequently it appears in TCS NQT | Exact question pattern asked | Shortcut formula / trick | TCS-level example question |
|---|---|---:|---|---|---|
| 1 | Direct SI | Very high | Find SI for given principal, rate, and time. | `SI = (P × R × T) / 100` | Find the SI on Rs 8,000 at 12% per annum for 3 years. |
| 2 | Direct CI | Very high | Find CI or amount for given principal, rate, and time. | `A = P(1 + R/100)^T`, `CI = A - P` | Find the CI on Rs 10,000 at 10% per annum for 2 years, compounded annually. |
| 3 | SI and CI difference for 2 years | Very high | Given difference between CI and SI for 2 years, find rate, principal, or difference. | `CI - SI = P(R/100)^2` for 2 years | The SI and CI on a sum for 2 years differ by Rs 96. If the rate is 8%, find the principal. |
| 4 | Amount-based SI | High | Given amount after SI, find principal, SI, rate, or time. | `A = P + SI = P(1 + RT/100)` | A sum amounts to Rs 12,000 in 4 years at 5% SI. Find the principal. |
| 5 | Amount-based CI | High | Given amount after CI, find principal, CI, rate, or time. | `A = P(1 + R/100)^T` | A sum amounts to Rs 13,310 in 3 years at 10% CI. Find the principal. |
| 6 | Find principal | Medium-high | SI/CI or amount is given; principal is asked. | `P = SI × 100 / (R × T)` or `P = A/(1 + R/100)^T` | SI on a sum at 8% for 5 years is Rs 2,400. Find the sum. |
| 7 | Find rate | Medium | Principal, time, and SI/CI are given; rate is asked. | `R = SI × 100 / (P × T)` | At what rate will Rs 5,000 yield SI of Rs 1,500 in 3 years? |
| 8 | Find time | Medium | Principal, rate, and SI/CI are given; time is asked. | `T = SI × 100 / (P × R)` | In what time will Rs 8,000 yield SI of Rs 2,400 at 10% per annum? |
| 9 | SI doubles/triples | Medium | Find time or rate when a sum doubles or triples under SI. | For doubling under SI, `T = 100/R`. | In what time will a sum double itself at 12.5% SI? |
| 10 | Half-yearly CI | Medium-low | CI with half-yearly compounding. | Use `R/2` per half-year and `2T` periods: `A = P(1 + R/200)^(2T)` | Find CI on Rs 16,000 at 20% per annum for 1.5 years, compounded half-yearly. |
| 11 | Quarterly CI | Low | CI with quarterly compounding. | Use `R/4` per quarter and `4T` periods: `A = P(1 + R/400)^(4T)` | Find the amount on Rs 8,000 at 12% per annum for 1 year compounded quarterly. |
| 12 | Mixed-rate SI | Low | Different SI rates for different time spans. | Break time into segments and sum each segment separately. | A sum is lent at 3% for 2 years, 8% for next 3 years, and 10% after that. Find total SI after 6 years. |

## Most repeated question forms

- Direct SI questions appear most often in recent TCS NQT SI/CI practice material, including straight calculation, reverse finding, and time/rate variants [web:11].
- Direct CI questions and SI-vs-CI difference questions for 2 years are the next most common because they are short, formula-based, and easy to ask in MCQ format [web:11].
- Half-yearly and quarterly CI are less frequent but still show up as standard exam twists in TCS-level practice [web:11].

## Shortcut sheet

- SI: `P × R × T / 100`.
- CI annually: `P(1 + R/100)^T`.
- CI half-yearly: `P(1 + R/200)^(2T)`.
- CI quarterly: `P(1 + R/400)^(4T)`.
- Difference between CI and SI for 2 years: `P(R/100)^2`.
- Difference between CI and SI for 3 years: `P(R/100)^2(3 + R/100)`.

## TCS-level examples

1. A sum of Rs 9,000 is invested at 4.5% SI for 4 years. Find the interest.
2. Find the CI on Rs 15,000 at 8% per annum for 2 years.
3. The difference between CI and SI on Rs 15,000 for 2 years is Rs 96. Find the rate.
4. A sum amounts to Rs 12,000 in 4 years at SI. If the rate is 5%, find the principal.
5. Find the amount on Rs 8,000 at 12% per annum for 1 year, compounded quarterly.

## Quick ranking logic

- Highest priority: direct SI, direct CI, and 2-year CI-SI difference.
- Next priority: amount-based reverse questions and finding principal, rate, or time.
- Lower priority: half-yearly, quarterly, and mixed-rate SI/CI questions.