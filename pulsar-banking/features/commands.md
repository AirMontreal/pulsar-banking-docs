# Commandes

---

## Commandes des Joueurs

| Commande | Description |
|----------|-------------|
| `/openbilling` | Ouvrir le panneau de facturation/factures |

> Le panneau de facturation peut également être ouvert avec la touche **F5** (configurable via `Config.Billing.OpenKey`).

---

## Commandes Administrateur

Toutes les commandes administrateur nécessitent `Config.AdminPermission` (`'admin'`) **et** que votre licence soit dans `Config.AdminLicenses`.

Les commandes administrateur ont un **délai de recharge de 5 secondes** entre les utilisations.

### /bankadmin

| Utilisation | Description |
|-------------|-------------|
| `/bankadmin give [citizenid] [amount]` | Déposer de l'argent sur le compte courant principal d'un joueur |
| `/bankadmin freeze [account_number]` | Geler un compte (bloque toutes les transactions) |
| `/bankadmin unfreeze [account_number]` | Dégeler un compte précédemment gelé |

**Exemples :**

```
/bankadmin give ABC12345 50000
/bankadmin freeze PB-1234567
/bankadmin unfreeze PB-1234567
```

> Toutes les actions administratives sont enregistrées dans le journal d'audit et éventuellement envoyées sur Discord via webhook.
