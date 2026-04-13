# rac-us-ca

**California state tax and benefit encodings.**

All California-specific .rac files and California-administered source slices
belong here, NOT in rac-compile or rac-us.

## Structure

Files organized under `statute/` by California Revenue and Taxation Code (RTC) section:

```
rac-us-ca/
├── statute/               # All enacted statutes
│   └── rtc/              # Revenue and Taxation Code
│       ├── 17041/        # § 17041 - Personal Income Tax Rates
│       │   └── income_tax.rac
│       ├── 17043/        # § 17043 - Mental Health Services Tax
│       │   └── mhs_tax.rac
│       ├── 17054/        # § 17054 - Standard Deduction
│       │   └── standard_deduction.rac
│       ├── 17052/        # § 17052 - California EITC (CalEITC)
│       │   └── caleitc.rac
│       └── 17052.1/      # § 17052.1 - Young Child Tax Credit
│           └── yctc.rac
│
├── ftb/                  # Franchise Tax Board guidance
│   └── 2024/
│       └── parameters.yaml
│
└── tests/                # Validation test cases
    └── integration/
```

Additional jurisdiction-local source slices belong under `sources/slices/`, for
example California SNAP overlays administered by CDSS.

## References

Cross-file references use paths relative to the repo root:
```
references {
  ca_agi: statute/rtc/17041/california_agi
  federal_agi: rac-us/statute/26/62/a/adjusted_gross_income
}
```

## Federal Conformity

California generally conforms to federal tax law with modifications. Key differences:
- Different tax brackets (9 rates: 1% to 12.3%)
- Mental Health Services Tax: 1% surtax on income over $1 million
- Different standard deduction amounts
- State-specific credits (CalEITC, YCTC)

## File Types

- `.rac` - Executable formulas (compile to Python/JS/WASM)
- `parameters.yaml` - Time-varying values (rates, thresholds, brackets)
- `tests.yaml` - Validation test cases

## Key Statutes

### Income Tax (RTC 17041)
California has 9 marginal tax brackets ranging from 1% to 12.3%:
- 1%, 2%, 4%, 6%, 8%, 9.3%, 10.3%, 11.3%, 12.3%
- Thresholds vary by filing status

### Mental Health Services Tax (RTC 17043)
- 1% surtax on taxable income exceeding $1 million
- Enacted via Proposition 63 (2004)
- Brings top marginal rate to 13.3% for high earners

### Standard Deduction (RTC 17054)
- Single/MFS: $5,540 (2024)
- MFJ/HOH/QW: $11,080 (2024)

### CalEITC (RTC 17052)
- California Earned Income Tax Credit
- Max credit: $3,644 (3+ children, 2024)
- Income limit: $31,950

### Young Child Tax Credit (RTC 17052.1)
- For children under 6
- Max credit: $1,154 (2024)
- Must qualify for CalEITC

## Related Repos

- **rac-us** - Federal tax statutes (Title 26 IRC)
- **rac-compile** - DSL compiler and runtime
- **rac-validators** - Validation against external calculators

## Repo Boundary

- Federal statute cores and national current-effective SNAP layers belong in
  `rac-us`.
- California-administered overlays belong here, even when they sit on top of a
  federal program like SNAP.
