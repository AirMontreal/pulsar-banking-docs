# Pulsar Banking

**Système bancaire avancé pour FiveM — QBCore & ESX**

Pulsar Banking est une solution bancaire complète et moderne pour votre serveur FiveM. Elle offre une expérience bancaire réaliste et immersive avec une interface React soignée, un support multi-framework et un ensemble de fonctionnalités approfondies.

---

## Fonctionnalités principales

- **Multi-Framework** — Supporte QBCore et ESX (détection automatique)
- **Système bancaire complet** — Comptes courants, épargne, joints et d'organisation
- **Système de cartes** — Cartes de débit, crédit et entreprise sous forme d'objets physiques
- **Système de prêts** — Prêts personnels et professionnels avec score de crédit
- **Marché d'investissement** — Actions et cryptos en temps réel
- **Comptes d'organisation** — Accès par rôle, paie et gestion des membres
- **Système de facturation** — Créer, envoyer et gérer des factures entre joueurs
- **Objectifs d'épargne** — Définir et suivre des objectifs financiers
- **Règles intelligentes** — Virements automatiques, arrondi à l'épargne
- **Système de badges** — Plus de 15 badges pour récompenser l'activité
- **Panneau admin** — Geler des comptes, journaux d'audit, webhooks Discord
- **Multi-langue** — 8 langues incluses (EN, FR, ES, DE, IT, PT, NL, TR)
- **Interface moderne** — React 18 + Tailwind CSS + Framer Motion

---

## Prérequis

| Dépendance | Requis |
|------------|--------|
| [oxmysql](https://github.com/overextended/oxmysql) | Oui |
| [ox_lib](https://github.com/overextended/ox_lib) | Oui |
| [ox_inventory](https://github.com/overextended/ox_inventory) ou [qb-inventory](https://github.com/qbcore-framework/qb-inventory) | Oui (auto-détecté) |
| [ox_target](https://github.com/overextended/ox_target) ou [qb-target](https://github.com/qbcore-framework/qb-target) | Oui (auto-détecté) |
| QBCore ou ESX | Oui (défini dans la config) |

---

## Démarrage rapide

1. Importez `sql/install.sql` dans votre base de données
2. Ajoutez les objets d'inventaire depuis le dossier `install/`
3. Placez la ressource dans votre dossier `resources/`
4. Ajoutez `ensure pulsar-banking` à votre `server.cfg`
5. Configurez `config/config.lua` selon vos besoins
6. Redémarrez votre serveur

Consultez le [Guide d'installation](installation.md) pour les détails complets.

---

## Support

Pour obtenir de l'aide, ouvrez un ticket sur notre serveur Discord ou contactez-nous via Tebex.
