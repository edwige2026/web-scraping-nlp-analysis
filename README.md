# Web Scraping & NLP: Exploratory Media Content Analysis

A portfolio project demonstrating a reproducible workflow for collecting public article metadata (where permitted), storing records in SQLite, exploring text and publication patterns with Python, and testing structured, local LLM-assisted content analysis. The original work was completed as an academic assignment; this repository reorganizes the workflow for clarity and reproducibility.

## Project goals

- Design a cautious, resumable collection workflow with Selenium and SQLite.
- Inspect data quality and describe categories, authors, publication dates and article length.
- Explore German named-entity recognition as a source of candidate person mentions.
- Prototype a JSON-based prompt for local LLM analysis, with explicit uncertainty and human review.

## Repository structure

```text
notebooks/
  01_collect_articles.ipynb       # opt-in scraper template; selectors may need updating
  02_exploratory_analysis.ipynb   # descriptive statistics and plots
  03_llm_content_analysis.ipynb   # optional local Ollama workflow
docs/
  methodology.md
outputs/
  figures/                        # generated figures (not raw article content)
  tables/                         # generated aggregate tables
data/                             # local data only; ignored by Git
```

## Quick start

Python 3.10 or later is recommended. Create an environment and install dependencies:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name media-analysis --display-name "Python (media-analysis)"
```

Place an authorized local SQLite database at `data/ScrapedNiusData.db`. Open the notebooks in order. The scraper is intentionally **not executed automatically**. Review the website's current terms, robots directives and applicable law before collecting anything. Website markup changes and selectors must be validated.

For the optional LLM notebook, install [Ollama](https://ollama.com/) locally and pull the model with `ollama pull llama3.2`. The notebook uses a small sample by default and includes execution cells commented out until you choose to run them.

## Important research limitations

An LLM's political-framing label is not ground truth. Topic keywords alone cannot establish ideological orientation. Any conclusions require a transparent sampling strategy, a documented codebook, human validation, inter-annotator agreement where feasible, and uncertainty reporting. The supplied notebooks are exploratory tools, not a validated political-classification system.

## Data, copyright and privacy

The source website and its article text may be protected by copyright. This repository does not include the original SQLite database, scraped article texts, assignment PDFs or raw source material. Do not publish them unless redistribution is permitted. Check site rules before scraping; do not bypass restrictions or overload the service. Keep secrets and personal data out of commits.

## Attribution

Academic assignment: DML95, “NIUS Analysis”. The notebooks have been reorganized and documented for portfolio presentation. Confirm your institution's rules on publishing assessed work and cite any third-party sources used in your final public version.
