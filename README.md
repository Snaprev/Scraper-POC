## ✍️ Technical Assignment – BolScout Scraper Proof-of-Concept

*(single-person test – approx. 6-8 h effort)*

Hi Yogesh & Aditya,

Below is the **mini-challenge** we discussed in our first call, now **updated with the self-healing test site**.

---

### 1. Background

BolScout will hold **20 M+ products** from **bol.com**.

Some data comes from the official Seller API, but key fields (site price, reviews, listing tweaks) require scraping.

We need a **cloud-hosted scraper** that can:

1. Work **per product** *or* **per category**.
2. Detect & store **changes only** (price, stock, rating, review-count).
3. **Heal itself** when selectors / HTML change.
4. Run forever with minimal babysitting.

---

### 2. What to build for the test

| # | Requirement | Notes |
| --- | --- | --- |
| **1** | **Scraper** that accepts `MODE=product` *or* `MODE=category`. • `product` – crawl the EAN/URL we pass. • `category` – crawl the first 2 result pages of a category. | Any tech stack you like (Scrapy, Playwright, requests, etc.). |
| **2** | **Fields to collect**: EAN, title, price, availability, rating, review-count, first 3 review snippets. |  |
| **3** | **Change detector**: store previous snapshot in **SQLite** (or Postgres). Update a row only if a field changed. |  |
| **4** | **Self-healing demo** *(NEW)*: We’ll give you a **dummy site URL** whose HTML we control. Your scraper must extract a target field (e.g., price). After you demo success, we’ll **rename/shift the selector** and run again—scraper should adapt automatically (AI or rule-based) and still capture the field. | https://zp1v56uxy8rdx5ypatb0ockcb9tr6a-oci3--5173--55edb8f4.local-credentialless.webcontainer-api.io/ |
| **5** | **Cloud run**: Dockerfile + one-liner (Railway free tier). |  |
| **6** | **Anti-bot mitigation**: at least one technique (rotating UA, delay, proxy, stealth lib). |  |

*Optional bonus*: merge in bol.com API fields that don’t need scraping.

---

### 3. Deliverables

1. **Git repo** (we’ll send invite).
2. `README.md` – local run + Railway deploy instructions.
3. Railway link *or* `docker run` command.
4. Short screen-capture (<2 min) showing:
    - initial scrape → DB rows
    - dummy-site selector change → scraper heals → DB still correct.

---

### 4. Evaluation

| Weight | Focus |
| --- | --- |
| 40 % | Self-healing robustness (dummy-site test) |
| 25 % | Code clarity & structure |
| 20 % | Change-detection / DB logic |
| 10 % | Cloud deploy |
| 5 % | Anti-bot measures |

---

### 5. Timing

Please target **one week** after repo access. Ping us on LinkedIn if you’re blocked.

---

### 6. Good luck!

Show us how you keep a scraper alive even when the HTML rug gets pulled out.

We’re eager to see your solution.

— Adam, Jelino & Mohammed

BolScout Engineering
