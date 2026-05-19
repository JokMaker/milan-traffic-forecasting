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
- Milan grid data: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/QJWLFU

**Minimum data for running predictions** is included in `data/sample/`:
- `square_5161_full.parquet` — highest traffic area
- `square_4159_full.parquet` — study area 2
- `square_4556_full.parquet` — study area 3

---

## Project Structure



milan_traffic_project/
├── milan_traffic_analysis.ipynb   ← main notebook (all tasks)
├── requirements.txt               ← dependencies
├── README.md                      ← this file
├── data/
│   ├── sample/                    ← minimum data for predictions
│   │   ├── square_5161_full.parquet
│   │   ├── square_4159_full.parquet
│   │   └── square_4556_full.parquet
│   └── milano-grid.geojson        ← Milan grid tessellation
├── outputs/                       ← generated plots and tables
└── models/                        ← saved model weights
├── lstm_square_5161.keras
├── lstm_square_4159.keras
├── lstm_square_4556.keras
├── gru_square_5161.keras
├── gru_square_4159.keras
└── gru_square_4556.keras

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
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](YOUR_COLAB_LINK_HERE)
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
| SARIMA | 331.20         | 68.16          | 88.33          | 4.2s           |
| LSTM   | 104.34         | 20.12          | 31.91          | 30.9s          |
| GRU    | 99.09          | 16.11          | 28.96          | 32.5s          |

**Best model: GRU** — lowest MAE across all three areas.

---

## Hardware Used
- **Platform:** Google Colab (T4 GPU)
- **RAM:** 15GB
- **Storage:** Google Drive (5TB)
- **Python:** 3.10
- **TensorFlow:** 2.15.0

---

## AI Usage Statement
Claude (Anthropic) was used as an AI assistant throughout this project to 
support code development, debugging, and analysis interpretation. All 
analytical decisions, interpretations, and conclusions reflect the author's 
own understanding. The use of AI tools is disclosed in accordance with the 
ALU academic integrity policy.

---

## References
[1] G. Barlacchi et al., "A multi-source dataset of urban life in the city 
of Milan and the Province of Trentino," Sci. Data, vol. 2, p. 150055, 2015.

[2] Telecom Italia, "Telecommunications - SMS, Call, Internet - MI," 
Harvard Dataverse, V1, 2015. doi: 10.7910/DVN/EGZHFV

[3] Telecom Italia, "Shape of Milan Grid," Harvard Dataverse, V1, 2015. 
doi: 10.7910/DVN/QJWLFU

---

## License
This project is submitted for academic purposes at African Leadership 
University. The dataset is used under the ODbL 1.0 license.
