# Transactions

---

## Types de Transactions

| Type | Description |
|------|-------------|
| **Deposit** | Ajouter de l'argent liquide sur votre compte |
| **Withdrawal** | Retirer de l'argent liquide de votre compte |
| **Transfer** | Envoyer de l'argent vers un autre compte |
| **Wire Transfer** | Virement vers une autre banque (frais plus élevés) |
| **Loan Payment** | Remboursement de prêt automatique ou manuel |
| **Interest** | Intérêts gagnés sur l'épargne |
| **Fee** | Frais de tenue de compte, frais de DAB, etc. |
| **Invoice** | Paiement reçu ou envoyé via la facturation |

---

## Dépôts

- Disponibles aux guichets de banque et aux DAB
- Limite de dépôt au DAB : $50,000 par transaction
- Limite journalière de dépôt au DAB : $100,000
- Aucun frais de dépôt par défaut

---

## Retraits

- Disponibles aux guichets de banque et aux DAB
- Limite de retrait au DAB : $25,000 par transaction
- Limite journalière de retrait au DAB : $50,000
- Limite journalière au guichet : $50,000

---

## Virements

- Virement entre vos propres comptes ou vers d'autres joueurs
- Recherche par numéro de compte ou nom de joueur
- Montants rapides : $100, $500, $1K, $5K, $10K, $50K
- Délai de 15 secondes entre les virements
- Limite journalière de virement : $100,000
- Confirmation requise pour les virements supérieurs à $50,000

### Contacts Sauvegardés

Sauvegardez les destinataires fréquents pour des virements rapides. Jusqu'à 20 contacts sauvegardés.

---

## Historique des Transactions

- Historique complet accessible dans l'interface bancaire
- Filtrage par type, date et montant
- Recherche de transactions par description
- Catégorisation automatique (dépôt, virement, frais, etc.)

---

## Délais de Recharge

| Action | Délai |
|--------|-------|
| Virement | 15 secondes |
| Retrait | 10 secondes |
| Dépôt | 10 secondes |

---

## Limites de Débit

- Maximum **60 transactions par heure** par joueur
- Configurable dans `Config.Security.MaxTransactionsPerHour`

---

## Notifications

Les joueurs reçoivent des notifications en jeu pour :

- Dépôts reçus
- Retraits effectués
- Virements entrants
- Intérêts gagnés
- Paiements de prêt à venir
- Frais prélevés
- Avertissements de solde bas (en dessous de $500)
