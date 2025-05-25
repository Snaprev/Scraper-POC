## ✍️ Technical Assignment – BolScout Scraper Proof-of-Concept

Hi there,

This is the **final brief**. The pilot targets **bol.com only** (no MarketMentor references).

---

### 1. Background

BolScout will eventually store **≈ 50 million** bol.com products.

For the pilot we want to see how you scrape **10 000 Electronics products** in depth and prove the scraper can **self-heal** when bol.com changes its HTML.

---

### 2. Deliverable scope

| # | Must-have | Acceptance criteria |
| --- | --- | --- |
| **1** | **Scraper** with two modes | • `MODE=product` – crawl one product URL/EAN we pass.• `MODE=category` – crawl Electronics catalogue until **≥ 10 000 distinct products** are in the DB (handle pagination / infinite scroll). |
| **2** | **Data fields** per product | EAN, title, brand, current price, list price, availability, rating, review-count, main image URL, bullet specs **plus every review on page 1**: reviewer name, review title, review text, stars, review date. |
| **3** | **Change detection** | Store snapshots in **SQLite or Postgres**. On re-crawl update only changed columns; maintain `updated_at`. |
| **4** | **Self-healing demo** | We give you a **dummy site URL**. First run extracts a target price. We will then rename the selector; rerun without code edits → scraper still captures the price (AI or rule-based recovery). https://snazzy-kringle-73884f.netlify.app/ |
| **5** | **Cloud run** | Provide a Dockerfile plus a one-liner to deploy on Railway (free tier). Scraper should run until it reaches 10 k products, then idle or exit cleanly. |
| **6** | **Anti-bot measures** | At least one of: rotating User-Agent, proxy pool, request throttling, or stealth browser. |
| **7** | **Config** | Use ENV vars such as `BOL_CATEGORY`, `MAX_PRODUCTS`, `DB_URL`, etc. |

*Optional bonus*: fetch supplementary fields via the bol.com Seller API and merge them.

---

### 3. What to submit

1. **Git repo** with code and a clear `README.md`.
2. Railway service URL *or* `docker run …` command.
3. SQL dump / CSV proving **≥ 10 000 Electronics rows**, including review details.
4. Short screen-capture (< 2 min) that shows:
    - change detection in DB
    - dummy-site selector change → scraper self-heals successfully.

---

### 4. Evaluation weights

| Weight | Focus |
| --- | --- |
| 35 % | Robustness & self-healing (dummy-site test) |
| 25 % | Depth / correctness of 10 k-product dataset |
| 20 % | Code quality & clarity |
| 10 % | Cloud deployment & automation |
| 10 % | Anti-bot strategy |

---

### 5. Timeline

Repo invite today → **submission within 7 calendar days**.

Questions? Ping Mohammed on LinkedIn.

---

Good luck! We’re looking forward to seeing your solution.

— Adam, Jelino & Mohammed

BolScout Engineering
