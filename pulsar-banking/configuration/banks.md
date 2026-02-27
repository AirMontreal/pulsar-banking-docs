# Banks Configuration

Configuration file: `config/banks.lua`

---

## Overview

Pulsar Banking comes with **8 pre-configured bank locations** across the GTA map. Each bank has its own fees, interest rates, and available services.

---

## Bank List

| ID | Name | Type | Main Bank |
|----|------|------|-----------|
| fleeca_legion | Fleeca Bank - Legion Square | Fleeca | No |
| fleeca_alta | Fleeca Bank - Alta Street | Fleeca | No |
| fleeca_burton | Fleeca Bank - Burton | Fleeca | No |
| fleeca_delperro | Fleeca Bank - Del Perro | Fleeca | No |
| fleeca_greatocean | Fleeca Bank - Great Ocean Highway | Fleeca | No |
| fleeca_route68 | Fleeca Bank - Route 68 | Fleeca | No |
| pacific_standard | Pacific Standard Bank | Pacific | Yes |
| blaine_county | Blaine County Savings | Blaine | Yes |

---

## Bank Structure

Each bank entry supports the following options:

```lua
['bank_id'] = {
    name = 'Bank Name',                           -- Display name
    bankType = 'fleeca',                           -- Type: 'fleeca', 'pacific', 'blaine'
    isMainBank = false,                            -- Main banks have different blip styling
    coords = vector3(x, y, z),                     -- Bank position
    heading = 340.0,                               -- NPC facing direction
    blip = {
        sprite = 108,                              -- Blip icon (108 = bank)
        color = 69,                                -- Blip color (69 = green, 2 = dark green)
        scale = 0.65,                              -- Blip size
        label = 'Bank Name',                       -- Blip label on map
    },
    counter = {
        coords = vector3(x, y, z),                 -- Interaction point
        radius = 1.5,                              -- Interaction radius
    },
    ped = {
        coords = vector4(x, y, z, heading),        -- NPC position + heading
    },
    fees = {
        deposit = 0.0,                             -- Deposit fee (%)
        withdrawal = 0.0,                          -- Withdrawal fee (%)
        transfer = 0.005,                          -- Transfer fee (0.5%)
        atm = 2.00,                                -- ATM fee ($)
    },
    interestRates = {
        savings = 0.01,                            -- Savings interest (1%)
        loanBase = 0.05,                           -- Base loan rate (5%)
    },
    services = { 'checking', 'savings', 'loans', 'cards' },
}
```

---

## Per-Bank Fees

| Bank | Transfer Fee | ATM Fee | Savings Rate | Loan Rate |
|------|-------------|---------|--------------|-----------|
| Fleeca branches | 0.5% | $2.00 | 1% | 5% |
| Pacific Standard | 0.2% | $0.50 | 2% | 3.5% |
| Blaine County | 0.8% | $2.00 | 0.5% | 7% |

> Per-bank fees override the global fees from `config/config.lua`.

---

## Available Services

| Service | Description |
|---------|-------------|
| checking | Checking account creation |
| savings | Savings account creation |
| loans | Loan applications |
| cards | Card ordering (debit/credit) |

> **Note:** fleeca_route68 and blaine_county do not offer card services by default.

---

## Adding a New Bank

Add a new entry to the `Config.Banks` table:

```lua
['my_custom_bank'] = {
    name = 'My Custom Bank',
    bankType = 'fleeca',
    isMainBank = false,
    coords = vector3(100.0, 200.0, 30.0),
    heading = 180.0,
    blip = { sprite = 108, color = 69, scale = 0.65, label = 'My Custom Bank' },
    counter = { coords = vector3(100.0, 200.0, 30.0), radius = 1.5 },
    ped = { coords = vector4(100.0, 202.0, 30.0, 180.0) },
    fees = {
        deposit = 0.0,
        withdrawal = 0.0,
        transfer = 0.005,
        atm = 2.00,
    },
    interestRates = {
        savings = 0.01,
        loanBase = 0.05,
    },
    services = { 'checking', 'savings', 'loans', 'cards' },
}
```

---

## Removing a Bank

Simply delete or comment out the bank entry from `Config.Banks`. The script will only load banks present in the config.

---

## Blip Colors Reference

| Color ID | Color |
|----------|-------|
| 0 | White |
| 1 | Red |
| 2 | Dark Green |
| 3 | Blue |
| 5 | Yellow |
| 69 | Green |
