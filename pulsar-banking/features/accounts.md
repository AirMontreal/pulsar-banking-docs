# Comptes

---

## Types de Comptes

| Type | Description | Maximum par joueur |
|------|-------------|-------------------|
| **Checking** | Compte courant pour les dépôts, retraits et virements | 2 |
| **Savings** | Compte épargne rémunéré pour l'épargne à long terme | 2 |
| **Joint** | Compte partagé entre deux joueurs | 2 |
| **Organization** | Compte professionnel lié à un emploi, avec des rôles membres | 2 |

Nombre maximum total de comptes par joueur : **5** (configurable).

---

## Créer un Compte

1. Rendez-vous à un guichet de banque ou à un DAB
2. Ouvrez l'interface bancaire
3. Sélectionnez "New Account"
4. Choisissez le type de compte
5. Définissez un code PIN (par défaut : `0000`)

> Les comptes d'organisation nécessitent un emploi et sont gérés par le patron/propriétaire.

---

## Fonctionnalités du Compte

### Protection par Code PIN

- Chaque compte dispose d'un code PIN à 4 chiffres (5 pour les cartes entreprise)
- Requis pour toutes les transactions
- Maximum 5 tentatives échouées avant le verrouillage (15 min)

### Surnoms de Compte

Les joueurs peuvent renommer leurs comptes pour une identification plus facile (ex. : "Loyer", "Fonds Pro").

### Numéros de Compte

Générés automatiquement avec le préfixe `PB` (ex. : `PB-1234567`).

---

## Comptes Joints

- Deux joueurs partagent un seul compte
- Les deux peuvent déposer, retirer et effectuer des virements
- L'un ou l'autre joueur peut fermer le compte

---

## Comptes d'Organisation

- Liés à un emploi (QBCore) ou à une société (ESX)
- Permissions basées sur les rôles : Propriétaire, Gestionnaire, Employé
- Prennent en charge la paie, la facturation et la gestion des membres
- Maximum 50 membres par organisation

Voir [Organisations](organizations.md) pour plus de détails.

---

## Limites de Compte

| Limite | Par défaut |
|--------|-----------|
| Solde maximum (courant) | Illimité |
| Solde maximum (épargne) | Illimité |
| Solde minimum (courant) | $0 |
| Solde minimum (épargne) | $0 |
| Limite de retrait journalier | $50,000 |
| Limite de virement journalier | $100,000 |

---

## Fermer un Compte

1. Le solde doit être $0 (ou vous pouvez retirer le solde restant)
2. Aucun prêt actif lié au compte
3. Des frais de fermeture peuvent s'appliquer (par défaut : $0)
