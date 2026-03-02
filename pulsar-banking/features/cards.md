# Cartes

---

## Présentation

Les cartes sont des objets d'inventaire physiques que les joueurs peuvent commander aux guichets de banque. Chaque carte est liée à un compte bancaire spécifique.

---

## Types de Cartes

### Carte de Débit
- Gratuite à la commande
- Liée à un compte courant ou épargne
- Limite journalière de $10,000
- Aucune condition de score de crédit

### Carte de Crédit
- Frais de $100/mois
- Nécessite un score de crédit de 600 ou plus
- Limite de crédit basée sur le score (jusqu'à $100,000)
- Taux d'intérêt de 18% sur le solde créditeur
- Cycle de facturation de 30 jours

### Carte Entreprise
- Gratuite à la commande
- Liée à un compte d'organisation
- Limite journalière de $25,000
- Code PIN à 5 chiffres

---

## Commander une Carte

1. Rendez-vous dans une banque proposant le service `cards`
2. Ouvrez l'interface bancaire
3. Naviguez vers la section Cartes
4. Sélectionnez le type de carte
5. L'objet carte sera ajouté à votre inventaire

---

## Sécurité des Cartes

- Les cartes possèdent des numéros générés uniques (préfixe : `4532`)
- Protection par code PIN pour toutes les transactions par carte
- Les cartes expirent après leur durée configurée (2 à 3 ans)
- Si un objet carte est retiré de l'inventaire, la carte est bloquée (`Config.BlockCardOnItemRemove = true`)

---

## Détails de la Carte de Crédit

### Limites de Crédit selon le Score

| Plage de Score | Limite de Crédit |
|---------------|-----------------|
| 500 - 599 | $5,000 |
| 600 - 699 | $15,000 |
| 700 - 799 | $50,000 |
| 800 - 850 | $100,000 |

### Facturation

- Le solde créditeur accumule 18% d'intérêts
- Cycle de facturation : 30 jours
- Paiement dû à la fin de chaque cycle
- Les paiements en retard affectent le score de crédit (-25)
