# Configuration des DAB

Fichier de configuration : `config/atms.lua`

---

## Présentation

Les distributeurs automatiques de billets (DAB) sont détectés automatiquement dans le monde du jeu en fonction des modèles de props. Vous pouvez également ajouter des emplacements de DAB personnalisés manuellement.

---

## Modèles de DAB

Les props GTA suivants sont reconnus comme des DAB :

```lua
Config.ATMModels = {
    `prop_atm_01`,
    `prop_atm_02`,
    `prop_atm_03`,
    `prop_fleeca_atm`,
}
```

> Ces modèles couvrent tous les DAB par défaut présents sur la carte GTA. Si vous ajoutez des props de DAB personnalisés via un MLO, ajoutez leur nom de modèle ici.

---

## Paramètres des DAB

| Option | Par défaut | Description |
|--------|-----------|-------------|
| Config.ATMFee | $2.00 | Frais par transaction au DAB |
| Config.ATMDailyLimit | $50,000 | Retraits journaliers maximum au DAB |

Limites supplémentaires des DAB depuis `config/config.lua` :

| Option | Par défaut |
|--------|-----------|
| ATMMaxWithdraw | $25,000 par transaction |
| ATMMaxDeposit | $50,000 par transaction |
| ATMDailyWithdrawLimit | $50,000 |
| ATMDailyDepositLimit | $100,000 |

---

## Emplacements de DAB Personnalisés

Ajoutez des coordonnées pour placer des DAB à des positions personnalisées :

```lua
Config.CustomATMLocations = {
    vector3(100.0, 200.0, 30.0),
    vector3(300.0, 400.0, 25.0),
}
```

> Les emplacements personnalisés utilisent l'interaction DAB par défaut sans nécessiter la présence d'un prop réel.

---

## Marqueurs de DAB

Par défaut, les marqueurs de DAB sont **désactivés** sur la carte :

```lua
-- Dans config/config.lua
Config.ShowATMBlips = false
```

Définissez cette valeur à true pour afficher les emplacements des DAB sur la mini-carte.

---

## Interaction avec les DAB

| Option | Valeur | Fichier |
|--------|--------|---------|
| Distance d'interaction | 1.5 | config/config.lua |
| Distance d'affichage | 10.0 | config/config.lua |
| Utiliser le système de cible | true | config/config.lua |
| Disponible 24h/24 | Oui | Même lorsque les horaires bancaires sont activés |
