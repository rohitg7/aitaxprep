# Example: Simple W-2 Return — Expected Output

This is a complete tax return for a single filer with one W-2, one bank account (interest), and one brokerage account (dividends).

# Federal Tax Return 2025
<!-- schema_version: 1.0 -->
<!-- tax_year: 2025 -->
<!-- generated_by: example -->
<!-- generated_date: 2026-03-15 -->

## Filing Information
| Field | Value |
|-------|-------|
| filing_status | single |
| first_name | John |
| last_name | Doe |
| ssn | ***-**-1234 |
| occupation | Software Engineer |
| address | 123 Main St |
| apt | Apt 4B |
| city | Austin |
| state | TX |
| zip | 78701 |
| phone | 5125550100 |
| email | john.doe@email.com |

## Dependents
| name | ssn | relationship | months_lived | child_tax_credit | other_credit |
|------|-----|-------------|-------------|-----------------|-------------|

## Form 1040: U.S. Individual Income Tax Return

### Income
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 1a | Wages, salaries, tips | 95000.00 | W-2: TechCorp Inc |
| 1z | Add lines 1a through 1h | 95000.00 | Sum |
| 2a | Tax-exempt interest | 0.00 | |
| 2b | Taxable interest | 850.00 | 1099-INT: Chase Bank |
| 3a | Qualified dividends | 1200.00 | 1099-DIV: Vanguard |
| 3b | Ordinary dividends | 1500.00 | 1099-DIV: Vanguard |
| 4a | IRA distributions | 0.00 | |
| 4b | Taxable amount | 0.00 | |
| 5a | Pensions and annuities | 0.00 | |
| 5b | Taxable amount | 0.00 | |
| 6a | Social security benefits | 0.00 | |
| 6b | Taxable amount | 0.00 | |
| 7 | Capital gain or (loss) | 0.00 | |
| 8 | Other income from Schedule 1 | 0.00 | |
| 9 | Total income | 97350.00 | Sum of 1z, 2b, 3b, 4b, 5b, 6b, 7, 8 |
| 10 | Adjustments from Schedule 1 | 0.00 | |
| 11 | Adjusted gross income | 97350.00 | Line 9 - Line 10 |
| 12 | Standard deduction | 15700.00 | Single filer (verify against IRS Rev. Proc.) |
| 13 | Qualified business income deduction | 0.00 | |
| 14 | Total deductions | 15700.00 | Line 12 + Line 13 |
| 15 | Taxable income | 81650.00 | Line 11 - Line 14 |

### Tax and Credits
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 16 | Tax | 13823.00 | Qualified Dividends and Capital Gain Tax Worksheet (verify rates against IRS) |
| 17 | Amount from Schedule 2, Part I | 0.00 | |
| 18 | Add lines 16 and 17 | 13823.00 | Sum |
| 19 | Child tax credit | 0.00 | |
| 20 | Amount from Schedule 3 | 0.00 | |
| 21 | Add lines 19 and 20 | 0.00 | Sum |
| 22 | Subtract line 21 from line 18 | 13823.00 | Line 18 - Line 21 |
| 23 | Other taxes from Schedule 2, Part II | 0.00 | |
| 24 | Total tax | 13823.00 | Line 22 + Line 23 |

### Payments
| Line | Description | Value | Source |
|------|-------------|-------|--------|
| 25a | W-2 federal tax withheld | 16200.00 | W-2: TechCorp Inc Box 2 |
| 25b | 1099 federal tax withheld | 0.00 | |
| 25c | Other withholding | 0.00 | |
| 25d | Total | 16200.00 | Sum of 25a-25c |
| 26 | Estimated tax payments | 0.00 | |
| 33 | Total payments | 16200.00 | Sum |

### Refund or Amount Owed
| Line | Description | Value |
|------|-------------|-------|
| 34 | Overpaid | 2377.00 |
| 35a | Refunded to you | 2377.00 |
| 35b | Routing number | 021000021 |
| 35c | Account type | checking |
| 35d | Account number | 123456789 |
| 37 | Amount you owe | 0.00 |

## Validation Report

### IRS Sources Consulted
| Check | Status | IRS Source Used |
|-------|--------|----------------|
| Standard deduction amount verified | ✅ | Rev. Proc. 2025-XX (verify) |
| Tax bracket rates verified | ✅ | Rev. Proc. 2025-XX (verify) |
| Form 1040 instructions consulted | ✅ | i1040 (2025) |
| Mid-year IRS changes checked | ✅ | IRS Newsroom as of 2026-03-15 |

### Cross-Form Consistency
| Check | Status |
|-------|--------|
| 1040 Line 1a = W-2 Box 1 (95000) | ✅ |
| 1040 Line 2b = 1099-INT Box 1 (850) | ✅ |
| 1040 Line 3a = 1099-DIV Box 1b (1200) | ✅ |
| 1040 Line 3b = 1099-DIV Box 1a (1500) | ✅ |
| 1040 Line 25a = W-2 Box 2 (16200) | ✅ |
| Line 3a ≤ Line 3b | ✅ |
| Line 9 = sum of income lines | ✅ |
| Line 15 = Line 11 - Line 14 | ✅ |
| Line 34 = Line 33 - Line 24 | ✅ |

### Warnings
- Standard deduction amount ($15,700) is an estimate — verify against the IRS Revenue Procedure for tax year 2025
- Tax calculation ($13,823) uses the Qualified Dividends worksheet due to qualified dividends on Line 3a — verify tax bracket rates
- Schedule B not required (interest $850 < $1,500 and dividends $1,500 = $1,500 threshold — borderline, verify if $1,500 means "more than" or "at least")
