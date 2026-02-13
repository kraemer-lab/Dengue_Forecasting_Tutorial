# Forecasting Dengue Incidence in Brazil with Python and Machine Learning Models

A hands-on tutorial on designing, training, and evaluating probabilistic forecasts of dengue incidence using the [DARTS](https://unit8co.github.io/darts/) library and Temporal Convolutional Network (TCN) models. Students work through data retrieval, cleaning, univariate and covariate-based forecasting for Rio de Janeiro, and visualisation and evaluation of forecast outputs.

**Authors:** Ciara Judge, Cathal Mills, Moritz Kraemer; February 2026

---

## What you will do

- **Target:** Forecast log(cases + 1) for **Rio de Janeiro** on a **six‑month horizon**, using 23 prescribed quantiles to summarise the predictive distribution.
- **Data:** Train on cleaned monthly dengue case data from **2015 to 2022/2023**, with optional climate, socioeconomic, and demographic covariates.
- **Workflow:** Clean the data → train a TCN model → generate predictions → visualise and evaluate (e.g. RMSE, CRPS, WIS).

Follow-up exercises extend the code to new locations, new or extra covariates, and single time-point forecasts.

---

## Repository structure: where to find everything

| Item | Location |
|------|----------|
| **Introductory presentation (slide content)** | [`ML Forecasting in Python Tutorial.txt`](https://docs.google.com/presentation/d/16HXQDXYctLxwyElXG3J06qiYyYGoXRIMMkFlnChBsYk/edit?slide=id.p1#slide=id.p1) — narrative and key points for the lecture that precedes the practical. |
| **Colab notebook (main practical)** | [`ML_forecasting_tutorial.ipynb`](ML_forecasting_tutorial.ipynb) —  a static copy is here in the repo, but open in [Google Colab](https://colab.research.google.com/drive/1vGGYLWkG1_anx2LO7dvbXOccOtiUrmZC?usp=sharing) save a copy and run step-by-step. |
| **Epidemiological training data (Brazil)** | [`data/BRA_epi_training.csv`](data/BRA_epi_training.csv) — monthly case incidence by municipality (2015–2023). |
| **Covariate data & descriptors** | [`data/README.md`](data/README.md) — full list of climate, socioeconomic, and demographic datasets; citations and licenses. Covariate *files* are obtained from the **Global.health** portal (see [Data: where to get it](#data-where-to-get-it)). |

---

## Learning outcomes

By the end of the tutorial you will be able to:

1. **Design and evaluate** forecasting models for infectious diseases.
2. **Use the Python library DARTS** for time-series forecasting (TCN and related models).
3. **Integrate covariate data** (e.g. temperature, humidity) into infectious-disease forecasting models.
4. **Adapt the code** to new locations, horizons, and predictor sets.

---

## Tutorial structure (in the notebook)

1. **Data: cleaning and preparation**  
   - Obtaining data from Global.health and loading it in Colab.  
   - Merging the epidemiological target with historical covariates and seasonal forecasts into a single table.  
   - Filtering to Rio de Janeiro and exploring the series.

2. **Model: TCN (6‑month horizon, univariate)**  
   - Building training/test splits.  
   - Defining and fitting a Temporal Convolutional Network.  
   - Generating 6‑month-ahead probabilistic forecasts (quantiles).

3. **Visualisation and evaluation**  
   - Plotting history and forecasts (including fan charts).  
   - Point metrics (e.g. RMSE) and probabilistic scores: CRPS, WIS (Weighted Interval Score).  
   - Concepts: calibration, sharpness, bias.

4. **Introducing covariates**  
   - Adding past covariates (e.g. temperature) to the TCN.  
   - Fitting and predicting with the covariate model.

5. **Exercises**  
   - Visualise the temperature-model results.  
   - Change forecast horizon (e.g. to 3 months).  
   - Fit models with other variables (e.g. relative humidity).  
   - Compare several environmental predictors and build a multivariate model.

---

## How to run the tutorial

### 1. Open the notebook in Google Colab
- Open [this notebook in google colab](https://colab.research.google.com/drive/1vGGYLWkG1_anx2LO7dvbXOccOtiUrmZC?usp=sharing).
- Go to *File → Save a Copy in Google Drive* and use this copy for the tutorial.

***OR***
- Go to [Google Colab](https://colab.research.google.com/).
- Upload or open [`ML_forecasting_tutorial.ipynb`](ML_forecasting_tutorial.ipynb) (e.g. *File → Upload notebook* or clone this repo and open the file from Colab).

### 2. Set up a data folder in Google Drive

- Create a folder in your Google Drive (e.g. `forecasting_tutorial`).
- In the notebook, set `DATA_DIR` to that folder (e.g. `'/content/drive/MyDrive/forecasting_tutorial'`) after mounting Drive.

### 3. Get the data

- **Epidemiological data:** You can use the copy in this repo ([`data/BRA_epi_training.csv`](data/BRA_epi_training.csv)) or download it from the Global.health portal (see below). Place `BRA_epi_training.csv` in your `DATA_DIR`.
- **Covariate NetCDF files:** Download the Brazil (BRA) covariate files from the **Global.health data portal** and place them in the same folder. The notebook lists the exact filenames (e.g. `BRA-reanalysis_monthly.zs.nc`, `BRA-spe06.zs.nc`, `BRA-population.zs.nc`, `BRA-seasonal_forecast_monthly.zs.nc`, etc.). One covariate file is too large to host in this repository; all covariate data for the tutorial is provided via the portal.

Detailed dataset descriptions, citations, and licenses are in **[`data/README.md`](data/README.md)**.

### 4. Run the notebook

- Mount Google Drive in the first cells, set `DATA_DIR`, install `darts`, then run the rest of the notebook in order.

---

## Data: where to get it

- **Global.health data repository:** [https://sim-dev-data.covid-19.global.health/data-downloads](https://sim-dev-data.covid-19.global.health/data-downloads)  
  Sign in with a Google account; access may need to be granted by an admin. Brazil files use the prefix **`BRA`** (e.g. `BRA_epi_training.csv`, `BRA-reanalysis_monthly.zs.nc`).
- **This repository** contains:
  - **Epidemiological:** [`data/BRA_epi_training.csv`](data/BRA_epi_training.csv).
  - **Documentation:** [data/README.md](data/README.md) describes all covariate datasets (climate, socioeconomic, demographic), file formats (CSV, NetCDF), and how they are used. The actual covariate NetCDF files (including the one that is too large to host here) are downloaded from the Global.health portal.

---

## Background: dengue and why forecast?

- **Dengue** is a mosquito-borne virus of growing public health concern (e.g. record-breaking case counts and deaths in recent years), endemic in the Americas, Africa, Australasia, and expanding into Europe.
- Dynamics are **climate-sensitive and seasonal**, so environmental and demographic variables (temperature, precipitation, urbanisation, etc.) can inform forecasts.
- **Probabilistic forecasting** (e.g. quantiles) supports decision-making under uncertainty; evaluation uses scoring rules that capture both **calibration** and **sharpness** (e.g. CRPS, WIS).

---

## Model and evaluation (short)

- **Temporal Convolutional Network (TCN):** a deep-learning architecture that uses convolutional layers so predictions at time *t* depend only on current and past information; well-suited to time series with long-range structure.
- **Evaluation:** the tutorial covers point metrics (e.g. RMSE on the median), CRPS (Continuous Ranked Probability Score), and WIS (Weighted Interval Score) and links them to calibration and sharpness.

---

## References and recommended reading

- [WHO Dengue situation reports](https://www.who.int/emergencies/disease-outbreak-news/item/2023-DON498)
- [DARTS documentation and API](https://unit8co.github.io/darts/)
- [Tutorial data descriptors (this repo)](data/README.md)
- Lim et al., *The overlapping global distribution of dengue, chikungunya, zika and yellow fever*, Nature Communications (2025)
- Colon-Gonzalez et al., *Climate-based modelling and forecasting of dengue in 3 endemic departments of Peru* (and related climate–dengue literature)

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details. Individual datasets in the [data](data/) folder or obtained from Global.health have their own licenses and citation requirements; see [data/README.md](data/README.md).
