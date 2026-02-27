# Transactions

---

## Transaction Types

| Type | Description |
|------|-------------|
| **Deposit** | Add cash to your account |
| **Withdrawal** | Take cash from your account |
| **Transfer** | Send money to another account |
| **Wire Transfer** | Transfer to a different bank (higher fee) |
| **Loan Payment** | Automatic or manual loan repayment |
| **Interest** | Interest earned on savings |
| **Fee** | Maintenance fees, ATM fees, etc. |
| **Invoice** | Payment received or sent via billing |

---

## Deposits

- Available at bank counters and ATMs
- ATM deposit limit: $50,000 per transaction
- ATM daily deposit limit: $100,000
- No deposit fee by default

---

## Withdrawals

- Available at bank counters and ATMs
- ATM withdrawal limit: $25,000 per transaction
- ATM daily withdrawal limit: $50,000
- Bank counter daily limit: $50,000

---

## Transfers

- Transfer between your own accounts or to other players
- Search by account number or player name
- Quick transfer amounts: $100, $500, $1K, $5K, $10K, $50K
- 15-second cooldown between transfers
- Daily transfer limit: $100,000
- Confirmation required for transfers above $50,000

### Saved Contacts

Save frequent recipients for quick transfers. Up to 20 saved contacts.

---

## Transaction History

- Full history accessible in the banking UI
- Filter by type, date, and amount
- Search transactions by description
- Categorized automatically (deposit, transfer, fee, etc.)

---

## Cooldowns

| Action | Cooldown |
|--------|----------|
| Transfer | 15 seconds |
| Withdrawal | 10 seconds |
| Deposit | 10 seconds |

---

## Rate Limits

- Maximum **60 transactions per hour** per player
- Configurable in `Config.Security.MaxTransactionsPerHour`

---

## Notifications

Players receive in-game notifications for:

- Deposits received
- Withdrawals completed
- Incoming transfers
- Interest earned
- Loan payments due
- Fees charged
- Low balance warnings (below $500)
