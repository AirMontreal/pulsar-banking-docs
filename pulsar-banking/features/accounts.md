# Accounts

---

## Account Types

| Type | Description | Max Per Player |
|------|-------------|----------------|
| **Checking** | Everyday account for deposits, withdrawals, and transfers | 2 |
| **Savings** | Interest-earning account for long-term savings | 2 |
| **Joint** | Shared account between two players | 2 |
| **Organization** | Business account linked to a job, with member roles | 2 |

Total maximum accounts per player: **5** (configurable).

---

## Creating an Account

1. Visit any bank counter or ATM
2. Open the banking UI
3. Select "New Account"
4. Choose the account type
5. Set a PIN (default: `0000`)

> Organization accounts require a job and are managed by the boss/owner.

---

## Account Features

### PIN Protection

- Each account has a 4-digit PIN (5 for enterprise cards)
- Required for all transactions
- Max 5 failed attempts before lockout (15 min)

### Account Nicknames

Players can rename their accounts for easier identification (e.g., "Rent Money", "Business Fund").

### Account Numbers

Generated automatically with the prefix `PB` (e.g., `PB-1234567`).

---

## Joint Accounts

- Two players share one account
- Both can deposit, withdraw, and transfer
- Either player can close the account

---

## Organization Accounts

- Linked to a job (QBCore) or society (ESX)
- Role-based permissions: Owner, Manager, Employee
- Support payroll, invoicing, and member management
- Max 50 members per organization

See [Organizations](organizations.md) for details.

---

## Account Limits

| Limit | Default |
|-------|---------|
| Max checking balance | Unlimited |
| Max savings balance | Unlimited |
| Min checking balance | $0 |
| Min savings balance | $0 |
| Daily withdrawal limit | $50,000 |
| Daily transfer limit | $100,000 |

---

## Closing an Account

1. Balance must be $0 (or you can withdraw the remaining balance)
2. No active loans tied to the account
3. A closure fee may apply (default: $0)
