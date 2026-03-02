# Configuration des Prêts & du Score de Crédit

Fichier de configuration : `config/loans.lua`

---

## Types de Prêts

### Prêt Personnel

| Option | Valeur |
|--------|--------|
| Montant minimum | $1,000 |
| Montant maximum | $100,000 |
| Durée minimum | 7 jours |
| Durée maximum | 90 jours |
| Score de crédit minimum | 400 |
| Score d'approbation automatique | 700+ |
| Prêts actifs maximum | 2 |

### Prêt Professionnel

| Option | Valeur |
|--------|--------|
| Montant minimum | $1,000 |
| Montant maximum | $250,000 |
| Durée minimum | 14 jours |
| Durée maximum | 180 jours |
| Score de crédit minimum | 550 |
| Score d'approbation automatique | 700+ |
| Prêts actifs maximum | 1 |

**Conditions du prêt professionnel :**

```lua
Config.BusinessLoan = {
    requireJob = true,
    blacklistedJobs = { 'unemployed' },
}
```

---

## Système de Score de Crédit

| Option | Par défaut | Description |
|--------|-----------|-------------|
| defaultScore | 500 | Score de départ pour les nouveaux joueurs |
| minScore | 300 | Score minimum possible |
| maxScore | 850 | Score maximum possible |

### Variations du Score

| Événement | Impact |
|-----------|--------|
| Prêt remboursé à temps | **+30** |
| Défaut de paiement | **-150** |
| Paiement en retard | **-25** |
| Ancienneté du compte (par cycle) | **+5** (max +50) |
| Facture payée à temps | **+5** (max +50) |
| Facture payée en retard | **+2** |
| Facture en souffrance | **-15** (max -75) |

---

## Pénalités de Prêt

| Option | Par défaut | Description |
|--------|-----------|-------------|
| gracePeriodHours | 24 | Heures de grâce après la date d'échéance avant pénalités |
| penaltyRate | 2% | Taux supplémentaire appliqué en cas de retard |
| maxOverdueBeforeDefault | 5 | Paiements manqués avant la mise en défaut du prêt |

---

## Processus d'Approbation des Prêts

1. Le joueur soumet une demande de prêt dans une banque
2. Si le score de crédit est >= autoApproveMinScore (700) : **approbation automatique**
3. Si le score de crédit est inférieur au seuil d'approbation automatique : **approbation manuelle par un banquier**
4. Les banquiers du grade suffisant peuvent approuver/refuser (voir [Jobs](jobs.md))

---

## Personnaliser les Types de Prêts

```lua
Config.Loans = {
    personal = {
        name = 'Personal Loan',
        minAmount = 1000,
        maxAmount = 100000,
        minTermDays = 7,
        maxTermDays = 90,
        minCreditScore = 400,
        autoApproveMinScore = 700,
        maxActiveLoans = 2,
    },
}
```
