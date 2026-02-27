# Admin Panel

---

## Overview

Server administrators can manage player accounts, freeze suspicious activity, and monitor transactions through admin commands and Discord logging.

---

## Admin Access

Admin access is controlled by:

```lua
Config.AdminPermission = 'admin'      -- Framework permission level
Config.AdminLicenses = {
    'your_license_hash_here',          -- Rockstar license hash
}
```

Both conditions are checked — you need the permission level **and** your license must be whitelisted.

---

## Admin Commands

All commands have a 5-second cooldown to prevent spam.

### `/bankadmin`

Opens the admin panel with the following capabilities:

- **Search accounts** — Find accounts by player name or account number
- **View account details** — Balance, transactions, owner info
- **Freeze/Unfreeze accounts** — Block all transactions on an account
- **View transaction history** — Full audit trail
- **Manage loans** — View and modify active loans

---

## Account Freezing

### Manual Freeze
Admins (and bank managers grade 2+) can manually freeze accounts.

### Auto-Freeze
When enabled, accounts are automatically frozen if:
- Transaction amount exceeds $100,000 **AND**
- Player's credit score is below 350

```lua
Config.Security.AutoFreezeEnabled = true
Config.Security.AutoFreezeThreshold = 100000
Config.Security.AutoFreezeCreditScore = 350
```

### Frozen Account Behavior
- All transactions are blocked (deposit, withdraw, transfer)
- Player sees a "frozen" message when trying to use the account
- Only admins/managers can unfreeze

---

## Audit Logging

All admin actions are logged in the `pulsar_audit_log` database table:

- Who performed the action
- What action was taken
- When it happened
- Target account/player

Logs are automatically cleaned up after 30 days (configurable via `Config.Cleanup.AuditLogDays`).

---

## Discord Webhooks

Set up Discord logging for real-time alerts:

```lua
Config.Notifications.DiscordWebhook = 'https://discord.com/api/webhooks/...'
```

### Logged Events

| Event | Default |
|-------|---------|
| Large transactions (> $50,000) | Enabled |
| Loan applications | Enabled |
| Account creation | Enabled |
| Account closure | Enabled |
| Suspicious activity | Enabled |
| Admin actions | Enabled |

### Webhook Customization

```lua
Config.Notifications.DiscordBotName = 'Pulsar Banking'
Config.Notifications.DiscordAvatarUrl = ''  -- Custom avatar URL
Config.Notifications.DiscordColor = 16750848  -- Embed color (decimal)
```

---

## Banker Job Permissions

Bank employees with the right grade can also perform admin-like tasks:

| Action | Required Grade |
|--------|---------------|
| Approve loans | Associate (1+) |
| Freeze accounts | Manager (2+) |
| View all accounts | Associate (1+) |
| Generate reports | Manager (2+) |

See [Jobs Configuration](../configuration/jobs.md) for details.
