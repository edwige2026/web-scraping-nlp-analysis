# Methodology and interpretation

## Workflow

1. **Collection:** Selenium can collect public-facing article fields where the site's current rules and applicable law permit it. DOM selectors are inherently brittle and should be checked before each collection run.
2. **Storage:** SQLite keeps article records in a local database. A unique title constraint prevents many duplicate insertions but does not guarantee deduplication when titles change.
3. **Exploration:** Descriptive summaries characterize the collected sample; they do not establish representativeness. Text length, category counts and person mentions can be affected by missing content and extraction errors.
4. **LLM-assisted analysis:** A local model produces structured candidate labels and evidence excerpts. It may hallucinate, misinterpret quotations or conflate topic with framing. Human review is necessary.

## Recommended improvements before making substantive claims

- Define a collection window and sampling frame in advance.
- Validate extraction completeness on a manually inspected random sample.
- Create a codebook with operational definitions and positive/negative examples for each label.
- Have at least two human annotators label a sample independently, then report agreement and adjudication.
- Compare LLM output with human labels and report precision/recall or a confusion matrix.
- Report uncertainty and avoid claims about the entire outlet from a convenience sample.
- Keep copyrighted source text and the SQLite database private unless redistribution is authorized.
