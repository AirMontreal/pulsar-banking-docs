# Configuration des Cartes

Fichier de configuration : `config/cards.lua`

---

## Présentation

Pulsar Banking inclut 3 types de cartes qui fonctionnent comme des objets d'inventaire physiques. Les cartes peuvent être commandées dans n'importe quelle banque proposant le service de cartes.

---

## Types de Cartes

### Carte de Débit

| Option | Valeur |
|--------|--------|
| Nom de l'objet | debit_card |
| Limite journalière | $10,000 |
| Score de crédit requis | Non |
| Frais mensuels | $0 |
| Expiration | 3 ans |

### Carte de Crédit

| Option | Valeur |
|--------|--------|
| Nom de l'objet | credit_card |
| Limite journalière | $15,000 |
| Score de crédit requis | Oui (minimum 600) |
| Frais mensuels | $100 |
| Expiration | 2 ans |
| Taux d'intérêt | 18% |
| Cycle de facturation | 30 jours |

**Limites de crédit selon le score :**

| Score de crédit | Limite |
|----------------|--------|
| 500 - 599 | $5,000 |
| 600 - 699 | $15,000 |
| 700 - 799 | $50,000 |
| 800 - 850 | $100,000 |

### Carte Entreprise

| Option | Valeur |
|--------|--------|
| Nom de l'objet | enterprise_card |
| Limite journalière | $25,000 |
| Score de crédit requis | Non |
| Frais mensuels | $0 |
| Expiration | 3 ans |
| Longueur du PIN | 5 chiffres |

> Les cartes entreprise sont liées aux comptes d'organisation.

---

## Paramètres Généraux

| Option | Par défaut | Description |
|--------|-----------|-------------|
| Config.CardNumberPrefix | 4532 | Préfixe pour les numéros de carte générés |
| Config.BlockCardOnItemRemove | true | Bloque la carte lorsque l'objet est retiré de l'inventaire |

---

## Personnaliser un Type de Carte

```lua
Config.Cards = {
    debit = {
        name = 'Debit Card',
        itemName = 'debit_card',        -- Doit correspondre au nom de l'objet dans l'inventaire
        dailyLimit = 10000,
        requiresCreditScore = false,
        minCreditScore = 0,
        fee = 0.00,                     -- Frais mensuels
        expiryYears = 3,
    },
}
```

---

## Ajouter un Nouveau Type de Carte

1. Ajoutez la définition de la carte dans `config/cards.lua`
2. Ajoutez l'objet correspondant à votre système d'inventaire (ox_inventory ou qb-inventory)
3. Ajoutez l'image de la carte dans le dossier d'images de votre inventaire
