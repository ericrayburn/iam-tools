# Discovery Lead Engine — Operator and Edit Runbook

This file is self contained. A fresh Claude chat reads this file plus `discovery.html` and executes. No memory search. No reference to any prior chat.

---

## What the app is

- One file: `C:\Users\Administrator\Documents\iam-tools\discovery.html`.
- It runs in the browser. No server. No cost. It calls no API.
- Live URL once pushed: `https://ericrayburn.github.io/iam-tools/discovery.html`.
- It builds a prompt from your inputs. You paste the prompt into Claude. Claude writes the outreach.

## How you use it each time

1. Click the source link for the metro. The news site opens.
2. Click the **Grab Article** bookmarklet. The article body copies to your clipboard.
3. Return to the app. Press Ctrl V into the Article box.
4. Pick a prompt tab: Article Analysis, Decision Maker, or LinkedIn Outreach.
5. Press **Build Prompt**. Press **Copy Prompt to Claude**.
6. Paste into a Claude session with Series B Discovery context. Use Sonnet.

The Grab Article button installs once. Drag the yellow button to your bookmarks bar. After that, one click on any site copies the article.

---

## EDIT THE SOURCE SITES — what to tell Claude in a new chat

The site list lives inside `discovery.html`, between the markers `START EDIT` and `END EDIT`, in the array `SOURCE_SITES`. Each entry has three fields: `name`, `url`, `metro`.

Open a fresh chat. Paste one of the blocks below. Claude needs nothing else.

### Add a site
```
Read C:\Users\Administrator\Documents\iam-tools\discovery.html.
Find the SOURCE_SITES array between START EDIT and END EDIT.
Add this entry, keep the formatting aligned, change nothing else:
  name: [SITE NAME]
  url: [FULL https URL of the page I browse]
  metro: [which of the 16 metros it covers]
Save the file. Show me the new line.
```

### Remove a site
```
Read C:\Users\Administrator\Documents\iam-tools\discovery.html.
In the SOURCE_SITES array, remove the entry whose name is [SITE NAME].
Change nothing else. Save the file. Confirm the removal.
```

### Change a site
```
Read C:\Users\Administrator\Documents\iam-tools\discovery.html.
In the SOURCE_SITES array, find the entry named [SITE NAME].
Change its [url OR metro] to [NEW VALUE]. Change nothing else. Save the file.
```

That is the whole job. The list is plain text. Claude edits one array and saves. No build step.

---

## EDIT THE PROMPTS — what to tell Claude

The three prompts live in `discovery.html` in the functions `buildArticle`, `buildDecision`, and `buildOutreach`. The source of truth for the wording is the four files in:
`C:\Users\Administrator\Documents\IAM_BIDDING\Series_B_Discovery\Prompt_*.md`.

To change a prompt:
```
Read C:\Users\Administrator\Documents\iam-tools\discovery.html.
Find the function [buildArticle / buildDecision / buildOutreach].
Edit the prompt text to match [what you want]. Keep the input placeholders.
Save the file.
```

If you change a `Prompt_*.md` file, tell Claude to sync the matching function so the two stay equal.

---

## REGENERATE THE GRAB ARTICLE BOOKMARKLET

The bookmarklet is the `href` on the link with `id="grabBtn"` in `discovery.html`. It is one line of JavaScript that starts with `javascript:`. It extracts the article body and copies it.

If a site reads wrong, the F9 reader view is the fallback. Press F9 in Edge, then Ctrl A, then Ctrl C.

To improve the extraction:
```
Read C:\Users\Administrator\Documents\iam-tools\discovery.html.
Find the link with id="grabBtn". Its href is the Grab Article bookmarklet.
The article selector list is the array named s inside that code.
Add this CSS selector to the front of that list: [selector].
Keep it one line. Save the file. After I push, I re-drag the button to my bookmarks bar.
```

After any bookmarklet change you must drag the button to your bookmarks bar again. The old bookmark holds the old code.

---

## PUBLISH A CHANGE

The app runs locally by opening the file. It also runs on GitHub Pages after a push.

```
cd C:\Users\Administrator\Documents\iam-tools
git add discovery.html DISCOVERY_RUNBOOK.md index.html
git commit -m "Update discovery sites"
git push
```

GitHub Pages updates within a minute. No secret ever goes in this repo.

---

## GUARDRAILS

- This repo is public. Never place an email password, app password, or credential in any file here.
- The site list is the only thing you edit for routine changes. Leave the rest alone.
- Keep `url` values to the page you actually browse, not an RSS feed. You read the page, not the feed.
