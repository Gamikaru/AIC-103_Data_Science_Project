# Project Structure

This section provides an overview of the project's directory layout and the purpose of each folder.

## Directory Overview

.
├── LICENSE
├── Makefile
├── README.md
├── aic_103_data_science_project
│   ├── __init__.py
│   ├── config.py
│   ├── dataset.py
│   ├── features.py
│   ├── modeling
│   │   ├── __init__.py
│   │   ├── predict.py
│   │   └── train.py
│   └── plots.py
├── data
│   ├── external
│   ├── interim
│   ├── processed
│   │   ├── cleaned_license_data.csv
│   │   ├── merged_altered_data.csv
│   │   └── merged_installed_data.csv
│   └── raw
│       ├── altered.json
│       ├── cleaned_license_data.csv
│       ├── incident.json
│       ├── inspection.csv
│       ├── installed.json
│       ├── license.csv
│       ├── merged_altered_data.csv
│       ├── merged_installed_data.csv
│       └── order.csv
├── docs
│   ├── data_exploration.md
│   ├── data_reporting.md
│   ├── deliverables.md
│   ├── getting-started.md
│   ├── getting_started.md
│   ├── index.md
│   ├── license.md
│   ├── overview.md
│   ├── presentation.md
│   └── project_structure.md
├── environment.yml
├── mkdocs.yml
├── models
├── notebooks
│   ├── altered-ETL.ipynb
│   ├── inspections-ETL.ipynb
│   ├── installed-ETL.ipynb
│   └── licence-ETL.ipynb
├── pyproject.toml
├── references
├── reports
│   └── figures
├── setup.cfg
├── site
│   ├── 404.html
│   ├── assets
│   │   ├── images
│   │   │   └── favicon.png
│   │   ├── javascripts
│   │   │   ├── bundle.60a45f97.min.js
│   │   │   ├── bundle.60a45f97.min.js.map
│   │   │   ├── lunr
│   │   │   │   ├── min
│   │   │   │   │   ├── lunr.ar.min.js
│   │   │   │   │   ├── lunr.da.min.js
│   │   │   │   │   ├── lunr.de.min.js
│   │   │   │   │   ├── lunr.du.min.js
│   │   │   │   │   ├── lunr.el.min.js
│   │   │   │   │   ├── lunr.es.min.js
│   │   │   │   │   ├── lunr.fi.min.js
│   │   │   │   │   ├── lunr.fr.min.js
│   │   │   │   │   ├── lunr.he.min.js
│   │   │   │   │   ├── lunr.hi.min.js
│   │   │   │   │   ├── lunr.hu.min.js
│   │   │   │   │   ├── lunr.hy.min.js
│   │   │   │   │   ├── lunr.it.min.js
│   │   │   │   │   ├── lunr.ja.min.js
│   │   │   │   │   ├── lunr.jp.min.js
│   │   │   │   │   ├── lunr.kn.min.js
│   │   │   │   │   ├── lunr.ko.min.js
│   │   │   │   │   ├── lunr.multi.min.js
│   │   │   │   │   ├── lunr.nl.min.js
│   │   │   │   │   ├── lunr.no.min.js
│   │   │   │   │   ├── lunr.pt.min.js
│   │   │   │   │   ├── lunr.ro.min.js
│   │   │   │   │   ├── lunr.ru.min.js
│   │   │   │   │   ├── lunr.sa.min.js
│   │   │   │   │   ├── lunr.stemmer.support.min.js
│   │   │   │   │   ├── lunr.sv.min.js
│   │   │   │   │   ├── lunr.ta.min.js
│   │   │   │   │   ├── lunr.te.min.js
│   │   │   │   │   ├── lunr.th.min.js
│   │   │   │   │   ├── lunr.tr.min.js
│   │   │   │   │   ├── lunr.vi.min.js
│   │   │   │   │   └── lunr.zh.min.js
│   │   │   │   ├── tinyseg.js
│   │   │   │   └── wordcut.js
│   │   │   └── workers
│   │   │       ├── search.f8cc74c7.min.js
│   │   │       └── search.f8cc74c7.min.js.map
│   │   └── stylesheets
│   │       ├── main.a40c8224.min.css
│   │       ├── main.a40c8224.min.css.map
│   │       ├── palette.06af60db.min.css
│   │       └── palette.06af60db.min.css.map
│   ├── getting-started
│   │   └── index.html
│   ├── index.html
│   ├── overview
│   │   └── index.html
│   ├── search
│   │   └── search_index.json
│   ├── sitemap.xml
│   └── sitemap.xml.gz
└── untitled.md

## Folder Descriptions

- **`data/`**: Contains all data files, organized into `raw`, `processed`, `interim`, and `external` subdirectories.
- **`notebooks/`**: Jupyter notebooks for data exploration and analysis.
- **`aic_103_data_science_project/`**: Source code modules for data processing, feature engineering, modeling, and visualization.
- **`docs/`**: Project documentation built with MkDocs.
- **`models/`**: Trained and serialized models.
- **`reports/`**: Generated analysis reports and figures.
- **`references/`**: Data dictionaries, manuals, and other explanatory materials.

