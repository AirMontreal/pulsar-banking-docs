# Événements

Liste de tous les événements pour les développeurs souhaitant s'intégrer à Pulsar Banking.

---

## Événements Serveur

### Comptes

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:accounts:create` | Créer un nouveau compte |
| `pulsar-banking:server:accounts:updateIcon` | Mettre à jour l'icône du compte |
| `pulsar-banking:server:accounts:changePIN` | Changer le code PIN du compte |
| `pulsar-banking:server:accounts:close` | Fermer un compte |
| `pulsar-banking:server:accounts:addMember` | Ajouter un membre à un compte joint/org. |
| `pulsar-banking:server:accounts:removeMember` | Retirer un membre d'un compte |
| `pulsar-banking:server:accounts:paySalary` | Payer un salaire à un membre |
| `pulsar-banking:server:accounts:payAllSalaries` | Payer tous les salaires des membres |
| `pulsar-banking:server:accounts:printCertificate` | Imprimer un certificat de compte |

### Transactions

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:transactions:deposit` | Déposer de l'argent (callback) |
| `pulsar-banking:server:transactions:withdraw` | Retirer de l'argent (callback) |
| `pulsar-banking:server:transactions:transfer` | Virement entre comptes (callback) |
| `pulsar-banking:server:transactions:getHistory` | Obtenir l'historique des transactions (callback) |

### Cartes

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:cards:request` | Demander une nouvelle carte |
| `pulsar-banking:server:cards:activate` | Activer une carte |
| `pulsar-banking:server:cards:updateStatus` | Bloquer/débloquer une carte |
| `pulsar-banking:server:cards:changePIN` | Changer le code PIN d'une carte |
| `pulsar-banking:server:cards:delete` | Supprimer une carte |
| `pulsar-banking:server:cards:rerequest` | Demander une carte de remplacement |
| `pulsar-banking:server:cards:verifyAndUse` | Vérifier et utiliser une carte |

### Prêts

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:loans:apply` | Soumettre une demande de prêt |
| `pulsar-banking:server:loans:getAll` | Obtenir tous les prêts du joueur (callback) |
| `pulsar-banking:server:credit:getScore` | Obtenir le score de crédit (callback) |

### Investissements

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:investments:buy` | Acheter un actif |
| `pulsar-banking:server:investments:sell` | Vendre un actif |
| `pulsar-banking:server:investments:createDeposit` | Créer un dépôt à terme |
| `pulsar-banking:server:investments:withdrawDeposit` | Retirer un dépôt à terme |
| `pulsar-banking:server:investments:getAll` | Obtenir le portefeuille (callback) |
| `pulsar-banking:server:investments:getMarketData` | Obtenir les données du marché (callback) |

### Facturation / Factures

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:billing:create` | Créer une facture |
| `pulsar-banking:server:billing:pay` | Payer une facture |
| `pulsar-banking:server:billing:cancel` | Annuler une facture |
| `pulsar-banking:server:billing:getAll` | Obtenir toutes les factures (callback) |

### Objectifs

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:goals:create` | Créer un objectif d'épargne |
| `pulsar-banking:server:goals:contribute` | Contribuer à un objectif |
| `pulsar-banking:server:goals:cancel` | Annuler un objectif |

### Contrats

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:contracts:create` | Créer un contrat de travail |
| `pulsar-banking:server:contracts:sign` | Signer un contrat |
| `pulsar-banking:server:contracts:terminate` | Résilier un contrat |
| `pulsar-banking:server:contracts:delete` | Supprimer un contrat |
| `pulsar-banking:server:contracts:print` | Imprimer un contrat |

### Règles Automatiques

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:autorules:create` | Créer une règle automatique |
| `pulsar-banking:server:autorules:toggle` | Activer/désactiver une règle automatique |
| `pulsar-banking:server:autorules:delete` | Supprimer une règle automatique |

### Contacts

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:contacts:add` | Sauvegarder un contact |
| `pulsar-banking:server:contacts:delete` | Supprimer un contact |
| `pulsar-banking:server:contacts:update` | Mettre à jour le nom d'un contact |

### Administration

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:admin:approveLoan` | Approuver un prêt en attente |
| `pulsar-banking:server:admin:denyLoan` | Refuser une demande de prêt |
| `pulsar-banking:server:admin:freezeAccount` | Geler/dégeler un compte |

### Notifications

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:server:notifications:markRead` | Marquer une notification comme lue |
| `pulsar-banking:server:notifications:markAllRead` | Marquer toutes les notifications comme lues |

---

## Événements Client

| Événement | Description |
|-----------|-------------|
| `pulsar-banking:client:useCard` | Déclenché lorsqu'un objet carte est utilisé depuis l'inventaire |
| `pulsar-banking:client:useContract` | Déclenché lorsqu'un objet contrat est utilisé |
| `pulsar-banking:client:useCertificate` | Déclenché lorsqu'un objet certificat est utilisé |
| `pulsar-banking:client:notify` | Afficher une notification côté client |
| `pulsar-banking:client:accounts:refresh` | Actualiser les données de compte dans l'interface |
| `pulsar-banking:client:balance:update` | Mettre à jour l'affichage du solde |
| `pulsar-banking:client:billing:refresh` | Actualiser l'interface de facturation |
| `pulsar-banking:client:atmClose` | Fermer le DAB et arrêter l'animation |

---

## Événement de Braquage

Lorsque l'intégration de braquage est activée, cet événement est déclenché lors de retraits importants :

```lua
-- Déclenché lorsque les conditions sont remplies :
-- Amount >= Config.Gameplay.Robbery.TriggerAmount
-- Online police >= Config.Gameplay.Robbery.PoliceRequired
TriggerEvent('pulsar-banking:robbery:triggered', source, amount, bankId)
```

Écoutez cet événement dans votre script de braquage pour lancer un scénario de braquage de banque.
