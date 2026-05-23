# Milan Mobile Network Traffic Analysis
### MLT1 Formative 1 | African Leadership University
**Student:** Jok John Maker Kur

---

## Overview
This project performs comparative time series analysis and forecasting of 
mobile network traffic in Milan, Italy using the Telecom Italia Big Data 
Challenge dataset. Three forecasting models are implemented and compared:
- **SARIMA** — classical statistical baseline
- **LSTM** — Long Short-Term Memory neural network
- **GRU** — Gated Recurrent Unit neural network

Forecasting is performed on three geographical areas (Squares 5161, 4159, 
and 4556) for the week of December 16–22, 2013.

---

## Dataset
The full dataset (~19GB) is available from Harvard Dataverse:
- Telecom traffic data: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/EGZHFV

**Minimum data for running predictions** is included in `data/sample/`:
- `square_5161_full.parquet` — highest traffic area
- `square_4159_full.parquet` — study area 2
- `square_4556_full.parquet` — study area 3

---

## Project Structure

```
milan-traffic-forecasting/
├── milan_traffic_analysis.ipynb   ← main notebook (all tasks)
├── requirements.txt               ← dependencies
├── README.md                      ← this file
├── data/
│   └── sample/                    ← minimum data for predictions
│       ├── square_5161_full.parquet
│       ├── square_4159_full.parquet
│       └── square_4556_full.parquet
├── outputs/                       ← generated plots and tables
└── models/                        ← saved model weights
    ├── lstm_square_5161.keras
    ├── lstm_square_4159.keras
    ├── lstm_square_4556.keras
    ├── gru_square_5161.keras
    ├── gru_square_4159.keras
    └── gru_square_4556.keras
```

---

## How to Run

### Prerequisites
Python 3.10+ is required. Install dependencies using:

**Windows:**
```bash
pip install -r requirements.txt
```

**Linux/macOS:**
```bash
pip install -r requirements.txt
```

### Option 1 — Google Colab (Recommended)
1. Open the notebook in Google Colab:
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://github.com/JokMaker/milan-traffic-forecasting/blob/master/milan_traffic_analysis.ipynb)
2. Mount your Google Drive when prompted
3. Upload the `data/sample/` folder to your Drive at:
   `/content/drive/MyDrive/milan_traffic_project/data/sample/`
4. Run all cells from top to bottom

### Option 2 — Local (Windows/Linux/macOS)
1. Clone the repository:
```bash
git clone https://github.com/JokMaker/milan-traffic-forecasting.git
cd milan-traffic-forecasting
```
2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Launch Jupyter:
```bash
jupyter notebook milan_traffic_analysis.ipynb
```
4. Update the `project_path` variable in Cell 1 to your local path:
```python
project_path = '/your/local/path/milan_traffic_project'
```
5. Run all cells from top to bottom

### Option 3 — Kaggle
1. Upload the notebook to Kaggle
2. Upload the `data/sample/` folder as a Kaggle dataset
3. Update `project_path` to `/kaggle/input/milan-traffic/`
4. Run all cells

---

## Running Only the Prediction Algorithm
To run just the forecasting models using the minimum sample data:
1. Ensure `data/sample/` contains the 3 parquet files
2. Open the notebook and run:
   - Cell 1 (Environment Setup)
   - Cell 28 (3.1 Forecasting Data Preparation)
   - Cell 29 (3.2 Normalization & Sequences)
   - Cell 30 (3.3 SARIMA)
   - Cell 31 (3.4 LSTM)
   - Cell 32 (3.5 GRU)
   - Cell 33 (3.6 Model Comparison)

---

## Results Summary

| Model  | Square 5161 MAE | Square 4159 MAE | Square 4556 MAE | Avg Train Time |
|--------|----------------|----------------|----------------|----------------|
| SARIMA | 331.20         | 68.16          | 88.33          | 4.7s           |
| LSTM   | 109.54         | 17.79          | 34.04          | 40.5s          |
| GRU    | 95.68          | 15.98          | 30.56          | 28.8s          |

**Best model: GRU** — lowest MAE across all three areas.

---

## Hardware Used
- **Platform:** Google Colab (T4 GPU)
- **RAM:** 15GB
- **Storage:** Google Drive (5TB)
- **Python:** 3.12.13
- **TensorFlow:** 2.20.0
- **Statsmodels:** 0.14.6
- **Pandas:** 2.2.2
- **NumPy:** 2.0.2

---

## Video Demo
Watch the project demonstration here:
https://drive.google.com/drive/folders/1S1QlpZ3hVYwhObddckZZd5-U0yo5_3U0?usp=sharing

---

## AI Usage Statement
I used Claude (Anthropic) as a coding assistant during this project to help 
with debugging and refining written interpretations. All analytical decisions 
were mine, including the choice of models, the sequence length of 144, the 
grid search parameters, and the interpretations of the data. I ran all the 
code myself, verified the results, and understood every part of the 
implementation before including it in this submission.

---

## References
[1] G. Barlacchi et al., "A multi-source dataset of urban life in the city 
of Milan and the Province of Trentino," Sci. Data, vol. 2, p. 150055, 2015.

[2] Telecom Italia, "Telecommunications - SMS, Call, Internet - MI," 
Harvard Dataverse, V1, 2015. doi: 10.7910/DVN/EGZHFV

---

## License
This project is submitted for academic purposes at African Leadership 
University. The dataset is used under the ODbL 1.0 license.