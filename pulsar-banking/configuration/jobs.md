# Configuration des Emplois

Fichier de configuration : `config/jobs.lua`

---

## Présentation

L'emploi de banquier permet aux joueurs de travailler dans des banques, d'approuver des prêts, de gérer des comptes et de générer des rapports. Les permissions sont basées sur les grades de l'emploi.

---

## Grades du Métier de Banquier

| Grade | Nom | Peut approuver les prêts | Approbation max |
|-------|-----|--------------------------|----------------|
| 0 | Teller | Non | $0 |
| 1 | Associate | Oui | $25,000 |
| 2 | Manager | Oui | $100,000 |
| 3 | Director | Oui | $500,000 |

---

## Permissions par Grade

| Permission | Teller (0) | Associate (1) | Manager (2) | Director (3) |
|------------|-----------|--------------|------------|-------------|
| Approuver les prêts | Non | Oui | Oui | Oui |
| Geler les comptes | Non | Non | Oui | Oui |
| Voir tous les comptes | Non | Oui | Oui | Oui |
| Générer des rapports | Non | Non | Oui | Oui |

---

## Configuration

```lua
Config.BankJobs = {
    ['banker'] = {
        label = 'Bank Manager',
        grades = {
            [0] = { name = 'Teller', canApproveLoan = false, maxLoanApproval = 0 },
            [1] = { name = 'Associate', canApproveLoan = true, maxLoanApproval = 25000 },
            [2] = { name = 'Manager', canApproveLoan = true, maxLoanApproval = 100000 },
            [3] = { name = 'Director', canApproveLoan = true, maxLoanApproval = 500000 },
        },
        canFreezeAccounts = { 2, 3 },
        canViewAllAccounts = { 1, 2, 3 },
        canGenerateReports = { 2, 3 },
    },
}
```

---

## Personnalisation

### Changer le Nom de l'Emploi

Si votre serveur utilise un nom d'emploi différent (ex. : bankier, banquier) :

1. Modifiez la clé dans `Config.BankJobs` :
   ```lua
   ['your_job_name'] = { ... }
   ```
2. Mettez à jour `Config.BankManagerJob` dans `config/config.lua` :
   ```lua
   Config.BankManagerJob = 'your_job_name'
   ```

### Ajouter Plus de Grades

Ajoutez des entrées de grade supplémentaires dans la table `grades`. Assurez-vous que les numéros de grade correspondent aux grades d'emploi de votre framework.
