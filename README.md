# NYC Museum Exhibitions

A listing of what's on at New York City museums. It updates itself every night.

## What's here

- `index.html` is the site. It reads `data/exhibitions.json`.
- `data/exhibitions.json` holds the listings.
- `collector/collect.mjs` reads each museum's exhibitions page, uses an AI model to pull out titles, dates, links and photos, and rewrites the listings file.
- `collector/venues.json` is the list of museums. Add a museum by adding a line.
- `.github/workflows/nightly.yml` runs the collector every night on GitHub.

## Setup

1. **Vercel.** In Vercel choose Add New, then Project, and import this repository. Leave every setting as it is and press Deploy. Vercel republishes the site whenever the listings file changes.
2. **AI key.** Create an API key at console.anthropic.com. In this repository on GitHub go to Settings, then Secrets and variables, then Actions, and add a secret named `ANTHROPIC_API_KEY`.
3. **First run.** On GitHub open the Actions tab, pick "Update listings" and press Run workflow. It takes a few minutes.

## When something breaks

If a museum's page can't be read, the run is marked failed and GitHub emails you. The site keeps showing that museum's listings from the last good run. Open the failed run to see which museum it was.

## Using Grok instead

Add a secret named `XAI_API_KEY`. Under Settings, Secrets and variables, Actions, Variables, add `AI_PROVIDER` set to `xai` and `AI_MODEL` set to the Grok model name.
