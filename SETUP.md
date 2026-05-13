# Project Setup Guide

This guide will help you set up a virtual environment and install all dependencies for the **5G Traffic Prediction** project.

## 1. Create a Virtual Environment

It is highly recommended to use a virtual environment to avoid dependency conflicts.

### Windows (PowerShell)
```powershell
# Create the environment
python -m venv venv

# Activate the environment
.\venv\Scripts\Activate.ps1
```

### Windows (Command Prompt)
```cmd
# Create the environment
python -m venv venv

# Activate the environment
venv\Scripts\activate
```

### Linux / macOS
```bash
# Create the environment
python3 -m venv venv

# Activate the environment
source venv/bin/activate
```

## 2. Install Dependencies

Once the environment is activated, install the required packages:

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## 3. Register Kernel for Jupyter

To use this virtual environment inside the Jupyter Notebook:

```bash
python -m ipykernel install --user --name=venv --display-name "Python (5G-Thesis)"
```

## 4. Run the Project

1. Open Jupyter Notebook or VS Code.
2. Open `Network_Traffic_Prediction_Thesis.ipynb`.
3. Select the **"Python (5G-Thesis)"** kernel from the top-right corner.
4. Run all cells.
