# Configuration de la Facturation & des Factures

Fichier de configuration : `config/billing.lua`

---

## Présentation

Le système de facturation permet aux joueurs de créer, envoyer et gérer des factures. Il fonctionne de manière autonome (touche F5) et n'est pas lié à un emplacement bancaire spécifique.

---

## Paramètres

| Option | Par défaut | Description |
|--------|-----------|-------------|
| Enabled | true | Activer/désactiver le système de facturation |
| OpenKey | F5 | Touche pour ouvrir le panneau de facturation |
| DefaultTaxRate | 0% | Taxe par défaut appliquée aux nouvelles factures |
| MaxLineItems | 10 | Nombre maximum de lignes par facture |
| DueDays | 7 | Jours par défaut avant l'échéance d'une facture |
| MaxPendingInvoices | 10 | Nombre maximum de factures impayées par destinataire |
| AutoOverdue | true | Marquer automatiquement les factures comme en souffrance après la date d'échéance |
| OverdueCheckInterval | 30 min | Fréquence de vérification des factures en souffrance |

---

## Restrictions par Emploi

Par défaut, **tous les emplois** peuvent envoyer des factures. Pour restreindre :

```lua
-- Seuls ces emplois peuvent créer des factures :
AllowedJobs = { 'police', 'ambulance', 'mechanic', 'realestate' },

-- Tous les emplois peuvent facturer (par défaut) :
AllowedJobs = {},
```

---

## Impact sur le Score de Crédit

Les factures affectent le score de crédit du joueur :

| Événement | Impact |
|-----------|--------|
| Facture payée à temps | **+5** (max +50 au total) |
| Facture payée en retard | **+2** |
| Facture en souffrance/impayée | **-15** (max -75 au total) |

Ces valeurs sont configurées dans `config/loans.lua` sous `Config.CreditScore`.

---

## Configuration Complète

```lua
Config.Billing = {
    Enabled = true,
    OpenKey = 'F5',
    DefaultTaxRate = 0,
    MaxLineItems = 10,
    DueDays = 7,
    AllowedJobs = {},
    MaxPendingInvoices = 10,
    AutoOverdue = true,
    OverdueCheckInterval = 30,
}
```
