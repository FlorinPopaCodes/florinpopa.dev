---
title: "educhk — Academic Domain Checker for the Edge"
description: "A lightweight npm package and Cloudflare Worker that checks if a domain belongs to an educational institution. O(1) lookups across 25,000+ domains."
date: 2026-02-08
---

I needed a fast way to check whether an email belongs to a university — at the edge, with zero latency overhead. The existing solutions were either too heavy, required network calls, or hadn't been updated in years.

So I built [educhk](https://github.com/FlorinPopaCodes/educhk).

## What it does

Given any domain, it tells you whether it belongs to a known academic institution:

```js
import { isAcademic } from 'educhk';

isAcademic('stanford.edu');        // true
isAcademic('cs.stanford.edu');     // true — walks up subdomains
isAcademic('gmail.com');           // false
isAcademic('alumni.stanford.edu'); // false — stoplist excluded
```

It covers 25,000+ educational domains sourced from [JetBrains Swot](https://github.com/JetBrains/swot), loaded into `Set` objects for O(1) lookups. No network calls, no database, no cold starts.

## The edge part

There's also a live API deployed as a Cloudflare Worker:

```bash
curl https://educhk.florin-popa-codes.workers.dev/stanford.edu
# {"domain":"stanford.edu","academic":true}
```

A daily GitHub Action syncs the latest Swot data, publishes a new npm version, and deploys the worker — so the domain list stays current without manual intervention.

## How it works

The domain data gets flattened into three JSON arrays: academic, abused, and stoplist. At runtime these become `Set` objects. The lookup function walks up subdomains — `cs.stanford.edu` checks `cs.stanford.edu`, then `stanford.edu`, then `edu` — until it finds a match or runs out of parents.

Stoplist domains (like `alumni.` subdomains) are excluded automatically, and commonly abused domains are flagged separately.

## Links

- [GitHub](https://github.com/FlorinPopaCodes/educhk)
- [npm](https://www.npmjs.com/package/educhk)
- [Live API](https://educhk.florin-popa-codes.workers.dev/stanford.edu)
