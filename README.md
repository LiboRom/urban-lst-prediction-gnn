# GCN-LST-Prediction-Seville

Implementation and evaluation of Graph Neural Networks for spatio-temporal Land Surface Temperature (LST) prediction in an urban environment. This repository contains the code developed as part of a Master's Thesis focused on urban climate modelling using remote sensing, meteorological data and graph-based deep learning.

---

## Project Overview

Urban heat is an increasingly important challenge in modern cities. Accurate prediction of Land Surface Temperature (LST) can help urban planners better understand heat distribution and support mitigation strategies.

This project investigates the use of Graph Convolutional Networks (GCNs) for modelling the spatial and temporal dynamics of LST in a district of Seville (Spain). The proposed approach combines satellite observations, meteorological variables and urban morphology indicators within a graph-based representation of the study area.

The work also evaluates the impact of incorporating synthetic observations generated through Sentinel-3 downscaling and compares graph-based models against several machine learning and deep learning baselines.

---

## Models Evaluated

The following models were implemented and compared:

* XGBoost
* LSTM
* GRU
* Graph Convolutional Network (GCN)
* GCN + GRU
* GraphSAGE

Performance was evaluated using:

* RMSE
* MAE
* R²
* MAPE

---

## Data Sources

The project combines information from multiple sources:

### Satellite data

* Landsat 8/9

  * Land Surface Temperature (LST)
  * NDVI
  * Albedo

* Sentinel-3 SLSTR

  * LST observations
  * Downscaling experiments

### Meteorological data

ERA5-Land:

* Air temperature
* Relative humidity
* Solar radiation
* Wind speed
* Precipitation

### Urban morphology

* Digital Elevation Model (DEM)
* Building indicators
* Aspect ratio
* Urban morphology descriptors

obtained from:

* CNIG / IGN
* OpenStreetMap

---

## Repository Contents

```text
.
├── notebooks/
│   ├── TFM_LIBORIO_v2.zip
│   └── training_automatization.zip
│
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

### Main notebooks

#### TFM_LIBORIO_v2

Contains:

* Data acquisition
* Data preprocessing
* Sentinel-3 downscaling
* Graph construction
* Model implementation
* Training and evaluation

#### training_automatization

Contains:

* Automated experimentation
* Multi-seed evaluation
* Hyperparameter studies
* Ablation studies
* Comparative analysis

---

## Important Note

The notebooks were developed and executed in Google Colab.

Due to GitHub rendering limitations with large Colab notebooks containing extensive outputs and visualizations, the notebooks are distributed as compressed files and should be opened directly in Google Colab.

---

## Running the Project

### 1. Download the notebooks

Download and extract the contents of the `notebooks` directory.

### 2. Open in Google Colab

Upload the notebook to Google Colab:

https://colab.research.google.com/

### 3. Mount Google Drive

The project assumes access to Google Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```
---

## Google Earth Engine Setup

Several parts of the workflow require access to Google Earth Engine.

### Create a Google Account

A Google account is required.

### Register for Earth Engine

Request access at:

https://earthengine.google.com/

### Create a Google Cloud Project

Create a project in:

https://console.cloud.google.com/

Example:

```text
gcn-lst-seville
```

### Enable Earth Engine API

Inside the Google Cloud Console:

```text
APIs & Services
→ Enable APIs and Services
→ Earth Engine API
```

### Authenticate

In Colab:

```python
import ee

ee.Authenticate()
ee.Initialize(project="your-project-id")
```

---
## Copernicus Data Space

Some Sentinel-3 data retrieval procedures require an account in the Copernicus Data Space Ecosystem.

Registration:

https://dataspace.copernicus.eu/

### Sentinel Hub Authentication

The workflows described in Sections **1.3.3** and **1.3.4** require authentication through Sentinel Hub services.

Before running these sections, users must create OAuth credentials and obtain:

* `client_id`
* `client_secret`

To generate them:

1. Create a Copernicus Data Space Ecosystem account.
2. Log in to the dashboard.
3. Navigate to **User Settings → OAuth Clients**.
4. Create a new OAuth client.
5. Save the generated `client_id` and `client_secret`.

Example:

```python
CLIENT_ID = "your-client-id"
CLIENT_SECRET = "your-client-secret"
```

⚠️ Do not share these credentials publicly or upload them to GitHub repositories.

### Additional Access Requirements

The download procedures implemented in Sections **1.4** and **1.5** also require a valid Copernicus Data Space Ecosystem account.

Some services automatically generate temporary access tokens from the OAuth credentials. Therefore, a properly configured Copernicus account is required before executing the complete Sentinel-3 data acquisition workflow.
---

## Reproducibility

The complete workflow depends on external services whose availability may change over time:

* Google Earth Engine
* Copernicus Data Space Ecosystem
* ERA5-Land
* CNIG services
* OpenStreetMap

For this reason, some datasets are not included in the repository and may need to be regenerated following the procedures described in the notebooks.

---

## Study Area

The experiments were conducted over an urban district located in Seville (Spain).

The area is represented as a regular spatial grid where each grid cell corresponds to a graph node. Spatial relationships between neighbouring cells are encoded as graph edges, allowing Graph Neural Networks to exploit local spatial dependencies.

---

## Author

**Liborio Román Montes**

Double Degree in Computer Engineering and Mathematics

Master's Degree in Artificial Intelligence

University of Seville

---

## License

This project is released under the MIT License.
