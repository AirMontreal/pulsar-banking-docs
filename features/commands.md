# Commands

---

## Player Commands

| Command | Description |
|---------|-------------|
| `/openbilling` | Open the billing/invoices panel |

> The billing panel can also be opened with the **F5** key (configurable via `Config.Billing.OpenKey`).

---

## Admin Commands

All admin commands require `Config.AdminPermission` (`'admin'`) **and** your license to be in `Config.AdminLicenses`.

Admin commands have a **5-second cooldown** between uses.

### /bankadmin

| Usage | Description |
|-------|-------------|
| `/bankadmin give [citizenid] [amount]` | Deposit money into a player's primary checking account |
| `/bankadmin freeze [account_number]` | Freeze an account (blocks all transactions) |
| `/bankadmin unfreeze [account_number]` | Unfreeze a previously frozen account |

**Examples:**

```
/bankadmin give ABC12345 50000
/bankadmin freeze PB-1234567
/bankadmin unfreeze PB-1234567
```

> All admin actions are logged in the audit log and optionally sent to Discord via webhook.
