# Investments & Market Configuration

Configuration file: `config/investments.lua`

---

## Overview

Pulsar Banking includes a full investment market with real-time stock and crypto prices. Players can buy, sell, and hold assets in their portfolio.

---

## Market Settings

| Option | Default | Description |
|--------|---------|-------------|
| `UpdateInterval` | `5 min` | Price update frequency |
| `TradingFee` | `0.5%` | Fee per trade |
| `MaxPortfolioValue` | `$500,000` | Max portfolio value (anti-exploit) |
| `MaxOrderQuantity` | `1,000` | Max units per order |
| `TrendChangeInterval` | `30 min` | How often trends shift |
| `PriceHistoryRetention` | `168 hours` | 7 days of history |
| `MinPrice` | `$0.01` | Minimum asset price |
| `MaxPrice` | `$999,999.99` | Maximum asset price |

---

## Crypto Prices (CoinGecko)

Real-time crypto prices fetched from the **CoinGecko API** (free, no API key).

| In-Game Asset | Real-World Asset | CoinGecko ID |
|---------------|-----------------|---------------|
| BTC | Bitcoin | `bitcoin` |
| ETH | Ethereum | `ethereum` |
| Gold | PAX Gold | `pax-gold` |

```lua
Config.Market.RealPrices = {
    Enabled = true,
    Assets = {
        btc  = 'bitcoin',
        eth  = 'ethereum',
        gold = 'pax-gold',
    },
    Currency = 'usd',
    FetchInterval = 5,  -- minutes
}
```

---

## Stock Prices (Yahoo Finance)

Real-time stock prices fetched from **Yahoo Finance** (free, no API key).

| In-Game Asset | Real-World Stock | Ticker |
|---------------|-----------------|--------|
| Los Santos Customs | AutoZone | `AZO` |
| Maze Bank Corp | JPMorgan Chase | `JPM` |
| Merryweather Security | Lockheed Martin | `LMT` |
| LifeInvader | Meta Platforms | `META` |
| Pacific Standard | Goldman Sachs | `GS` |
| Fleeca Holdings | Bank of America | `BAC` |
| Crude Oil | WTI Crude Futures | `CL=F` |

```lua
Config.Market.StockPrices = {
    Enabled = true,
    Assets = {
        lsc_stock     = 'AZO',
        maze_stock    = 'JPM',
        merryweather  = 'LMT',
        lifeinvader   = 'META',
        pacific_stock = 'GS',
        fleeca_stock  = 'BAC',
        oil           = 'CL=F',
    },
    PriceScale = 1,       -- Divide real price by this (1 = 1:1)
    FetchInterval = 5,    -- minutes
}
```

### Price Scaling

If real stock prices are too high for your economy, increase `PriceScale`:

| PriceScale | META ($600 real) | In-Game Price |
|------------|-----------------|---------------|
| 1 | $600 | $600 |
| 10 | $600 | $60 |
| 100 | $600 | $6 |

---

## Term Deposits

Fixed-term savings with guaranteed interest rates.

| Duration | Interest Rate |
|----------|---------------|
| 7 days | 0.1% |
| 14 days | 0.3% |
| 30 days | 0.5% |
| 90 days | 1.0% |

| Option | Default | Description |
|--------|---------|-------------|
| `earlyWithdrawalPenalty` | `50%` | Penalty for withdrawing early |
| `maxActiveDeposits` | `3` | Max active deposits per player |
| `minAmount` | `$1,000` | Minimum deposit |
| `maxAmount` | `$500,000` | Maximum deposit |

```lua
Config.TermDeposits = {
    options = {
        { days = 7,  interestRate = 0.001, label = '7 Days'  },
        { days = 14, interestRate = 0.003, label = '14 Days' },
        { days = 30, interestRate = 0.005, label = '30 Days' },
        { days = 90, interestRate = 0.01,  label = '90 Days' },
    },
    earlyWithdrawalPenalty = 0.50,
    maxActiveDeposits = 3,
    minAmount = 1000,
    maxAmount = 500000,
}
```

---

## Adding Custom Assets

### Add a Crypto Asset

1. Find the CoinGecko ID at [coingecko.com](https://www.coingecko.com)
2. Add it to `Config.Market.RealPrices.Assets`:
   ```lua
   sol = 'solana',
   ```

### Add a Stock Asset

1. Find the Yahoo Finance ticker symbol
2. Add it to `Config.Market.StockPrices.Assets`:
   ```lua
   my_stock = 'AAPL',   -- Apple Inc.
   ```

### Disabling Real Prices

Set `Enabled = false` to use simulated prices instead of real market data:

```lua
Config.Market.RealPrices.Enabled = false
Config.Market.StockPrices.Enabled = false
```
