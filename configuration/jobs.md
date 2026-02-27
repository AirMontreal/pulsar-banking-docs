# Jobs Configuration

Configuration file: `config/jobs.lua`

---

## Overview

The banker job allows players to work at banks, approve loans, manage accounts, and generate reports. Permissions are based on job grades.

---

## Banker Job Grades

| Grade | Name | Can Approve Loans | Max Loan Approval |
|-------|------|-------------------|-------------------|
| 0 | Teller | No | $0 |
| 1 | Associate | Yes | $25,000 |
| 2 | Manager | Yes | $100,000 |
| 3 | Director | Yes | $500,000 |

---

## Permissions by Grade

| Permission | Teller (0) | Associate (1) | Manager (2) | Director (3) |
|------------|------------|---------------|-------------|--------------|
| Approve Loans | No | Yes | Yes | Yes |
| Freeze Accounts | No | No | Yes | Yes |
| View All Accounts | No | Yes | Yes | Yes |
| Generate Reports | No | No | Yes | Yes |

---

## Configuration

```lua
Config.BankJobs = {
    ['banker'] = {
        label = 'Bank Manager',
        grades = {
            [0] = { name = 'Teller', canApproveLoan = false, maxLoanApproval = 0 },
            [1] = { name = 'Associate', canApproveLoan = true, maxLoanApproval = 25000 },
            [2] = { name = 'Manager', canApproveLoan = true, maxLoanApproval = 100000 },
            [3] = { name = 'Director', canApproveLoan = true, maxLoanApproval = 500000 },
        },
        canFreezeAccounts = { 2, 3 },
        canViewAllAccounts = { 1, 2, 3 },
        canGenerateReports = { 2, 3 },
    },
}
```

---

## Customizing

### Change the Job Name

If your server uses a different job name (e.g., `bankier`, `banquier`):

1. Change the key in `Config.BankJobs`:
   ```lua
   ['your_job_name'] = { ... }
   ```
2. Update `Config.BankManagerJob` in `config/config.lua`:
   ```lua
   Config.BankManagerJob = 'your_job_name'
   ```

### Add More Grades

Add additional grade entries to the `grades` table. Make sure grade numbers match your framework's job grades.
