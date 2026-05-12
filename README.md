# Smart Food Redistribution AI Module

This repository contains the AI component for a Smart Food Redistribution System. It provides:

- Food Freshness Prediction using a Decision Tree Classifier
- NGO Recommendation based on donor location, capacity, distance, and urgency
- Waste Quantity Prediction using Linear Regression
- Optional image-based freshness detection with OpenCV
- Flask API endpoints for future integration with frontend/backend

## Project Structure

- `ai_module/` - modular AI logic
- `datasets/` - CSV datasets for training and evaluation
- `models/` - saved model and dataset artifacts
- `training/` - scripts to train models and save artifacts
- `tests/` - basic integration tests using Flask test client
- `app.py` - Flask API server
- `requirements.txt` - Python dependencies

## Setup

1. Create a Python environment and install dependencies:

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

2. Train the models:

```bash
python training/train_freshness.py
python training/train_waste.py
python training/train_ngo.py
```

3. Run the Flask API:

```bash
python app.py
```

## API Endpoints

- `POST /predict-freshness`
- `POST /predict-waste`
- `POST /recommend-ngo`
- `POST /predict-all`
- `POST /predict-image-freshness`

Example payload for `/predict-all`:

```json
{
  "food_type": "vegetables",
  "cooked_hours_ago": 2,
  "temperature_c": 22,
  "humidity": 60,
  "event_type": "wedding",
  "guest_count": 120,
  "food_prepared_kg": 40,
  "donor_latitude": 12.9716,
  "donor_longitude": 77.5946,
  "urgency_level": "medium"
}
```

## Notes

- The dataset files are intentionally small and explainable for beginners.
- The NGO recommender uses distance and available capacity scoring instead of a complex machine learning model.
- `predict_image_freshness` is optional and requires `opencv-python`.

## Testing

Run the integration tests:

```bash
python -m unittest tests.test_ai_module.py
```
