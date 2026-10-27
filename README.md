# KedaiBuku.my data platform – TTTC3213 Data Engineering

Lab project for TTTC3213. KedaiBuku.my is a fictional Malaysian online bookstore; it has no real website.

## Getting started
1. Click **Use this template** → **Create a new repository**, name it `kedaibuku-de`, and choose **Private**.
2. In your new repository, click **Code** → **Codespaces** → **Create codespace on main**.
3. Wait 5–8 minutes for the first setup to finish ("Setup complete" in the Terminal).
4. Stop your codespace after every lab: **Codespaces** (bottom left) → **Stop Current Codespace**.
## Lab 1 answers
### Why is `.env.example` committed when `.env` is not?
`.env` stores real secrets like passwords and API keys, so it must be ignored by git to avoid leaking sensitive credentials.
`.env.example` only contains placeholder variable names without real secrets. It is committed so new team members know which environment variables the project requires.

## Lab 3 answers

### Step 4: What does one row mean in each file?
| File | One row means |
|---|---|
| `books.csv` | One book in the catalogue (title, price, rating, category, URL) |
| `customers.csv` | One registered customer (name, email, phone, MyKad, state) |
| `orders.csv` | One order — one customer buying one book on one date |
| `reviews.csv` | One review — one customer's star rating and text about one book |

### Which columns link the files together?
- **`book_id`** links `books`, `orders`, and `reviews`.
- **`customer_id`** links `customers`, `orders`, and `reviews`.

### Which columns hold personal data (PII)?
- `customers.full_name`, `customers.email`, `customers.phone`, `customers.mykad` (MyKad number), `customers.state`
- `reviews.review_text` — about 2% of reviews accidentally leak a phone number in free text
- `orders.customer_id` and `reviews.customer_id` are identifiers that point to PII but are not PII themselves

### Which source do you collect once, and which every day?
- **Collect once (or rarely):** the book catalogue from `books.toscrape.com` — it is a static catalogue that changes infrequently.
- **Collect every day:** the GBP→MYR exchange rate from the BNM API — rates change daily.
- **Collect every day (growing continuously):** customers, orders, and reviews — these are transactional records that keep arriving as the shop operates.
