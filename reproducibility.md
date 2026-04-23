# Reproducibility Guide

This guide explains how to run the analysis and regenerate the final visualizations using the code in this repository.

You do not need advanced experience with Python, just a terminal and Python installed.

## What this will do

You will:

1. Download the repository  
2. Create a clean Python environment  
3. Install the required packages  
4. Open and run the final notebook  


## Step 1: Download the repository

Open a terminal (Mac) or Command Prompt / PowerShell (Windows), then run:

```bash
git clone https://github.com/arkeshdas/Measles-Comeback-US.git
cd Measles-Comeback-US
```

## Step 2: Create a virtual environment

### Mac / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

After this, your terminal should show something like:

```bash
(.venv)
```


## Step 3: Install required packages

```bash
pip install -r requirements.txt
```


## Step 4: Register the environment for Jupyter

This lets the notebook use your virtual environment.

```bash
python -m ipykernel install --user --name measles-project --display-name "Python (measles-project)"
```


## Step 5: Launch Jupyter

```bash
jupyter notebook
```

This will open a browser window.


## Step 6: Open and run the notebook

Navigate to:

```
final_visualizations/final_vis.ipynb
```

Then:

* Select kernel: **Python (measles-project)**
* Run all cells (Kernel → Restart & Run All)

This will regenerate the final visualizations.


## Where outputs go

Figures will be saved to:

```
final_visualizations/
```


## Notes

* All required datasets are already included in the `data/` folder. No external downloads are needed.
* The notebook performs all data cleaning, merging, and visualization.
* Some figures (especially maps) may take a few seconds to render.


## Common issues

### "python not found"

Try:

```bash
python3 --version
```

If that works, use `python3` instead of `python` in the commands above.


### Kernel not showing in Jupyter

Close Jupyter and run:

```bash
python -m ipykernel install --user --name measles-project
```

Then reopen Jupyter.

### Plotly image export not working

Make sure `kaleido` installed correctly:

```bash
pip install kaleido
```


## Done

If everything worked, you should now be able to run the notebook and reproduce all figures in the project.

To deactivate the virtual environment run:

```bash
deactivate
```

