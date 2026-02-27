# Organizations

---

## Overview

Organization accounts are business accounts linked to a job. They support multiple members with role-based permissions, payroll, and invoicing.

---

## Creating an Organization Account

1. Must have a job (QBCore) or society (ESX)
2. Must be the boss/owner of that job
3. Visit a bank counter
4. Select "Organization Account"
5. The account is created and linked to your job

---

## Roles & Permissions

| Permission | Owner | Manager | Employee |
|------------|-------|---------|----------|
| Withdraw | Yes | Yes | No |
| Deposit | Yes | Yes | Yes |
| Transfer | Yes | Yes | No |
| Manage Members | Yes | Yes | No |
| View Logs | Yes | Yes | No |
| Settings | Yes | No | No |
| Invoices | Yes | Yes | Yes |
| Close Account | Yes | No | No |

---

## Member Management

- **Add members** — Owner/Manager can invite players
- **Remove members** — Owner/Manager can kick members
- **Change roles** — Owner can promote/demote members
- **Max members:** 50 per organization

---

## Payroll

If `Config.Enterprise.AutoPayroll = true`:

- Automatic salary payments at set intervals
- Configurable interval (default: 60 minutes)
- Funds deducted from the organization account

---

## Organization Limits

| Limit | Default |
|-------|---------|
| Max members per org | 50 |
| Max orgs per player (as owner) | 3 |
| Org-to-personal daily limit | $100,000 |
| Business tax rate | 0% |
| Min balance to create | $0 |
| Creation fee | $0 |

---

## Org-to-Personal Transfers

By default, transfers from organization to personal accounts are allowed:

```lua
Config.Enterprise.AllowOrgToPersonalTransfer = true
Config.Enterprise.OrgToPersonalDailyLimit = 100000
```

To require approval for large transfers:

```lua
Config.Enterprise.ApprovalRequired = true
Config.Enterprise.ApprovalThreshold = 50000
```

---

## ESX Specific

For ESX servers, the boss detection can be configured:

```lua
-- Minimum grade level to be considered a boss
Config.Enterprise.OrgBossMinGrade = nil  -- nil = use grade_name detection
```
