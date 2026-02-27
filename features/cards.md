# Cards

---

## Overview

Cards are physical inventory items that players can order from bank counters. Each card is linked to a specific bank account.

---

## Card Types

### Debit Card
- Free to order
- Linked to checking/savings account
- $10,000 daily limit
- No credit score requirement

### Credit Card
- $100/month fee
- Requires credit score of 600+
- Credit limit based on score (up to $100,000)
- 18% interest rate on credit balance
- 30-day billing cycle

### Enterprise Card
- Free to order
- Linked to organization account
- $25,000 daily limit
- 5-digit PIN

---

## Ordering a Card

1. Visit a bank that offers the `cards` service
2. Open the banking UI
3. Navigate to the Cards section
4. Select the card type
5. The card item will be added to your inventory

---

## Card Security

- Cards have unique generated numbers (prefix: `4532`)
- PIN protection for all card transactions
- Cards expire after their configured duration (2-3 years)
- If a card item is removed from inventory, the card is blocked (`Config.BlockCardOnItemRemove = true`)

---

## Credit Card Details

### Credit Limits by Score

| Score Range | Credit Limit |
|------------|--------------|
| 500 - 599 | $5,000 |
| 600 - 699 | $15,000 |
| 700 - 799 | $50,000 |
| 800 - 850 | $100,000 |

### Billing

- Credit balance accrues 18% interest
- Billing cycle: 30 days
- Payment due at end of each cycle
- Late payments affect credit score (-25)
