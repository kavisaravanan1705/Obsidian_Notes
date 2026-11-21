# 📘 Simple Interest & Compound Interest Shortcuts
> *Aptitude Cheat Sheet — Exam-Ready Reference*

---

## 🔢 1. SI Basic Shortcut

### Formula
```
SI = (P × R × T) / 100
Amount = P + SI
```

### Fast Method
> Find **1 year interest first**, then multiply.

**Example:** Find SI on ₹8000 at 5% for 3 years.

| Step | Working |
|------|---------|
| 10% of 8000 | = 800 |
| 5% of 8000 | = 400 (half of above) |
| × 3 years | = **1200** ✅ |

### ⚡ Faster Trick
$$5\% = \frac{1}{20}$$
$$8000 \div 20 = 400 \xrightarrow{\times 3} \boxed{1200}$$

---

## 🔄 2. CI Basic Shortcut

### Growth Method (Year-by-Year)

**Example:** P = 10000, R = 10%, T = 2 years

| Year | Opening        | Interest  | Closing                            |
| ---- | -------------- | --------- | ---------------------------------- |
| 1    | 10,000 of 10 % | 1,000<br> | 11,000 [10,000+1000 = 11,000]      |
| 2    | 11,000 of 10 % | 1,100<br> | 12,100 [1100+10,000 = 12,100]      |
|      |                |           | Principle amt + interest = closing |

$$\text{CI} = 12100 - 10000 = \boxed{2100}$$

### Multiplier Method
```
A = P(1 + R/100)^T
```
$$10000 \times 1.1 \times 1.1 = 10000 \times 1.21 = \boxed{12100}$$

---

## ➖ 3. CI − SI Difference Shortcut

### Formula (2 years)
$$\text{CI} - \text{SI} = P \times \left(\frac{R}{100}\right)^2$$

**Example:** P = 10000, R = 10%

$$10000 \times \left(\frac{10}{100}\right)^2 = 10000 \times \frac{1}{100} = \boxed{100}$$

### ⚡ Fast Trick
```
10% of 10000 = 1000
10% of 1000  = 100  ← This IS the difference ✅
```

---

## 🔍 4. Finding Principal (SI)

### Formula
$$P = \frac{SI \times 100}{R \times T}$$

**Example:** SI = 2400, R = 8, T = 5

| Step | Working |
|------|---------|
| Total % | 8 × 5 = **40%** |
| Principal | 2400 × 100 ÷ 40 = **₹6000** ✅ |

---

## 📈 5. Finding Rate

### Formula
$$R = \frac{SI \times 100}{P \times T}$$

**Example:** SI = 800, P = 5000, T = 2

### ⚡ Fast Trick
```
(SI ÷ Principal) × 100 = 800 ÷ 5000 × 100 = 16%
Then ÷ Time → 16 ÷ 2 = 8% ✅
```

---

## ⏱️ 6. Finding Time

### Formula
$$T = \frac{SI \times 100}{P \times R}$$

**Example:** SI = 1000, P = 4000, R = 5%

### ⚡ Fast Trick
```
1-year SI = 5% of 4000 = 200
Total SI = 1000
Time = 1000 ÷ 200 = 5 years ✅
```

---

## 💰 7. Finding Amount (SI)

### Shortcut
> Total Interest % = R × T

**Example:** P = 9000, R = 10%, T = 2

| Step | Working |
|------|---------|
| Total % | 10 × 2 = **20%** |
| Interest | 20% of 9000 = **1800** |
| Amount | 9000 + 1800 = **₹10,800** ✅ |

---

## 📊 8. Percentage Growth (CI)

**Example:** P = 10000, R = 20%, T = 2

| Year | Opening | Interest | Closing |
|------|---------|----------|---------|
| 1 | 10,000 | 2,000 | 12,000 |
| 2 | 12,000 | 2,400 | **14,400** |

### Multiplier Shortcut
$$1.2^2 = 1.44 \quad\Rightarrow\quad 10000 \times 1.44 = \boxed{14400}$$

### 📋 Growth Table

| Rate | 2-Year Multiplier |
|------|------------------|
| 5% | 1.1025 |
| 10% | 1.21 |
| 20% | 1.44 |
| 25% | 1.5625 |

---

## ⏳ 9. Doubling Time Shortcut

### SI Rule
$$\text{Time} = \frac{100}{\text{Rate}}$$
> **Example:** Rate = 8% → Time = 100 ÷ 8 = **12.5 years**

### CI Rule (Rule of 72)
$$\text{Time} \approx \frac{72}{\text{Rate}}$$
> **Example:** Rate = 9% → Time = 72 ÷ 9 = **8 years**

> [!tip] Memory Hook
> **SI → 100 rule** | **CI → 72 rule**

---

## 📐 10. Difference Between CI of Consecutive Years

**Question type:** Difference between CI of 2nd and 1st year = 100, Rate = 10%

### Formula
$$P = \frac{\text{Difference} \times 100}{\text{Rate}}$$

$$= \frac{100 \times 100}{10} = \boxed{1000}$$

---

## 🔙 11. Finding Principal in CI (Reverse)

**Example:** Amount after 2 years = 12100, R = 10%

### Formula
$$P = \frac{\text{Amount}}{(1 + R/100)^T}$$

$$= \frac{12100}{1.21} = \boxed{10000}$$

### Percentage Method
```
10% for 2 years → growth = 21%
Amount = 121%
Principal = 12100 × 100 ÷ 121 = 10000 ✅
```

---

## 🧮 12. Finding Principal from CI−SI Difference

**Question:** Difference = 144, Rate = 12%

### Formula
$$P = \frac{\text{Difference} \times 10000}{R^2}$$

$$= \frac{144 \times 10000}{144} = \boxed{10000}$$

---

## 🏆 Golden Rules Summary

### SI Rules
- [ ] Interest is the **same every year**
- [ ] **Multiply** yearly interest by time
- [ ] Principal **remains constant**

### CI Rules
- [ ] Principal **changes every year**
- [ ] **Add** interest to principal each year
- [ ] Subtract principal at end if CI is asked (not Amount)

### Amount vs Interest Rule
> [!warning] Common Exam Trap
> - Question asks **Interest** → Do NOT add principal
> - Question asks **Amount** → Add principal

---

## 🧠 SI vs CI Memory Trick

| | SI | CI |
|--|----|----|
| Principal | Same always | Changes every year |
| Method | Multiply | Add yearly |
| Mnemonic | **S**ame **P**rincipal | **C**hanging **P**rincipal |

---

## 🎯 Ultimate Exam Strategy

> [!important] Always ask yourself before solving:
> **"Can I use the percentage method here?"**

| Method | Speed |
|--------|-------|
| ✅ Percentage method | Fast — use this |
| ❌ Formula method | Slow — avoid if possible |

---

*Tags: #aptitude #SI #CI #shortcuts #math #exam-prep #quantitative*