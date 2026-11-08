---
type: research
status: done
language: en
translation_of: ../ru/recommendations.md
---

## 1. Prioritization

Based on the scale of drop-off, financial scenarios, and observed UX risks, the following preliminary priorities are proposed.

| Priority | Area | Rationale |
|---|---|---|
| P0 | Analytics Validation | Without accurate events, we cannot reliably establish the causes of losses or measure improvements |
| P1 | Dashboard Completion | The largest drop-off within the product and the greatest modeled effect from improved conversion. Changes here affect all subsequent stages |
| P2 | Payment Completion | Substantial losses immediately before the final event |
| P3 | Landing Page | The largest absolute loss, but visitor intent is unknown |
| P4 | Verify → Dashboard | Conversion is 99.17%; limited room for improvement |

These are priorities for **research and hypothesis testing**, not confirmed interface defects.

## 2. Recommended Action Plan

### 2.1. Validate Analytics

#### Goal

Make sure that the metrics actually correspond to user actions.

Validate the definitions of:

- Your Information Completed.
- Borrower Information Completed.
- Verification Payment Completed.

Also validate the order in which events are recorded and the configuration of the sequential funnel.

Then extend the analytics:

| Metric | Purpose |
|---|---|
| Form Start Rate | Share of users who start filling out the form |
| Form Progress | Share of required fields completed |
| Section Completion | Completion of each section, regardless of order |
| Validation Errors | Frequency and type of input errors |
| Abandonment by Progress | Completion level at which users stop interacting |
| Continue Click Rate | Share of users who click Continue |
| Payment Modal Open Rate | Share of users who open the payment form |
| Payment Modal Abandonment Rate | Share of users who close the payment form without attempting payment |
| Payment Attempt Rate | Share of unique users who make at least one payment attempt |
| Payment Attempt Count | Total payment attempts, including retries |
| Unique Payment Users | Unique users who attempt payment |
| Payment Attempts per User | Average attempts per user among users who attempt payment |
| Payment Success Rate (per Attempt) | Successful attempts as a share of all payment attempts |
| Payment Failure Rate (per Attempt) | Failed attempts as a share of all payment attempts |
| Unique Payment Conversion Rate | Share of unique users who successfully pay at least once |
| Payment Decline Reason | Bank or provider decline reasons: insufficient funds, suspected fraud, blocked cards, or cards reported stolen |
| Payment Authentication Failure | 3D Secure / SCA errors, failures, or cancellations |
| Payment Processing Error | Technical gateway errors, timeouts, or provider unavailability |
| Payment Retry Rate | Share of users who retry after a failed attempt |
| Payment Recovery Rate | Share of users who successfully pay after an initial failure |

### 2.2. Investigate Dashboard

#### Goal

Find the actual reasons for incomplete forms.

#### Investigate

- Whether users see all sections.
- Whether they understand how much required information is needed.
- Which fields cause difficulties.
- At what completion percentage they stop interacting.
- Whether they understand what enables Continue.

#### Potential UX hypotheses to test

- Splitting the form into steps.
- Adding a progress indicator.
- Making the next action more visible.
- Providing clearer validation feedback.

### 2.3. Investigate Payment

#### Goal

1. Separate purchase abandonment from payment-processing errors.

#### Transitions to measure

1. Continue Clicked →
2. Payment Modal Opened →
3. Payment Attempted →
4. Payment Completed.

#### Also investigate

- Why users close the modal.
- Payment-field errors.
- The effect of order price.

### 2.4. Investigate Landing Page

#### Goals

1. Establish which visitors actually intend to order a verification.
2. Analyze traffic sources, search queries, and differences between user categories.

Use the findings to test hypotheses about the clarity of the service, pricing, and next steps.

### 2.5. Validate Improvements

Once the reasons for drop-off are confirmed, conduct UX testing and controlled experiments.

#### Primary product metric

1. Conversion from Dashboard →
2. Verification Payment Completed.

#### Additional metrics

- Form Completion Rate.
- Payment Completion Rate.
- Average order value.
- Share of verifications that are successfully completed and billed.

## 3. Limitations of This Assessment

This research is based on the supplied funnel, a review of the interface, and observations of its behavior.

The following assumptions are made for this case study:

1. All metrics cover one comparable period and the specified user sample.
2. The funnel represents unique users in a sequential model.
3. Financial modeling uses illustrative prices of $35 and $50, not the actual average order value.
4. Downstream conversion rates remain constant when modeling improvements.
5. Additional final events are provisionally treated as billable orders.
6. Financial results are not extrapolated to a month or a year because the observation period is unknown.

Actual lost revenue, profitability, and the effect of UX changes cannot be calculated reliably without additional product and financial data.

## 10. Final Recommendation

**The main growth opportunity lies between opening the Dashboard and completing payment.**

The current funnel shows substantial user losses, but insufficient event detail and possible sequencing issues prevent us from establishing why they occur.

The financial scenarios suggest that improvements to the *Dashboard* and payment process could have a significant effect.

#### Recommended sequence

1. Validate the analytics.
2. Establish the actual reasons for user abandonment.
3. Prioritize confirmed UX problems by their impact on the business.
4. Test changes and measure their impact on conversion and billable verifications.

This approach moves the work from assumptions toward measurable product decisions and helps direct resources based on evidence.
