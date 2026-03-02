# Exports & API

Exports côté serveur pour intégrer Pulsar Banking avec d'autres ressources.

---

## Exports Serveur

### GetAccountBalance

Retourne le solde total des comptes d'un joueur.

```lua
local balance = exports['pulsar-banking']:GetAccountBalance(citizenid, accountType)
```

| Paramètre | Type | Requis | Description |
|-----------|------|--------|-------------|
| `citizenid` | string | Oui | Identifiant citoyen du joueur |
| `accountType` | string | Non | Type de compte (`'checking'`, `'savings'`). Par défaut `'checking'` |

**Retourne :** `number` — Solde total

**Exemple :**
```lua
-- Obtenir le solde courant d'un joueur
local balance = exports['pulsar-banking']:GetAccountBalance('ABC12345')
print('Solde : $' .. balance)

-- Obtenir le solde épargne
local savings = exports['pulsar-banking']:GetAccountBalance('ABC12345', 'savings')
```

---

### GetPlayerAccounts

Retourne tous les comptes appartenant à un joueur.

```lua
local accounts = exports['pulsar-banking']:GetPlayerAccounts(citizenid)
```

| Paramètre | Type | Requis | Description |
|-----------|------|--------|-------------|
| `citizenid` | string | Oui | Identifiant citoyen du joueur |

**Retourne :** `table` — Tableau d'objets compte

**Exemple :**
```lua
local accounts = exports['pulsar-banking']:GetPlayerAccounts('ABC12345')
for _, account in ipairs(accounts) do
    print(account.account_number, account.account_type, account.balance)
end
```

---

## Exemples d'Intégration

### Vérifier le solde avant un achat

```lua
-- Dans votre script de boutique (côté serveur)
local balance = exports['pulsar-banking']:GetAccountBalance(citizenid)
if balance >= price then
    -- Traiter l'achat
end
```

### Afficher tous les comptes d'un joueur

```lua
-- Côté serveur
local accounts = exports['pulsar-banking']:GetPlayerAccounts(citizenid)
for _, acc in ipairs(accounts) do
    print(string.format('[%s] %s - $%s', acc.account_type, acc.account_number, acc.balance))
end
```
