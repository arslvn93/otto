# First-Run Onboarding

This runs exactly once, the first time an agent uses Otto. The job is to collect the agent's profile via a form, build the workspace, and save the profile file.

---

## Step 1 — Show the onboarding form

Read the file `reference/onboarding_form.html` (in this skill's directory). Call the `show_widget` tool with:

- **title:** `otto_onboarding`
- **loading_messages:** `["Setting up your profile"]`
- **widget_code:** the exact contents of `onboarding_form.html` — do not modify the HTML in any way

Say one short warm line before the form, like: *"Before I can help, I need about two minutes to get to know you. Fill this out and I'll handle the rest."*

Then show the form. Do not ask any questions in chat. The form collects everything.

---

## Step 2 — Parse the response

When the agent submits the form, a structured message arrives in this format:

```
Agent profile — Full name: {value} · Brokerage: {value} · Phone: {value} · Email: {value} · Website: {value} · Areas: {value} · Specialties: {value} · Years: {value} · Instagram: {value} · Facebook: {value} · Linkedin: {value} · Tone: {value} · Signoff: {value} · Standing rules: {value}
```

Parse each field from this message. Any field left blank by the agent should be recorded as "—" in the profile.

If the agent clicked "Skip" instead of "Set up Otto", the message will say `(Skipped the form)`. In that case, ask the bare minimum in chat: name, brokerage, phone, email, and tone. Then proceed with the rest as "—".

---

## Step 3 — Build the workspace

Create a top-level folder named `Otto Workspace` in the agent's working directory (the same directory the skill is being used in — do not create it inside the skill folder itself, which is read-only). Inside it, create these four category subfolders, exactly as named:

```
Otto Workspace/
├── Listings/
├── Buyers/
├── Marketing/
└── Prospecting/
```

Do NOT create `Open Houses/`, `Offers/`, `Under Contract/`, or `Post-Close/` at the top level. Those are all stages within a specific listing or buyer engagement and nest inside the relevant `Listings/{slug}/` or `Buyers/{family-name}/` folder on demand.

If `Otto Workspace` already exists, do not overwrite it — just verify the four subfolders exist and create any that are missing.

---

## Step 4 — Write the profile

Save to `Otto Workspace/my_profile.md`. This path is critical — the profile MUST live at the workspace root, not in the skill folder. Plugin skill folders are read-only, so writing there will silently fail and force onboarding to re-run every conversation.

Use this exact format:

```markdown
# Agent Profile

## Personal Information
- **Name:** {full_name}
- **Brokerage:** {brokerage}
- **Phone:** {phone}
- **Email:** {email}
- **Website:** {website or "—"}

## Business Details
- **Areas Served:** {areas}
- **Specialties:** {specialties or "—"}
- **Years of Experience:** {years or "—"}
- **Social Media:**
  - Instagram: {instagram or "—"}
  - Facebook: {facebook or "—"}
  - LinkedIn: {linkedin or "—"}

## Brand & Communication
- **Tone:** {tone}
- **Email Sign-Off:** {signoff}
- **Signature Block:**
  {full_name}
  {brokerage}
  {phone} · {email}
  {website}

## Personal Notes
None provided

## Standing Rules & Preferences
{If the agent provided standing_rules, convert each rule into a bullet point. If empty, write the placeholder below.}
_None yet — Otto will add rules here as you teach them._
```

For the **Signature Block**: if the agent pasted a full multi-line signature in the signoff field, use that as-is for the signature block. If they only provided a short sign-off like "Best, Jessica", build the signature block from their contact info fields (name, brokerage, phone, email, website).

For **Standing Rules**: if the agent wrote rules in the form, split them into individual bullet points (one rule per line). Phrase each as a clear directive. For example, if they wrote "Never use en or em dashes. Always include school catchment in listings." save as:
- Never use en or em dashes in any output.
- Always include school catchment information in listing descriptions.

---

## Step 5 — Verify the write

After writing, confirm the file now exists at `Otto Workspace/my_profile.md` by calling Read on it. If the write failed for any reason, stop and tell the agent — do NOT proceed as if setup succeeded.

---

## Step 6 — Confirm and return to SKILL.md

Send one short confirmation: *"All set, {first name}. Profile saved and your workspace is ready."*

Then immediately return to SKILL.md Step 2 — show the capability overview and the main menu. Do not list back the profile fields — the agent just typed them, they don't need a recap.

**If the agent asks during onboarding "why do you need this?"** → *"So every email, listing, and post comes out in your voice with your contact info baked in. You tell me once, I remember forever."*
