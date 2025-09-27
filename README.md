# Energy Optimization — ISYE 6669 (Project)

## Project overview
This repository contains my course project for ISYE 6669. The goal is to minimize operational energy costs for a manufacturing facility by optimally scheduling electricity purchases, hydrogen purchases, and asset operation (electrolyser, solar expansion, battery). The work is divided into two parts:

- **Part A (baseline / deterministic)** — formulate and solve the baseline deterministic optimization for electricity and hydrogen procurement and storage. Implemented as a Jupyter notebook.
- **Part B (design & extensions)** — extend the model to include an electrolyser (on/off decisions), solar expansion decisions, battery integration, and payback calculations. Implemented as a notebook with supplementary scripts and analysis.

## Repository layout
- `inputs/` — all raw input CSV files (electricity demand, prices, hydrogen demand, solar forecast).
- `code/` — notebooks and scripts for Part A and Part B (primary analysis and models).
- `outputs/` — generated outputs (solution CSVs, electrolyser use). Note: some outputs may be intentionally ignored by `.gitignore`; final deliverables are tracked as needed.
- `docs/` — reports and PDF deliverables.
- `requirements.txt` — Python package dependencies.
- `LICENSE` — project license (MIT).

## Part A
In this part I:
- Built a deterministic convex optimization model using CVXPY.
- Modeled hydrogen storage and electricity purchase decisions with solar forecast incorporated.
- Solved the model and saved per-hour solutions (CSV).
- The main implementation is in `code/PartA_code.ipynb`.

## Part B 
In this part I:
- Added discrete electrolyser on/off decisions (binary variables) and electrolyser production.
- Modeled discrete solar expansion (integer blocks) and battery charge/discharge.
- Compared costs across configurations and calculated simple payback estimates.
- The main implementation is in `code/DO_PartB-2.ipynb` (notebook) and supporting materials in `docs/`.

## Quick setup 
1. Create and activate a Python virtual environment:
   - python3 -m venv .venv
   - source .venv/bin/activate
2. Install Python dependencies:
   - pip install -r requirements.txt
3. Install/enable solvers as required:
   - For convex problems: ECOS, SCS (pip install ecos scs)
   - For MIP/integer parts: install CBC or another MIP solver. (System install may be required; see solver docs.)

## Running the notebooks or scripts
- Run interactively:
  - jupyter notebook
  - open `code/PartA_code.ipynb` or `code/DO_PartB-2.ipynb`
- Run and execute notebooks headlessly:
  - jupyter nbconvert --to notebook --execute code/PartA_code.ipynb --inplace
  - jupyter nbconvert --to notebook --execute code/DO_PartB-2.ipynb --inplace
- Example: run Part A from terminal (after activating venv)
  - python -c "import nbformat, nbconvert; ... " (or use nbconvert as above)
- If notebooks rely on system solvers (CBC), follow solver install instructions before executing those cells.

## Outputs
- Primary outputs are saved to `outputs/` (CSV files with hourly results and electrolyser usage).
- I tracked the stable results in the repo where appropriate. If you expect frequent regenerated outputs, consider using GitHub Releases or Git LFS for large files.

## Reproducibility notes
- Models use CVXPY; solver availability affects results and feasibility:
  - Convex relaxations: ECOS, SCS
  - MIP: CBC, GUROBI, CPLEX, etc.
- If a solver is unavailable or versions mismatch, results/solve times may differ.

## Development & testing
- To re-run and reproduce results end-to-end:
  1. Ensure `inputs/` contains the correct CSV files.
  2. Activate the virtual environment and install dependencies.
  3. Execute the notebooks in order: Part A → Part B.
- Check `requirements.txt` and adjust solver-related installs if needed.

## License
This project is released under the MIT License. See `LICENSE` for details.

------------------------------------
If you have questions or suggestions, feel free to contact me.

-Vedika :)

