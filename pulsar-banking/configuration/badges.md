# Badges Configuration

Configuration file: `config/badges.lua`

---

## Overview

Badges are achievements that players earn by using banking features. They serve as milestones and encourage feature exploration.

---

## Badge List

### Basics

| Badge | Description |
|-------|-------------|
| First Deposit | Make your first deposit |
| First Transfer | Complete your first transfer |
| First Withdrawal | Make your first withdrawal |

### Savings

| Badge | Description |
|-------|-------------|
| Bronze Saver | Save $1,000 across all accounts |
| Silver Saver | Save $10,000 across all accounts |
| Gold Saver | Save $100,000 across all accounts |
| Millionaire | Have a total balance over $1,000,000 |

### Investments

| Badge | Description |
|-------|-------------|
| Rookie Investor | Make your first market trade |
| Pro Investor | Complete 10 market trades |
| Market Whale | Complete 100 market trades |

### Loans

| Badge | Description |
|-------|-------------|
| Perfect Credit | Reach a credit score above 800 |
| Loan Master | Repay 5 loans without being late |
| Early Bird | Repay a loan before its term ends |

### Other

| Badge | Description |
|-------|-------------|
| Diversified | Own 3 or more different account types |
| Goal Achiever | Complete a savings goal |
| Smart Money | Set up your first auto-rule |

---

## Badge Categories

| Category | Badges |
|----------|--------|
| basics | First Deposit, First Transfer, First Withdrawal |
| savings | Bronze/Silver/Gold Saver, Millionaire |
| investments | Rookie/Pro Investor, Market Whale |
| loans | Perfect Credit, Loan Master, Early Bird |
| accounts | Diversified |
| goals | Goal Achiever |
| smart | Smart Money |

---

## Adding a Custom Badge

```lua
Config.Badges = {
    ['my_badge'] = {
        name = 'My Badge',
        description = 'Description of how to earn it',
        icon = 'my_icon',       -- Icon identifier used in NUI
        category = 'basics',    -- Category for grouping
    },
}
```

> **Note:** Custom badges require server-side logic to trigger them. The badge definition in config only defines the display — the awarding logic is in the server code.
