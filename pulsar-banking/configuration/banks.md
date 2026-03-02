# Configuration des Banques

Fichier de configuration : `config/banks.lua`

---

## Présentation

Pulsar Banking est livré avec **8 emplacements bancaires préconfigurés** sur la carte GTA. Chaque banque possède ses propres frais, taux d'intérêt et services disponibles.

---

## Liste des Banques

| ID | Nom | Type | Banque Principale |
|----|-----|------|------------------|
| fleeca_legion | Fleeca Bank - Legion Square | Fleeca | Non |
| fleeca_alta | Fleeca Bank - Alta Street | Fleeca | Non |
| fleeca_burton | Fleeca Bank - Burton | Fleeca | Non |
| fleeca_delperro | Fleeca Bank - Del Perro | Fleeca | Non |
| fleeca_greatocean | Fleeca Bank - Great Ocean Highway | Fleeca | Non |
| fleeca_route68 | Fleeca Bank - Route 68 | Fleeca | Non |
| pacific_standard | Pacific Standard Bank | Pacific | Oui |
| blaine_county | Blaine County Savings | Blaine | Oui |

---

## Structure d'une Banque

Chaque entrée de banque supporte les options suivantes :

```lua
['bank_id'] = {
    name = 'Bank Name',                           -- Nom affiché
    bankType = 'fleeca',                           -- Type : 'fleeca', 'pacific', 'blaine'
    isMainBank = false,                            -- Les banques principales ont un style de marqueur différent
    coords = vector3(x, y, z),                     -- Position de la banque
    heading = 340.0,                               -- Direction du PNJ
    blip = {
        sprite = 108,                              -- Icône du marqueur (108 = banque)
        color = 69,                                -- Couleur du marqueur (69 = vert, 2 = vert foncé)
        scale = 0.65,                              -- Taille du marqueur
        label = 'Bank Name',                       -- Libellé du marqueur sur la carte
    },
    counter = {
        coords = vector3(x, y, z),                 -- Point d'interaction
        radius = 1.5,                              -- Rayon d'interaction
    },
    ped = {
        coords = vector4(x, y, z, heading),        -- Position du PNJ + orientation
    },
    fees = {
        deposit = 0.0,                             -- Frais de dépôt (%)
        withdrawal = 0.0,                          -- Frais de retrait (%)
        transfer = 0.005,                          -- Frais de virement (0.5%)
        atm = 2.00,                                -- Frais DAB ($)
    },
    interestRates = {
        savings = 0.01,                            -- Intérêts épargne (1%)
        loanBase = 0.05,                           -- Taux de base des prêts (5%)
    },
    services = { 'checking', 'savings', 'loans', 'cards' },
}
```

---

## Frais par Banque

| Banque | Frais de virement | Frais DAB | Taux épargne | Taux prêt |
|--------|------------------|-----------|-------------|-----------|
| Agences Fleeca | 0.5% | $2.00 | 1% | 5% |
| Pacific Standard | 0.2% | $0.50 | 2% | 3.5% |
| Blaine County | 0.8% | $2.00 | 0.5% | 7% |

> Les frais par banque remplacent les frais globaux définis dans `config/config.lua`.

---

## Services Disponibles

| Service | Description |
|---------|-------------|
| checking | Ouverture d'un compte courant |
| savings | Ouverture d'un compte épargne |
| loans | Demandes de prêt |
| cards | Commande de cartes (débit/crédit) |

> **Remarque :** fleeca_route68 et blaine_county ne proposent pas de services de carte par défaut.

---

## Ajouter une Nouvelle Banque

Ajoutez une nouvelle entrée dans la table `Config.Banks` :

```lua
['my_custom_bank'] = {
    name = 'My Custom Bank',
    bankType = 'fleeca',
    isMainBank = false,
    coords = vector3(100.0, 200.0, 30.0),
    heading = 180.0,
    blip = { sprite = 108, color = 69, scale = 0.65, label = 'My Custom Bank' },
    counter = { coords = vector3(100.0, 200.0, 30.0), radius = 1.5 },
    ped = { coords = vector4(100.0, 202.0, 30.0, 180.0) },
    fees = {
        deposit = 0.0,
        withdrawal = 0.0,
        transfer = 0.005,
        atm = 2.00,
    },
    interestRates = {
        savings = 0.01,
        loanBase = 0.05,
    },
    services = { 'checking', 'savings', 'loans', 'cards' },
}
```

---

## Supprimer une Banque

Supprimez ou commentez simplement l'entrée de la banque dans `Config.Banks`. Le script ne chargera que les banques présentes dans la configuration.

---

## Référence des Couleurs de Marqueur

| ID Couleur | Couleur |
|-----------|---------|
| 0 | Blanc |
| 1 | Rouge |
| 2 | Vert foncé |
| 3 | Bleu |
| 5 | Jaune |
| 69 | Vert |
