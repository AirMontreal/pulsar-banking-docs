# Installation

Step-by-step guide to install Pulsar Banking on your FiveM server.

---

## 1. Requirements

Make sure you have the following resources installed and running:

| Resource | Link |
|----------|------|
| **oxmysql** | [GitHub](https://github.com/overextended/oxmysql) |
| **ox_lib** | [GitHub](https://github.com/overextended/ox_lib) |
| **ox_inventory** or **qb-inventory** | Auto-detected |
| **ox_target** or **qb-target** | Auto-detected |
| **QBCore** or **ESX** | Set in config |

---

## 2. Database Setup

Import the SQL file into your database:

```sql
-- Using HeidiSQL, phpMyAdmin, or your preferred tool:
-- Import the file: sql/install.sql
```

This creates all 21 required tables (`pulsar_accounts`, `pulsar_transactions`, `pulsar_loans`, etc.).

> **Note:** If `Config.Debug = true` in your config, the script will also auto-check and create missing tables on startup.

---

## 3. Inventory Items

### ox_inventory

Copy the items from `install/ox_inventory_items.lua` into your `ox_inventory/data/items.lua`:

```lua
['debit_card'] = {
    label = 'Debit Card',
    weight = 0,
    stack = false,
    close = true,
    description = 'A bank debit card',
},
['credit_card'] = {
    label = 'Credit Card',
    weight = 0,
    stack = false,
    close = true,
    description = 'A bank credit card',
},
['enterprise_card'] = {
    label = 'Enterprise Card',
    weight = 0,
    stack = false,
    close = true,
    description = 'An enterprise bank card',
},
```

Then copy the card images from `install/ox_inventory_images/` into your `ox_inventory/web/images/` folder.

### qb-inventory

Copy the items from `install/qb_inventory_items.lua` into your `qb-core/shared/items.lua`.

---

## 4. Resource Placement

1. Place the `Pulsar-Banking` folder in your server's `resources/` directory
2. Rename it to `pulsar-banking` (lowercase, no spaces) if needed

---

## 5. Server Configuration

Add the following to your `server.cfg`:

```cfg
# Make sure dependencies start first
ensure oxmysql
ensure ox_lib
ensure ox_inventory  # or qb-inventory

# Start Pulsar Banking
ensure pulsar-banking
```

> **Important:** `pulsar-banking` must start **after** its dependencies.

---

## 6. Framework Configuration

Open `config/config.lua` and set your framework:

```lua
-- For QBCore servers:
Config.Framework = 'qbcore'

-- For ESX servers:
Config.Framework = 'esx'
```

The script will auto-detect your target system (`ox_target` / `qb-target`) and inventory system (`ox_inventory` / `qb-inventory`).

---

## 7. First Start

1. Start your server
2. Check the server console for any errors
3. Join the server and approach a bank or ATM
4. The banking UI should open when you interact

---

## 8. Post-Installation

After confirming the script works:

- Review all files in `config/` to customize settings to your server
- Set up [Discord Webhooks](configuration/general.md#notifications--discord) for logging
- Configure [bank locations](configuration/banks.md) if needed
- Set up the [banker job](configuration/jobs.md) for your players

---

## Updating

When updating to a new version:

1. Back up your current `config/` folder
2. Replace all files except your `config/` folder
3. Check the changelog for any new config options to add
4. Restart the resource

> **Never** delete or replace your `config/` files during an update — they contain your custom settings.
