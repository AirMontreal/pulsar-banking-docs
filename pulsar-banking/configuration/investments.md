# Configuration des Investissements & du Marché

Fichier de configuration : `config/investments.lua`

---

## Présentation

Pulsar Banking inclut un marché d'investissement complet avec des cours d'actions et de cryptomonnaies en temps réel. Les joueurs peuvent acheter, vendre et conserver des actifs dans leur portefeuille.

---

## Paramètres du Marché

| Option | Par défaut | Description |
|--------|-----------|-------------|
| UpdateInterval | 5 min | Fréquence de mise à jour des prix |
| TradingFee | 0.5% | Frais par transaction |
| MaxPortfolioValue | $500,000 | Valeur maximale du portefeuille (anti-exploit) |
| MaxOrderQuantity | 1,000 | Quantité maximale par ordre |
| TrendChangeInterval | 30 min | Fréquence de changement des tendances |
| PriceHistoryRetention | 168 heures | 7 jours d'historique |
| MinPrice | $0.01 | Prix minimum d'un actif |
| MaxPrice | $999,999.99 | Prix maximum d'un actif |

---

## Prix des Cryptomonnaies (CoinGecko)

Prix des cryptomonnaies en temps réel récupérés depuis l'**API CoinGecko** (gratuit, sans clé API).

| Actif en jeu | Actif réel | ID CoinGecko |
|-------------|-----------|-------------|
| BTC | Bitcoin | bitcoin |
| ETH | Ethereum | ethereum |
| Gold | PAX Gold | pax-gold |

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

## Prix des Actions (Yahoo Finance)

Prix des actions en temps réel récupérés depuis **Yahoo Finance** (gratuit, sans clé API).

| Actif en jeu | Action réelle | Symbole |
|-------------|--------------|---------|
| Los Santos Customs | AutoZone | AZO |
| Maze Bank Corp | JPMorgan Chase | JPM |
| Merryweather Security | Lockheed Martin | LMT |
| LifeInvader | Meta Platforms | META |
| Pacific Standard | Goldman Sachs | GS |
| Fleeca Holdings | Bank of America | BAC |
| Crude Oil | WTI Crude Futures | CL=F |

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
    PriceScale = 1,       -- Diviser le prix réel par cette valeur (1 = 1:1)
    FetchInterval = 5,    -- minutes
}
```

### Mise à l'Échelle des Prix

Si les prix réels des actions sont trop élevés pour votre économie, augmentez PriceScale :

| PriceScale | META ($600 réel) | Prix en jeu |
|-----------|----------------|------------|
| 1 | $600 | $600 |
| 10 | $600 | $60 |
| 100 | $600 | $6 |

---

## Dépôts à Terme

Épargne à durée fixe avec des taux d'intérêt garantis.

| Durée | Taux d'intérêt |
|-------|---------------|
| 7 jours | 0.1% |
| 14 jours | 0.3% |
| 30 jours | 0.5% |
| 90 jours | 1.0% |

| Option | Par défaut | Description |
|--------|-----------|-------------|
| earlyWithdrawalPenalty | 50% | Pénalité pour retrait anticipé |
| maxActiveDeposits | 3 | Nombre maximum de dépôts actifs par joueur |
| minAmount | $1,000 | Dépôt minimum |
| maxAmount | $500,000 | Dépôt maximum |

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

## Ajouter des Actifs Personnalisés

### Ajouter une Cryptomonnaie

1. Trouvez l'ID CoinGecko sur [coingecko.com](https://www.coingecko.com)
2. Ajoutez-le à `Config.Market.RealPrices.Assets` :
   ```lua
   sol = 'solana',
   ```

### Ajouter une Action

1. Trouvez le symbole Yahoo Finance correspondant
2. Ajoutez-le à `Config.Market.StockPrices.Assets` :
   ```lua
   my_stock = 'AAPL',   -- Apple Inc.
   ```

### Désactiver les Prix Réels

Définissez Enabled = false pour utiliser des prix simulés au lieu des données de marché réelles :

```lua
Config.Market.RealPrices.Enabled = false
Config.Market.StockPrices.Enabled = false
```
