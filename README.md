# multimodal-misleading-content

Research project exploring whether semantic inconsistency between an image and
its accompanying text, as measured with vision-language models such as CLIP,
can help flag potentially misleading multimodal content.

## Objective

Develop and evaluate research workflows for measuring image-text alignment and
assessing its usefulness as a signal for potentially misleading content. This
repository contains the initial project structure only; it does not yet make
claims about model performance or research findings.

## Preliminary workflow

1. Collect and document source data in `data/raw/`.
2. Prepare reproducible analysis-ready data in `data/processed/`.
3. Develop and evaluate image-text consistency methods under `src/`.
4. Record experiment configurations and outputs in `configs/` and
   `experiments/`.
5. Use notebooks for exploratory analysis and `app/` for any future interface.

See the README files within key directories for their intended use.
