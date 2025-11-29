# Copilot Instructions for Diabetics Prediction Project

## Project Overview
This is a machine learning analysis project for diabetes prediction using scikit-learn. The project structure separates data (`data/`), exploratory analysis/notebooks (`notebooks/`), and results (`results/`). Work is tracked through the primary entry point (`main.py`) and interactive Jupyter notebooks.

## Architecture & Data Flow
- **Data Layer**: CSV files in `data/` (particularly `diabetes2.csv`) - loaded with pandas
- **Processing Pipeline**: StandardScaler for feature normalization (imported in notebooks)
- **Development Pattern**: Iterative analysis happens in `notebooks/`, production logic goes in `main.py`

Key pattern from current notebook: load data → drop NAs → separate features (X) from target (class column)

## Development Setup & Workflows

### Environment Management
- Uses `uv` as Python package manager (see `uv.lock`)
- Python 3.9+ required (`pyproject.toml`)
- Virtual environment at `.venv/` (excluded from git)

### Running Analysis
- **Interactive**: Jupyter notebooks in `notebooks/` directory (dev dependency)
- **Production**: Execute via `python main.py`
- **Data File**: Always reference as relative path `../data/diabetes2.csv` from notebook/script context

### Dependencies
Core ML stack: `scikit-learn` (1.6.1+), `pandas` (2.3.3+), `numpy` (2.0.2+)
Visualization: `matplotlib` (3.9.4+), `seaborn` (0.13.2+)

## Project-Specific Conventions

1. **Target Column**: The dataset uses `"class"` as the target column (not `"target"` or `"label"`) - update column references accordingly

2. **Data Cleaning Pattern**: 
   ```python
   df = df.dropna()  # Simple NA removal; modify based on dataset specifics
   X = df.drop(columns=["class"])  # Features only
   y = df["class"]  # Target
   ```

3. **File Organization**:
   - Experimental/exploratory code → `notebooks/` (Jupyter)
   - Finalized models/pipelines → `main.py`
   - Analysis outputs → `results/`

## Critical Integration Points

- **Data Input**: `data/diabetes2.csv` is the primary dataset; also contains `dataset.zip` for reference
- **Feature Preprocessing**: StandardScaler pipeline is standard practice (already imported in notebooks)
- **Cross-component Communication**: Notebooks should produce outputs/models saved to `results/` that could be consumed by `main.py`

## Notes for AI Agents

- This is a **greenfield-style project** with minimal existing code - focus on establishing clear patterns
- The `.venv/` directory and `uv.lock` are dependency artifacts; don't modify these directly
- When adding new features/models, mirror the notebook → main.py promotion pattern
