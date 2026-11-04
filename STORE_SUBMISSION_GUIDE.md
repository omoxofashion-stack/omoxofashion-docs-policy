# Chrome Web Store: copy-paste answers

Everything below is in English because the Store dashboard needs it.
Replace [Your Brand], URLs, etc. Answer ONLY what is true for your setup.

---

## 1. Listing tab

**Name** (max 75 chars)
Keyword Matcher: Sponsored Product Suggestions

**Summary** (max 132 chars; must equal manifest "description")
Shows one clearly labelled sponsored product suggestion on Google Search when your query contains specific product keywords.

**Detailed description**
```
Keyword Matcher shows ONE clearly labelled "Sponsored" product suggestion from [Your Brand]
above Google Search results, but only when your search contains specific product keywords
(for example: "gym vest").

HOW IT WORKS
- The extension reads the search text of Google & flipkart search pages (google.com / google.co.in / flipkart.com).
- It first checks the text inside your browser. If the text does not contain one of our product
  keywords (or contains a blocked keyword), nothing is sent anywhere.
- If it matches, the search text is sent over HTTPS to our server to pick the best product.
- The suggestion is always labelled "Sponsored". You can click "Why this ad?" for an explanation
  or "x" to dismiss it.

PRIVACY
- We do not sell your data and do not build advertising profiles.
- The search text is used only to choose the suggestion and is not stored by our server.
- Service providers used: Render (hosting) and Hugging Face (text-similarity scoring when there is no direct keyword match).
- Full policy: https://github.com/omoxofashion-stack/omoxofashion-docs-policy.git/

DISCLOSURE
This extension displays sponsored content for omoxofashion's own products. Contact: info@omoxofashion.co.in
```

**Category:** Shopping
**Language:** English
**Icon:** icons/icon128.png (from the extension folder)
**Screenshots:** 1280x800 (or 640x400). Show a Google results page with the "Sponsored" card clearly visible.
**Privacy policy URL / Website / Support email:** fill in your own.

---

## 2. Privacy practices tab

**Single purpose description**
```
Show one clearly labelled sponsored product suggestion from [Your Brand] on Google Search results
when the user's search contains specific product keywords.
```

**Permission justification: host permission (https://omoxo-products-embeddings-fortytwo.onrender.com/*)**
```
Needed to send the user's search text to the developer's product-matching server and receive the
matching product suggestion. Only searches that contain the developer's product keywords are sent.
```

**Permission justification: content script on Google Search pages**
```
Needed to read the search text on Google search result pages and to display the labelled sponsored
suggestion card on that page. No other sites are accessed.
```

**Remote code:** "No, I am not using Remote code."
(The extension loads no remote scripts; it only receives JSON data from the server.)

**Data usage: what user data do you collect?**
Tick every category that could apply. When in doubt, disclose MORE rather than less.
Most likely candidates for this extension: **Web history** and/or **User activity** and/or
**Website content** (because the search text comes from the Google search page URL).
Do NOT tick categories you do not handle (e.g. Health, Financial, Location, Authentication).

**Certifications (all three must be TRUE for you to tick them):**
- I do not sell or transfer user data to third parties, outside of the approved use cases
  (note: hosting providers and Hugging Face act only as your service providers)
- I do not use or transfer user data for purposes that are unrelated to my item's single purpose
- I do not use or transfer user data to determine creditworthiness or for lending purposes

**Privacy policy URL:** the public URL of privacy-policy.html (GitHub Pages, your website, etc.)

---

## 3. Test instructions (for reviewers)
```
1. Open https://www.google.com and search for: gym vest
2. A card labelled "Sponsored" appears above the results. Click "Why this ad?" to see the explanation,
   and "x" to dismiss it.
3. Search for: women vest, or: laptop bag  -> no card appears and nothing is sent to the server
   (the search does not match our keywords, or contains a blocked keyword).
Note: our server may take up to ~60 seconds to wake up on the first request.
```
Before submitting, open your Render URL once in a browser so the server is awake.

---

## 4. Pre-submit checklist
- [ ] config.js: API_BASE, BRAND_NAME, PRIVACY_POLICY_URL, INFO_TEXT, keywords filled in
- [ ] manifest.json host_permissions has your EXACT Render URL (no *.onrender.com, no 127.0.0.1)
- [ ] Privacy policy published at a public https URL; placeholders and the yellow "TEMPLATE NOTES" box removed
- [ ] Policy statements match reality (check server code: no query logging/storing)
- [ ] Extension tested via chrome://extensions > Load unpacked
- [ ] ZIP made from the files INSIDE the extension folder (manifest.json at the zip root)
- [ ] Screenshots show the "Sponsored" label
