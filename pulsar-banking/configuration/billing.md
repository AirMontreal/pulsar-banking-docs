# Billing & Invoices Configuration

Configuration file: `config/billing.lua`

---

## Overview

The billing system allows players to create, send, and manage invoices. It works standalone (press F5) and is not tied to a specific bank location.

---

## Settings

| Option | Default | Description |
|--------|---------|-------------|
| `Enabled` | `true` | Enable/disable the billing system |
| `OpenKey` | `F5` | Key to open the billing panel |
| `DefaultTaxRate` | `0%` | Default tax applied to new invoices |
| `MaxLineItems` | `10` | Max items per invoice |
| `DueDays` | `7` | Default days until invoice is due |
| `MaxPendingInvoices` | `10` | Max unpaid invoices per recipient |
| `AutoOverdue` | `true` | Auto-mark invoices as overdue past due date |
| `OverdueCheckInterval` | `30 min` | How often to check for overdue invoices |

---

## Job Restrictions

By default, **all jobs** can send invoices. To restrict:

```lua
-- Only these jobs can create invoices:
AllowedJobs = { 'police', 'ambulance', 'mechanic', 'realestate' },

-- All jobs can invoice (default):
AllowedJobs = {},
```

---

## Credit Score Impact

Invoices affect the player's credit score:

| Event | Impact |
|-------|--------|
| Invoice paid on time | **+5** (max +50 total) |
| Invoice paid late | **+2** |
| Invoice overdue/unpaid | **-15** (max -75 total) |

These values are configured in `config/loans.lua` under `Config.CreditScore`.

---

## Full Configuration

```lua
Config.Billing = {
    Enabled = true,
    OpenKey = 'F5',
    DefaultTaxRate = 0,
    MaxLineItems = 10,
    DueDays = 7,
    AllowedJobs = {},
    MaxPendingInvoices = 10,
    AutoOverdue = true,
    OverdueCheckInterval = 30,
}
```
