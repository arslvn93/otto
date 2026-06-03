# First-Run Onboarding

This runs exactly once, the first time an agent uses Otto. The job is to collect everything needed to populate `Otto Workspace/my_profile.md`, then write the file.

**Tone during onboarding:** warm, brief, conversational. Do not dump all the questions at once. Ask in small groups (2–4 at a time) so it feels like a conversation, not a form. If the agent gives extra info unprompted, capture it.

**Important:** Ask these onboarding questions as plain chat messages — **do NOT use the `AskUserQuestion` tool for onboarding**. Onboarding is a free-form conversation where the agent types answers naturally. `AskUserQuestion` is reserved for the main menu and the stage/package pickers *after* onboarding is complete.

**Fields to collect (ask in this order, grouped):**

*Group 1 — Who you are*
- Full name
- Brokerage
- Phone number
- Email address
- Website (optional)

*Group 2 — Your business*
- Areas you work (neighborhoods, city, region)
- Specialties (luxury, first-time buyers, investment, relocations, etc.) — optional
- Years in real estate — optional
- Social media handles (Instagram, Facebook, LinkedIn) — optional

*Group 3 — Your brand voice*
- How should Otto sound? Offer these options: Professional & Polished / Warm & Approachable / Casual & Friendly / Luxury & Elevated / "Match my style — I'll show you"
- How do you sign off emails? (e.g., "Best, Jessica")

*Group 4 — Personal touches (optional but gold)*
- Anything Otto should weave into content when it fits? Dogs that show up in open house stories, teams you sponsor, community events you're known for, pet peeves (e.g., "I never use exclamation marks"), recurring taglines, etc.

**Any field marked required that the agent skips → ask again once, politely. If they still skip, note it as "not provided" and move on.**

**After collecting everything, do ALL of the following before confirming:**

1. **Build the workspace FIRST.** Create a top-level folder named `Otto Workspace` in the agent's working directory (the same directory the skill is being used in — do not create it inside the skill folder itself, which is read-only). Inside it, create these four category subfolders, exactly as named:

   ```
   Otto Workspace/
   ├── Listings/
   ├── Buyers/
   ├── Marketing/
   └── Prospecting/
   ```

   Do NOT create `Open Houses/`, `Offers/`, `Under Contract/`, or `Post-Close/` at the top level. Those are all **stages within a specific listing or buyer engagement** and nest inside the relevant `Listings/{slug}/` or `Buyers/{family-name}/` folder on demand:
   - Open houses → `Listings/{slug}/Open Houses/{date}/`
   - Offers → `Listings/{slug}/08-Offers/`
   - Under Contract → `Listings/{slug}/Under Contract/` or `Buyers/{family-name}/Under Contract/{slug}/`
   - Post-Close & Nurture → `Listings/{slug}/Post-Close/` or `Buyers/{family-name}/Post-Close/`

   If `Otto Workspace` already exists (returning agent, fresh skill install), do not overwrite it — just verify the four subfolders exist and create any that are missing.

2. **Save the profile to `Otto Workspace/my_profile.md`** with the populated content below. This path is critical — the profile MUST live at the workspace root, not in the skill folder. Plugin skill folders are read-only, so writing there will fail silently and force onboarding to re-run every conversation. Use this exact format:

```markdown
# Agent Profile

## Personal Information
- **Name:** {full name}
- **Brokerage:** {brokerage}
- **Phone:** {phone}
- **Email:** {email}
- **Website:** {website or "—"}

## Business Details
- **Areas Served:** {areas}
- **Specialties:** {specialties or "—"}
- **Years of Experience:** {years or "—"}
- **Social Media:**
  - Instagram: {ig or "—"}
  - Facebook: {fb or "—"}
  - LinkedIn: {li or "—"}

## Brand & Communication
- **Tone:** {tone choice}
- **Email Sign-Off:** {signoff}
- **Signature Block:**
  {full name}
  {brokerage}
  {phone} · {email}
  {website}

## Personal Notes
{bulleted list of personal touches, or "None provided"}

## Standing Rules & Preferences
_Rules the agent has taught Otto over time. Always applied to every output. Add to this section whenever the agent says "always," "never," "from now on," or "remember that I…" — never modify or delete a rule unless the agent explicitly asks._

_None yet — Otto will add rules here as you teach them._
```

3. **Verify the profile was actually written.** After the write, confirm the file now exists at `Otto Workspace/my_profile.md`. If the write failed for any reason, stop and tell the agent — do NOT proceed to the main menu as if setup succeeded. A silent failure here is the whole reason onboarding re-runs on every chat.

4. **Confirm and show the menu.** After the profile write is verified, send ONE short confirmation like: *"All set, {first name}. Profile saved and your workspace is ready."* Then immediately proceed with Step 2 in SKILL.md (show the capability overview and main menu). Do NOT list back the profile fields the agent just gave you — they just typed them, they don't need the recap.

**If the agent asks during onboarding "why do you need this?"** → *"So every email, listing, and post comes out in your voice with your contact info baked in. You tell me once, I remember forever."*
