# CEM888.AI — Landing Page & Signup Legal Requirements

**Last Updated: September 8, 2026**

What must appear on the public site and at signup so every new user enters a
binding agreement and CEM888's IP is claimed on first contact. Each item is
marked **[DONE]** or **[TODO]** with the live implementation status.

---

## A. Landing Page (visible without an account)

### A1. Copyright + trademark footer strip — **[TODO — must add]**
A footer line visible on every public page:

> © 2026 CEM Unlimited LLC. All rights reserved. CEM888.AI™ and the Eye of
> Horus mark are trademarks of CEM Unlimited LLC.

Rationale: statutory copyright notice (© + year + owner) defeats an
"innocent infringement" defense under 17 U.S.C. § 401(d), and the ™ notice
publicly claims the common-law mark (free — no registration needed yet).

### A2. Legal links in footer — **[TODO — must add]**
Links to: **Terms of Service** · **Privacy Policy** · **EULA** ·
**Early-Access/Beta Agreement**. Required so every visitor has a path to the
contract before they sign up.

### A3. Above-the-fold marketing disclaimer (AI claims) — **[TODO — recommended]**
One line near any "consciousness / personality / autonomous agent" claim:

> CEM888 agents are AI software. They may make mistakes. You are responsible
> for directing them and validating their actions.

Cuts FTC deception risk (claims that overstate AI capability) and feeds the
contractual assumption-of-risk language.

### A4. Subscription auto-renewal disclosure at checkout — **[TODO — must add]**
Wherever a price is shown ($29/mo) and at the Stripe checkout:

> Billed $29.00/month until cancelled. Subscriptions auto-renew. Cancel
> anytime — access continues to the end of the billing period.

Required by FTC ROSCA (Restore Online Shoppers' Confidence Act): clear and
conspicuous disclosure of recurring charges BEFORE payment, plus an easy
cancellation path. This is the single most likely regulator/chargeback
vector for a subscription product — put it directly above the pay button.

### A5. DMCA / IP contact — **[TODO — add to footer or Terms]**
"legal@cem888.ai" for copyright complaints. (Details live in ToS §15.)

---

## B. Registration / Signup (the binding moment)

### B1. Clickwrap checkbox — **[DONE — implemented 2026-09-08 in register.html]**
Before the submit button, a REQUIRED checkbox with a link (not just text):

> ☐ I have read and agree to the Terms of Service, the Privacy Policy, and
> the End User License Agreement. I am 18 or older.

Submit button is **disabled until checked** (that's what makes it a valid
clickwrap — the user must affirmatively act). Unchecked = no contract = no
liability shield.

### B2. Risk assumption at signup — **[DONE — implemented 2026-09-08 in register.html]**
A short acknowledgment under the checkbox, plain-English:

> By creating an agent you direct its actions. You are responsible for what
> you instruct it to do, including file, system, and account actions, and you
> accept the risk of agent mistakes or data loss.

Mirrors ToS §6 and the EULA §3. Put the blunt version at signup so nobody can
claim surprise later.

### B3. Authority representation (business signups) — **[TODO — recommended]**
Checkbox or line for anyone registering on behalf of a company:

> I represent that I am authorized to bind the entity I register on behalf
> of.

(Kills the "I'm not authorized" defense in B2B disputes.)

---

## C. Enforcement note (how acceptance is proven)

Every signup should store, at minimum: email, timestamp, version/date of the
Terms accepted, and the fact the clickwrap box was checked. Keep this record
in the tenant record / dashboard DB (field: `legal_agreed_at`,
`legal_terms_version`). If there's no place to store it yet, the register
handler must capture it before CEM-151 is closed.

---

## D. Where the full contract stack lives

- Terms of Service → `/terms.html` (also `TERMS_OF_SERVICE.md` in the legal repo)
- Privacy Policy → `/privacy.html` (also `PRIVACY_POLICY.md`)
- EULA → new page `/eula.html` **[TODO — needs to be added + linked]**
- Early-Access/Beta Agreement → new page `/beta.html` **[TODO — needs to be added + linked]**
- Proprietary LICENSE → `LICENSE.md` in the legal repo + packaged with installers
