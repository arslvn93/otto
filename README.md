# Otto — Real Estate Assistant Plugin

Otto is a drop-in AI assistant for licensed real estate agents. Once installed, Claude automatically reaches for Otto whenever you ask for help with a listing, email, social post, script, or client conversation — no prompt pasting, no template uploads, no setup clicks past a two-minute onboarding chat.

## What Otto does

- Writes MLS-ready listing descriptions in your voice
- Drafts buyer and seller emails for every stage of a transaction (welcome, offer, counter, price reduction, closing congrats, referral request, annual check-in)
- Produces Just Listed, Just Sold, Open House, and market update social posts for Instagram, Facebook, and LinkedIn
- Generates CMA cover letters, pre-listing checklists, transaction timelines, and buyer consultation questionnaires
- Handles tough conversations — objection handling, FSBO outreach, expired listing scripts
- Enforces Fair Housing compliance and avoids overused real estate clichés
- Saves every piece of content to an organized `Otto Workspace/` folder, nested by listing, buyer, or campaign

## How it works

The first time you use Otto, it spends about two minutes asking you for your name, brokerage, contact info, market area, brand tone, and email sign-off. It saves all of that to a profile and creates an `Otto Workspace/` folder with seven category subfolders (Listings, Buyers, Open Houses, Offers, Post-Close, Marketing, Prospecting).

From that point on, every email and post comes out in your voice with your contact info baked in. When you ask Otto to draft an open house promo for a listing it has already worked on, it nests the new files inside that listing's existing folder automatically — no manual filing.

## Installation

See `INSTALL_GUIDE.md` for the customer-facing install instructions.

## What's inside

```
otto/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── otto/
│       ├── SKILL.md              ← Otto's brain
│       ├── my_profile.md         ← Sentinel file, replaced on first run
│       ├── templates/
│       │   ├── emails/           ← 10 email templates
│       │   ├── social/           ← Instagram / Facebook / LinkedIn posts
│       │   ├── listings/         ← MLS descriptions, CMA cover letters
│       │   └── checklists/       ← Seller prep, buyer intake, timelines
│       └── reference/
│           ├── brand_rules.md    ← Brand voice, words to avoid, Fair Housing
│           ├── ref_glossary.md
│           ├── ref_objection_handling.md
│           └── ref_scripts_phone_and_door.md
├── README.md                     ← You are here
└── INSTALL_GUIDE.md              ← Customer-facing install instructions
```

## Support

Email: arslan@salesgenius.co
Website: https://arslanahmed.com

---

© SalesGenius / Arslan Ahmed. All rights reserved. Otto is a proprietary product.
