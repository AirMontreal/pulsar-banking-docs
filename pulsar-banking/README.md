# Pulsar Banking

**Advanced Banking System for FiveM — QBCore & ESX**

Pulsar Banking is a complete, modern banking solution for your FiveM server. It provides a realistic and immersive banking experience with a beautiful React-based UI, multi-framework support, and a deep feature set.

---

## Key Features

- **Multi-Framework** — Supports QBCore and ESX (target & inventory auto-detected)
- **Full Banking System** — Checking, savings, joint, and organization accounts
- **Card System** — Debit, credit, and enterprise cards with physical items
- **Loan System** — Personal and business loans with credit scoring
- **Investment Market** — Real-time stocks and crypto with live prices
- **Organization Accounts** — Role-based access, payroll, and member management
- **Invoice System** — Create, send, and manage invoices between players
- **Savings Goals** — Set and track financial goals
- **Smart Money Rules** — Auto-transfers, round-up savings
- **Achievement System** — 15+ badges to reward player activity
- **Admin Panel** — Freeze accounts, audit logs, Discord webhooks
- **Multi-Language** — 8 languages included (EN, FR, ES, DE, IT, PT, NL, TR)
- **Modern UI** — React 18 + Tailwind CSS + Framer Motion

---

## Requirements

| Dependency | Required |
|------------|----------|
| [oxmysql](https://github.com/overextended/oxmysql) | Yes |
| [ox_lib](https://github.com/overextended/ox_lib) | Yes |
| [ox_inventory](https://github.com/overextended/ox_inventory) or [qb-inventory](https://github.com/qbcore-framework/qb-inventory) | Yes (auto-detected) |
| [ox_target](https://github.com/overextended/ox_target) or [qb-target](https://github.com/qbcore-framework/qb-target) | Yes (auto-detected) |
| QBCore or ESX | Yes (set in config) |

---

## Quick Start

1. Import `sql/install.sql` into your database
2. Add inventory items from `install/` folder
3. Place the resource in your `resources/` folder
4. Add `ensure pulsar-banking` to your `server.cfg`
5. Configure `config/config.lua` to your needs
6. Restart your server

See the full [Installation Guide](installation.md) for details.

---

## Support

For support, open a ticket on our Discord server or contact us via Tebex.
