# ATMs Configuration

Configuration file: `config/atms.lua`

---

## Overview

ATMs are automatically detected in the game world based on prop models. You can also add custom ATM locations manually.

---

## ATM Models

The following GTA props are recognized as ATMs:

```lua
Config.ATMModels = {
    `prop_atm_01`,
    `prop_atm_02`,
    `prop_atm_03`,
    `prop_fleeca_atm`,
}
```

> These cover all default ATM models in the GTA map. If you add custom ATM props via MLO, add their model name here.

---

## ATM Settings

| Option | Default | Description |
|--------|---------|-------------|
| `Config.ATMFee` | `$2.00` | Fee per ATM transaction |
| `Config.ATMDailyLimit` | `$50,000` | Max daily ATM withdrawals |

Additional ATM limits from `config/config.lua`:

| Option | Default |
|--------|---------|
| `ATMMaxWithdraw` | `$25,000` per transaction |
| `ATMMaxDeposit` | `$50,000` per transaction |
| `ATMDailyWithdrawLimit` | `$50,000` |
| `ATMDailyDepositLimit` | `$100,000` |

---

## Custom ATM Locations

Add coordinates to place ATMs at custom positions:

```lua
Config.CustomATMLocations = {
    vector3(100.0, 200.0, 30.0),
    vector3(300.0, 400.0, 25.0),
}
```

> Custom locations use the default ATM interaction without requiring an actual prop model to be present.

---

## ATM Blips

By default, ATM blips are **disabled** on the map:

```lua
-- In config/config.lua
Config.ShowATMBlips = false
```

Set to `true` to show ATM locations on the minimap.

---

## ATM Interaction

| Option | Value | File |
|--------|-------|------|
| Interact distance | `1.5` | `config/config.lua` |
| Draw distance | `10.0` | `config/config.lua` |
| Use target | `true` | `config/config.lua` |
| Available 24/7 | Yes | Even when bank hours are enabled |
