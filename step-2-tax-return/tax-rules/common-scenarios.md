# Common Tax Scenarios

Step-by-step guides for the most common filing situations.

> ⚠️ **Verify all thresholds and rules** against official IRS sources for the filing tax year.

## Scenario 1: Simple W-2 Employee

**Documents**: W-2
**Forms needed**: Form 1040 only

```
1. Line 1a = W-2 Box 1 (wages)
2. Line 9 = Line 1a (total income)
3. Line 11 = Line 9 (AGI, no adjustments)
4. Line 12 = Standard deduction for filing status
5. Line 15 = Line 11 - Line 12 (taxable income)
6. Line 16 = Tax from tax table
7. Line 25a = W-2 Box 2 (withholding)
8. Line 33 = Line 25a (total payments)
9. Line 34 or 37 = Refund or amount owed
```

**→ [See complete example](../examples/simple-w2-return/)**

## Scenario 2: W-2 + Bank Interest + Dividends

**Documents**: W-2, 1099-INT, 1099-DIV
**Forms needed**: Form 1040, possibly Schedule B

```
1. Check: Is total interest > $1,500 OR total dividends > $1,500?
   YES → Also need Schedule B
   NO  → Just Form 1040

2. Line 1a = sum of W-2 Box 1
3. Line 2b = sum of 1099-INT Box 1
4. Line 3a = sum of 1099-DIV Box 1b (qualified)
5. Line 3b = sum of 1099-DIV Box 1a (ordinary)
6. Line 9 = total income
7. If qualified dividends > 0 → Use QDCG worksheet for Line 16
```

## Scenario 3: W-2 + Stock Sales (Investor)

**Documents**: W-2, 1099-B
**Forms needed**: Form 1040, Form 8949, Schedule D

```
1. For each 1099-B transaction:
   - Determine short-term (≤1 year) vs long-term (>1 year)
   - Determine box (A/B/C for short, D/E/F for long)
   - Check for wash sales (add disallowed loss to basis)
   - Enter on Form 8949

2. Total short-term → Schedule D Line 7
3. Total long-term → Schedule D Line 15
4. Net capital gain/loss → Schedule D Line 21
5. If net loss: cap at -$3,000 (-$1,500 if MFS)
6. Schedule D Line 21 → Form 1040 Line 7
7. Use QDCG worksheet for Line 16 (capital gains get lower rate)
```

## Scenario 4: Freelancer / Self-Employed

**Documents**: 1099-NEC, business expense records
**Forms needed**: Form 1040, Schedule C, Schedule SE, Schedule 1

```
1. Schedule C:
   - Gross income = sum of 1099-NEC Box 1 + other business income
   - Total expenses = sum of deductible business expenses
   - Net profit = Gross income - Total expenses
   - Net profit → Schedule 1 Line 3

2. Schedule SE:
   - If net profit > $400:
     - SE tax = 92.35% × net profit × 15.3%
     - 50% of SE tax → Schedule 1 Line 15 (deduction)
     - SE tax → Schedule 2 Part II Line 4

3. Schedule 1:
   - Line 3 = Schedule C net profit
   - Line 15 = 50% of SE tax (deduction)
   - Line 10 → Form 1040 Line 8
   - Line 26 → Form 1040 Line 10

4. Form 1040:
   - Line 8 = Schedule 1 Line 10
   - Line 10 = Schedule 1 Line 26
   - Line 23 = Schedule 2 total (includes SE tax)
```

## Scenario 5: Homeowner with Mortgage

**Documents**: W-2, 1098, property tax bill
**Forms needed**: Form 1040, possibly Schedule A

```
1. Calculate potential itemized deductions:
   - 1098 Box 1 (mortgage interest) → Schedule A Line 8a
   - Property tax paid → Schedule A Line 5b
   - State income tax (W-2 Box 17) → Schedule A Line 5a
   - SALT cap: Lines 5a + 5b + 5c cannot exceed $10,000

2. Total itemized = medical + SALT + interest + charity
3. Compare: itemized total vs standard deduction
4. Use whichever is LARGER for Form 1040 Line 12
```

## Scenario 6: W-2 + HSA

**Documents**: W-2 (with Box 12 Code W), 1099-SA, 5498-SA
**Forms needed**: Form 1040, Form 8889, Schedule 1

```
1. Form 8889:
   - Line 2 = HSA contributions (your contributions, not employer)
   - Line 9 = Employer contributions (W-2 Box 12 Code W)
   - Line 13 = HSA deduction → Schedule 1 Line 13
   - If distributions: Lines 14a-14c, 17a-17b

2. Check contribution limits (VERIFY with IRS):
   - Self-only coverage: $X
   - Family coverage: $X
   - Age 55+ catch-up: additional $1,000

3. HSA deduction → Schedule 1 Line 13 → Form 1040 Line 10
```

## Scenario 7: Student with Education Credits

**Documents**: 1098-T, tuition payment records
**Forms needed**: Form 1040, Form 8863, Schedule 3

```
1. Determine eligibility:
   - AOTC: First 4 years, at least half-time, no felony drug conviction
   - LLC: Any post-secondary education, no year limit

2. Form 8863:
   - Qualified expenses = tuition + required fees - scholarships
   - AOTC: 100% of first $2,000 + 25% of next $2,000 = up to $2,500
   - LLC: 20% of up to $10,000 = up to $2,000

3. Check income phase-outs (VERIFY with IRS)
4. Nonrefundable portion → Schedule 3 Line 2
5. AOTC refundable portion (40%) → Form 1040 Line 29
```

## General Tips for AI

1. **Always determine filing status first** — it affects everything
2. **Process supporting forms before Form 1040** — they feed into it
3. **Compare standard vs itemized** — choose the larger deduction
4. **Check for qualified dividends and capital gains** — they get lower tax rates
5. **Don't forget the SE tax deduction** — 50% goes on Schedule 1
6. **Verify every threshold against the IRS** — they change annually
