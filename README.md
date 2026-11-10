# INFO 2950-204 — Final Project

Shared workspace for our INFO 2950 final project, Section 204.

**Current phase:** Phase IV (due Nov 19, 2026)

## Team

| Name | NetID | GitHub |
|---|---|---|
| Richard Ballard | rpb233 | [@rbllrd](https://github.com/rbllrd) |
| Josephine Kelly | jnk56 | [@jx-56](https://github.com/jx-56) |
| Jason Choi | jc3697 | [@jc3697-creator](https://github.com/jc3697-creator) |
| Orazio Petito | opp2 | [@OrazioP26](https://github.com/OrazioP26) |

**Section mentor:** Jingruo Chen (jc3564) — added as a collaborator on 09/20/2026.

## Repo Layout

- `Phase 1/`, `Phase 2/`: notebooks and PDFs as submitted for each phase
- `Phase 3/`: final submitted notebook and PDF (`info2950_204_project_phase3.ipynb`, `info2950-204_project_phase3.pdf`), plus each hypothesis's working notebook (`hypothesis1_elevation.ipynb`, `hypothesis2_mercedes.ipynb`)
- `data/raw/`: raw API pulls (OpenF1, Open-Meteo)
- `data_cleaning.ipynb`: turns `data/raw/` into `analysis_ready.csv`
- `analysis_ready.csv`: analysis-ready table used by all analyses, the team-session table
- `openmeteo_input.csv`: intermediate file of session coordinates, dates, and start hours used to query Open-Meteo
- `.gitignore`: ignores the local Python environment, API/notebook caches (`.cache.sqlite`), notebook checkpoints, and OS files

## Dataset ideas (Phase I)

| # | Idea | Sources | Join key |
|---|---|---|---|
| 1 | Fundraising composition and cosponsorship behavior | [Congress.gov](https://api.congress.gov/), [OpenFEC](https://api.open.fec.gov/developers/) | member × Congress |
| 2 | Weather effects on F1 qualifying performance | [OpenF1](https://openf1.org/docs/), [Open-Meteo](https://open-meteo.com/en/docs/historical-weather-api) | circuit location × hour |
| 3 | College admissions and local COVID severity | [IPEDS via Urban Institute](https://educationdata.urban.org/), [NYT COVID-19 data](https://github.com/nytimes/covid-19-data) | county FIPS |

**Chosen:** Idea 2 (F1 qualifying and weather/elevation), selected in Phase II.

## Setup

```bash
git clone https://github.com/rbllrd/info2950-204_project.git
cd info2950-204_project
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

### API keys

No API keys are needed: OpenF1 and Open-Meteo are free and keyless.

## Workflow

1. `git pull origin main` before you start
2. Branch for anything non-trivial: `git checkout -b yourname/short-description`
3. Small commits, messages that say what changed and why
4. Push and open a pull request

Raw API pulls are committed to `data/raw/` so the raw data can be linked from our data description; re-run collection only when the raw files themselves need updating.

**Rate limit note:** OpenF1 allows 3 requests/second, 30/minute. Cache responses
to `data/raw/` so repeated analysis doesn't re-hit the API.

## Log

**Phase III contributions summary:**

Jason - Data cleaning notebook (Q1-based relative pace, stable team IDs, wet-Q1 flag, Q1 track temperature); regenerated raw data and analysis-ready dataset.

Orazio - Hypothesis 1 analysis (elevation × team regression, F-test, Mexico City robustness check).

Josie - Hypothesis 2 analysis (temperature × Mercedes regression, permutation test, cloud-cover model); wet-vs-dry Mercedes analysis.

Richard - Final notebook assembly; introduction, data description, preregistration, conclusions, limitations, and bibliography; analysis revisions.

| Date | Who | What |
|---|---|---|
| 11/10/2026 | Richard | Submitted Phase III notebook; revised H1/H2 analyses (Q1 measure, dry sessions, clustered SEs, permutation tests)
| 11/10/2026 | Josie | Added wet-vs-dry Mercedes analysis and revisions to H1/H2 interpretation |
| 11/10/2026 | Richard | Prepared milestone 3 for submission; wrote data description, limitations, preregistration, and bibliography |
| 11/09/2026 | Josie | Ran the temperature × Mercedes regression and recorded significance for H2 |
| 11/09/2026 | Orazio | Ran the elevation × team regression (plus Mexico check) and wrote up that H1 isn’t significant |
| 11/08/2026 | Jason | Built data_cleaning.ipynb (Q1-based relative pace from OpenF1 session results, stable team IDs across rebrands and seasons, wet-Q1 flag and Q1 track temperature, half-season check); regenerated and pushed data/raw/, fixing the issue of absent raw-data; rebuilt analysis_ready.csv (all 88 sessions); added repo layout to README |
| 10/20/2026 | Josie | Making peer edits on part 1 and 2 questions, formalizing questions for reviewers |
| 10/20/2026 | Orazio | Reframing research question and hypotheses based on peer review, EDA and analysis-ready dataset, repo cleanup |
| 10/20/2026 | Jason | Open F1 weather data pull, annotated comments and edits, typo fixes |
| 10/20/2026 | Richard | Exploratory data analysis, data description and limitations, final data cleaning/revisions, repo organization |
| 10/15/2026 | Josie | Jupyter notebook setup, Phase2Peer.ipynb creation, data cleaning |
| 10/15/2026 | Orazio | Preregistering analyses and forming hypothesis, higher level logic |
| 10/15/2026 | Jason | Data cleaning, notes for code to ensure comprehension |
| 10/15/2026 | Richard | Data descriptions, limitations, research questions |
| 10/15/2026 | Orazio | EDA + analysis_ready.csv, Gebru description / stronger limitations, `.gitignore` |
| 09/20/2026 | Richard | Repo setup, README creation |
| 09/20/2026 | Richard | Mentors added as collaborators |
| 09/20/2026 | Josie | F1/Weather APIs dataset descriptions, questions, info summary |
| 09/20/2026 | Jason | Congressional Data(Cosponsorship, Fundraising) APIs dataset descriptions, questions, info summary |
| 09/20/2026 | Orazio | Covid College Admissions dataset descriptions, questions, info summary |
