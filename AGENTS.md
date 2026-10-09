# Repository Guidelines

## Project Structure & Module Organization

This repository is an early-stage research project on identifying potentially
misleading image-text content through semantic inconsistency. Keep reusable
Python code in `src/`, organized by responsibility:

- `src/data/`: loading, validation, and preparation.
- `src/models/`: model adapters and model-related components.
- `src/features/`: image-text representations and derived features.
- `src/evaluation/`: metrics, benchmark protocols, and reports.
- `src/inference/`: scoring or prediction entry points.

Store acquired source material in `data/raw/`, reproducible derivatives in
`data/processed/`, and third-party resources in `data/external/`. Use
`notebooks/` only for exploration; promote stable logic into `src/`.
Configurations belong in `configs/`, run notes or small metadata in
`experiments/`, tests in `tests/`, and any future demonstration interface in
`app/`.

## Build, Test, and Development Commands

No dependency manager, formatter, linter, test framework, or runnable model is
configured yet. The pinned lightweight local dependencies are listed in
`requirements-local.txt`; install them only when a task authorizes it with
`python -m pip install -r requirements-local.txt`. `requirements-cloud.txt`
inherits those tools but deliberately defers GPU and model packages until a
cloud runtime and compatible PyTorch/CUDA build are selected. Once tests are
introduced, document the exact command here (for example, `python -m pytest`).

## Coding Style & Naming Conventions

Follow standard Python conventions: four-space indentation, `snake_case` for
modules, functions, variables, and test files; `PascalCase` for classes; and
`UPPER_SNAKE_CASE` for constants. Prefer small, typed functions with focused
docstrings where behavior is not obvious. Name modules by their responsibility,
such as `src/features/alignment_scores.py`, rather than by a temporary
experiment.

Keep experiment-specific settings out of source files; place versioned settings
in `configs/` with descriptive names such as `clip_baseline.yaml`.

## Testing Guidelines

Place tests under `tests/` and mirror the source layout when practical, e.g.,
`tests/features/test_alignment_scores.py`. Name test functions `test_<behavior>`
and cover expected behavior, boundary cases, and data-validation failures.
Avoid tests that require downloading data or model weights unless they are
explicitly marked and documented.

## Commit & Pull Request Guidelines

The repository history currently contains only an initial commit, so no existing
commit convention can be inferred. Use concise imperative subjects, for example
`Add image-text score validation`. Keep commits focused.

Pull requests should explain the research or engineering motivation, summarize
changed data/configuration assumptions, link relevant issues, and include test
results. Do not claim experimental effectiveness without reproducible evidence.

## Data and Research Hygiene

Do not commit datasets, credentials, private content, or large generated model
artifacts. Record provenance, licenses, preprocessing decisions, and evaluation
limitations alongside experiments so results remain auditable.

## Research and AI Development Rules

- Treat experimental claims as hypotheses until reproducible measurements support them.
- Never invent, estimate, or fabricate results, dataset statistics, benchmark scores, citations, or observations.
- Explain any change to the research objective, evaluation method, dataset splits, or experimental protocol.
- Prefer reproducible experiments over one-off demonstrations.
- Record result-affecting random seeds, model identifiers, preprocessing, hyperparameters, dataset versions, and evaluation settings.
- Keep baseline implementations separate from proposed improvements for fair comparison.
- Do not call a more complex model an improvement without evidence from the same evaluation protocol.
- Preserve failed experiments and document why they failed rather than hiding or replacing them.
- Perform error analysis on correct and incorrect predictions whenever practical.
- Distinguish semantic image-text alignment from factual correctness; CLIP similarity is not proof that a claim is true or false.
- Distinguish model-produced observations from conclusions supported by external evidence.
- Prefer frozen pretrained models for initial baselines before introducing fine-tuning.
- Validate implementations with a small CPU or toy experiment before running expensive GPU experiments.
- Keep heavy inference, training, and large-scale embedding generation in the cloud GPU environment unless explicitly required otherwise.
- Never place API keys, access tokens, passwords, or other secrets in source code, configuration files, notebooks, or Git history.
- Make the smallest targeted repository change that completes the task.
