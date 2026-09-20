# INFO 2950-204 — Final Project

Shared workspace for our INFO 2950 final project, Section 204.

**Current phase:** Phase I — Project Brainstorming (due Sep 22, 2026)

## Team

| Name | NetID | GitHub |
|---|---|---|
| Richard Ballard | rpb233 | [@rbllrd](https://github.com/rbllrd) |
| Josephine Kelly | jnk56 | [@jx-56](https://github.com/jx-56) |
| Jason Choi | jc3697 | [@jc3697](https://github.com/jc3697-creator) |
| Orazio Petito | opp2 | [@oraziop26](https://github.com/OrazioP26) |

**Section mentors:** Jingruo Chen (jc3564) — added as collaborators on 09/20/2026.

## Layout

```
data/raw/          As downloaded or pulled. Never edited by hand.
data/interim/      Intermediate merges and partial cleaning
data/processed/    Analysis-ready tables
notebooks/         Exploration, one notebook per question
src/               Reusable code: API collectors, cleaners, join logic
docs/              Write-ups and meeting notes
reports/figures/   Exported plots
```

Nothing in `data/raw/` gets modified. All transformations happen in code, so any
result can be regenerated from the original pull.

## Dataset ideas (Phase I)

| # | Idea | Sources | Join key |
|---|---|---|---|
| 1 | Fundraising composition and cosponsorship behavior | [Congress.gov](https://api.congress.gov/), [OpenFEC](https://api.open.fec.gov/developers/) | member × Congress |
| 2 | Weather effects on F1 race performance | [OpenF1](https://openf1.org/docs/), [Open-Meteo](https://open-meteo.com/en/docs/historical-weather-api) | circuit location × hour |
| 3 | College admissions and local COVID severity | [IPEDS via Urban Institute](https://educationdata.urban.org/), [NYT COVID-19 data](https://github.com/nytimes/covid-19-data) | county FIPS |

Write-up: `docs/`

## Setup

```bash
git clone https://github.com/rbllrd/info2950-204_project.git
cd info2950-204_project
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### API keys

Only Idea 1 needs keys, and both are free:

- Congress.gov — https://api.congress.gov/sign-up/ (5,000 requests/hour)
- OpenFEC — https://api.open.fec.gov/developers/ (1,000 requests/hour)

Copy `.env.example` to `.env` and fill them in. `.env` is git-ignored — never
commit a key.

OpenF1, Open-Meteo, the Urban Institute portal, and the NYT repo need no key.

## Workflow

1. `git pull origin main` before you start
2. Branch for anything non-trivial: `git checkout -b yourname/short-description`
3. Small commits, messages that say what changed and why
4. Push and open a pull request

Data files are git-ignored — commit the collection script, not the output.

**Rate limit note:** OpenF1 allows 3 requests/second, 30/minute. Cache responses
to `data/raw/` so repeated analysis doesn't re-hit the API.

## Log

| Date | Who | What |
|---|---|---|
| 09/20/2026 | Richard | Repo setup, README creation |
| 09/20/2026 | Richard | Mentors added as collaborators |
| 09/20/2026 | Josie | F1/Weather APIs dataset descriptions, questions, info summary |
| 09/20/2026 | Jason | Congressional Data(Cosponsorship, Fundraising) APIs dataset descriptions, questions, info summary |
| 09/20/2026 | Orazio | Covid College Admissions dataset descriptions, questions, info summary |
