# Otto — Real Estate Assistant Plugin

**Version 0.2.0**

Otto is a drop-in AI assistant for licensed real estate agents. Once installed, Otto runs entire transaction-stage workflows in batch — generating every email, checklist, survey, and post you need for a new listing, a new buyer, an under-contract deal, or a post-close nurture sequence — all in one shot, all in your voice, all saved into an organized workspace folder automatically.

## What's new in v0.2.0

- **Four stage-based packages** that batch-generate every deliverable for a transaction milestone in one pass
- **Main menu** powered by AskUserQuestion — every fresh conversation starts with a one-click pick of what you want to work on, no trigger phrases to memorize
- **17 new templates** covering seller onboarding surveys, go-to-market prep, weekly showing feedback, buyer onboarding, offer process education, conditional/firm deal congrats, NOF emails, conditions reminders, birthday messages, occasion calendars, and pop-bys
- **Numbered subfolder layout** so every listing/buyer folder sorts itself in transaction order

## How Otto works

The first time you use Otto, it spends about two minutes asking you for your name, brokerage, contact info, market area, brand tone, and email sign-off. It saves all of that to a profile and creates an `Otto Workspace/` folder.

From that point on, every conversation starts with Otto showing you a simple menu:

- **Start a Listing package** — new property going to market
- **Start a Buyer package** — new buyer client onboarding
- **Start an Under Contract package** — deal accepted, working through conditions
- **Start a Post-Close & Nurture package** — deal closed, starting nurture sequence
- **Other** — anything else (one-off email, social post, listing description, script, etc.)

Pick a package, answer the batch intake questions once, and Otto generates everything — a 9-item listing package produces a welcome email, onboarding survey, pre-listing checklist, go-to-market email, MLS description, weekly showing feedback template, price reduction email, offer presentation email, and just-sold next-steps email — all saved into numbered subfolders inside that listing's folder.

## Inside each package

### Listing Package (9 mass-production items)
Welcome email · Seller onboarding survey · Pre-listing checklist · Go-to-market prep email · MLS listing description · Weekly showing feedback template · Price reduction email · Offer presentation email · Just-sold + next steps email

*Plus one-time items on request:* social posts, open house promo + follow-up, CMA cover letter, counter-offer emails

### Buyer Package (6 mass-production items)
Buyer consultation questionnaire · Welcome + next steps email · Buyer onboarding survey · New listing alert template · Offer process review email · Offer prep questionnaire

*Plus one-time items on request:* showings recap, conditional accepted congrats, firm deal congrats

### Under Contract Package (2 mass-production items)
Transaction checklist / timeline · Purchaser visit request email

*Plus one-time items on request:* conditions reminder doc, NOF to client, NOF to other agent

### Post-Close & Nurture Package (5 mass-production items)
Closing congratulations · Referral request · Annual check-in · Birthday message (text + email) · Occasion reminders calendar doc

*Plus one-time items on request:* seasonal pop-by email

## Beyond packages — everything Otto still does

Otto is also still a one-off content engine. Pick "Other" from the menu (or just ask) and Otto can:

- Write MLS-ready listing descriptions in your voice
- Draft any individual email at any stage of a transaction
- Produce Just Listed, Just Sold, Open House, and market update social posts for Instagram, Facebook, and LinkedIn
- Generate CMA cover letters, checklists, and questionnaires
- Handle tough conversations — objection handling, FSBO outreach, expired listing scripts
- Update your agent profile any time your details change

Otto enforces Fair Housing compliance, avoids overused real estate clichés, and saves every output to the right folder automatically.

## Workspace organization

Every piece of content Otto produces goes into `Otto Workspace/` on your computer, organized into category folders:

```
Otto Workspace/
├── Listings/{address-slug}/         ← numbered 01-Welcome through 09-Sold
├── Buyers/{family-name}/            ← numbered 01-Consultation through 08-Under-Contract
├── Open Houses/                     ← only for open houses NOT tied to your own listings
├── Offers/                          ← offers on properties not yet in Listings
├── Post-Close/{family-name}/        ← numbered 01-Congrats through 06-Pop-By
├── Marketing/{YYYY-MM}/             ← non-property marketing
└── Prospecting/                     ← FSBO, expired, circle prospecting
```

When you start a new package on a property or client that already has a folder, Otto nests inside it instead of creating a duplicate.

## Installation

See `INSTALL_GUIDE.md` for the customer-facing install instructions.

## What's inside the plugin

```
otto/
├── .claude-plugin/
│   └── marketplace.json             ← marketplace manifest (root)
├── plugins/otto/
│   ├── .claude-plugin/
│   │   └── plugin.json              ← plugin manifest
│   └── skills/otto/
│       ├── SKILL.md                 ← Otto's brain (main menu, packages, routing)
│       ├── templates/
│       │   ├── emails/              ← 22 email templates
│       │   ├── social/              ← 4 social post templates (IG / FB / LI variants)
│       │   ├── listings/            ← MLS descriptions, CMA cover letters
│       │   └── checklists/          ← 8 checklist, survey, and reminder templates
│       └── reference/
│           ├── packages.md          ← Full spec for all 4 packages
│           ├── brand_rules.md       ← Brand voice, words to avoid, Fair Housing
│           ├── ref_glossary.md
│           ├── ref_objection_handling.md
│           └── ref_scripts_phone_and_door.md
├── README.md                        ← You are here
└── INSTALL_GUIDE.md                 ← Customer-facing install instructions
```

## Support

Email: arslan@salesgenius.co
Website: https://arslanahmed.com

---

© SalesGenius / Arslan Ahmed. All rights reserved. Otto is a proprietary product.
