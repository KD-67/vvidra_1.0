# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Environment

- The platform is Windows/PowerShell, so don't default to bash commands.
- Python lives at `backend\.venv\Scripts\python.exe`. Use it for pip installs and running Python, and update `requirements.txt` after installing anything.
- Never read or commit `.env`.

## Commands

Dev servers:

- `fastapi dev app/main.py` (from `backend/`)
- `npm run dev` (from `frontend/`)

The Vite proxy forwards `/graphql` to port 8000.

Other frontend scripts (from `frontend/`, defined in `package.json`): `npm run build`, `npm run preview`, `npm run check`, `npm run lint`, `npm run format`.

No test framework is configured.

## Architecture

See `README.md` and the PDFs in `documentation/` for the full rationale. Two independently specified models are combined only in a coupling stage:

- **Feasibility model**: a hierarchical, discrete-time stochastic state-space model that projects the distribution of reachable marker states forward under a candidate intervention, as a weighted particle cloud, personalized by Bayesian posterior updating from cohort-level priors.
- **Desirability model**: a graded, vector-valued objective field with asymmetric deviation penalties (modified Derringer-Suich), anchored to a personalized reference point. Acceptability thresholds are annotations on the field, not hard constraints.
- **Coupling**: evaluates the desirability field over the feasibility cloud and returns, per candidate intervention, a desirability cloud plus the probability mass at each threshold. Ranking is outside the scope of this PoC.

Markers, objectives, and interventions are supplied as configuration, not hard-coded.

Stack: FastAPI with Strawberry GraphQL (`backend/`), SvelteKit with Svelte 5 runes mode (`frontend/`).
