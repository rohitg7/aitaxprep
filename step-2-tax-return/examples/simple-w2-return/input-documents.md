# Example: Simple W-2 Return — Source Documents

These are the input documents (from Step 1) that produce the [expected tax return](./expected-return.md).

## Document Index

| # | File | Type | Description |
|---|------|------|-------------|
| 1 | w2_1.md | W-2 | TechCorp Inc - wages |
| 2 | 1099_int_1.md | 1099-INT | Chase Bank - interest |
| 3 | 1099_div_1.md | 1099-DIV | Vanguard - dividends |

---

## w2_1.md

```markdown
# W-2: Wage and Tax Statement
<!-- schema_version: 1.0 -->
<!-- document_type: w2 -->

## Employer Information
| Field | Value |
|-------|-------|
| employer_name | TechCorp Inc |
| ein | 84-1234567 |
| employer_address | 500 Tech Blvd, Austin, TX 78702 |

## Employee Information
| Field | Value |
|-------|-------|
| employee_name | John Doe |
| ssn | ***-**-1234 |
| employee_address | 123 Main St, Apt 4B, Austin, TX 78701 |

## Compensation
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Wages, salaries, tips | 95000.00 |
| 2 | Federal income tax withheld | 16200.00 |
| 3 | Social security wages | 95000.00 |
| 4 | Social security tax withheld | 5890.00 |
| 5 | Medicare wages and tips | 95000.00 |
| 6 | Medicare tax withheld | 1377.50 |
| 7 | Social security tips | 0.00 |
| 8 | Allocated tips | 0.00 |
| 10 | Dependent care benefits | 0.00 |
| 11 | Nonqualified plans | 0.00 |
| 12a_code | Code | DD |
| 12a_amount | Amount | 7200.00 |
| 12b_code | Code | W |
| 12b_amount | Amount | 3600.00 |
| 12c_code | Code | |
| 12c_amount | Amount | |
| 12d_code | Code | |
| 12d_amount | Amount | |
| 13_statutory_employee | Statutory employee | false |
| 13_retirement_plan | Retirement plan | true |
| 13_third_party_sick_pay | Third-party sick pay | false |
| 14 | Other | |

## State Information
| Field | Value |
|-------|-------|
| state | TX |
| state_id | |
| state_wages | 95000.00 |
| state_tax | 0.00 |
| local_wages | |
| local_tax | |
| locality_name | |
```

---

## 1099_int_1.md

```markdown
# 1099-INT: Interest Income
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_int -->

## Payer Information
| Field | Value |
|-------|-------|
| payer_name | Chase Bank |
| payer_tin | 13-4994650 |
| payer_address | 270 Park Ave, New York, NY 10017 |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | John Doe |
| ssn | ***-**-1234 |

## Interest Income
| Box | Description | Value |
|-----|-------------|-------|
| 1 | Interest income | 850.00 |
| 2 | Early withdrawal penalty | 0.00 |
| 3 | Interest on U.S. savings bonds and Treasury obligations | 0.00 |
| 4 | Federal income tax withheld | 0.00 |
| 5 | Investment expenses | 0.00 |
| 6 | Foreign tax paid | 0.00 |
| 7 | Foreign country or U.S. possession | |
| 8 | Tax-exempt interest | 0.00 |
| 9 | Specified private activity bond interest | 0.00 |
| 10 | Market discount | 0.00 |
| 11 | Bond premium | 0.00 |
| 12 | Bond premium on Treasury obligations | 0.00 |
| 13 | Bond premium on tax-exempt bond | 0.00 |
```

---

## 1099_div_1.md

```markdown
# 1099-DIV: Dividend Income
<!-- schema_version: 1.0 -->
<!-- document_type: 1099_div -->

## Payer Information
| Field | Value |
|-------|-------|
| payer_name | Vanguard |
| payer_tin | 23-1945930 |
| payer_address | PO Box 982901, El Paso, TX 79998 |

## Recipient Information
| Field | Value |
|-------|-------|
| recipient_name | John Doe |
| ssn | ***-**-1234 |

## Dividends
| Box | Description | Value |
|-----|-------------|-------|
| 1a | Total ordinary dividends | 1500.00 |
| 1b | Qualified dividends | 1200.00 |
| 2a | Total capital gain distributions | 0.00 |
| 2b | Unrecaptured section 1250 gain | 0.00 |
| 2c | Section 1202 gain | 0.00 |
| 2d | Collectibles (28%) gain | 0.00 |
| 3 | Nondividend distributions | 0.00 |
| 4 | Federal income tax withheld | 0.00 |
| 5 | Section 199A dividends | 0.00 |
| 6 | Investment expenses | 0.00 |
| 7 | Foreign tax paid | 0.00 |
| 8 | Foreign country or U.S. possession | |
| 9 | Cash liquidation distributions | 0.00 |
| 10 | Noncash liquidation distributions | 0.00 |
| 11 | FATCA filing requirement | false |
| 12 | Exempt-interest dividends | 0.00 |
| 13 | Specified private activity bond interest dividends | 0.00 |
```
