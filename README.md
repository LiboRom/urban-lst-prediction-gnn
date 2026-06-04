# GCN-LST-Prediction-Seville

## Overview

This repository contains the code developed for the Master's Thesis:

**"Implementation and Evaluation of a Graph Convolutional Network for Spatio-Temporal Land Surface Temperature Prediction in an Urban Environment"**

The objective of this project is to predict **Land Surface Temperature (LST)** in an urban district of Seville (Spain) by combining:

* Satellite imagery from Landsat 8/9
* Sentinel-3 observations
* Meteorological variables from ERA5-Land
* Urban morphology indicators
* Graph Neural Networks (GCN)

The project explores the integration of remote sensing, geospatial data processing and machine learning techniques for urban climate modelling.

---

## Main Contributions

* Construction of a spatial graph representing an urban area.
* Integration of multi-source geospatial datasets.
* Downscaling of Sentinel-3 LST observations.
* Development of Graph Convolutional Network models.
* Comparison against traditional Machine Learning and Deep Learning baselines:

  * XGBoost
  * LSTM
  * GRU
  * GCN
  * GCN + GRU
  * GraphSAGE
* Automated experimentation framework for large-scale model evaluation.

---

## Repository Structure

```text
.
├── TFM_LIBORIO_v2.ipynb
├── training_automatization.ipynb
├── data/
├── outputs/
├── requirements.txt
├── LICENSE
└── README.md
```

### Main notebooks

#### `TFM_LIBORIO_v2.ipynb`

Main notebook containing:

* Data acquisition
* Data preprocessing
* Graph construction
* Downscaling pipeline
* Model implementations
* Evaluation procedures

#### `training_automatization.ipynb`

Notebook dedicated to:

* Automated experimentation
* Hyperparameter studies
* Ablation studies
* Multi-seed evaluation
* Comparative analysis of models

---

## Study Area

The experiments were conducted over an urban district located in the city of Seville (Spain).

The study area is discretized into a regular spatial grid whose nodes represent urban locations. Graph edges connect neighbouring nodes, allowing the GCN models to exploit spatial dependencies.

---

## Data Sources

### Landsat 8/9

Used for:

* Land Surface Temperature (LST)
* NDVI
* Surface characteristics

Source:

https://developers.google.com/earth-engine/datasets

---

### Sentinel-3 SLSTR

Used for:

* Additional LST observations
* Downscaling experiments

Source:

https://dataspace.copernicus.eu/

---

### ERA5-Land

Used for:

* Air temperature
* Relative humidity
* Solar radiation
* Wind speed
* Precipitation

Source:

https://cds.climate.copernicus.eu/

---

### CNIG / IGN

Used for:

* Digital Elevation Models
* Urban morphology variables

Source:

https://centrodedescargas.cnig.es/

---

### OpenStreetMap

Used for:

* Building-related indicators
* Urban geometry descriptors

Source:

https://www.openstreetmap.org/

---

## Running the Project Locally

### 1. Clone the repository

```bash
git clone https://github.com/your_username/gcn-lst-prediction-seville.git

cd gcn-lst-prediction-seville
```

---

### 2. Create a Python environment

```bash
python -m venv venv

source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

---

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Google Earth Engine Requirements

Several sections of the project use Google Earth Engine (GEE).

To reproduce these experiments:

### Create a Google account

A Google account is required.

---

### Register in Earth Engine

Request access:

https://earthengine.google.com/

---

### Create a Google Cloud Project

Open:

https://console.cloud.google.com/

Create a new project.

Example:

```text
gcn-lst-project
```

---

### Enable Earth Engine API

Inside Google Cloud:

```text
APIs & Services
    → Enable APIs
        → Earth Engine API
```

Activate it.

---

### Authenticate locally

Install the Earth Engine package:

```bash
pip install earthengine-api
```

Authenticate:

```bash
earthengine authenticate
```

A browser window will open.

---

### Initialize Earth Engine

Inside Python:

```python
import ee

ee.Initialize(project="your-project-id")
```

---

## Sentinel-3 Access

Some experiments require downloading Sentinel-3 products.

A Copernicus Data Space Ecosystem account may be necessary:

https://dataspace.copernicus.eu/

Depending on API changes, authentication tokens may need to be configured manually.

---

## Reproducibility Notes

The complete workflow depends on external services whose availability may change over time:

* Google Earth Engine
* Copernicus Data Space Ecosystem
* ERA5-Land archives
* CNIG services

Some datasets used during the thesis are not included in this repository due to storage limitations.

Users may need to regenerate the datasets following the procedures described in the notebook.

---

## Results

The repository contains implementations and experiments comparing:

| Model     | Type                        |
| --------- | --------------------------- |
| XGBoost   | Machine Learning            |
| LSTM      | Recurrent Neural Network    |
| GRU       | Recurrent Neural Network    |
| GCN       | Graph Neural Network        |
| GCN + GRU | Spatio-Temporal Graph Model |
| GraphSAGE | Graph Neural Network        |

Performance is evaluated using:

* RMSE
* MAE
* R²
* MAPE

---

## Author

**Liborio Román Montes**

Double Degree in Computer Engineering and Mathematics

Master's Degree in Artificial Intelligence

University of Seville

---

## License

This project is distributed under the MIT License.
