# AIC-103_Data_Science_Project

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

Data Science project analyzing elevator incident data

## Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         aic_103_data_science_project and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── aic_103_data_science_project   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes aic_103_data_science_project a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

# AIC-103 Data Science Project

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" alt="CookieCutter Data Science Template"/>
</a>

**Data Science project analyzing elevator incident data for Rocket Elevator**

## Overview

This project analyzes elevator data collected by Rocket Elevator to derive actionable insights aimed at enhancing operational efficiency, ensuring safety compliance, and improving customer satisfaction. Through comprehensive data extraction, transformation, and loading (ETL) processes, the project integrates multiple datasets related to elevator licensing, installation, alterations, inspections, and incidents. Advanced data analysis and visualization techniques are employed to uncover patterns, trends, and correlations, facilitating data-driven decision-making and strategic planning.

## Project Structure

```
├── LICENSE
├── README.md
├── environment.yml
├── mkdocs.yml
├── setup.cfg
├── Makefile
├── pyproject.toml
├── aic_103_data_science_project
│   ├── __init__.py
│   ├── config.py
│   ├── dataset.py
│   ├── features.py
│   ├── plots.py
│   ├── modeling
│   │   ├── __init__.py
│   │   ├── predict.py
│   │   └── train.py
├── data
│   ├── raw
│   │   ├── license.csv
│   │   ├── installed.json
│   │   ├── altered.json
│   │   ├── inspection.csv
│   │   ├── incident.json
│   ├── processed
│   │   ├── cleaned_license_data.csv
│   │   ├── merged_installed_data.csv
│   │   ├── merged_altered_data.csv
├── docs
│   ├── index.md
│   ├── data_exploration.md
│   ├── data_reporting.md
│   ├── getting_started.md
│   ├── overview.md
│   ├── project_structure.md
│   ├── license.md
├── models
├── notebooks
│   ├── altered-ETL.ipynb
│   ├── incident-exploration.ipynb
│   ├── inspections-ETL.ipynb
│   ├── installed-ETL.ipynb
│   ├── licence-ETL.ipynb
├── reports
│   ├── final_report.md
│   ├── license_data_findings.md
│   ├── installed_data_findings.md
│   ├── altered_data_findings.md
│   ├── inspection_data_findings.md
│   ├── incidents_data_findings.md
│   ├── figures
│   │   ├── expiry_table.png
│   │   ├── expiry_table_styled.png
│   │   ├── license_expiry_timeseries.png
│   │   ├── incident_wordcloud.png
│   │   ├── missing_location_data.png
```

## Getting Started

### Prerequisites

- [Anaconda](https://www.anaconda.com/products/distribution) installed on your system.

### Setup Instructions

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/AIC-103_Data_Science_Project.git
   cd AIC-103_Data_Science_Project
   ```

2. **Create and Activate the Conda Environment:**

   ```bash
   conda env create -f environment.yml
   conda activate aic_103_env  # Replace 'aic_103_env' with the actual environment name in environment.yml
   ```

3. **Verify Dependency Installation:**

   ```bash
   conda list
   ```
   If any package is missing, install it using:
   ```bash
   conda install package_name
   ```

4. **Run Jupyter Notebooks:**

   Navigate to the `notebooks` directory and open the Jupyter notebooks:

   ```bash
   jupyter notebook
   ```

## Usage

### Data Processing and Analysis

The `aic_103_data_science_project` package contains modules for data processing, feature engineering, modeling, and visualization.

### Notebooks:

- `licence-ETL.ipynb`: ETL processes for the License dataset.
- `installed-ETL.ipynb`: ETL processes for the Installed dataset.
- `altered-ETL.ipynb`: ETL processes for the Altered dataset.
- `inspections-ETL.ipynb`: ETL processes for the Inspection dataset.
- `incident-exploration.ipynb`: Analysis and visualization of incident data.

### Reports:

Generated reports and visualizations are stored in the `reports` directory.

## Project Documentation

### Viewing Documentation Locally

The project documentation is built using **MkDocs** and the **Material Theme**.

1. **Install MkDocs and the Material Theme:**
   ```bash
   pip install mkdocs mkdocs-material
   ```

2. **Serve the Documentation Locally:**
   ```bash
   mkdocs serve
   ```

   Access the documentation at `http://127.0.0.1:8000/`.

## Contributing

Contributions are welcome! Follow these steps:

1. **Fork the Repository.**
2. **Create a New Branch:**
   ```bash
   git checkout -b feature/YourFeatureName
   ```
3. **Commit Your Changes:**
   ```bash
   git commit -m "Add your message here"
   ```
4. **Push to the Branch:**
   ```bash
   git push origin feature/YourFeatureName
   ```
5. **Open a Pull Request.**

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## References

### **Datasets:**
- `license.csv` - License Dataset
- `installed.json` - Installed Dataset
- `altered.json` - Altered Dataset
- `inspection.csv` - Inspection Dataset
- `incident.json` - Incident Dataset

### **Tools and Libraries:**
- Python (Pandas, NLTK, WordCloud, Matplotlib)
- MkDocs for documentation
- CookieCutter Data Science Template for project structuring

### **Documentation:**
- Project documentation files are in the `docs/` directory.
- Visualizations are in `reports/figures/`.

### **GitHub Repository:**
- [AIC-103_Data_Science_Project](https://github.com/Gamikaru/AIC-103_Data_Science_Project)

## Reports

The final report summarizing findings and recommendations is available in the `reports` directory as `final_report.md`. Visualizations are located in `reports/figures/`.

---

**Note:** Ensure all collaborators have access to the private GitHub repository. Update placeholder links and filenames with actual paths.


