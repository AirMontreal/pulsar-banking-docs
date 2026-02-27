# General Settings

Main configuration file: `config/config.lua`

---

## Framework & System

| Option | Default | Description |
|--------|---------|-------------|
| Config.Framework | qbcore | Set your framework: qbcore or esx (must be set manually) |
| Config.Debug | false | Enable debug prints in console |
| Config.Locale | en | Language: en, fr, es, de, it, pt, nl, tr |
| Config.Currency | $ | Currency symbol |
| Config.CurrencyFormat | en-US | Number formatting locale |
| Config.UseTarget | true | Use target system or draw markers |
| Config.TargetSystem | auto | Auto-detected, or force: ox\_target / qb-target |
| Config.InventorySystem | auto | Auto-detected, or force: ox\_inventory / qb-inventory |

---

## Account Settings

| Option | Default | Description |
|--------|---------|-------------|
| Config.DefaultPIN | 0000 | Default PIN for new accounts |
| Config.MaxAccountsPerPlayer | 5 | Total max accounts per player |
| Config.MaxPersonalAccounts | 2 | Max checking/savings accounts |
| Config.MaxBusinessAccounts | 2 | Max organization accounts |
| Config.MaxJointAccounts | 2 | Max joint accounts |
| Config.AccountNumberPrefix | PB | Prefix for account numbers |

---

## Limits

| Option | Default | Description |
|--------|---------|-------------|
| DailyWithdrawLimit | $50,000 | Max daily withdrawals |
| DailyTransferLimit | $100,000 | Max daily transfers |
| LargeTransactionThreshold | $50,000 | Threshold for large transaction alerts |
| LowBalanceThreshold | $500 | Low balance warning level |

---

## Account Limits (Extended)

```lua
Config.AccountLimits = {
    MaxCheckingBalance = 0,        -- 0 = unlimited
    MaxSavingsBalance = 0,
    MaxOrganizationBalance = 0,
    MinCheckingBalance = 0,
    MinSavingsBalance = 0,
    ATMMaxWithdraw = 25000,        -- Per ATM transaction
    ATMMaxDeposit = 50000,
    ATMDailyWithdrawLimit = 50000,
    ATMDailyDepositLimit = 100000,
    MaxTransferAmount = 500000,    -- Per transfer
    MinTransferAmount = 1,
    OverdraftEnabled = false,      -- Allow negative balance
    OverdraftLimit = 5000,
    OverdraftInterestRate = 0.05,  -- 5%
    OverdraftFee = 35,             -- Flat fee
}
```

---

## Fees & Commissions

| Fee | Default | Description |
|-----|---------|-------------|
| TransferFee | 0% | Percentage fee on transfers |
| TransferFlatFee | $0 | Flat fee added to transfers |
| ATMWithdrawFee | $0 | Per ATM withdrawal |
| ATMDepositFee | $0 | Per ATM deposit |
| MonthlyMaintenanceFee | $0 | Charged every interest cycle |
| OpenAccountFee | $0 | Fee to open an account |
| CloseAccountFee | $0 | Fee to close an account |
| WireTransferFee | $250 | Cross-bank transfers |
| ExchangeFee | 2% | Currency exchange (future) |

---

## Interest Rates

| Option | Default | Description |
|--------|---------|-------------|
| SavingsRate | 0.5% | Interest per cycle for savings |
| CheckingRate | 0% | Interest per cycle for checking |
| CompoundInterest | true | Compound or simple interest |
| MinBalanceForInterest | $100 | Minimum balance to earn interest |
| MaxInterestPayout | $10,000 | Max payout per cycle (anti-exploit) |
| HighBalanceThreshold | $500,000 | Threshold for bonus rate |
| HighBalanceBonusRate | 0.1% | Bonus rate for high balances |
| WealthTaxThreshold | $5,000,000 | Threshold for wealth tax |
| WealthTaxRate | 0% | Wealth tax rate (disabled) |

> **Interest Cycle:** Runs every `Config.InterestCycleMinutes` (default: 60 minutes).

---

## Security

| Option | Default | Description |
|--------|---------|-------------|
| MaxPINAttempts | 5 | Attempts before lockout |
| PINLockoutMinutes | 15 | Lockout duration |
| TransferCooldownSeconds | 15 | Cooldown between transfers |
| WithdrawCooldownSeconds | 10 | Cooldown between withdrawals |
| DepositCooldownSeconds | 10 | Cooldown between deposits |
| MaxTransactionsPerHour | 60 | Rate limit per player |
| AutoFreezeEnabled | true | Auto-freeze suspicious accounts |
| AutoFreezeThreshold | $100,000 | Amount that triggers review |
| AutoFreezeCreditScore | 350 | Credit score threshold |
| LargeTransferConfirmation | true | Confirm large transfers |
| LargeTransferThreshold | $50,000 | Confirmation threshold |

---

## Enterprise / Organizations

| Option | Default | Description |
|--------|---------|-------------|
| MaxMembers | 50 | Max members per organization |
| MaxOrgsPerPlayer | 3 | Max organizations per player (as owner) |
| MinBalanceToCreate | $0 | Min balance to create an org |
| CreationFee | $0 | Fee to create an org |
| AutoPayroll | false | Automatic salary payments |
| BusinessTaxRate | 0% | Tax on org income |
| AllowOrgToPersonalTransfer | true | Allow org to personal transfers |
| OrgToPersonalDailyLimit | $100,000 | Daily org to personal limit |

### Role Permissions

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

## Gameplay

### Bank Hours
```lua
BankHours = {
    Enabled = false,    -- Set true to restrict hours
    OpenHour = 8,       -- 8 AM
    CloseHour = 22,     -- 10 PM
}
```
> ATMs remain available 24/7 even with bank hours enabled.

### Robbery Integration
```lua
Robbery = {
    Enabled = false,
    TriggerAmount = 100000,
    EventName = 'pulsar-banking:robbery:triggered',
    CooldownMinutes = 60,
    PoliceRequired = 2,
}
```

### Death Penalty
```lua
DeathPenalty = {
    Enabled = false,
    Percentage = 0.00,
    FlatAmount = 0,
    MaxLoss = 0,
    DeductFromBank = false,
}
```

### Welfare System
```lua
Welfare = {
    Enabled = false,
    Amount = 500,
    IntervalMinutes = 60,
    RequiredJob = 'unemployed',
    MaxBalance = 10000,
}
```

---

## Notifications & Discord

| Option | Default | Description |
|--------|---------|-------------|
| DiscordWebhook | empty | Discord webhook URL (empty = disabled) |
| DiscordBotName | Pulsar Banking | Bot display name |
| DiscordColor | 16750848 | Embed color (decimal) |

### Discord Logging Events

| Event | Default |
|-------|---------|
| Large Transactions | Yes (above $50,000) |
| Loan Applications | Yes |
| Account Creation | Yes |
| Account Closure | Yes |
| Suspicious Activity | Yes |
| Admin Actions | Yes |

---

## Quality of Life

| Option | Default | Description |
|--------|---------|-------------|
| EnableFavorites | true | Save frequent recipients |
| MaxFavorites | 20 | Max saved contacts |
| QuickAmounts | 100, 500, 1k, 5k, 10k, 50k | Preset quick amounts |
| EnableAccountNicknames | true | Rename accounts |
| EnableRoundUpSavings | true | Auto round-up to savings |
| EnableSounds | true | UI sound effects |
| SoundVolume | 0.5 | Sound volume (0-1) |
| EnableBalanceHUD | false | Balance HUD on screen |
| BalanceHUDKey | F6 | Key to toggle HUD |

---

## Scheduled Tasks

| Option | Default | Description |
|--------|---------|-------------|
| InterestCycleMinutes | 60 | Interest payout interval |
| LoanCheckMinutes | 30 | Loan payment check interval |

---

## Data Cleanup

| Option | Default | Description |
|--------|---------|-------------|
| AuditLogDays | 30 | Delete old audit logs |
| NotificationDays | 14 | Delete old read notifications |
