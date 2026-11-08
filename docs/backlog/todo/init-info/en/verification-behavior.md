---
type: research
status: done
language: en
translation_of: ../ru/verification-behavior.md
---

# Truv — Dashboard: Original Logic and Behavior

This document records the behavior of the original interface (**Control A**) based on the supplied screenshots and user descriptions. Redesign hypotheses are not included.

## 1. Entering the Dashboard

- A user opens an employer verification page, such as [Employment Verification for Walmart](https://truv.com/verifications/walmart-employment-verification).
- On the landing page, the user clicks **Verify Walmart employee**.
- The **Dashboard** opens.

## 2. Dashboard Structure

The main column contains these sections, from top to bottom:

1. **Borrower details** — borrower information, including required fields.
2. **Verification details** — verification type, employer, and **Add employer**.
3. **Your information** — requester information, including required fields.
4. **Continue** — the button that proceeds to payment.

The right column contains **Order summary**, showing the order's items and total. In the supplied example, the initial price was **$50**.

**Borrower details** and **Your information** are on the same page. The user did not describe a mandatory sequence for entering individual fields. The visual order of sections should not be confused with the sequence of analytics completion events.

## 3. Adding an Employer

1. Clicking **Add employer** adds another employer input.
2. Once the user enters a value, that employer appears in **Order summary**, and the total is recalculated.
3. While the added field is empty, no new employer appears in **Order summary**, and the total stays the same.

**Important:** adding an empty field alone does not change the order's items or price.

## 4. Order Summary

- Shows the selected verification type, employers, and order price.
- Updates dynamically when an additional employer is entered.
- Does not include empty employer fields.
- The starting price on the reviewed screen is **$50**.

## 5. Continue Button

- Appears at the bottom of the page after the form sections.
- Is **disabled** until all required fields in both main sections are complete.
- Becomes enabled once the required fields are complete.
- Opens the **Payment information** modal when clicked.

Completing **Borrower details** alone is not enough: the required **Your information** fields must also be complete.

## 6. Visibility and Scrolling

At a browser window height of **840 px**:

- **Your information** is not visible without scrolling down.
- **Continue** is also below the fold.
- The original interface has no explicit form-completion progress indicator.

This observation applies to the stated viewport height; behavior at other screen sizes was not tested.

## 7. Payment Form

After the user clicks an enabled **Continue**:

- The **Payment information** modal opens over the Dashboard.
- **Apple Pay**, **Google Pay**, and card payment are available.
- Card fields include card number, expiration date, security code, and country.
- Payment terms and agreement links are shown.
- The primary action is **Start a verification**.
- Users can close the modal and return to the Dashboard.
- The modal states that Truv charges only for **successful verifications**.

## 8. Interface Sequence

```text
Landing Page
    ↓ Verify
Dashboard Loaded
    ├─ Borrower details
    ├─ Verification details (Add employer → Order summary)
    ├─ Your information
    └─ Continue (after required fields are complete)
         ↓
Payment information (modal)
         ↓
Start a verification
```

This diagram represents section layout and available actions, **not a confirmed sequence of analytics events**. Payment completion and the subsequent verification result require separate confirmation.

## 9. What Has Not Been Established

- Which actions trigger `Borrower Information Completed` and `Your Information Completed`.
- Whether users can continue with an empty added employer field.
- Whether entered data survives a page reload.
- What happens after **Start a verification** on successful and unsuccessful attempts.
- When `Verification Payment Completed` is recorded.

This document describes the **original Dashboard (Control A)** as the reference for subsequent UX experiments.
