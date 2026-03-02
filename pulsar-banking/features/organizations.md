# Organisations

---

## Présentation

Les comptes d'organisation sont des comptes professionnels liés à un emploi. Ils prennent en charge plusieurs membres avec des permissions basées sur les rôles, la paie et la facturation.

---

## Créer un Compte d'Organisation

1. Avoir un emploi (QBCore) ou une société (ESX)
2. Être le patron/propriétaire de cet emploi
3. Se rendre à un guichet de banque
4. Sélectionner "Organization Account"
5. Le compte est créé et lié à votre emploi

---

## Rôles & Permissions

| Permission | Propriétaire | Gestionnaire | Employé |
|------------|-------------|-------------|---------|
| Retrait | Oui | Oui | Non |
| Dépôt | Oui | Oui | Oui |
| Virement | Oui | Oui | Non |
| Gérer les membres | Oui | Oui | Non |
| Voir les journaux | Oui | Oui | Non |
| Paramètres | Oui | Non | Non |
| Factures | Oui | Oui | Oui |
| Fermer le compte | Oui | Non | Non |

---

## Gestion des Membres

- **Ajouter des membres** — Le propriétaire/gestionnaire peut inviter des joueurs
- **Retirer des membres** — Le propriétaire/gestionnaire peut expulser des membres
- **Changer les rôles** — Le propriétaire peut promouvoir/rétrograder les membres
- **Membres maximum :** 50 par organisation

---

## Paie

Si `Config.Enterprise.AutoPayroll = true` :

- Versements automatiques de salaires à intervalles définis
- Intervalle configurable (par défaut : 60 minutes)
- Fonds prélevés sur le compte de l'organisation

---

## Limites d'Organisation

| Limite | Par défaut |
|--------|-----------|
| Membres maximum par org. | 50 |
| Organisations maximum par joueur (en tant que propriétaire) | 3 |
| Limite journalière org. vers personnel | $100,000 |
| Taux de taxe professionnelle | 0% |
| Solde minimum pour créer | $0 |
| Frais de création | $0 |

---

## Virements Organisation vers Personnel

Par défaut, les virements d'un compte d'organisation vers des comptes personnels sont autorisés :

```lua
Config.Enterprise.AllowOrgToPersonalTransfer = true
Config.Enterprise.OrgToPersonalDailyLimit = 100000
```

Pour exiger une approbation pour les virements importants :

```lua
Config.Enterprise.ApprovalRequired = true
Config.Enterprise.ApprovalThreshold = 50000
```

---

## Spécifique à ESX

Pour les serveurs ESX, la détection du patron peut être configurée :

```lua
-- Grade minimum pour être considéré comme patron
Config.Enterprise.OrgBossMinGrade = nil  -- nil = utiliser la détection par grade_name
```
