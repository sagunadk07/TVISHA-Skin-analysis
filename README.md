# Tvisha Skin Care — AI Skin Analysis

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Flask](https://img.shields.io/badge/Flask-Web_App-green)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep_Learning-red)

# Tvisha Skin Care — AI Skin Analysis

A Flask web application that uses a trained EfficientNet-B0 model to detect 8 skin conditions and provide personalized product recommendations.

---

## Project Structure

```
tvisha/
├── main.py                          # Flask app entry point
├── model_inference.py               # EfficientNet-B0 model loading & inference
├── recommendation_engine.py         # CSV-driven recommendation system
├── best_skin_model_8class.pth       # Trained PyTorch model
├── pyproject.toml                   # Project dependencies (uv)
├── requirements.txt                 # pip compatibility
├── templates/
│   ├── index.html                   # Upload page
│   └── result.html                  # Results page
└── static/
    └── data/
        └── skin_recommendations.csv # Recommendation data (editable)
```

---

## Setup & Installation

### Option A — Using `uv` (recommended)

**Step 1: Install uv**

Open PowerShell as Administrator and run:
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Then **close and reopen** PowerShell (uv won't be on PATH until you do).

Verify it works:
```powershell
uv --version
```

**Step 2: Navigate to project folder**
```powershell
cd C:\path\to\tvisha
```

**Step 3: Create virtual environment**
```powershell
uv venv
```

**Step 4: Activate it**
```powershell
.venv\Scripts\activate
```

**Step 5: Install dependencies**
```powershell
uv sync
```

**Step 6: Run the app**
```powershell
python main.py
```

Open your browser at: **http://127.0.0.1:5000**

---

### Option B — Using pip (if uv isn't working)

```powershell
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

---

## Detected Skin Conditions

| Class | Condition |
|-------|-----------|
| Redness | Skin Redness & Sensitivity |
| dark spots | Dark Spots & Hyperpigmentation |
| inflammatory acne | Inflammatory Acne |
| non inflammatory acne black heads | Blackheads |
| non inflammatory acne white heads | Whiteheads |
| pigmentation | Uneven Pigmentation |
| pores | Enlarged Pores |
| wrinkles | Fine Lines & Wrinkles |

---

## Editing Recommendations

All recommendations live in `static/data/skin_recommendations.csv`.  
You can edit this file in Excel or Notepad — no code changes needed.

Column format:
```
predicted_class | concern_name | explanation | ingredients | suggested_products | skincare_advice
```

Use `|` (pipe character) to separate multiple items within a cell.

---

## Troubleshooting

**"uv is not recognized"** — Close and reopen PowerShell after installing uv.

**"Module not found: torch"** — Run `uv sync` again inside the activated venv.

**"Model file not found"** — Make sure `best_skin_model_8class.pth` is in the same folder as `main.py`.

**"Recommendation CSV not found"** — Make sure `static/data/skin_recommendations.csv` exists.

**Port already in use** — Change the port: `python main.py --port 5001` or kill the process using port 5000.
