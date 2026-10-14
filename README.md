# 1688 Finder

The GitHub Pages frontend searches through a Cloudflare Worker proxy. Real results require a TMAPI account/API key; the website never exposes that key.

## Deploy the backend
1. Get an API key from https://console.tmapi.io/ and check the provider's pricing/limits.
2. Install Node.js and Wrangler: `npm install -g wrangler`
3. In the `worker` directory, run `wrangler login`, then `wrangler deploy`.
4. Add the secret with `wrangler secret put TMAPI_KEY` (run from the worker directory).
5. Copy the deployed Worker URL and set `window.PRODUCT_API_BASE` in `config.js` to that URL.

## Publish
Commit `index.html`, `config.js`, and the `worker/` directory to the `main` branch. GitHub Pages serves the frontend; Cloudflare Worker runs the private API proxy.

## Provider
The worker is written for TMAPI's documented 1688 keyword-search endpoint, `https://api.tmapi.top/1688/search/items`. It requires a valid TMAPI key and the provider response schema. Authenticated live results have not been verified in this repository.
