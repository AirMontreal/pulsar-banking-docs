# Installation

Guide étape par étape pour installer Pulsar Banking sur votre serveur FiveM.

---

## 1. Prérequis

Assurez-vous que les ressources suivantes sont installées et en cours d'exécution :

| Ressource | Lien |
|-----------|------|
| **oxmysql** | [GitHub](https://github.com/overextended/oxmysql) |
| **ox_lib** | [GitHub](https://github.com/overextended/ox_lib) |
| **ox_inventory** ou **qb-inventory** | Auto-détecté |
| **ox_target** ou **qb-target** | Auto-détecté |
| **QBCore** ou **ESX** | Défini dans la config |

---

## 2. Base de données

Importez le fichier SQL dans votre base de données :

```sql
-- Via HeidiSQL, phpMyAdmin ou votre outil préféré :
-- Importez le fichier : sql/install.sql
```

Cela crée les 21 tables requises (`pulsar_accounts`, `pulsar_transactions`, `pulsar_loans`, etc.).

> **Note :** Si `Config.Debug = true` dans votre config, le script vérifiera et créera automatiquement les tables manquantes au démarrage.

---

## 3. Objets d'inventaire

### ox_inventory

Copiez les objets depuis `install/ox_inventory_items.lua` dans votre `ox_inventory/data/items.lua` :

```lua
['debit_card'] = {
    label = 'Carte de débit',
    weight = 0,
    stack = false,
    close = true,
    description = 'Une carte de débit bancaire',
},
['credit_card'] = {
    label = 'Carte de crédit',
    weight = 0,
    stack = false,
    close = true,
    description = 'Une carte de crédit bancaire',
},
['enterprise_card'] = {
    label = 'Carte entreprise',
    weight = 0,
    stack = false,
    close = true,
    description = 'Une carte bancaire entreprise',
},
```

Copiez ensuite les images depuis `install/ox_inventory_images/` vers votre dossier `ox_inventory/web/images/`.

### qb-inventory

Copiez les objets depuis `install/qb_inventory_items.lua` dans votre `qb-core/shared/items.lua`.

---

## 4. Placement de la ressource

1. Placez le dossier `Pulsar-Banking` dans le répertoire `resources/` de votre serveur
2. Renommez-le en `pulsar-banking` (minuscules, sans espaces) si nécessaire

---

## 5. Configuration du serveur

Ajoutez ceci à votre `server.cfg` :

```cfg
# Démarrer les dépendances en premier
ensure oxmysql
ensure ox_lib
ensure ox_inventory  # ou qb-inventory

# Démarrer Pulsar Banking
ensure pulsar-banking
```

> **Important :** `pulsar-banking` doit démarrer **après** ses dépendances.

---

## 6. Configuration du framework

Ouvrez `config/config.lua` et définissez votre framework :

```lua
-- Pour les serveurs QBCore :
Config.Framework = 'qbcore'

-- Pour les serveurs ESX :
Config.Framework = 'esx'
```

Le script détectera automatiquement votre système de target (`ox_target` / `qb-target`) et d'inventaire (`ox_inventory` / `qb-inventory`).

---

## 7. Premier démarrage

1. Démarrez votre serveur
2. Vérifiez la console serveur pour détecter d'éventuelles erreurs
3. Rejoignez le serveur et approchez-vous d'une banque ou d'un ATM
4. L'interface bancaire devrait s'ouvrir à l'interaction

---

## 8. Post-installation

Après avoir confirmé que le script fonctionne :

- Parcourez tous les fichiers dans `config/` pour personnaliser les paramètres
- Configurez les [Webhooks Discord](configuration/general.md#notifications--discord) pour la journalisation
- Configurez les [emplacements des banques](configuration/banks.md) si nécessaire
- Configurez le [job de banquier](configuration/jobs.md) pour vos joueurs

---

## Mise à jour

Lors d'une mise à jour vers une nouvelle version :

1. Sauvegardez votre dossier `config/` actuel
2. Remplacez tous les fichiers sauf votre dossier `config/`
3. Consultez le changelog pour les nouvelles options de config à ajouter
4. Redémarrez la ressource

> **Ne jamais** supprimer ou remplacer vos fichiers `config/` lors d'une mise à jour — ils contiennent vos paramètres personnalisés.
