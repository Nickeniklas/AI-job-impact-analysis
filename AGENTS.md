# AGENTS.md

## Project Overview

This project is a starter analysis workspace for exploring AI's expected impact on the jobs market in 2030 using a Kaggle dataset.

Primary notebook:

- `dataset_analysis.ipynb`

Dataset source:

- KaggleHub slug: `muhammadwaqas023/ai-impact-in-future-on-jobs-market-in-2030`

## Current Progress

- Created a Python Jupyter notebook for exploratory dataset analysis.
- Added a project-local virtual environment at `.venv/`.
- Added `requirements.txt` with the notebook dependencies.
- Registered a Jupyter kernel named `AI Job Impact Analysis`.
- Switched dataset loading from the older `kaggle` API package to `kagglehub`.
- Configured notebook download cache under `data/kagglehub`.
- Added `.gitignore` entries for local environment, downloaded data, notebook checkpoints, and cache files.
- Verified that the notebook JSON is valid.
- Verified imports from `.venv` for `kagglehub`, `pandas`, `matplotlib`, and `numpy`.

## Files

- `dataset_analysis.ipynb`: Main analysis notebook.
- `requirements.txt`: Python dependencies for the notebook.
- `.gitignore`: Ignores local/generated files.
- `AGENTS.md`: Project handoff notes and workflow guidance.

Generated local files/directories:

- `.venv/`: Local Python virtual environment. Ignored by git.
- `data/`: Dataset download/cache location. Ignored by git.
- `.matplotlib/`: Project-local matplotlib cache. Ignored by git.

## Environment Setup

From the project root:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m ipykernel install --user --name ai-job-impact-analysis --display-name "AI Job Impact Analysis"
.venv/bin/jupyter lab
```

The local Python used during setup was Python `3.13.7`.

## Notebook Workflow

The notebook currently:

1. Sets project-local cache paths.
2. Imports `kagglehub`, `pandas`, `numpy`, and `matplotlib`.
3. Downloads the Kaggle dataset with:

```python
path = kagglehub.dataset_download(
    "muhammadwaqas023/ai-impact-in-future-on-jobs-market-in-2030"
)
```

4. Finds supported files in the downloaded dataset directory.
5. Loads the first supported file into a pandas DataFrame.
6. Runs starter exploratory analysis:
   - shape and schema
   - summary statistics
   - missing values
   - duplicates
   - unique counts
   - numeric distributions
   - categorical value counts
   - numeric correlations

Supported data file extensions:

- `.csv`
- `.xlsx`
- `.xls`
- `.json`
- `.parquet`

## Next Steps

- Run the KaggleHub download cell and confirm the actual downloaded file names.
- If multiple data files are present, choose the intended file instead of always using `downloaded_files[0]`.
- Add dataset-specific analysis questions once columns are known.
- Add cleaned/derived columns where useful.
- Add clearer charts tailored to the dataset's real fields.
- Summarize findings in the final notebook section.

## Notes for Future Agents

- Keep downloaded data out of git.
- Keep `.venv/` out of git.
- Prefer editing the notebook in a minimal, valid JSON-preserving way.
- After notebook edits, validate with:

```bash
python3 -m json.tool dataset_analysis.ipynb
```

- Verify imports with:

```bash
.venv/bin/python -c "import kagglehub, pandas, matplotlib, numpy; print('imports ok')"
```

- This directory is not currently a git repository, so `git status` will fail unless git is initialized later.
