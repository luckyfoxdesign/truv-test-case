---
type: research
status: done
language: en
translation_of: ../ru/financial-assumptions.md
---

# Financial Opportunity Assessment

## 1. Current Funnel & Potential Losses

Overall conversion is **3.24%**: only 8,959 of 276,373 visitors reach the payment-completion event.

### 1.2. Assumptions for Financial Modeling

The case study does not provide data on:

- The distribution of users across categories.
- The target categories the business wants to focus on.
- The number of employers in each order.
- The actual average order value.
- The share of verifications for which money was actually charged.
- The cost of performing verifications.
- The period covered by the funnel.

**Important**

- The actual average order value could be higher or lower.
- The calculations exclude refunds, chargebacks, fraud, fees, and other financial adjustments.
- The payment form states that users are charged only for successful verifications. Reaching `Verification Payment Completed` therefore does not necessarily mean recognized revenue.
- The assessment estimates the notional value of additional orders, assuming they become billable.

### 1.3. Pricing by Category

Prices observed during the interface review are used to estimate the value of additional orders.

| Category | Income & Employment | Employment History | Assets | Assets + Income |
|---|---|---|---|---|
| Mortgage Lending | $50 | $50 | $50 | $100 |
| Home Equity Lending | $50 | $50 | $50 | $100 |
| Auto Lending | $35 | $35 | $35 | $70 |
| Consumer Lending | $35 | $35 | $35 | $70 |
| Government | $35 | $35 | $35 | $70 |
| Background / Employment Screening | — | $40 | — | — |
| Tenant Screening | $25 | $25 | $25 | $50 |

_These are prices for the order configurations reviewed. Adding employers may increase the total._

The calculations use two illustrative scenarios:

- **$35 per order** — based on Auto, Consumer, and Government pricing.
- **$50 per order** — based on Mortgage and Home Equity pricing.

### 1.4. Funnel Breakdown

The table shows how many users did not reach the next stage and the notional value of their orders if all of them had completed payment.

| Stage | Users (From → To) | Drop-off | Lost Users | At $35 | At $50 |
|---|---|---|---|---|---|
| Page Load → Verify | 276,373 → 130,934 | 52.62% | 145,439 | $5.09M | $7.27M |
| Verify → Dashboard | 130,934 → 129,846 | 0.83% | 1,088 | $38.08K | $54.40K |
| Dashboard → Your Information | 129,846 → 21,865 | 83.16% | 107,981 | $3.78M | $5.40M |
| Your Information → Borrower Information | 21,865 → 18,791 | 14.06% | 3,074 | $107.59K | $153.70K |
| Borrower Information → Payment | 18,791 → 8,959 | 52.32% | 9,832 | $344.12K | $491.60K |

**Calculation**

Lost Users × order price.

For example, Dashboard → Your Information: `107,981 × $35 = $3,779,335`.

**Important**

- This is the theoretical value of incomplete orders, not actual lost revenue.
- The calculation assumes that every user who left could have made a purchase, which is unrealistic.

These figures illustrate the scale of drop-off, but are not used directly to forecast revenue.

## 2. Selected Opportunities

Two transitions were selected for further analysis.

### P1 — Dashboard → Your Information

| From | To | Conversion | Lost Users | Drop-off |
|---:|---:|---:|---:|---:|
| 129,846 | 21,865 | 16.84% | 107,981 | 83.16% |

**Why this transition**

- It has the largest relative drop-off within the Dashboard.
- The form's layout and length may make completion harder.

### P2 — Borrower Information → Payment

| From | To | Conversion | Lost Users | Drop-off |
|---:|---:|---:|---:|---:|
| 18,791 | 8,959 | 47.68% | 9,832 | 52.32% |

**Why this transition**

- More than half of users do not complete payment after Borrower Information Completed.
- Potential issues include required fields, the transition to the modal, purchase abandonment, and payment errors.
- Because the event sequence needs validation, these losses cannot yet be attributed to specific interface elements.

## 3. Conversion Improvement Scenarios

Estimate the additional final events from improving a selected transition by **+1, +3, and +5 percentage points**.

### Calculation Assumptions

- Only one transition improves at a time.
- Downstream conversion rates remain constant because we do not know how a change at one stage will affect behavior at later stages.
- Additional final events are provisionally treated as billable orders.
- All calculations apply to the original sample, not to a month or a year.

### 3.1. Dashboard Improvement

Current Dashboard → Your Information conversion is **16.84%**.

After Your Information, 8,959 of 21,865 users reach final payment: **40.97%**.

Estimation formula: `129,846 × improvement in percentage points / 100 × (8,959 / 21,865)`.

| Improvement | New conversion | Additional payments | At $35 | At $50 |
|---|---|---|---|---|
| +1 pp | 17.84% | ≈532 | $18,621 | $26,602 |
| +3 pp | 19.84% | ≈1,596 | $55,863 | $79,805 |
| +5 pp | 21.84% | ≈2,660 | $93,106 | $133,008 |

**Example (+1 pp):**

1. `129,846 × 0.01 = 1,298.46` additional users reach Your Information.
2. `1,298.46 × (8,959 / 21,865) ≈ 532` reach the final event.
3. `532.03 × $50 ≈ $26,602` is the notional value of additional orders.

### 3.2. Payment Improvement

Current Borrower Information → Payment conversion is **47.68%**.

Since Payment is the final stage, every additional transition immediately counts as an additional final event.

Estimation formula: `18,791 × improvement in percentage points / 100`.

| Improvement | New conversion | Additional payments | At $35 | At $50 |
|---|---|---|---|---|
| +1 pp | 48.68% | ≈188 | $6,577 | $9,396 |
| +3 pp | 50.68% | ≈564 | $19,731 | $28,187 |
| +5 pp | 52.68% | ≈940 | $32,884 | $46,978 |

**Example (+1 pp):**

1. `18,791 × 0.01 = 187.91` additional payment completions.
2. `187.91 × $50 = $9,395.50`, or ≈$9,396.

_Monetary amounts are calculated without rounding intermediate results._

## 4. Prioritization & Next Steps

| Priority | Area | Potential at +1 pp ($50) | Next Step |
|---|---|---|---|
| P0 | Analytics | — | Validate event order and recording logic |
| P1 | Dashboard | $26,602 | Identify where users stop filling out the form |
| P2 | Payment | $9,396 | Separate abandonment before payment, abandonment within the form, and payment-provider errors |

**Dashboard is the first candidate for UX research:** for the same absolute improvement in conversion, it has the largest potential financial effect in this model.

**Payment is the second candidate:** users have already completed a substantial part of the process, but the reasons for abandonment before payment remain unknown.

### What to investigate

**Dashboard**

- Form starts and completion progress.
- Completion of each section, regardless of order.
- Required-field errors.
- Visibility of Your Information and Continue.
- Points at which users stop filling out the form.

**Payment**

- Continue Clicked → Payment Modal Opened.
- Payment Attempted → Payment Completed.
- Closing the modal.
- Bank and payment-provider decline reasons.
- Retry attempts and successful payment recovery.

## 5. Conclusion

With a conversion improvement of **+1 percentage point**:

- Dashboard could yield ≈532 additional final events and $18,621–$26,602 in notional order value.
- Payment could yield ≈188 additional final events and $6,577–$9,396 in notional order value.

**Prioritize Dashboard, then Payment**, but only as directions for testing hypotheses.

The financial figures are scenarios: actual average order value, the share of billable successful verifications, and the feasibility of the assumed improvement are unknown.

Before implementing changes, validate the analytics and establish the actual reasons for user abandonment.
