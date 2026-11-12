# aether.json

One file in the project folder points the scripts at a product. Only
`product.name` and at least one `intent.strong` or `intent.medium` phrase are
required; everything else has a safe default.

```json
{
  "product": {
    "name": "Ledgerly",
    "description": "Invoicing for freelancers: send, chase and reconcile in one place.",
    "audience": "freelancers and small studios",
    "price": "$12/month",
    "checkout_url": "https://ledgerly.example/pricing"
  },
  "site": {
    "base_url": "https://ledgerly.example/guides",
    "dir": "site",
    "title": "Freelance invoicing guides",
    "lede": "Specific answers on getting paid on time.",
    "author": "",
    "track_ref": true
  },
  "intent": {
    "strong": ["invoice not paid", "client won't pay", "late payment"],
    "medium": ["invoice template", "how to invoice", "payment reminder"],
    "weak": ["freelance", "client"],
    "negative": ["hiring", "we are looking for"]
  },
  "sources": {
    "hn_queries": ["freelance invoice", "client late payment"],
    "subreddits": ["freelance", "smallbusiness"],
    "stackexchange": ["freelancing"],
    "rss": []
  },
  "cta": {
    "title": "Stop chasing invoices: try {product}",
    "body": "Send, remind and reconcile automatically.",
    "button": "Start for {price}"
  }
}
```

| Field | Meaning |
|---|---|
| `product.checkout_url` | http(s) only. Empty: pages are published without a buy box. |
| `site.base_url` | Where the pages will be served. Empty: relative canonicals, no sitemap. |
| `site.dir` | Output folder inside the project. Use `docs` for GitHub Pages. |
| `site.track_ref` | Adds `utm_campaign=<page slug>` to the buy link, so the user's own checkout analytics show which page earned each sale. |
| `intent.strong` / `medium` / `weak` | Lower-case phrases a buyer in pain would type. Weights 3 / 2 / 1. Partial words match ("ats rejec"). |
| `intent.negative` | A post containing any of these scores 0 (job ads, vendors, spam). |
| `sources.stackexchange` | Site names, optionally `site:tag`. |
| `cta.*` | Buy box text. `{product}` and `{price}` are filled in. |

Choosing intent phrases: write what someone says when they have the problem,
not the product category. "invoice not paid" beats "invoicing software".
Start with 5-10 strong phrases; refine after the first `top` results.

`sources` map to `listen.py` flags: `hn_queries` to `--hn`, `subreddits` to
`--reddit`, `stackexchange` to `--se`, `rss` to `--rss`.
