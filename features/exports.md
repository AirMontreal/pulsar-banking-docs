# Exports & API

Server-side exports for integrating Pulsar Banking with other resources.

---

## Server Exports

### GetAccountBalance

Returns the total balance for a player's accounts.

```lua
local balance = exports['pulsar-banking']:GetAccountBalance(citizenid, accountType)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `citizenid` | string | Yes | Player's citizen ID |
| `accountType` | string | No | Account type (`'checking'`, `'savings'`). Defaults to `'checking'` |

**Returns:** `number` — Total balance

**Example:**
```lua
-- Get a player's checking balance
local balance = exports['pulsar-banking']:GetAccountBalance('ABC12345')
print('Balance: $' .. balance)

-- Get savings balance
local savings = exports['pulsar-banking']:GetAccountBalance('ABC12345', 'savings')
```

---

### GetPlayerAccounts

Returns all accounts belonging to a player.

```lua
local accounts = exports['pulsar-banking']:GetPlayerAccounts(citizenid)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `citizenid` | string | Yes | Player's citizen ID |

**Returns:** `table` — Array of account objects

**Example:**
```lua
local accounts = exports['pulsar-banking']:GetPlayerAccounts('ABC12345')
for _, account in ipairs(accounts) do
    print(account.account_number, account.account_type, account.balance)
end
```

---

## Integration Examples

### Check balance before purchase

```lua
-- In your shop script (server-side)
local balance = exports['pulsar-banking']:GetAccountBalance(citizenid)
if balance >= price then
    -- Process purchase
end
```

### Display all player accounts

```lua
-- Server-side
local accounts = exports['pulsar-banking']:GetPlayerAccounts(citizenid)
for _, acc in ipairs(accounts) do
    print(string.format('[%s] %s - $%s', acc.account_type, acc.account_number, acc.balance))
end
```
