# FAQ & Dépannage

---

## Problèmes d'installation

### Le script ne démarre pas

**Vérifiez que vos dépendances sont en cours d'exécution :**
```
ensure oxmysql
ensure ox_lib
ensure ox_inventory  -- ou qb-inventory
ensure pulsar-banking  -- DOIT être après les dépendances
```

### Erreurs SQL au démarrage

Assurez-vous d'avoir importé `sql/install.sql` dans votre base de données. Le script nécessite les 21 tables.

### Objets d'inventaire introuvables

- **ox_inventory :** Copiez les objets depuis `install/ox_inventory_items.lua` dans `ox_inventory/data/items.lua`
- **qb-inventory :** Copiez les objets depuis `install/qb_inventory_items.lua` dans `qb-core/shared/items.lua`
- Copiez les images depuis `install/ox_inventory_images/` vers le dossier d'images de votre inventaire

---

## Problèmes de configuration

### Framework non détecté

Définissez-le manuellement dans `config/config.lua` :
```lua
Config.Framework = 'qbcore'  -- ou 'esx'
```

### Les ATMs ne fonctionnent pas

- Vérifiez que les modèles d'ATM sont corrects dans `config/atms.lua`
- Vérifiez `Config.ATMInteractDistance` (défaut : 1.5)

### Les intérêts ne sont pas versés

- `Config.Interest.SavingsRate` doit être supérieur à 0
- Le compte doit avoir au moins `Config.Interest.MinBalanceForInterest`

---

## Problèmes de gameplay

### Le joueur ne peut pas créer de compte

- Nombre maximum de comptes atteint (`Config.MaxAccountsPerPlayer = 5`)
- Frais d'ouverture insuffisants

### Le joueur ne peut pas effectuer de virement

- Limite journalière atteinte (100 000 $)
- Délai actif (15 secondes) ou compte gelé

### Le joueur ne peut pas obtenir un prêt

- Score de crédit trop bas (min. 400 personnel, 550 entreprise)
- Prêt professionnel nécessite un emploi

### Le compte est gelé

Peut être gelé par un admin, un manager (grade 2+) ou automatiquement. Seuls les admins/managers peuvent dégeler.

---

## Erreurs courantes

### `SCRIPT ERROR: attempt to index a nil value`

Valeur de config manquante — vérifiez que tous les fichiers config sont présents.

### `No such export`

`ox_lib` et `oxmysql` doivent démarrer avant `pulsar-banking`.

### L'interface ne s'ouvre pas

- Vérifiez la console (F8) pour les erreurs JavaScript
- Vérifiez que `build/` contient `index.html` et `assets/`

---

## Support

1. Activez `Config.Debug = true`
2. Vérifiez la console serveur et client (F8)
3. Ouvrez un ticket sur notre serveur Discord
