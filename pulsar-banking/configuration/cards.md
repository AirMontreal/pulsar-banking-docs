# Cards Configuration

Configuration file: `config/cards.lua`

---

## Overview

Pulsar Banking includes 3 card types that function as physical inventory items. Cards can be ordered from any bank that offers the cards service.

---

## Card Types

### Debit Card

| Option | Value |
|--------|-------|
| Item Name | debit_card |
| Daily Limit | $10,000 |
| Requires Credit Score | No |
| Monthly Fee | $0 |
| Expiry | 3 years |

### Credit Card

| Option | Value |
|--------|-------|
| Item Name | credit_card |
| Daily Limit | $15,000 |
| Requires Credit Score | Yes (minimum 600) |
| Monthly Fee | $100 |
| Expiry | 2 years |
| Interest Rate | 18% |
| Billing Cycle | 30 days |

**Credit Limits by Score:**

| Credit Score | Limit |
|--------------|-------|
| 500 - 599 | $5,000 |
| 600 - 699 | $15,000 |
| 700 - 799 | $50,000 |
| 800 - 850 | $100,000 |

### Enterprise Card

| Option | Value |
|--------|-------|
| Item Name | enterprise_card |
| Daily Limit | $25,000 |
| Requires Credit Score | No |
| Monthly Fee | $0 |
| Expiry | 3 years |
| PIN Length | 5 digits |

> Enterprise cards are linked to organization accounts.

---

## General Settings

| Option | Default | Description |
|--------|---------|-------------|
| Config.CardNumberPrefix | 4532 | Prefix for generated card numbers |
| Config.BlockCardOnItemRemove | true | Block card when item is removed from inventory |

---

## Customizing a Card Type

```lua
Config.Cards = {
    debit = {
        name = 'Debit Card',
        itemName = 'debit_card',        -- Must match inventory item name
        dailyLimit = 10000,
        requiresCreditScore = false,
        minCreditScore = 0,
        fee = 0.00,                     -- Monthly fee
        expiryYears = 3,
    },
}
```

---

## Adding a New Card Type

1. Add the card definition in `config/cards.lua`
2. Add the corresponding item to your inventory system (ox_inventory or qb-inventory)
3. Add the card image to your inventory's image folder
