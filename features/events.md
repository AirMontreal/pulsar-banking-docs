# Events

List of all events for developers who want to integrate with Pulsar Banking.

---

## Server Events

### Accounts

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:accounts:create` | Create a new account |
| `pulsar-banking:server:accounts:updateIcon` | Update account icon |
| `pulsar-banking:server:accounts:changePIN` | Change account PIN |
| `pulsar-banking:server:accounts:close` | Close an account |
| `pulsar-banking:server:accounts:addMember` | Add member to joint/org account |
| `pulsar-banking:server:accounts:removeMember` | Remove member from account |
| `pulsar-banking:server:accounts:paySalary` | Pay salary to a member |
| `pulsar-banking:server:accounts:payAllSalaries` | Pay all member salaries |
| `pulsar-banking:server:accounts:printCertificate` | Print account certificate |

### Transactions

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:transactions:deposit` | Deposit money (callback) |
| `pulsar-banking:server:transactions:withdraw` | Withdraw money (callback) |
| `pulsar-banking:server:transactions:transfer` | Transfer between accounts (callback) |
| `pulsar-banking:server:transactions:getHistory` | Get transaction history (callback) |

### Cards

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:cards:request` | Request a new card |
| `pulsar-banking:server:cards:activate` | Activate a card |
| `pulsar-banking:server:cards:updateStatus` | Block/unblock a card |
| `pulsar-banking:server:cards:changePIN` | Change card PIN |
| `pulsar-banking:server:cards:delete` | Delete a card |
| `pulsar-banking:server:cards:rerequest` | Request replacement card |
| `pulsar-banking:server:cards:verifyAndUse` | Verify card for use |

### Loans

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:loans:apply` | Apply for a loan |
| `pulsar-banking:server:loans:getAll` | Get all player loans (callback) |
| `pulsar-banking:server:credit:getScore` | Get credit score (callback) |

### Investments

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:investments:buy` | Buy an asset |
| `pulsar-banking:server:investments:sell` | Sell an asset |
| `pulsar-banking:server:investments:createDeposit` | Create term deposit |
| `pulsar-banking:server:investments:withdrawDeposit` | Withdraw term deposit |
| `pulsar-banking:server:investments:getAll` | Get portfolio (callback) |
| `pulsar-banking:server:investments:getMarketData` | Get market data (callback) |

### Billing / Invoices

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:billing:create` | Create an invoice |
| `pulsar-banking:server:billing:pay` | Pay an invoice |
| `pulsar-banking:server:billing:cancel` | Cancel an invoice |
| `pulsar-banking:server:billing:getAll` | Get all invoices (callback) |

### Goals

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:goals:create` | Create a savings goal |
| `pulsar-banking:server:goals:contribute` | Contribute to a goal |
| `pulsar-banking:server:goals:cancel` | Cancel a goal |

### Contracts

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:contracts:create` | Create employment contract |
| `pulsar-banking:server:contracts:sign` | Sign a contract |
| `pulsar-banking:server:contracts:terminate` | Terminate a contract |
| `pulsar-banking:server:contracts:delete` | Delete a contract |
| `pulsar-banking:server:contracts:print` | Print a contract |

### Auto-Rules

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:autorules:create` | Create an auto-rule |
| `pulsar-banking:server:autorules:toggle` | Enable/disable auto-rule |
| `pulsar-banking:server:autorules:delete` | Delete an auto-rule |

### Contacts

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:contacts:add` | Save a contact |
| `pulsar-banking:server:contacts:delete` | Delete a contact |
| `pulsar-banking:server:contacts:update` | Update contact name |

### Admin

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:admin:approveLoan` | Approve a pending loan |
| `pulsar-banking:server:admin:denyLoan` | Deny a loan application |
| `pulsar-banking:server:admin:freezeAccount` | Freeze/unfreeze an account |

### Notifications

| Event | Description |
|-------|-------------|
| `pulsar-banking:server:notifications:markRead` | Mark notification as read |
| `pulsar-banking:server:notifications:markAllRead` | Mark all as read |

---

## Client Events

| Event | Description |
|-------|-------------|
| `pulsar-banking:client:useCard` | Triggered when card item is used from inventory |
| `pulsar-banking:client:useContract` | Triggered when contract item is used |
| `pulsar-banking:client:useCertificate` | Triggered when certificate item is used |
| `pulsar-banking:client:notify` | Display a client-side notification |
| `pulsar-banking:client:accounts:refresh` | Refresh account data in the UI |
| `pulsar-banking:client:balance:update` | Update balance display |
| `pulsar-banking:client:billing:refresh` | Refresh billing UI |
| `pulsar-banking:client:atmClose` | Close ATM and stop animation |

---

## Robbery Event

When robbery integration is enabled, this event is triggered on large withdrawals:

```lua
-- Triggered when conditions are met:
-- Amount >= Config.Gameplay.Robbery.TriggerAmount
-- Online police >= Config.Gameplay.Robbery.PoliceRequired
TriggerEvent('pulsar-banking:robbery:triggered', source, amount, bankId)
```

Listen for this event in your robbery script to start a bank robbery scenario.
