# FAQ & Troubleshooting

---

## Installation Issues

### The script doesn't start

**Check your dependencies are running:**
```
ensure oxmysql
ensure ox_lib
ensure ox_inventory  -- or qb-inventory
ensure pulsar-banking  -- MUST be after dependencies
```

### SQL errors on startup

Make sure you imported `sql/install.sql` into your database. The script requires all 21 tables to be present.

### Inventory items not showing

- **ox_inventory:** Copy items from `install/ox_inventory_items.lua` into `ox_inventory/data/items.lua`
- **qb-inventory:** Copy items from `install/qb_inventory_items.lua` into `qb-core/shared/items.lua`
- Copy card images from `install/ox_inventory_images/` to your inventory's image folder

---

## Configuration Issues

### Framework not detected

Set it manually in `config/config.lua`:
```lua
Config.Framework = 'qbcore'  -- or 'esx'
```

### Target system not working

```lua
Config.UseTarget = true
Config.TargetSystem = 'ox_target'  -- or 'qb-target'
```

If you don't use a target system, set `Config.UseTarget = false` to use marker-based interaction.

### Interest not being paid

Check these settings:
- `Config.Interest.SavingsRate` — Must be greater than 0
- `Config.Interest.MinBalanceForInterest` — Account must have at least this balance
- `Config.InterestCycleMinutes` — How often interest is calculated (default: 60 min)

### ATMs not working

- Verify ATM models are correct in `config/atms.lua`
- Check `Config.ATMInteractDistance` (default: 1.5)
- If using custom MLO ATMs, add their prop model to `Config.ATMModels`

---

## Gameplay Issues

### Player can't create an account

Possible reasons:
- Reached max accounts (`Config.MaxAccountsPerPlayer = 5`)
- Reached max for that type (e.g., 2 checking accounts)
- Account opening fee not affordable

### Player can't transfer money

Possible reasons:
- Daily transfer limit reached ($100,000)
- Transfer cooldown active (15 seconds)
- Account is frozen
- Insufficient balance
- Rate limit exceeded (60 transactions/hour)

### Player can't get a loan

Possible reasons:
- Credit score too low (min 400 for personal, 550 for business)
- Already has max active loans
- Business loan requires a job
- No banker online to approve (if score < 700)

### Player can't order a credit card

- Credit score must be at least 600
- Bank must offer the `cards` service (check `config/banks.lua`)

### Account is frozen

An account can be frozen by:
- Admin action
- Bank manager (grade 2+)
- Auto-freeze (large transaction + low credit score)

Only admins or bank managers can unfreeze accounts.

---

## Performance

### Server lag when interest is calculated

- Lower `Config.Interest.MaxInterestPayout` to reduce calculations
- Increase `Config.InterestCycleMinutes` to run less frequently

### Market prices not updating

- Check your server can reach external APIs (CoinGecko, Yahoo Finance)
- Ensure `Config.Market.RealPrices.Enabled = true`
- Check server console for API errors

---

## Common Errors

### `SCRIPT ERROR: attempt to index a nil value`

Usually means a config value is missing. Make sure you have all config files present and up to date.

### `No such export`

Make sure `ox_lib` and `oxmysql` are started before `pulsar-banking` in your `server.cfg`.

### UI not opening

- Check the browser console (F8 in-game) for JavaScript errors
- Verify `build/` folder contains `index.html` and `assets/` files
- Ensure no other resource is conflicting on the same NUI focus

---

## Support

If your issue isn't listed here:

1. Enable debug mode: `Config.Debug = true`
2. Check server console for error messages
3. Check client console (F8) for client-side errors
4. Open a support ticket on our Discord server
