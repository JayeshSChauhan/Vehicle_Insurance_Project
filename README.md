# Vehicle Insurance ML Pipeline

A complete end‑to‑end Machine Learning pipeline for vehicle insurance claim prediction, from data ingestion through model training, evaluation, and deployment.

---

## 🚀 Features

- **Data Ingestion & Validation**  
  Fetch raw data, validate against schema, log issues.

- **Data Transformation**  
  Clean, feature‑engineer, and prepare datasets for training.

- **Model Training & Evaluation**  
  Train your model, evaluate performance metrics, generate reports.

- **Model Pushing**  
  Serialize and upload the trained model to S3‑compatible storage.

- **Flask Demo**  
  A simple REST API (`app.py`) to serve predictions.

- **Notebooks**  
  - `notebook/exp-notebook.ipynb` — exploratory analysis  
  - `notebook/mongoDB_demo.ipynb` — demo of MongoDB integration  

---

## 📂 Project Structure

```
Vehicle_Insurance_Project/
├── artifact/              # All generated artifacts: models, reports, artifacts
├── config/                
│   ├── model.yaml         # Training parameters
│   └── schema.yaml        # Data schema definitions
├── logs/                  # Log files (Pipeline runs, errors, etc.)
├── notebook/              
│   ├── data.csv           # Sample data CSV  
│   ├── exp-notebook.ipynb 
│   └── mongoDB_demo.ipynb 
├── src/                   
│   ├── components/        # Core pipeline modules
│   │   ├── data_ingestion.py
│   │   ├── data_validation.py
│   │   ├── data_transformation.py
│   │   ├── model_trainer.py
│   │   ├── model_evaluation.py
│   │   └── model_pusher.py
│   ├── cloud_storage/     # S3‑compatible upload logic
│   │   └── aws_storage.py
│   └── __init__.py
├── static/                # Static assets (HTML, CSS)
├── templates/             # Flask HTML templates
├── app.py                 # Flask API for online predictions
├── demo.py                # Quick demo script
├── structure.py           # Orchestrator: runs full pipeline
├── setup.py               # Project packaging info
└── .dockerignore          # Docker ignore rules
```

---

## ⚙️ Prerequisites

- Python 3.8 or higher  
- `pip`  

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## 🔧 Configuration

1. **`config/schema.yaml`**  
   Defines input data schema (columns, types, null‑checks).

2. **`config/model.yaml`**  
   Training hyperparameters:
   ```yaml
   train_test_split: 0.2
   random_state: 42
   model:
     type: XGBoost
     params:
       n_estimators: 100
       learning_rate: 0.1
   ```

3. **Cloud Storage Credentials**  
   Update your environment variables (or a `.env` file) for S3‑compatible upload:
   ```bash
   export AWS_ACCESS_KEY_ID="..."
   export AWS_SECRET_ACCESS_KEY="..."
   export AWS_ENDPOINT_URL="https://s3.us-west-004.backblazeb2.com"
   export AWS_REGION="us-west-004"
   ```

---

## 🏃‍♂️ Running the Pipeline

To run the **full pipeline** (ingestion → validation → training → evaluation → pushing):
```bash
python structure.py
```

- Artifacts (models, reports) appear under `artifact/`.
- Logs are written to `logs/`.

---

## 🔍 Exploratory Notebooks

Launch Jupyter and open:
```bash
jupyter notebook notebook/exp-notebook.ipynb
jupyter notebook notebook/mongoDB_demo.ipynb
```

---

## 💻 Flask Demo

Start the API server:
```bash
python app.py
```

- **POST** JSON payload to `http://localhost:5000/predict`  
- Returns model predictions as JSON.

Use the included `demo.py` for a quick example:
```bash
python demo.py
```

---

## 📦 Packaging

This repo uses `setup.py` so you can install it as a package:
```bash
pip install -e .
```

---

## 📈 Logs & Monitoring

- Logs are under `logs/`  
- Check `logs/pipeline.log` for run‑by‑run status.

---

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more details.

---

## 🙏 Acknowledgements

- Inspired by standard MLOps best practices  
- Mentor’s original AWS‑based implementation  
- Uses Backblaze B2 as S3‑compatible storage  

---

**Enjoy!** 🎉 Feel free to open an issue or drop a ⭐ if you find this useful.
