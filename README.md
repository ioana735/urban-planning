# 🌍 Urban Heat Simulator: Bucharest Case Study


![Python](https://img.shields.io/badge/Python-3.14-blue)
![Flask](https://img.shields.io/badge/Flask-Backend-green)
![React](https://img.shields.io/badge/React-Frontend-61DAFB)
![Machine Learning](https://img.shields.io/badge/ML-Scikit_Learn-orange)
![Google Earth Engine](https://img.shields.io/badge/Geospatial-Earth_Engine-purple)


## 📌 Overview
The Urban Heat Simulator is a full-stack web application designed to help visualize and predict the Urban Heat Island (UHI) effect in Bucharest. 

Instead of just looking at static temperature maps, this tool allows users to run interactive "what-if" scenarios. By changing the land-use categories of a specific area (e.g., converting roads to green spaces), the application uses a machine learning model to predict how the local temperature will change.

## 📸 Application Interface
![Parameters panel](docs/assets/parameters_panel.png)

![map](docs/assets/map.png)

## 🚀 How It Works (Key Features)
* **Interactive Scenario Planning:** Users can select a region and dynamically swap land-use allocations to see the predicted temperature impact.
* **Predictive ML Model:** The backend is powered by a Ridge Regression model trained on 774 data points from Bucharest, correlating 24 different land-use categories (from the Copernicus Urban Atlas) with surface temperatures.
* **Smart Priority Algorithm:** A custom logic engine that ensures user simulations respect real-world spatial constraints when replacing one land-use type with another.
* **Live Satellite Data:** Integrates with the Google Earth Engine (GEE) Python API to fetch historical Land Surface Temperature (LST) data.

## 💻 Tech Stack & Architecture

* **Frontend:** React.js (handles the interactive map, user inputs, and state management).
* **Backend:** Python / Flask (serves API endpoints and processes the simulation logic).
* **Machine Learning:** Scikit-Learn (Ridge Regression, Pandas, NumPy).
* **Geospatial Data:** Google Earth Engine API & Copernicus Urban Atlas.

## 👩‍💻 My Contribution (Ioana Nițan): NO₂ Air-Quality Model

This project was built by a team of 5 during the **ROSPIN Satellite Data Processing Masterclass (2nd edition, 2025)**. My part was extending the simulator from temperature to **air quality**, with a model that predicts nitrogen dioxide (NO₂) levels from land use and temperature.

📂 **Code:** [`no2-model` branch](../../tree/no2-model) (not yet merged into `main`)

**What I built:**
* **Data download:** scripts that fetch Copernicus **CAMS** NO₂ reanalysis and **ERA5** 2 m temperature for the Bucharest area through the CDS API ([`download_no2_cams.py`](../../blob/no2-model/backend/scripts/download_no2_cams.py), [`download_temp_era5.py`](../../blob/no2-model/backend/scripts/download_temp_era5.py)).
* **Data processing:** processed the raw Copernicus data and combined it with the land-use percentages into a training dataset of ~780 rows ([`no2_training_data.csv`](../../blob/no2-model/backend/scripts/no2_training_data.csv)).
* **Model:** trained a **Random Forest regressor** (scikit-learn) that takes the land-use mix + temperature and predicts NO₂, evaluated with RMSE on a 20% hold-out split, and saved it for the backend (`urban_no2_model.joblib`) ([`download_maps.py`](../../blob/no2-model/backend/scripts/download_maps.py)).

**Tech:** Python, pandas, NumPy, scikit-learn, cdsapi, Copernicus CAMS & ERA5.

## 🛠️ Local Setup & Installation

### Prerequisites
* Node.js and npm
* Python 3.x
* A Google Earth Engine account / Service Account Key

### 1. Clone the Repository
```bash
git clone [https://github.com/yourusername/urban-planning.git](https://github.com/yourusername/urban-planning.git)
cd urban-planning
