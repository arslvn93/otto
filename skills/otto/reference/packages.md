# Otto Packages Reference

Otto runs work in two modes: **packages** (batch) and **one-offs** (on-demand).

A **package** is a named workflow tied to a transaction stage. When the agent starts a package, Otto runs ONE consolidated intake — asking every question needed for every Mass Production item in that package — then generates all Mass Production items in a single batch and saves them to numbered subfolders inside the client/property folder.

**One Time items** belong to the same packages but are NOT generated automatically. They are only produced when the agent asks for them specifically (e.g., "draft a price reduction email for 742 Maple Drive") and they save into the same package folder.

---

## Package flow (how every package runs)

1. **Identify the target folder.** Use the slug rule for properties or the family-name rule for buyers. Run the lookup-before-create check against the matching category folder (`Listings/`, `Buyers/`, `Post-Close/`). Nest under-contract packages inside the existing listing or buyer folder if one already exists.
2. **Run the batch intake.** Ask every question for every Mass Production item in one conversational pass. Group the questions sensibly (property basics → seller info → marketing details → etc.). Do not ask per-item — agents hate that.
3. **Generate all Mass Production items.** Read each template, adapt using the intake answers and `my_profile.md`, save each to its numbered subfolder.
4. **Return one summary.** List every file created with relative paths from `Otto Workspace/`. Do not paste the content of each file back in chat — the agent will open the folder.
5. **Offer next steps.** End with: "One-time items in this package are: {list}. Just ask me for any of them when you need them."

---

## 1. LISTING PACKAGE

**Triggers:** "start listing package", "new listing at X", "I took a new listing", "listing side package for X"

**Root folder:** `Otto Workspace/Listings/{address-slug}/`

**Batch intake (ask in these groups):**

*Property basics*
- Full street address
- Beds / baths / sqft / year built
- Lot size
- Property type (detached, condo, townhouse, semi, etc.)
- Asking price
- Target list date (when it goes live on MLS)

*Seller info*
- Seller full name(s)
- Seller email + phone
- Motivation and timeline (why selling, how soon)
- Situation notes (tenants in place, estate sale, occupied/vacant, etc.)

*Marketing & logistics*
- Three to five key selling features
- Recent upgrades/renovations (with rough dates)
- Neighborhood highlights to emphasize
- Showing instructions (lockbox code, appointments only, 24h notice, etc.)
- Photographer / stager booked? Dates if yes
- Target buyer profile (first-time, luxury, investor, downsizer, etc.)

**Mass Production items (9 — all generated in batch):**

| # | Item | Template | Saves to |
|---|---|---|---|
| 1 | Seller welcome email | `templates/emails/email_seller_welcome.md` | `01-Welcome/welcome-email.md` |
| 2 | Seller onboarding survey | `templates/checklists/survey_seller_onboarding.md` | `02-Onboarding/onboarding-survey.md` |
| 3 | Pre-listing checklist | `templates/checklists/checklist_seller_prelisting.md` | `03-Pre-Listing/pre-listing-checklist.md` |
| 4 | Go-to-market prep email | `templates/emails/email_seller_go_to_market.md` | `04-Go-To-Market/go-to-market-email.md` |
| 5 | MLS listing description | `templates/listings/listing_description_generator.md` | `05-Listing-Copy/mls-description.md` |
| 6 | Weekly showing feedback email template | `templates/emails/email_weekly_showing_feedback.md` | `06-Showing-Feedback/weekly-feedback-template.md` |
| 7 | Price reduction email | `templates/emails/email_price_reduction.md` | `07-Price-Changes/price-reduction-email.md` |
| 8 | Offer presentation email | `templates/emails/email_offer_presentation.md` | `08-Offers/offer-presentation-email.md` |
| 9 | Just-sold + next steps email | `templates/emails/email_seller_just_sold_next_steps.md` | `09-Sold/just-sold-next-steps.md` |

**One Time items** (available on request, save into same listing folder):
- Just listed social posts (IG/FB/LI) → `05-Listing-Copy/social/`
- Open house promo + follow-up → nests in `Open Houses/{YYYY-MM-DD}/`
- CMA cover letter → `00-CMA/cma-cover-letter.md`
- Counter-offer email → `08-Offers/counter-offer-{date}.md`
- Fresh regenerations of any Mass item with new context

---

## 2. BUYER PACKAGE

**Triggers:** "start buyer package", "new buyer client", "I took on a new buyer", "buy side package for the {family}"

**Root folder:** `Otto Workspace/Buyers/{family-name}/`

**Batch intake:**

*Client basics*
- Buyer full name(s)
- Email + phone
- Preferred contact method

*Search criteria*
- Target neighborhoods / area(s)
- Price range
- Must-haves (beds, baths, parking, outdoor space, etc.)
- Nice-to-haves
- Dealbreakers
- Timeline (when they need to be in a home)

*Financial readiness*
- Pre-approved? Mortgage broker / lender on file?
- Down payment ready and sourced?
- First-time buyer?
- Any programs (FHSA, first-time buyer incentive, etc.)

*Relationship context*
- How the lead came to you (referral source, open house, online, etc.)
- Have they worked with an agent before?
- Anything specific Otto should know (out of town, moving for job, growing family, etc.)

**Mass Production items (6):**

| # | Item | Template | Saves to |
|---|---|---|---|
| 1 | Buyer consultation questionnaire | `templates/checklists/questionnaire_buyer_consultation.md` | `01-Consultation/consultation-questionnaire.md` |
| 2 | Welcome + next steps email | `templates/emails/email_buyer_welcome.md` | `02-Welcome/welcome-email.md` |
| 3 | Buyer onboarding survey | `templates/checklists/survey_buyer_onboarding.md` | `03-Onboarding/onboarding-survey.md` |
| 4 | New listing alert email (reusable template) | `templates/emails/email_new_listing_alert.md` | `04-Listing-Alerts/alert-template.md` |
| 5 | Offer process review email | `templates/emails/email_buyer_offer_process_review.md` | `05-Offer-Process/offer-process-review.md` |
| 6 | Offer prep questionnaire | `templates/checklists/questionnaire_buyer_offer_prep.md` | `06-Offer-Prep/offer-prep-questionnaire.md` |

**One Time items:**
- Showings recap email → `07-Showings/showings-recap-{date}.md`
- Conditional offer accepted congrats + next steps → `08-Under-Contract/conditional-accepted.md`
- Firm deal congrats + next steps to closing → `08-Under-Contract/firm-deal-congrats.md`

---

## 3. UNDER CONTRACT PACKAGE

**Triggers:** "start under contract package", "we're under contract on X", "deal accepted on X", "went firm on X"

**Root folder:** Depends on the side picked in Menu 1.
- Listing side → `Otto Workspace/Listings/{address-slug}/Under Contract/`
- Buy side → `Otto Workspace/Buyers/{family-name}/Under Contract/{address-slug}/`

Always run the lookup-before-create check first. If the parent `Listings/{slug}/` or `Buyers/{family}/` folder doesn't exist yet, create a minimal stub parent and nest Under Contract inside it. Do NOT create a top-level `Under Contract/` folder — that no longer exists.

**Batch intake:**

*Deal basics*
- Property address
- Your side (listing or buyer)
- Client name(s)
- Other agent name + brokerage + email
- Firm or conditional?
- Accepted offer price
- Closing date
- Deposit amount + method + due date

*Conditions & dates*
- List of conditions (financing, home inspection, insurance, status certificate, sale of buyer's home, etc.)
- Waiver date for each condition

*Purchaser visit*
- Does the buyer want a pre-closing visit? Expected date and time?

**Mass Production items (2):**

| # | Item | Template | Saves to |
|---|---|---|---|
| 1 | Transaction checklist / timeline | `templates/checklists/checklist_transaction_timeline.md` | `01-Checklist/transaction-checklist.md` |
| 2 | Purchaser visit request email | `templates/emails/email_purchaser_visit_request.md` | `02-Purchaser-Visit/visit-request-email.md` |

**One Time items:**
- Conditions reminder doc (agent copies into their own calendar) → template `templates/checklists/reminders_conditions.md` → saves to `03-Conditions/conditions-reminders.md`
- NOF (Notice of Fulfilment) email to client → template `templates/emails/email_nof_to_client.md` → saves to `04-NOF/nof-email-client.md`
- NOF email to other agent → template `templates/emails/email_nof_to_other_agent.md` → saves to `04-NOF/nof-email-other-agent.md`

---

## 4. POST-CLOSE & NURTURE PACKAGE

**Triggers:** "start post close package", "deal closed on X", "start nurture for the {family}", "closing package"

**Root folder:** Depends on the side picked in Menu 1.
- Listing side (nurturing a past seller) → `Otto Workspace/Listings/{address-slug}/Post-Close/`
- Buy side (nurturing a past buyer) → `Otto Workspace/Buyers/{family-name}/Post-Close/`

Always run the lookup-before-create check first. If the parent `Listings/{slug}/` or `Buyers/{family}/` folder doesn't exist (common when starting nurture for a pre-Otto client), create a minimal stub parent and nest Post-Close inside it. Do NOT create a top-level `Post-Close/` folder — that no longer exists.

**Batch intake:**

*Closing basics*
- Client name(s)
- Property address
- Closing date
- Side (buyer or seller — or both if double-ended)
- Email + phone
- Birthday (month/day minimum)

*Nurture context*
- Significant dates to remember (closing anniversary, family birthdays, etc.)
- Occasions the client mentioned during the transaction (anniversary, kids' milestones, retirement, etc.)
- Any gift or pop-by style they mentioned liking

**Mass Production items (5):**

| # | Item | Template | Saves to |
|---|---|---|---|
| 1 | Closing congratulations email | `templates/emails/email_closing_congrats.md` | `01-Congrats/closing-congrats.md` |
| 2 | Referral request email (send ~2–3 weeks later) | `templates/emails/email_referral_request.md` | `02-Referral/referral-request.md` |
| 3 | Annual check-in email | `templates/emails/email_annual_checkin.md` | `03-Annual-Checkin/annual-checkin.md` |
| 4 | Birthday message (text + email variants) | `templates/emails/message_birthday.md` | `04-Birthday/birthday-message.md` |
| 5 | Occasion reminders doc for agent's calendar | `templates/checklists/reminders_client_occasions.md` | `05-Reminders/occasion-reminders.md` |

**One Time items:**
- Pop-by email (seasonal drop-off) → `06-Pop-By/pop-by-email-{season}.md`

---

## The menu flow

The exact menu tool calls are specified in `SKILL.md` under "Main menu (via AskUserQuestion)". It is a **3-step flow (4 steps when working on a single one-time item inside the New Listing branch):**

1. **Menu 1 — Side.** Listing or Buyer. Under Contract and Post-Close are stages *within* a side, never their own top-level choice.
2. **Menu 2 — Stage.** New Listing/Buyer Package, Under Contract, or Post-Close & Nurture.
3. **Menu 3 — Action.** Full package or one of that side+stage's one-time items.
4. **Menu 4 — Listing one-off (conditional).** Only shown when the agent picked "Work on a single one-time item" in the Listing → New Listing branch of Menu 3, because that branch has 4 one-time items and can't fit them all alongside "Full package" in a single 4-option menu.

If the agent picks "Full package" at Menu 3, begin that package's batch intake using the intake questions in this file. If they pick a specific one-time item (at Menu 3 or Menu 4), skip batch intake and ask only for the details that specific template needs.
