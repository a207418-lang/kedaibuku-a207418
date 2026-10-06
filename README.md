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
