---
type: research
status: done
language: en
translation_of: ../ru/hypotheses.md
---

# Hypotheses and Design Tasks for UX Experiments

## Goal

Increase the share of users who reach `Verification Payment Completed` after opening the Dashboard through small interface changes.

## 1. Basis for the Experiments

| Current funnel transition | Users (From → To) | Conversion | Drop-off |
|---|---|---|---|
| Dashboard Loaded → Your Information Completed | 129,846 → 21,865 | 16.84% | 83.16% |
| Borrower Information Completed → Verification Payment Completed | 18,791 → 8,959 | 47.68% | 52.32% |
| Dashboard Loaded → Verification Payment Completed | 129,846 → 8,959 | 6.90% | 93.10% |

**Interface observations**

- At a viewport height of 840 px, `Your information` and `Continue` are below the fold.
- `Continue` is disabled until required fields are complete.
- Payment opens in a modal after the user clicks `Continue`.

**Limitation**

- The order of `Your Information Completed` and `Borrower Information Completed` in analytics does not match the visual order of sections. These percentages therefore cannot be treated as proven abandonment within a specific section. Validate event definitions before running A/B tests.

## 2. Testing Rules

- **Control (A):** the current Dashboard. **Variant (B):** only the change described for that experiment.
- **Primary metric for Dashboard UX experiments:** unique-user conversion from `Dashboard Loaded → Verification Payment Completed` (currently 6.90%).
- **Diagnostic metrics:** form starts, completion of both sections regardless of order, `Continue Clicked`, `Payment Modal Opened`, `Payment Attempted`, and validation errors.
- **Guardrail metrics:** technical errors and payment declines, the share of successful billable verifications, and incorrect orders.
- **A target of +1 percentage point** is a reference for estimating potential, not a guaranteed outcome. For an individual transition, the target conversion is 16.84% → 17.84% or 47.68% → 48.68%.
- Randomize participants within comparable segments; do not mix verification types, prices, or devices. Determine the required sample size and duration through statistical calculation before launch.

## 3. Priority Design Tasks

### EXP-01 — Sticky Continue Panel

#### Problem

`Continue` is below the fold and remains invisible until the user scrolls.

#### Hypothesis

An always-visible button will help users recognize when they have entered all information required to open the payment form, improving Dashboard completion.

**Change (B)**

Fix a narrow panel containing `Continue` to the bottom of the viewport. Keep the order, number, and content of fields, and preserve the existing condition for enabling the button.

**Measure**

1. Primary: Dashboard → Payment Completed.
2. Required-field completion, `Continue` clicks, and scrolling to `Your information`.

**Decision criterion**

An increase in the primary metric without worsening errors or accessibility.

### EXP-02 — Step-by-Step Form with Progress

#### Problem

Two groups of information are presented on a long page, and the remaining work is unclear.

#### Hypothesis

Explicit steps and a progress indicator will make form completion more predictable and increase completion.

**Change (B)**

Two switchable steps: `Borrower details` (including `Verification details`) and `Your information`. Show the status of each step: _not started / in progress / complete_.

**Measure**

1. Primary: Dashboard → Payment Completed.
2. Completion of each step, tab switches, errors, and completion time.

### EXP-03 — Step-by-Step Form with Progress and a Sticky Button

#### Problem

Two groups of information are presented on a long page, and the remaining work is unclear.

#### Hypothesis

Explicit steps and a progress indicator will make form completion more predictable and increase completion.

**Change (B)**

- `Borrower details` (including `Verification details`) and `Your information`. Show each step's status: _not started / in progress / complete_.
- If the panel containing `Continue` does not fit on screen, make it sticky at the bottom of the viewport.
- Allow payment only after all required fields are complete.
- Retain entered data when switching tabs.

**Measure**

Primary: Dashboard → Payment Completed. Additional: completion of each step, tab switches, errors, and completion time.

**Important**

This variant combines the first two experiments. Comparing it with the original page measures **the effect of the combined changes**, but cannot isolate each change's contribution. Test EXP-01 and EXP-02 separately for a cleaner comparison.

### EXP-04 — Progress Indicator Without Changing the Form Structure

#### Problem

On a long page, users cannot see how many required fields they have completed or how many remain.

#### Hypothesis

Showing completion progress will make the remaining work clear and improve Dashboard completion.

**Change (B)**

Add a required-field progress indicator. Keep the current page structure, section order, and `Continue` behavior. Do not add tabs, new steps, or a sticky button.

**Measure**

1. Primary: Dashboard → Payment Completed.
2. Form Completion, Abandonment by Progress, and completion time.

## 4. Additional Small Tests

| ID | Change | Hypothesis to test | Diagnostic metric |
|---|---|---|---|
| EXP-05 | Explain which required fields remain next to the disabled `Continue` button | Users are more likely to finish when they understand why the button is disabled | Form Completion, Validation Errors |
| EXP-06 | Briefly explain the next step, final price, and successful-verification-only charging rule before payment | Fewer surprises when proceeding to payment | Continue Click Rate, Payment Attempt Rate |
| EXP-07 | After `Continue`, show the payment form on the right, next to `Order summary`, instead of in a modal | Payment within the order context reduces abandonment before payment | Payment Attempt Rate, Payment Completion |
| EXP-08 | Move category and verification-purpose selection to the landing page and prefill the Dashboard | Users understand what will be verified and see its value earlier | Verify Click Rate, Landing → Payment Completed |

**Important for EXP-07**

Show payment only after required fields are complete and the user clicks `Continue`. Do not change payment logic.

**Important for EXP-08**

The user selects the category and verification type on the landing page. Pass those values to the Dashboard, where they can still be changed. Additional fields may reduce `Verify` clicks, so evaluate end-to-end conversion from the landing page to payment.

## 5. Conclusion

The goal is not simply to increase `Continue` clicks, but to increase the share of users who reach the final event without worsening order quality or payment processing.

All proposed reasons for drop-off remain hypotheses.
