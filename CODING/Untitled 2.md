# HCL Aptitude Questions — Full Worked Solutions (50 Qs)

_Source: Sanfoundry HCL Aptitude Test, Quantitative Aptitude section (Ch1–Ch10). Each question below includes the concept/formula used, the step-by-step method, and the final answer._

---

## Chapter 1 — Number System Basics

**1. How many integers between 201 and 401 are co-prime to 20?**

- Formula: In any 20 consecutive integers, numbers co-prime to 20 (=2²×5) = φ(20) = 8.
- Steps: Take the range 201–400 (200 numbers = 10 complete blocks of 20). Each block contributes 8 co-prime numbers.
- **Answer: 10 × 8 = 80**

**2. Find X and Y if 77495X824Y is divisible by 8 and 9.**

- Formula: Divisible by 8 ⇒ last 3 digits divisible by 8. Divisible by 9 ⇒ digit sum divisible by 9.
- Steps: Last 3 digits = "24Y" → divisible by 8 when Y = 0 (240) or Y = 8 (248). Digit sum = 7+7+4+9+5+X+8+2+4+Y = 46+X+Y, must be a multiple of 9.
    - If Y=0: 46+X ≡ 0 (mod 9) → X = 8 (sum = 54 ✓)
    - If Y=8: 46+X+8 ≡ 0 (mod 9) → X = 0 (sum = 54 ✓)
- **Answer: X=8, Y=0 (or equivalently X=0, Y=8)**

**3. How many factors of 19! have unit digit 5?**

- Formula: A factor ends in 5 ⇔ it's divisible by 5 but **not** by 2.
- Steps: Prime-factorize 19! = 2¹⁶ × 3⁸ × 5³ × 7² × 11 × 13 × 17 × 19. Need power of 2 = 0, power of 5 = 1, 2, or 3 (3 choices), other primes free: 3(9 choices: 0–8) × 7(3: 0–2) × 11(2) × 13(2) × 17(2) × 19(2) × 5(3 choices)
- **Answer: 3 × 9 × 3 × 2×2×2×2 = 1296**

**4. Smallest number which when increased by 7 is divisible by 9, 11, 36.**

- Formula: N + 7 = LCM(9,11,36) × k
- Steps: LCM(9,36) = 36; LCM(36,11) = 396. Smallest: N = 396 − 7
- **Answer: 389**

**5. Unit digit of 258²⁵ − 364¹⁸**

- Formula: Units digits cycle — 8 → (8,4,2,6) period 4; 4 → (4,6) period 2.
- Steps: 258²⁵ → 25 mod 4 = 1 → units digit **8**. 364¹⁸ → 18 mod 2 = 0 (even) → units digit **6**. 8 − 6 = 2
- **Answer: 2**

---

## Chapter 2 — HCF, LCM & Number Systems

**6. Greatest tape length to measure equilateral triangles of side 38 and 114; how many equal parts?**

- Formula: Greatest measuring length = HCF(38,114)
- Steps: 114 = 3×38, so HCF = 38. Parts = 38/38 + 114/38 = 1 + 3
- **Answer: Tape = 38 units; 4 equal parts**

**7. Greatest number dividing 1543 & 2125 leaving remainders 6 & 5.**

- Formula: Required number = HCF(1543−6, 2125−5)
- Steps: HCF(1537, 2120) → Euclidean algorithm → HCF = 53
- **Answer: 53**

**8. Value of (2.99)²**

- Formula: (a−b)² = a² − 2ab + b², with a=3, b=0.01
- Steps: 9 − 0.06 + 0.0001 = 8.9401
- **Answer: 8.9401**

**9. Greatest 4-digit perfect square in base 8.**

- Formula: Largest 4-digit base-8 number = 7777₈; find greatest perfect square ≤ its decimal value.
- Steps: 7777₈ = 4095₁₀. √4095 ≈ 63.99 → 63² = 3969. Convert 3969 to base 8 = 7601₈
- **Answer: 7601₈ (= 3969 = 63²)**

**10. Find x: (53)₇ + (25)₈ = (x)₁₀**

- Formula: Convert each to base 10 and add.
- Steps: (53)₇ = 5×7+3 = 38; (25)₈ = 2×8+5 = 21; Sum = 59
- **Answer: x = 59**

---

## Chapter 3 — Averages & Algebra

**11. Average runs of 3 players (ratio 2:3:1) = 120. Lowest scorer hits a century next match, others keep their average. New average?**

- Formula: Total = Average × 3; split by ratio.
- Steps: Total = 360 → runs = 240k → k=60 → scores 120,180,60. New scores after next match: 120 (unchanged avg), 180 (unchanged avg), and (60+100)/2 = 80.
- **Answer: New average = (120+180+80)/3 = 380/3 ≈ 126.67**

**12. a, b, c, …, x, y, z are 26 natural numbers. Find (t−a)(t−b)…(t−y)(t−z).**

- Formula: The product runs through every letter a–z, and t is itself one of those 26 letters.
- Steps: The factor (t−t) = 0 is included in the product.
- **Answer: 0**

**13. Rohan has Rs.5 more than Mohan and Rs.8 more than Sohan; total = 47. Find Rohan's share.**

- Formula: Let Sohan = S → Rohan = S+8, Mohan = S+3
- Steps: S + (S+8) + (S+3) = 47 → 3S+11=47 → S=12 → Rohan = 20
- **Answer: Rs.20**

**14. pq = 24, p²+q² = 52. Find p.**

- Formula: (p+q)² = p²+q²+2pq; (p−q)² = p²+q²−2pq
- Steps: (p+q)² = 52+48 = 100 → p+q=10. (p−q)² = 52−48 = 4 → p−q=±2. p = (10+2)/2 = 6 or p = (10−2)/2 = 4
- **Answer: p = 6 or 4**

**15. x = a/(a+b), y = b/(a−b). Find ab/(a+b).**

- Note: This question's wording appears corrupted in the source (likely lost formatting for what's actually being asked in terms of x and y). Taken literally, ab/(a+b) = b·x, which still depends on b, so no clean numeric answer exists without more context.
- **Answer: Cannot be simplified to a fixed value as stated — recommend checking the original question wording.**

---

## Chapter 4 — Logarithms & Linear Equations

**16. Find 1/(log_x(yz)+1) + 1/(log_y(zx)+1) + 1/(log_z(xy)+1)**

- Formula: log_a(N) + 1 = log_a(N) + log_a(a) = log_a(aN); and 1/log_b(N) = log_N(b)
- Steps: Denominator 1 → log_x(xyz); denominator 2 → log_y(xyz); denominator 3 → log_z(xyz). Sum = log_{xyz}(x) + log_{xyz}(y) + log_{xyz}(z) = log_{xyz}(xyz)
- **Answer: 1**

**17. Simplify log_x(q) / log_xy(q)**

- Formula: Change of base: log_a N = ln N / ln a
- Steps: Ratio = ln(xy)/ln(x) = log_x(xy) = 1 + log_x(y)
- **Answer: 1 + log_x(y)** [equivalently log_x(xy)]

**18. 30 times of 30% of a number is 30 more than 30% of 3000. Find the number.**

- Formula: 30% of 3000 = 900; set up 30×0.3N = 900+30
- Steps: 9N = 930 → N = 930/9
- **Answer: N = 310/3 ≈ 103.33**

**19. Ram is 30 years younger than Raju; ratio of ages 28:7 (=4:1). Ages after 5 years?**

- Formula: Raju = 4k, Ram = k → Raju − Ram = 30
- Steps: 3k = 30 → k=10 → Ram=10, Raju=40. After 5 yrs: Ram=15, Raju=45
- **Answer: Ram = 15, Raju = 45**

**20. Alternate form of log_c(z) + log_c(1+z) = 0**

- Formula: log_c(A) + log_c(B) = log_c(AB); log_c(1) = 0
- Steps: log_c[z(1+z)] = 0 → z(1+z) = 1 → z² + z − 1 = 0
- **Answer: z² + z − 1 = 0**

---

## Chapter 5 — Profit, Loss & Ratios

**21. SP is Rs.500 more than CP; selling cost = Rs.200; profit% = 30%. Find CP.**

- Formula: Actual profit = (SP − CP) − selling expense; Profit% = (Profit/CP)×100
- Steps: Profit = 500 − 200 = 300. 300/CP × 100 = 30 → CP = 1000
- **Answer: CP = Rs.1000**

**22. Loss on selling at Rs.105 is half the CP. Find CP.**

- Formula: SP = CP − Loss, Loss = CP/2
- Steps: 105 = CP − CP/2 = CP/2 → CP = 210
- **Answer: CP = Rs.210**

**23. Product of two equal numbers is 10 times their sum. Find the sum.**

- Formula: a×a = 10(a+a)
- Steps: a² = 20a → a = 20. Sum = 20+20
- **Answer: Sum = 40**

**24. CP is 40% of Profit. Express SP in terms of CP.**

- Formula: CP = 0.4 × Profit → Profit = 2.5 × CP; SP = CP + Profit
- Steps: SP = CP + 2.5CP = 3.5CP
- **Answer: SP = 3.5 × CP**

**25. SP is Rs.100 more than CP; profit = 20%. Find CP.**

- Formula: Profit = 0.2 × CP
- Steps: 0.2CP = 100 → CP = 500
- **Answer: CP = Rs.500**

---

## Chapter 6 — Time & Work, Pipes & Cisterns

**26. X does work in 20 days, Y in 25 days. Time together?**

- Formula: Combined rate = 1/20 + 1/25
- Steps: = 5/100 + 4/100 = 9/100 → Time = 100/9
- **Answer: 100/9 ≈ 11.11 days**

**27. Pipes fill tank in 9 min and 290 sec. Time together (minutes)?**

- Formula: 290 sec = 29/6 min; combined rate = 1/9 + 6/29
- Steps: = (29+54)/261 = 83/261 → Time = 261/83
- **Answer: ≈ 3.14 minutes**

**28. Pipe fills in 8 sec, another in 60 sec; second pipe started 20 sec before first. Time to fill?**

- Formula: Work done alone in 20s + combined rate for remainder
- Steps: In 20s, slow pipe fills 20/60 = 1/3. Remaining = 2/3. Combined rate = 1/8+1/60 = 17/120 per sec. Time for remainder = (2/3)÷(17/120) = 80/17 ≈ 4.71s
- **Answer: ≈ 4.71 sec after both are open (≈ 24.71 sec total from when the slow pipe started)**

**29. 20 men complete work in 50 days. Work done by 70 men in 5 days?**

- Formula: Total man-days = 20×50 = 1000; Work fraction = (men×days)/total
- Steps: 70×5 = 350 → 350/1000
- **Answer: 35% of the work**

**30. Profit ratio A:B = 5:9; same investment period; A invests Rs.12905. Find B's investment.**

- Formula: Same duration ⇒ profit ratio = investment ratio
- Steps: B = 12905 × (9/5) = 2581 × 9
- **Answer: Rs.23,229**

---

## Chapter 7 — Trains, Speed & Mixtures

**31. Trains at 30 & 45 kmph cross each other (opposite directions) in 12s. Combined length?**

- Formula: Relative speed = sum of speeds (opposite direction); Length = speed × time
- Steps: 75 kmph = 20.83 m/s; Length = 20.83 × 12
- **Answer: ≈ 250 m**

**32. Train at 45 kmph, length 340m, crosses a 500m station. Time?**

- Formula: Time = (train length + station length)/speed
- Steps: 45 kmph = 12.5 m/s; Distance = 840m; Time = 840/12.5
- **Answer: 67.2 sec**

**33. Train 150m long passes a man in 12s. Find speed.**

- Formula: Speed = distance/time
- Steps: 150/12 = 12.5 m/s = 12.5 × 18/5
- **Answer: 45 km/h**

**34. Mixture with 27% milk mixed with 68% milk mixture in ratio 1:13. Find resulting %.**

- Formula: Weighted average = (m1×r1 + m2×r2)/(r1+r2)
- Steps: (27×1 + 68×13)/14 = (27+884)/14 = 911/14
- **Answer: ≈ 65.07%**

**35. Train at 73 kmph passes a man walking at 7 kmph (same direction) in 32s. Find train length.**

- Formula: Relative speed = difference of speeds (same direction); Length = relative speed × time
- Steps: 66 kmph = 18.33 m/s; Length = 18.33 × 32
- **Answer: ≈ 586.67 m**

---

## Chapter 8 — Simple Interest & Mensuration

**36. x invested for 2 years at r% SI; amount = 1.05x. Find r.**

- Formula: SI = P×r×t/100
- Steps: SI = 0.05x = x×r×2/100 → r = 0.05×100/2
- **Answer: r = 2.5%**

**37. Side of equilateral triangle tripled — % increase in area?**

- Formula: Area ∝ side²
- Steps: New area = 3² = 9× old → increase = 8× old = 800%
- **Answer: 800% increase**

**38. x invested for 10.5 years at r% SI; amount = 7.25x. Find r.**

- Formula: SI = P×r×t/100
- Steps: SI = 6.25x = x×r×10.5/100 → r = 625/10.5
- **Answer: r ≈ 59.52%**

**39. Total surface area of a hemisphere of diameter 14 cm.**

- Formula: TSA of hemisphere = 3πr²
- Steps: r = 7cm → 3 × (22/7) × 49
- **Answer: 462 cm²**

**40. Area of trapezoid, altitude 10m, parallel sides 6m & 12m.**

- Formula: Area = ½ × (sum of parallel sides) × height
- Steps: ½ × 18 × 10
- **Answer: 90 m²**

---

## Chapter 9 — Permutations & Calendars

**41. How many numbers can be formed with 2,4,6,8 without repetition?**

- Formula: Permutations of n distinct digits = n!
- Steps: 4! = 24 (arranging all four digits into 4-digit numbers)
- **Answer: 24**

**42. What day was 22 April 2025?**

- Formula: Odd-day method / Zeller-style counting from a known reference (Jan 1, 2025 = Wednesday)
- Steps: Days elapsed to Apr 22 = 31(Jan, from day1)+28(Feb)+31(Mar)+22(Apr) − 1 = 111 days after Jan 1. 111 mod 7 = 6 → Wednesday + 6 days
- **Answer: Tuesday**

**43. Face value of share Rs.40, profit on sale = 40%. If face value rises to Rs.50, new profit %?**

- Formula: Profit amount = 40% of original face value; new % = (same profit amount / new face value) × 100
- Steps: Profit = 0.4×40 = Rs.16 → New % = 16/50 × 100
- **Answer: 32%**

**44. Calendar for 2012 repeats in which year?**

- Formula: A leap year's calendar repeats in the next leap year with the same starting weekday (commonly +28 years, sometimes +12/+40 depending on the pattern).
- Steps: Tracking Jan 1 weekday year by year from 2012 (Sunday, leap) forward, the next leap year starting on Sunday is 2040.
- **Answer: 2040**

**45. Number of odd days in 125 years.**

- Formula: 100 years → 5 odd days; leap years contribute 2 odd days each, ordinary years 1.
- Steps: 100 years = 5 odd days. Remaining 25 years: 6 leap years → odd days = 25+6 = 31 → 31 mod 7 = 3. Total = 5+3 = 8 → mod 7 = 1
- **Answer: 1 odd day**

---

## Chapter 10 — Probability & Combinations

**46. Probability of drawing two non-numbered cards (with replacement) from a standard deck.**

- Formula: Non-numbered cards = Ace, J, Q, K = 16 of 52; P(with replacement) = P₁ × P₂
- Steps: P(one draw) = 16/52 = 4/13 → P(both) = (4/13)²
- **Answer: 16/169**

**47. Toss a coin twice — probability of head both times.**

- Formula: P(A and B) = P(A) × P(B) for independent events
- Steps: ½ × ½
- **Answer: 1/4**

**48. Unbiased die thrown — probability of getting 8.**

- Formula: A standard die has faces 1–6 only.
- Steps: Outcome "8" is impossible
- **Answer: 0**

**49. Bag has 2 red, 3 green, 4 blue balls (9 total). Ways to draw 3 with at least one blue?**

- Formula: P(at least one) = Total ways − ways with none of that type
- Steps: Total = C(9,3) = 84. Ways with no blue = C(5,3) = 10. At least one blue = 84 − 10
- **Answer: 74 ways**

**50. Ladder leans at 60° elevation; foot is 6m from wall. Find ladder length.**

- Formula: cos(θ) = adjacent/hypotenuse
- Steps: cos(60°) = 6/L → L = 6/0.5
- **Answer: 12 m**

---

_Note: A few questions (notably #2, #15, #18, #44) had ambiguous or possibly garbled wording in the original source; where multiple valid interpretations exist, the most standard interpretation is used and alternates are noted._