---
title: "educhk — Academic Domain Checker for the Edge"
description: "A fast lightweight npm package and Cloudflare Worker that checks if a domain belongs to 25,000+ educational institutions."
date: 2026-02-19
---

I brainstormed a few ideas during the weekend and I remembered a domain list that allows you to check if a domain represents an educational institution so students can get free or discounted products.

What I've built lets anyone check any domain with a single request or a function import.

I decided to build this because we are at a moment where building what you want to see in the world is easy. Plus, this saves the next developer a few hours and students can access resources easier and faster.

As I was trying to build using Cloudflare Workers, I used an existing package to figure out the architecture. I had the choice between a reverse trie, a bloom filter and a simple set. After evaluating all the pros and cons, I chose the set.

My problem was that there wasn't a package on npmjs.com that I was happy with: all were either stale or unmaintained. So I built and published one.

This package differs from others: it exports only two methods. Most developers either check if an email is from an academic domain or flag domains that have historically exploited student discounts.

p50 under 1 millisecond, p95 around 4 milliseconds.

I've also decided to leave a public API available as this costs me almost nothing to run. But if you decide to use it and you're not building a side-project or an MVP, you should probably just host this yourself.

## Links

- [GitHub](https://github.com/FlorinPopaCodes/educhk)
- [npm](https://www.npmjs.com/package/educhk)
- [Live API](https://educhk.florin-popa-codes.workers.dev/stanford.edu)
