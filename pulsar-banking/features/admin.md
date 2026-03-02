# Panneau d'Administration

---

## Présentation

Les administrateurs du serveur peuvent gérer les comptes des joueurs, geler les activités suspectes et surveiller les transactions via des commandes d'administration et la journalisation Discord.

---

## Accès Administrateur

L'accès administrateur est contrôlé par :

```lua
Config.AdminPermission = 'admin'      -- Niveau de permission du framework
Config.AdminLicenses = {
    'your_license_hash_here',          -- Hash de licence Rockstar
}
```

Les deux conditions sont vérifiées — vous avez besoin du niveau de permission **et** votre licence doit être sur liste blanche.

---

## Commandes Administrateur

Toutes les commandes ont un délai de recharge de 5 secondes pour éviter le spam.

### `/bankadmin`

Ouvre le panneau d'administration avec les fonctionnalités suivantes :

- **Rechercher des comptes** — Trouver des comptes par nom de joueur ou numéro de compte
- **Voir les détails du compte** — Solde, transactions, informations sur le propriétaire
- **Geler/Dégeler les comptes** — Bloquer toutes les transactions sur un compte
- **Voir l'historique des transactions** — Piste d'audit complète
- **Gérer les prêts** — Consulter et modifier les prêts actifs

---

## Gel de Compte

### Gel Manuel
Les administrateurs (et les responsables bancaires de grade 2+) peuvent geler manuellement des comptes.

### Gel Automatique
Lorsqu'il est activé, les comptes sont automatiquement gelés si :
- Le montant de la transaction dépasse $100,000 **ET**
- Le score de crédit du joueur est inférieur à 350

```lua
Config.Security.AutoFreezeEnabled = true
Config.Security.AutoFreezeThreshold = 100000
Config.Security.AutoFreezeCreditScore = 350
```

### Comportement d'un Compte Gelé
- Toutes les transactions sont bloquées (dépôt, retrait, virement)
- Le joueur voit un message "gelé" lorsqu'il essaie d'utiliser le compte
- Seuls les administrateurs/gestionnaires peuvent dégeler

---

## Journal d'Audit

Toutes les actions administratives sont enregistrées dans la table de base de données `pulsar_audit_log` :

- Qui a effectué l'action
- Quelle action a été réalisée
- Quand cela s'est produit
- Compte/joueur ciblé

Les journaux sont automatiquement supprimés après 30 jours (configurable via `Config.Cleanup.AuditLogDays`).

---

## Webhooks Discord

Configurez la journalisation Discord pour des alertes en temps réel :

```lua
Config.Notifications.DiscordWebhook = 'https://discord.com/api/webhooks/...'
```

### Événements Enregistrés

| Événement | Par défaut |
|-----------|-----------|
| Transactions importantes (> $50,000) | Activé |
| Demandes de prêt | Activé |
| Création de compte | Activé |
| Fermeture de compte | Activé |
| Activité suspecte | Activé |
| Actions administratives | Activé |

### Personnalisation du Webhook

```lua
Config.Notifications.DiscordBotName = 'Pulsar Banking'
Config.Notifications.DiscordAvatarUrl = ''  -- URL d'avatar personnalisé
Config.Notifications.DiscordColor = 16750848  -- Couleur de l'embed (décimal)
```

---

## Permissions des Employés de Banque

Les employés de banque avec le bon grade peuvent également effectuer des tâches similaires à celles d'un administrateur :

| Action | Grade requis |
|--------|-------------|
| Approuver les prêts | Associate (1+) |
| Geler les comptes | Manager (2+) |
| Voir tous les comptes | Associate (1+) |
| Générer des rapports | Manager (2+) |

Voir [Configuration des Emplois](../configuration/jobs.md) pour plus de détails.
