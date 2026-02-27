# Loans & Credit Score Configuration

Configuration file: `config/loans.lua`

---

## Loan Types

### Personal Loan

| Option | Value |
|--------|-------|
| Min Amount | $1,000 |
| Max Amount | $100,000 |
| Min Term | 7 days |
| Max Term | 90 days |
| Min Credit Score | 400 |
| Auto-Approve Score | 700+ |
| Max Active Loans | 2 |

### Business Loan

| Option | Value |
|--------|-------|
| Min Amount | $1,000 |
| Max Amount | $250,000 |
| Min Term | 14 days |
| Max Term | 180 days |
| Min Credit Score | 550 |
| Auto-Approve Score | 700+ |
| Max Active Loans | 1 |

**Business Loan Requirements:**

```lua
Config.BusinessLoan = {
    requireJob = true,
    blacklistedJobs = { 'unemployed' },
}
```

---

## Credit Score System

| Option | Default | Description |
|--------|---------|-------------|
| `defaultScore` | `500` | Starting score for new players |
| `minScore` | `300` | Minimum possible score |
| `maxScore` | `850` | Maximum possible score |

### Score Changes

| Event | Impact |
|-------|--------|
| Loan repaid on time | **+30** |
| Loan default | **-150** |
| Late payment | **-25** |
| Account age (per cycle) | **+5** (max +50) |
| Invoice paid on time | **+5** (max +50) |
| Invoice paid late | **+2** |
| Invoice overdue | **-15** (max -75) |

---

## Loan Penalties

| Option | Default | Description |
|--------|---------|-------------|
| `gracePeriodHours` | `24` | Hours after due date before penalties |
| `penaltyRate` | `2%` | Additional rate charged on overdue |
| `maxOverdueBeforeDefault` | `5` | Missed payments before loan defaults |

---

## Loan Approval Flow

1. Player applies for a loan at a bank
2. If credit score >= `autoApproveMinScore` (700): **auto-approved**
3. If credit score < auto-approve threshold: **pending banker approval**
4. Bankers with sufficient grade can approve/deny (see [Jobs](jobs.md))

---

## Customizing Loan Types

```lua
Config.Loans = {
    personal = {
        name = 'Personal Loan',
        minAmount = 1000,
        maxAmount = 100000,
        minTermDays = 7,
        maxTermDays = 90,
        minCreditScore = 400,
        autoApproveMinScore = 700,
        maxActiveLoans = 2,
    },
}
```
