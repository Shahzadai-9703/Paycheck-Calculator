# Paycheck Calculator — Take-Home Pay Calculator 2026

Free, fast, private paycheck / take-home pay calculator for the United States.
No signup, no ads, no tracking — every calculation runs in the visitor's
browser and no salary ever leaves their device.

**Live site:** https://shahzadai-9703.github.io/paycheck-calculator/
(once GitHub Pages is enabled — see below)

## What it calculates

- Gross pay from an annual salary or an hourly rate (hours/week × 52)
- Pay frequency: weekly (52), biweekly (26), semimonthly (24), monthly (12), annual
- Filing status: single / married filing jointly
- Federal income tax — 2026 brackets (IRS Rev. Proc. 2025-32) and standard
  deduction ($16,100 single / $32,200 joint)
- FICA — Social Security 6.2% up to the 2026 wage base ($184,500); Medicare
  1.45% on all wages + 0.9% additional over $200,000 single / $250,000 joint
- 401(k) contributions (2026 limit $24,500) and other pre-tax deductions —
  these lower federal/state taxable income but **not** Social Security/Medicare
  wages, which is how the law works and where many calculators go wrong
- State tax for the five Phase 1 states:
  - **California** — 9 brackets 1%–12.3% (+1% over $1M), standard deduction
    $5,900 / $11,800, plus CA SDI 1.3% of all wages (no cap)
  - **Texas** — no state income tax
  - **Washington** — no state income tax, but PFML (1.13% up to the
    $184,500 cap, employee share 71.43%) and WA Cares Fund (0.58%)
  - **New York** — 9 brackets 3.9%–10.9%, standard deduction $8,000 / $16,050,
    plus an NYC resident city-tax toggle (3.078%–3.876%)
  - **New Mexico** — 6 brackets 1.5%–5.9% (HB 252), standard deduction = federal
- All other states: federal + FICA only, clearly labelled on the page as
  "state tax not yet modelled — federal estimate only"

Outputs: gross, federal tax, Social Security, Medicare, state tax and levies,
pre-tax deductions, and net take-home per paycheck and per year, with a
line-by-line breakdown and the effective tax rate.

## How the math was checked

The engine is pure JavaScript with no dependencies. It was verified against
the worked examples in the project research (Nov 2026):

| Case | Expected | Engine |
|---|---|---|
| $60,000 single, biweekly, California | $1,841.50/paycheck, $47,878.92/yr | matches exactly |
| $60,000 single, biweekly, Texas | $1,938.08/paycheck, $50,390.00/yr | matches exactly |
| $75,000 single, Washington | $60,552/yr | $60,552.13 |
| $75,000 single, Texas | $61,592/yr | $61,592.50 |
| $100,000 single, New York (state tax) | ≈ $4,861 | $4,859.75 |
| $100,000 single, NYC resident (city tax) | ≈ $3,441 | $3,441.09 |
| $100,000 single, New Mexico (state tax) | ≈ $3,569 | $3,569.10 |

The California $60,000 example also matches a published 2026 withholding
example ($1,838.65/paycheck, EDD Method B) to within $3 — the gap is
withholding vs annual liability, which the page explains.

## Sources (figures last checked 15 November 2026)

- IRS Rev. Proc. 2025-32 (2026 federal brackets + standard deduction)
- IRS Topic 751; Social Security Administration (FICA, $184,500 wage base)
- IRS Notice 2025-67 (401(k) limit $24,500)
- California Franchise Tax Board, 2026 rate schedules (Oct 2026 Tax News)
- California Employment Development Department (SDI 1.3%)
- New York State Department of Taxation and Finance (NY + NYC schedules)
- New Mexico Taxation and Revenue Department; HB 252 (Laws 2024, ch. 67)
- Washington Employment Security Department (PFML 1.13%, WA Cares 0.58%)

## What it does NOT model

City/local income tax except NYC; tax credits; NY benefit recapture above
$107,650 and the NY Paid Family Leave premium; itemised deductions; multiple
jobs; bonuses (22% federal supplemental withholding); overtime; tips;
garnishments; self-employment tax; California's non-recognition of HSAs.
See the "What this calculator does NOT model" section on the page.

## Tech

One self-contained `index.html` — no build step, no framework, no external
resources, no cookies. Open it in any browser or serve it statically.

## Maintenance

Tax figures change every year. Each Oct–Jan, roll forward: federal brackets
and standard deduction (IRS Revenue Procedure), the Social Security wage base
(SSA, October), 401(k) limits (IRS Notice, November), and state schedules.
Update the "Figures last checked" date on the page with every rollover.

## Disclaimer

Estimates only — not tax advice.
