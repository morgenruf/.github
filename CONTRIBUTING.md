# Contributing

Applies to every repository in the Morgenruf organisation.

Contributions are welcome, including small ones. Fixing a confusing error message or
a wrong line in the docs is a real contribution.

## Before a large change

Open an issue first if the change is substantial. It is easier to agree on an approach
in a paragraph than in a five hundred line diff, and it avoids anyone spending an
evening on something that will not be merged.

Small and obvious fixes need no ceremony. Send the pull request.

## Running the bot locally

```bash
git clone https://github.com/morgenruf/morgenruf
cd morgenruf/app

python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
# Fill in the Slack credentials and set FLASK_SECRET_KEY to a real value:
#   openssl rand -hex 32

docker compose up -d db redis     # Postgres and Redis
python src/migrate.py             # apply migrations
python src/main.py
```

Slack needs to reach your machine, so point the app at a tunnel
(`ngrok http 3000`) and set `APP_URL` to that address.

## Tests

```bash
pytest -q                    # the whole suite
ruff check app/              # lint
ruff format app/             # format
```

Two things the CI will check that are easy to miss locally:

**Run the file you changed on its own**, not only as part of the suite. Several test
modules stub `sys.modules` entries, and a module that passes inside the full run can
fail alone once the ordering changes.

**Make a new test fail before you make it pass.** A test that passes against the
unfixed code is not testing the fix. If you are fixing a bug, the pull request should
be able to say what the test did before the change.

## Pull requests

- One concern per pull request. Unrelated cleanups make review harder and bisecting worse.
- Explain the why in the description. The diff already shows the what.
- Conventional commit style for the title: `fix:`, `feat:`, `docs:`, `chore:`, `refactor:`.
- Say what you did not do. A known gap that is written down is a decision; the same gap
  left unmentioned is a surprise.

Do not add AI attribution trailers or co-author lines for tools. The commit history
should read as the work of the people in it.

## What review looks for

Correctness first, then whether the change is understandable a year from now.

Expect questions about error paths and edge cases: what happens when Slack is
unreachable, when the token has expired, when the workspace has one member or two
hundred. Most of the awkward bugs in this codebase have lived in exactly those gaps.

## Security

Do not open a public issue for a security problem. [SECURITY.md](SECURITY.md) explains
how to report privately.
