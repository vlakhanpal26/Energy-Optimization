Energy optimization (ISYE 6669) — Project A

Hi — this repository contains my work for the ISYE 6669 Project A. I built a small deterministic optimization model (in a Jupyter notebook) to minimize energy costs by scheduling electricity and hydrogen purchases while using a solar forecast.

Repository contents
- `6669_Project_Electricity_Demand.csv` — electricity demand (input)
- `6669_Project_Electricity_Prices.csv` — electricity prices (input)
- `6669_Project_Hydrogen_Demand.csv` — hydrogen demand (input)
- `6669_Project_Solar_Forecast.csv` — solar forecast (input)
- `PartA_code.ipynb` — the main Jupyter notebook containing the optimization model (cvxpy)
- `ISYE_6669_ProjectA-2.pdf` — project report
- `requirements.txt` — minimal Python dependencies (numpy, cvxpy)
- `LICENSE` — MIT license
- `.github/workflows/ci.yml` — lightweight CI to install deps and run a smoke test
 - `requirements.txt` — minimal Python dependencies (numpy, cvxpy)
 - `LICENSE` — MIT license
 - `.github/workflows/ci.yml` — lightweight CI to install deps and run a smoke test

Repository layout (organized)
- `inputs/` — all input CSVs used by the notebooks and scripts
- `outputs/` — model outputs and generated CSVs (ignored by default)
- `code/` — notebooks and scripts (Part A and Part B code)
- `docs/` — PDF reports and other documentation
- other top-level files: `README.md`, `LICENSE`, `requirements.txt`, `.github/`

Files moved/where to look
- Inputs (examples): `inputs/6669_Project_Electricity_Demand.csv`, `inputs/6669_Project_Electricity_Prices.csv`, `inputs/6669_Project_Hydrogen_Demand.csv`, `inputs/6669_Project_Solar_Forecast.csv`
- Outputs (examples): `outputs/Solution.csv`, `outputs/Solution_24_hours.csv`, `outputs/Electrolyser_Use.csv`
- Code: `code/PartA_code.ipynb`, `code/do_partbcode.py`, `code/DO_PartB-2.ipynb`
- Docs: `docs/ISYE_6669_ProjectA-2.pdf`, `docs/DO_PARTBReport.pdf`

Part A (what I did)
- I implemented a deterministic optimization model using `cvxpy` to schedule electricity and hydrogen purchases while fully utilising available solar.
- The main notebook is `code/PartA_code.ipynb`. Running it writes solution CSVs into `outputs/`.

Part B (what I did)
- Part B continues the same project and extends the analysis to include electrolyser usage and additional constraints.
- The Part B code and notebook are in `code/` and expect the same `inputs/` CSVs; Part B produces `outputs/Electrolyser_Use.csv` and a short report in `docs/`.

Quick start (run locally)
1. Clone or use the local copy:

	git clone https://github.com/vlakhanpal26/energy-optimization.git
	cd energy-optimization

2. Create and activate a virtual environment (macOS / zsh):

	python3 -m venv .venv
	source .venv/bin/activate

3. Install dependencies:

	pip install --upgrade pip
	pip install -r requirements.txt

4. Run the code:

	- Part A notebook: open `code/PartA_code.ipynb` in Jupyter and run it. It will read from `inputs/` and write `outputs/`.
	- Part B notebook: open `code/DO_PartB-2.ipynb` or run `python code/do_partbcode.py`.

Notes & tips
- `cvxpy` may require additional solvers for some problems; try `pip install ecos scs` if you see solver errors.
- `outputs/` is listed in `.gitignore` so generated outputs are not tracked by default.
- If you'd like outputs tracked or archived in releases, let me know and I can adjust the workflow.

Author

— vlakhanpal26

Professional summary (student)
---------------------------------
I am a graduate student and this repository contains my coursework for ISYE 6669 (Project A and its continuation, Part B). The work implements a deterministic optimization model using CVXPY to minimize combined electricity and hydrogen procurement costs while accounting for solar generation. Part B extends the analysis to model electrolyser usage and produces additional outputs and a short report.

Repository structure
--------------------
- `inputs/` — CSV datasets used as inputs (electricity demand, prices, hydrogen demand, solar forecast)
- `code/` — notebooks and scripts implementing Part A and Part B analysis (notebooks are the primary artifacts)
- `outputs/` — generated outputs and result CSVs. Note: outputs are ignored by default; I selectively track final result files for reproducibility.
- `docs/` — PDF project reports and other documentation
- `.github/` — CI workflow definitions
- `requirements.txt`, `LICENSE`, `README.md`

What I implemented
------------------
- Part A: deterministic optimization in `code/PartA_code.ipynb` that schedules electricity and hydrogen purchases while fully utilising available solar forecast.
- Part B: extended analysis (notebook `code/DO_PartB-2.ipynb`) that examines electrolyser usage and additional constraints; results are described in `docs/DO_PARTBReport.pdf` and the relevant outputs are placed in `outputs/`.

Quick setup and run (macOS / zsh)
--------------------------------
1. Clone the repository and change directory:

	git clone https://github.com/vlakhanpal26/energy-optimization.git
	cd energy-optimization

2. Create and activate a Python virtual environment:

	python3 -m venv .venv
	source .venv/bin/activate

3. Install dependencies:

	pip install --upgrade pip
	pip install -r requirements.txt

4. Run Part A (notebook):

	jupyter notebook code/PartA_code.ipynb

	- Run the notebook cells in order. The notebook reads data from `inputs/` and writes outputs to `outputs/` when executed.

5. Run Part B (notebook):

	jupyter notebook code/DO_PartB-2.ipynb

Notes on outputs and reproducibility
----------------------------------
- The `outputs/` directory is ignored by default to avoid committing transient or intermediate files. I have committed final results intentionally when needed (e.g., `outputs/Solution.csv`) for reproducibility.
- If you need to regenerate outputs, run the notebooks after installing dependencies. For solver-related issues, install additional CVXPY solvers, e.g. `pip install ecos scs`.

Continuous integration
----------------------
- A lightweight GitHub Actions workflow is included at `.github/workflows/ci.yml`. It installs dependencies and runs a minimal smoke test to ensure imports succeed.

Licensing and contact
----------------------
- License: MIT (see `LICENSE`).
- If you have questions or want me to add tests, CI steps, or example runs, open an issue or contact me via my GitHub profile: `vlakhanpal26`.

— V. Lakhanpal (student)

Notes about outputs
- `Solution.csv` and `Solution_24_hours.csv` were generated by the notebook; they are now ignored by `.gitignore` and are not tracked in the repo. If you need those files committed, remove them from `.gitignore`.

Quick start (run locally)
1. Clone the repo (or use the local copy):

	git clone https://github.com/vlakhanpal26/energy-optimization.git
	cd energy-optimization

2. Create and activate a virtual environment (macOS / zsh):

	python3 -m venv .venv
	source .venv/bin/activate

3. Install dependencies:

	pip install --upgrade pip
	pip install -r requirements.txt

4. Start Jupyter and open the notebook:

	jupyter notebook PartA_code.ipynb

	Then run the cells in order. The notebook reads the CSV inputs, builds and solves the cvxpy problem, prints result vectors, and writes the solution CSVs when executed.

Notes & tips
- The notebook uses `cvxpy` and assumes a working solver is available (cvxpy will use its default solver). If you run into solver issues, try installing `ecos`, `scs`, or another supported solver: `pip install ecos scs`.
- The repository includes a minimal GitHub Actions workflow that installs the dependencies and runs a tiny smoke test. It verifies `numpy` and `cvxpy` can be imported.
- If you want the output CSVs removed from the repository history entirely (to shrink the repo), I can help with an interactive history rewrite (BFG or git-filter-repo). This is destructive and should be done carefully.

-----------------------

If you need changes or want me to add tests, documentation, or CI improvements, open an issue or contact me directly.

— Vedika
