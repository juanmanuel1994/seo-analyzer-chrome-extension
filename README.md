# SEO Analyzer — Chrome Extension

A Manifest V3 Chrome extension that performs on-page SEO analysis and gives you an instant visual score with a categorized list of issues.

---

## Features

| Check | What it detects |
|---|---|
| **Title tag** | Missing, too short (< 30 chars), too long (> 60 chars) |
| **Meta description** | Missing, too short (< 70 chars), too long (> 160 chars) |
| **H1 heading** | Missing or multiple H1 tags |
| **H2 headings** | Missing H2 structure |
| **H3 headings** | Listed for reference |
| **Canonical tag** | Missing `<link rel="canonical">` |
| **Images without alt** | Every `<img>` lacking an `alt` attribute |
| **Internal links** | Detected internal links (up to 30) |
| **External links** | Detected external links (up to 30) |

**Score:** 0–100 calculated from weighted penalties across all checks.

**Design:** Dark theme with red / yellow / green indicators per category.

---

## Installation (2 minutes)

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer mode** (toggle in the top-right corner)
3. Click **Load unpacked**
4. Select the `seo-analyzer` folder (this folder)
5. The SEO Analyzer icon appears in your toolbar — pin it for quick access

---

## How to use

1. Navigate to any webpage
2. Click the **SEO Analyzer** icon in the toolbar
3. The popup opens and analyzes the page instantly
4. Use the **refresh button** (↺) to re-analyze after page changes

### Reading the results

- **Score ring** — overall SEO health (green ≥ 80, yellow ≥ 50, red < 50)
- **Category rows** — click any category to expand / collapse its details
- **Dots** — green = OK, yellow = warning, red = error
- **Char counts** — shown inline for title and meta description

---

## Score breakdown

| Check | Max penalty |
|---|---|
| Missing title | −25 |
| Missing meta description | −20 |
| Missing H1 | −20 |
| Multiple H1s | −10 |
| Missing canonical | −10 |
| Images without alt | up to −15 |
| Missing H2 | −5 |
| No links | −5 |

---

## File structure

```
seo-analyzer/
├── manifest.json       # Manifest V3 config
├── content.js          # Injected into the page — collects SEO data
├── popup.html          # Extension popup UI
├── popup.css           # Dark theme styles
├── popup.js            # Score engine + rendering
├── generate-icons.js   # Icon generator (Node script, already run)
├── icons/
│   ├── icon16.png
│   ├── icon32.png
│   ├── icon48.png
│   └── icon128.png
└── README.md
```

---

## Permissions used

| Permission | Why |
|---|---|
| `activeTab` | Read the URL of the current tab |
| `scripting` | Inject the content script to analyze DOM |

No data is sent anywhere. Everything runs locally in your browser.

---

## Browser support

Chrome 88+ (Manifest V3 minimum). Also works in Edge (Chromium-based).
