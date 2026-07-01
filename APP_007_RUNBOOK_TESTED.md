# App 007 — Series B Discovery Lead Engine
## Complete Runbook (Tested)

**Last Updated:** 2026-07-01  
**Status:** Live at https://ericrayburn.github.io/iam-tools/discovery.html  
**File:** discovery.html (no backend, no server, no cost)

---

## What This App Does

App 007 converts news articles about Series B funding into outreach prompts for Claude. It has three modes:

1. **Article Analysis** — Read an article, score the fit, suggest next action
2. **Decision Maker** — Identify the best contact and generate LinkedIn search URLs
3. **LinkedIn Outreach** — Generate a complete 5-message LinkedIn sequence

The app does mechanical work (extract, format, link-build). Claude does judgment (read, evaluate, write).

---

## Quick Start (5 minutes)

### Step 1: Install Grab Article (one time only)

1. Open the app: https://ericrayburn.github.io/iam-tools/discovery.html
2. Scroll down to "Step 1 — Open a source and grab the article"
3. Drag the yellow **⬇ Grab Article** button to your browser bookmarks bar
4. You now have a bookmarklet. You are done with this step forever.

### Step 2: Use Article Analysis Mode

1. Find a funding news article (TechCrunch, Crunchbase, Built In, or any source)
2. Click the **Grab Article** bookmarklet from your bookmarks bar
   - A toast notification says "Article copied. Paste into Discovery."
3. Return to the app. Press Ctrl V into the "Article text" box
   - The article title, URL, and body paste automatically
4. (Optional) Paste the article URL into the "Article URL" field
5. Click **Build Prompt**
   - The right panel fills with a structured prompt
   - The prompt auto-detects: Series stage, funding amount, company name, signal tags
6. Click **Copy Prompt to Claude**
7. Paste into a Claude session with Series B Discovery context loaded
8. Claude outputs: news hook, fit check, signal score, tag, next step

### Step 3: Move to Decision Maker (if fit passes)

1. Click the **Decision Maker** tab
2. The company and tag auto-fill from Article Analysis (if you detected them)
3. Fill pain signal (e.g., "manual provisioning", "orphan accounts", "MFA gaps")
4. Click **Build Prompt**
5. Click **Copy Prompt to Claude**
6. Claude outputs: primary target role, multithread ladder, LinkedIn search URLs
7. Copy the URLs from Claude output

### Step 4: Move to LinkedIn Outreach (with a contact)

1. Click the **LinkedIn Outreach** tab
2. Fill all fields:
   - **Company** (auto-filled from earlier)
   - **Contact name** (from LinkedIn search results)
   - **Role** (from their LinkedIn profile)
   - **Tag** (auto-filled from earlier)
   - **Pain signal** (from Decision Maker step)
   - **Funding hook** (round, source, date, use of funds — from article)
   - **Recent post topic** (something they posted about recently)
3. Click **Build Prompt**
4. Click **Copy Prompt to Claude**
5. Claude outputs a 5-part LinkedIn sequence:
   - 3 warm-up comments
   - Connection note
   - Day 3 technical message
   - Day 10 financial message
   - Day 17 break-up message

---

## How the Grab Article Bookmarklet Works

The bookmarklet is a single JavaScript line stored in the href of the yellow button. When you click it on any news site:

1. It looks for article text in these selectors (in order):
   - `<article>` tag
   - `<main>` tag  
   - `[role=main]` attribute
   - `.article-body` class
   - `.post-content` class
   - `.entry-content` class
   - `.article__body` class
   - `.story-body` class
   - Falls back to the `<div>` with the most paragraph text

2. It extracts:
   - The page `<h1>` title (or fallback to `document.title`)
   - The current URL
   - All paragraph text

3. It formats as:
   ```
   [HEADLINE]
   
   SOURCE: [URL]
   
   [ARTICLE BODY]
   ```

4. It copies to your clipboard using `navigator.clipboard` (modern browsers) or fallback textarea method

5. Shows a toast: "Article copied. Paste into Discovery."

**If the bookmarklet fails on a site:**
- The site's HTML structure is unusual
- Use Edge's **F9 reader view** as a fallback: Press F9, Ctrl A, Ctrl C, then paste into app
- Or manually copy/paste the article text

---

## Detailed Workflows

### Workflow 1: Article Analysis

**What it does:**  
Reads a news article about a Series B company. Outputs fit check, signal score, tag recommendation, and next action.

**Inputs:**
- Article URL (optional) — the news link you grabbed from
- Article text (required) — full article body

**Outputs:**
1. **NEWS HOOK** — Company | Round | Source | Date | Use of funds (one line)
2. **FIT CHECK** — Stage, headcount, location, verdict (PASS or FAIL)
3. **SIGNAL SCORE** — 5 IAM/HR signals scored 0–5, marked visible or needs verification
4. **TAG** — Suggested package (PKG1, PKG2, PKG3, or Multi)
5. **NEXT STEP** — If PKG/Multi: move to Decision Maker. If WATCH: recheck in 7 days. If SKIP: archive.

**Auto-detection:**  
When you paste an article, the app auto-detects:
- Funding round (Series A/B/C)
- Amount ($X million/billion)
- Company name
- Signal tags (based on keywords: SOC2, provisioning, SaaS, etc.)

You see these in the "Detected" line below the article box.

### Workflow 2: Decision Maker

**What it does:**  
Given a company and pain signal, identify the best first contact and generate LinkedIn search URLs.

**Inputs:**
- Company (usually auto-filled from Article Analysis)
- Tag (PKG1/PKG2/PKG3/Multi — auto-filled from Article Analysis)
- Pain signal (e.g., "manual provisioning", "orphan accounts", "MFA gaps")

**Outputs:**
1. **PRIMARY TARGET** — Best entry role for this tag + reason
   - PKG1 (SaaS sprawl): Head of IT first, VP Engineering second
   - PKG2 (provisioning): VP Engineering first, Head of IT second
   - PKG3 (SOC2/MFA): CISO or Head of Security
2. **MULTITHREAD LADDER** — Fallback order if primary goes silent
3. **LINKEDIN SEARCH URLS** — 5 people search URLs, one per role

**LinkedIn URLs:**  
The app auto-generates LinkedIn search links for:
- VP Engineering
- CTO
- Head of Security
- Head of IT
- Director of Platform

Click any URL to search LinkedIn for that role at the company.

### Workflow 3: LinkedIn Outreach

**What it does:**  
Generate a complete 5-message LinkedIn sequence to warm up and pitch a contact.

**Inputs:**
- Company (auto-filled)
- Contact name (first and last name, from LinkedIn)
- Role (their title, from LinkedIn)
- Tag (auto-filled)
- Pain signal (auto-filled from Decision Maker)
- Funding hook (Series B, TechCrunch, 2026-05, hiring + platform)
- Recent post topic (something they posted about recently)

**Outputs:**
1. **WARM UP COMMENTS** (3 options) — Add numbers, counter-examples, or questions. Spread over 5–7 days.
2. **CONNECTION NOTE** (under 300 chars) — Open with the news hook. No congrats. Ask the tag opening question.
3. **DAY 3 — TECHNICAL** (under 100 words) — Name the architecture pain. Offer the case study.
4. **DAY 10 — FINANCIAL** (under 100 words) — Frame the cost of inaction. Offer the $2,500 48-hour audit.
5. **DAY 17 — BREAK UP** (one short message) — Permission to stop. Leave the door open.

**Tag Reference (built into app):**
- PKG1 (Identity Audit, $4,500): "How many ghost accounts do you think you carry?"
- PKG2 (Identity Engine, $12,000): "How long does it take to provision a new hire today?"
- PKG3 (Identity Fortress, $18,000): "When is your audit window and what MFA gaps did your last review surface?"
- Multi: Lead with PKG1, note PKG2 and PKG3 as upsell

---

## Source Sites (21 metros)

The app has 21 pre-loaded news sources by metro. Click any source link to open it in a new tab.

**National:**
- TechCrunch Fundings
- Crunchbase News
- FinSMEs

**By Metro:**
- NYC: AlleyWatch, Built In
- Boston: Boston Inno, Built In
- Austin: Austin Inno, Built In
- Chicago: Chicago Inno, Built In
- Dallas: Dallas Innovates
- Miami: Refresh Miami
- Atlanta: Hypepotamus
- Raleigh-Durham: WRAL TechWire, GrepBeat
- Charlotte: WRAL TechWire
- DC: Technical.ly, DC Inno
- Philadelphia: Technical.ly
- Pittsburgh: Technical.ly, Pittsburgh Inno
- Nashville: Nashville Inno
- Minneapolis-St. Paul: Tech.mn
- Indianapolis: TechPoint, IBJ Technology
- Detroit: Crain's Detroit

---

## Editing the App

### Add or Remove Source Sites

Edit the `SOURCE_SITES` array in discovery.html (lines 277–299).

**To add a site:**
```javascript
{ name: 'Site Name', url: 'https://...', metro: 'City or All' }
```

**To remove a site:**  
Delete the line for that site.

**To change a site:**  
Update its `name`, `url`, or `metro` value.

Then save and commit:
```bash
cd C:\Users\<username>\Documents\iam-tools
git add discovery.html
git commit -m "Update discovery sites"
git push
```

GitHub Pages updates within 1 minute. Test at the live URL.

### Edit the Prompts

The three prompts are in functions:
- `buildArticle()` (lines 332–373)
- `buildDecision()` (lines 375–403)
- `buildOutreach()` (lines 405–437)

To change a prompt, edit the string inside the function. Keep the input placeholders (e.g., `${company}`, `${tag}`).

Save and commit as above.

---

## Writing Constraints (Built In)

All prompts include these constraints. They are automatically appended to every prompt sent to Claude:

```
WRITING CONSTRAINTS
- No hyphens in compound modifiers. Active voice only. No contractions.
- Twenty words per sentence maximum. Clinical, peer level tone.
- News hook format: round, source, date, stated use of funds. No congrats.
- Banned terms: [30+ terms listed]
```

---

## Troubleshooting

### Grab Article bookmarklet doesn't copy

**Why:** The site's HTML structure is unusual, or the bookmarklet isn't in your bookmarks.

**Fix:**
1. Re-drag the yellow button to your bookmarks bar
2. Or use Edge's F9 reader view: Press F9, select all (Ctrl A), copy (Ctrl C)
3. Or manually copy/paste the article text

### App doesn't populate company or tag

**Why:** The article text didn't match detection patterns.

**Fix:**
1. Manually type the company name in the Company field
2. Manually select the tag from the dropdown
3. Detection is only a convenience; manual entry works fine

### LinkedIn URLs don't generate

**Why:** You're not in Decision Maker mode, or Company field is empty.

**Fix:**
1. Click the **Decision Maker** tab
2. Fill the Company field
3. Click **Build Prompt**
4. LinkedIn URLs appear below the output

### Copy button doesn't work

**Why:** Rare clipboard permission issue or browser doesn't support `navigator.clipboard`.

**Fix:**
1. Try again (transient issue)
2. Or manually select the output, Ctrl C, paste into Claude

### Bookmarklet breaks after an update

**Why:** You updated the file but the old bookmarklet code is still in your bookmarks.

**Fix:**
1. Delete the old bookmarklet from your bookmarks
2. Re-drag the new yellow button to your bookmarks bar

---

## Testing Checklist

### Test Article Analysis

- [ ] Open app, click Grab Article bookmarklet from bookmarks
- [ ] Grab a TechCrunch or Crunchbase article
- [ ] Verify "Article copied" toast appears
- [ ] Return to app, Ctrl V into Article box
- [ ] Verify title, URL, and body appear
- [ ] Verify "Detected" line shows round, amount, company, tag
- [ ] Click Build Prompt
- [ ] Verify output has 5 blocks: hook, fit check, signals, tag, next step
- [ ] Click Copy Prompt to Claude
- [ ] Verify text is on clipboard (paste into Notes or email)

### Test Decision Maker

- [ ] Click Decision Maker tab
- [ ] Verify Company and Tag auto-filled from Article mode
- [ ] Type a pain signal (e.g., "manual provisioning")
- [ ] Click Build Prompt
- [ ] Verify output has 3 blocks: primary target, multithread ladder, LinkedIn URLs
- [ ] Verify 5 LinkedIn search URLs appear below output
- [ ] Click one LinkedIn URL, verify it searches for that role at the company

### Test LinkedIn Outreach

- [ ] Click LinkedIn Outreach tab
- [ ] Verify Company and Tag auto-filled
- [ ] Fill Contact name, Role, Funding hook, Recent post topic
- [ ] Click Build Prompt
- [ ] Verify output has 5 sections: warm-up, connection, day 3, day 10, day 17
- [ ] Click Copy Prompt to Claude
- [ ] Verify text is on clipboard

### Test Tab Switching

- [ ] Click each tab: Article Analysis, Decision Maker, LinkedIn Outreach
- [ ] Verify correct fields show/hide per tab
- [ ] Verify Company and Tag persist across tabs
- [ ] Click Clear button
- [ ] Verify all fields empty and Detected line clears

### Test Mobile Responsiveness

- [ ] Resize browser to 375px wide (mobile)
- [ ] Verify layout stacks vertically (not side-by-side)
- [ ] Verify buttons and inputs are clickable
- [ ] Verify text is readable

---

## Known Limitations

1. **Bookmarklet extraction** — Site-specific HTML. F9 reader view is the fallback.
2. **Auto-detection** — Looks for keywords (Series B, SaaS, SOC2, etc.). Manual entry always works.
3. **LinkedIn URLs** — Generic search. Filter results by location, company size, etc. on LinkedIn.
4. **Prompt length** — Outputs are 300–600 words. Claude's context handles them fine.
5. **No authentication** — App is public. Never paste passwords or secrets. No data is sent anywhere.

---

## Context to Load in Claude

When you paste a prompt from this app into Claude, always load this context first:

```
Series B Discovery — Lead Engine context.

You are helping with cold outreach discovery for Series B companies.
The target ICP: 50–600 employees, regulated industry (BFSI, healthcare, tech), must pass SOC2/HIPAA/SOX/ISO 27001.
The niche: Machine identity governance on Microsoft Entra for regulated mid-market.
Use Sonnet for speed on outreach generation tasks.
```

---

## Guardrails

- **This repo is public.** Never place credentials, emails, passwords in any file.
- **Source list is the only routine edit.** Leave prompts and bookmarklet alone unless you have a reason to change them.
- **Test after edits.** Push to GitHub, wait 1 minute, verify at the live URL.
- **No API keys, no backend.** The app runs 100% in your browser. No tracking, no logs.

---

## Support

If something breaks:
1. Check the browser console (F12 → Console tab) for JavaScript errors
2. Re-drag the Grab Article bookmarklet to your bookmarks
3. Clear browser cache and reload the page
4. Open the file locally: `C:\Users\<username>\Documents\iam-tools\discovery.html`
5. Contact: Check DISCOVERY_RUNBOOK.md for the original setup steps