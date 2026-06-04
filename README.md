# GCN-LST-Prediction-Seville

Implementation and evaluation of Graph Neural Networks for spatio-temporal Land Surface Temperature (LST) prediction in an urban environment. This repository contains the code and datasets developed during the Master's Thesis focused on urban climate modelling through remote sensing, meteorological data and graph-based deep learning.

---

# Overview

Urban heat islands constitute one of the most important environmental challenges in modern cities. Understanding and predicting Land Surface Temperature (LST) is essential for urban planning, climate adaptation and sustainable development.

This project investigates the use of Graph Neural Networks (GNNs), particularly Graph Convolutional Networks (GCNs), to model the spatial and temporal evolution of LST in an urban district of Seville (Spain).

The proposed framework combines:

* Satellite observations from Landsat 8/9.
* Sentinel-3 observations.
* Meteorological variables from ERA5-Land.
* Urban morphology indicators.
* Graph-based spatial representations.

Additionally, the project evaluates the impact of incorporating synthetic observations generated through Sentinel-3 downscaling and compares graph-based architectures against classical machine learning and recurrent neural network approaches.

---

# Repository Structure

```text
.
├── notebooks/
│   ├── TFM_LIBORIO_v2.zip
│   └── training_automatization.zip
│
├── datasets/
│   ├── datos_landsat.csv
│   ├── datos_sentinel_downscalled.csv
│   ├── sevilla_dataset_final.csv
│   ├── sevilla_dataset_downscaled.csv
│   └── ...
│
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

---

# Repository Contents

## notebooks/

Contains the main notebooks used throughout the thesis.

### TFM_LIBORIO_v2

Main notebook containing:

* Data acquisition
* Data preprocessing
* Sentinel-3 downscaling
* Graph construction
* Model implementation
* Training and evaluation

### training_automatization

Notebook used for:

* Automated experimentation
* Multi-seed evaluation
* Hyperparameter studies
* Ablation studies
* Comparative analysis between models

---

## datasets/

Contains the most relevant datasets generated during the project.

Depending on repository size limitations, only the final processed datasets may be included.

Examples:

* Original Landsat observations
* Downscaled Sentinel-3 observations
* Final merged datasets
* Experimental datasets used during training

These files allow most experiments to be reproduced without repeating the complete data acquisition pipeline.

---

# Models Evaluated

The following models were implemented and compared:

### Machine Learning

* XGBoost

### Recurrent Neural Networks

* LSTM
* Stacked LSTM
* GRU
* Stacked GRU

### Graph Neural Networks

* GCN
* GCN + GRU
* GraphSAGE

Performance was evaluated using:

* RMSE
* MAE
* R²
* MAPE

---

# Data Sources

The project integrates information from several sources.

## Landsat 8/9

Used for:

* Land Surface Temperature (LST)
* NDVI
* Albedo

Source:

https://developers.google.com/earth-engine/datasets

---

## Sentinel-3 SLSTR

Used for:

* Additional LST observations
* Downscaling experiments

Source:

https://dataspace.copernicus.eu/

---

## ERA5-Land

Used for:

* Air temperature
* Relative humidity
* Solar radiation
* Wind speed
* Precipitation

Source:

https://cds.climate.copernicus.eu/

---

## CNIG / IGN

Used for:

* Digital Elevation Models
* Urban morphology variables

Source:

https://centrodedescargas.cnig.es/

---

## OpenStreetMap

Used for:

* Building-related indicators
* Urban geometry descriptors

Source:

https://www.openstreetmap.org/

---

# Running the Project

## Important Note

The project was developed and executed entirely in Google Colab.

Due to GitHub rendering limitations with large notebooks containing extensive outputs, figures and interactive components, the notebooks are distributed as compressed files and should be opened directly in Google Colab.

The local execution workflow has not been the primary target environment.

---

## Step 1: Download the repository

Clone the repository:

```bash
git clone https://github.com/your_username/gcn-lst-prediction-seville.git

cd gcn-lst-prediction-seville
```

---

## Step 2: Open the notebooks in Google Colab

Upload the notebooks to:

https://colab.research.google.com/

or import them directly from GitHub.

---

## Step 3: Mount Google Drive

Most notebook paths assume access to Google Drive.

```python
from google.colab import drive
drive.mount('/content/drive')
```

---

## Step 4: Install dependencies

Install the required libraries:

```python
!pip install torch
!pip install torch-geometric
!pip install tensorflow
!pip install xgboost
!pip install optuna
!pip install earthengine-api
!pip install geemap
!pip install rasterio
!pip install rasterstats
```

---

# Google Earth Engine Configuration

Several sections of the project rely on Google Earth Engine (GEE).

## Create a Google Account

A Google account is required.

---

## Register for Earth Engine

Request access at:

https://earthengine.google.com/

---

## Create a Google Cloud Project

Create a project at:

https://console.cloud.google.com/

Example:

```text
gcn-lst-seville
```

---

## Enable Earth Engine API

Within Google Cloud:

```text
APIs & Services
→ Enable APIs and Services
→ Earth Engine API
```

---

## Authenticate Earth Engine

Inside Colab:

```python
import ee

ee.Authenticate()
ee.Initialize(project="your-project-id")
```

---

# Copernicus Data Space Configuration

Some Sentinel-3 workflows require access to the Copernicus Data Space Ecosystem.

Registration:

https://dataspace.copernicus.eu/

Depending on API updates, authentication tokens may need to be configured manually.

---

# Reproducibility Notes

The complete workflow depends on external services whose availability may change over time:

* Google Earth Engine
* Copernicus Data Space Ecosystem
* ERA5-Land
* CNIG services
* OpenStreetMap

Some data acquisition procedures may therefore require adaptation if APIs or authentication mechanisms change in the future.

For this reason, the repository includes processed datasets whenever possible to facilitate reproducibility.

---

# Study Area

The experiments were conducted over an urban district located in Seville (Spain).

The study area is discretized into a regular spatial grid where each grid cell corresponds to a graph node. Spatial relationships between neighbouring nodes are represented through graph edges, enabling Graph Neural Networks to exploit local spatial dependencies.

---

# Author

**Liborio Román Montes**

Double Degree in Computer Engineering and Mathematics

Master's Degree in Artificial Intelligence

University of Seville

---

# License

This project is distributed under the MIT License.
