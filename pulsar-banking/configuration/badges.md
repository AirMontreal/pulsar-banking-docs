# Configuration des Badges

Fichier de configuration : `config/badges.lua`

---

## Présentation

Les badges sont des succès que les joueurs obtiennent en utilisant les fonctionnalités bancaires. Ils servent de jalons et encouragent l'exploration des fonctionnalités.

---

## Liste des Badges

### Les Essentiels

| Badge | Description |
|-------|-------------|
| First Deposit | Effectuez votre premier dépôt |
| First Transfer | Complétez votre premier virement |
| First Withdrawal | Effectuez votre premier retrait |

### Épargne

| Badge | Description |
|-------|-------------|
| Bronze Saver | Économisez $1,000 au total sur tous vos comptes |
| Silver Saver | Économisez $10,000 au total sur tous vos comptes |
| Gold Saver | Économisez $100,000 au total sur tous vos comptes |
| Millionaire | Avoir un solde total supérieur à $1,000,000 |

### Investissements

| Badge | Description |
|-------|-------------|
| Rookie Investor | Effectuez votre première transaction sur le marché |
| Pro Investor | Complétez 10 transactions sur le marché |
| Market Whale | Complétez 100 transactions sur le marché |

### Prêts

| Badge | Description |
|-------|-------------|
| Perfect Credit | Atteignez un score de crédit supérieur à 800 |
| Loan Master | Remboursez 5 prêts sans retard |
| Early Bird | Remboursez un prêt avant la fin de son terme |

### Autres

| Badge | Description |
|-------|-------------|
| Diversified | Posséder 3 types de comptes différents ou plus |
| Goal Achiever | Atteindre un objectif d'épargne |
| Smart Money | Configurer votre première règle automatique |

---

## Catégories de Badges

| Catégorie | Badges |
|-----------|--------|
| basics | First Deposit, First Transfer, First Withdrawal |
| savings | Bronze/Silver/Gold Saver, Millionaire |
| investments | Rookie/Pro Investor, Market Whale |
| loans | Perfect Credit, Loan Master, Early Bird |
| accounts | Diversified |
| goals | Goal Achiever |
| smart | Smart Money |

---

## Ajouter un Badge Personnalisé

```lua
Config.Badges = {
    ['my_badge'] = {
        name = 'My Badge',
        description = 'Description de la condition pour l\'obtenir',
        icon = 'my_icon',       -- Identifiant de l'icône utilisé dans le NUI
        category = 'basics',    -- Catégorie pour le regroupement
    },
}
```

> **Remarque :** Les badges personnalisés nécessitent une logique côté serveur pour les déclencher. La définition du badge dans la configuration ne définit que l'affichage — la logique d'attribution se trouve dans le code serveur.
