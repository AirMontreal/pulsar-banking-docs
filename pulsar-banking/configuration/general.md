# Paramètres Généraux

Fichier de configuration principal : `config/config.lua`

---

## Framework & Système

| Option | Par défaut | Description |
|--------|-----------|-------------|
| Config.Framework | qbcore | Définissez votre framework : qbcore ou esx (doit être défini manuellement) |
| Config.Debug | false | Active les messages de débogage dans la console |
| Config.Locale | en | Langue : en, fr, es, de, it, pt, nl, tr |
| Config.Currency | $ | Symbole de devise |
| Config.CurrencyFormat | en-US | Locale de formatage des nombres |
| Config.UseTarget | true | Utiliser le système de cible ou afficher des marqueurs |
| Config.TargetSystem | auto | Détecté automatiquement, ou forcer : ox\_target / qb-target |
| Config.InventorySystem | auto | Détecté automatiquement, ou forcer : ox\_inventory / qb-inventory |

---

## Paramètres de Compte

| Option | Par défaut | Description |
|--------|-----------|-------------|
| Config.DefaultPIN | 0000 | Code PIN par défaut pour les nouveaux comptes |
| Config.MaxAccountsPerPlayer | 5 | Nombre maximum total de comptes par joueur |
| Config.MaxPersonalAccounts | 2 | Nombre maximum de comptes courants/épargne |
| Config.MaxBusinessAccounts | 2 | Nombre maximum de comptes d'organisation |
| Config.MaxJointAccounts | 2 | Nombre maximum de comptes joints |
| Config.AccountNumberPrefix | PB | Préfixe pour les numéros de compte |

---

## Limites

| Option | Par défaut | Description |
|--------|-----------|-------------|
| DailyWithdrawLimit | $50,000 | Retraits journaliers maximum |
| DailyTransferLimit | $100,000 | Virements journaliers maximum |
| LargeTransactionThreshold | $50,000 | Seuil pour les alertes de transactions importantes |
| LowBalanceThreshold | $500 | Niveau d'avertissement de solde bas |

---

## Limites de Compte (Étendu)

```lua
Config.AccountLimits = {
    MaxCheckingBalance = 0,        -- 0 = illimité
    MaxSavingsBalance = 0,
    MaxOrganizationBalance = 0,
    MinCheckingBalance = 0,
    MinSavingsBalance = 0,
    ATMMaxWithdraw = 25000,        -- Par transaction au DAB
    ATMMaxDeposit = 50000,
    ATMDailyWithdrawLimit = 50000,
    ATMDailyDepositLimit = 100000,
    MaxTransferAmount = 500000,    -- Par virement
    MinTransferAmount = 1,
    OverdraftEnabled = false,      -- Autoriser un solde négatif
    OverdraftLimit = 5000,
    OverdraftInterestRate = 0.05,  -- 5%
    OverdraftFee = 35,             -- Frais fixe
}
```

---

## Frais & Commissions

| Frais | Par défaut | Description |
|-------|-----------|-------------|
| TransferFee | 0% | Frais en pourcentage sur les virements |
| TransferFlatFee | $0 | Frais fixe ajouté aux virements |
| ATMWithdrawFee | $0 | Par retrait au DAB |
| ATMDepositFee | $0 | Par dépôt au DAB |
| MonthlyMaintenanceFee | $0 | Prélevé à chaque cycle d'intérêts |
| OpenAccountFee | $0 | Frais d'ouverture de compte |
| CloseAccountFee | $0 | Frais de fermeture de compte |
| WireTransferFee | $250 | Virements interbancaires |
| ExchangeFee | 2% | Change de devises (futur) |

---

## Taux d'Intérêt

| Option | Par défaut | Description |
|--------|-----------|-------------|
| SavingsRate | 0.5% | Intérêts par cycle pour l'épargne |
| CheckingRate | 0% | Intérêts par cycle pour le courant |
| CompoundInterest | true | Intérêts composés ou simples |
| MinBalanceForInterest | $100 | Solde minimum pour percevoir des intérêts |
| MaxInterestPayout | $10,000 | Versement maximum par cycle (anti-exploit) |
| HighBalanceThreshold | $500,000 | Seuil pour le taux bonifié |
| HighBalanceBonusRate | 0.1% | Taux bonus pour les soldes élevés |
| WealthTaxThreshold | $5,000,000 | Seuil pour la taxe sur la fortune |
| WealthTaxRate | 0% | Taux de taxe sur la fortune (désactivé) |

> **Cycle d'intérêts :** S'exécute toutes les `Config.InterestCycleMinutes` (par défaut : 60 minutes).

---

## Sécurité

| Option | Par défaut | Description |
|--------|-----------|-------------|
| MaxPINAttempts | 5 | Tentatives avant le verrouillage |
| PINLockoutMinutes | 15 | Durée du verrouillage |
| TransferCooldownSeconds | 15 | Délai entre les virements |
| WithdrawCooldownSeconds | 10 | Délai entre les retraits |
| DepositCooldownSeconds | 10 | Délai entre les dépôts |
| MaxTransactionsPerHour | 60 | Limite de débit par joueur |
| AutoFreezeEnabled | true | Gel automatique des comptes suspects |
| AutoFreezeThreshold | $100,000 | Montant déclenchant une vérification |
| AutoFreezeCreditScore | 350 | Seuil de score de crédit pour le gel automatique |
| LargeTransferConfirmation | true | Confirmation pour les virements importants |
| LargeTransferThreshold | $50,000 | Seuil de confirmation |

---

## Entreprise / Organisations

| Option | Par défaut | Description |
|--------|-----------|-------------|
| MaxMembers | 50 | Membres maximum par organisation |
| MaxOrgsPerPlayer | 3 | Organisations maximum par joueur (en tant que propriétaire) |
| MinBalanceToCreate | $0 | Solde minimum pour créer une organisation |
| CreationFee | $0 | Frais de création d'une organisation |
| AutoPayroll | false | Versements de salaires automatiques |
| BusinessTaxRate | 0% | Taxe sur les revenus de l'organisation |
| AllowOrgToPersonalTransfer | true | Autoriser les virements org. vers personnel |
| OrgToPersonalDailyLimit | $100,000 | Limite journalière org. vers personnel |

### Permissions par Rôle

| Permission | Propriétaire | Gestionnaire | Employé |
|------------|-------------|-------------|---------|
| Retrait | Oui | Oui | Non |
| Dépôt | Oui | Oui | Oui |
| Virement | Oui | Oui | Non |
| Gérer les membres | Oui | Oui | Non |
| Voir les journaux | Oui | Oui | Non |
| Paramètres | Oui | Non | Non |
| Factures | Oui | Oui | Oui |
| Fermer le compte | Oui | Non | Non |

---

## Gameplay

### Horaires Bancaires
```lua
BankHours = {
    Enabled = false,    -- Mettre true pour restreindre les horaires
    OpenHour = 8,       -- 8h00
    CloseHour = 22,     -- 22h00
}
```
> Les DAB restent disponibles 24h/24 même lorsque les horaires bancaires sont activés.

### Intégration Braquage
```lua
Robbery = {
    Enabled = false,
    TriggerAmount = 100000,
    EventName = 'pulsar-banking:robbery:triggered',
    CooldownMinutes = 60,
    PoliceRequired = 2,
}
```

### Pénalité de Mort
```lua
DeathPenalty = {
    Enabled = false,
    Percentage = 0.00,
    FlatAmount = 0,
    MaxLoss = 0,
    DeductFromBank = false,
}
```

### Système d'Aides Sociales
```lua
Welfare = {
    Enabled = false,
    Amount = 500,
    IntervalMinutes = 60,
    RequiredJob = 'unemployed',
    MaxBalance = 10000,
}
```

---

## Notifications & Discord

| Option | Par défaut | Description |
|--------|-----------|-------------|
| DiscordWebhook | vide | URL du webhook Discord (vide = désactivé) |
| DiscordBotName | Pulsar Banking | Nom d'affichage du bot |
| DiscordColor | 16750848 | Couleur de l'embed (décimal) |

### Événements Enregistrés sur Discord

| Événement | Par défaut |
|-----------|-----------|
| Transactions importantes | Oui (au-dessus de $50,000) |
| Demandes de prêt | Oui |
| Création de compte | Oui |
| Fermeture de compte | Oui |
| Activité suspecte | Oui |
| Actions administratives | Oui |

---

## Qualité de Vie

| Option | Par défaut | Description |
|--------|-----------|-------------|
| EnableFavorites | true | Sauvegarder les destinataires fréquents |
| MaxFavorites | 20 | Nombre maximum de contacts sauvegardés |
| QuickAmounts | 100, 500, 1k, 5k, 10k, 50k | Montants rapides prédéfinis |
| EnableAccountNicknames | true | Renommer les comptes |
| EnableRoundUpSavings | true | Arrondi automatique vers l'épargne |
| EnableSounds | true | Effets sonores de l'interface |
| SoundVolume | 0.5 | Volume des sons (0-1) |
| EnableBalanceHUD | false | Affichage du solde sur le HUD |
| BalanceHUDKey | F6 | Touche pour basculer l'affichage HUD |

---

## Tâches Planifiées

| Option | Par défaut | Description |
|--------|-----------|-------------|
| InterestCycleMinutes | 60 | Intervalle de versement des intérêts |
| LoanCheckMinutes | 30 | Intervalle de vérification des paiements de prêt |

---

## Nettoyage des Données

| Option | Par défaut | Description |
|--------|-----------|-------------|
| AuditLogDays | 30 | Suppression des anciens journaux d'audit |
| NotificationDays | 14 | Suppression des anciennes notifications lues |
