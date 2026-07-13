# AI Mood Analyzer

An end-to-end AI-powered mood analyzer that detects emotions from text using machine learning. Designed with production-grade architecture, the project cleanly separates training, inference, and user interface layers for scalability and maintainability.

---

## Technology Stack

- **Python 3.11** - Core language
- **Scikit-learn** - Machine learning framework
- **FastAPI** - Inference API service
- **Pydantic** - Data validation
- **Streamlit** - Web-based user interface
- **MLflow** - Experiment tracking
- **Docker** - Container orchestration

---

## Key Features

- **Text-based Emotion Detection** - Accurately classifies user input into emotion categories
- **Scikit-learn ML Model** - Logistic Regression (One-vs-Rest) trained offline
- **FastAPI Inference Service** - High-performance REST API for real-time predictions
- **Streamlit Frontend** - User-friendly interface for emotion analysis
- **Production-Ready Architecture** - Modular design with separation of concerns
- **Docker Support** - Containerized deployment for training and inference

---

## Model Details

**Algorithm**: Logistic Regression with One-vs-Rest strategy  
**Vectorization Method**: TF-IDF  
**Framework**: Scikit-learn with MLflow integration

The model is trained offline and persisted as artifacts, which are loaded at runtime by the inference API. This design ensures fast inference without requiring model retraining during prediction.

---

## API Specification

### Inference Endpoint

**Method**: `POST /predict`

**Request Body**:
```json
{
  "texts": ["I feel excited about my new job!"]
}
```

**Response**:
```json
{
  "emotion": "happy"
}
```

**Features**:
- Input validation using Pydantic
- Batch prediction support for multiple texts
- Comprehensive error handling
- Health-check endpoint availability

---

## System Architecture

```
User (Streamlit UI)
        |
        v
FastAPI Inference Service
        |
        v
Saved ML Artifacts (model, vectorizer)
        ^
        |
Offline Training Pipeline
```

The Streamlit application communicates exclusively through the API, ensuring a clean separation between the frontend and model layers.

---

## Getting Started

### Prerequisites
- Python 3.11 or higher
- pip package manager
- Virtual environment (recommended)

### Installation & Setup

1. **Create and activate a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Start the FastAPI inference service**:
   ```bash
   uvicorn inference.app:app --host 0.0.0.0 --port 8000 --reload
   ```

4. **Access the API documentation**:
   Open your browser and navigate to `http://localhost:8000/docs`

5. **Run the Streamlit application**:
   ```bash
   cd streamlit_app
   pip install -r requirements.txt
   streamlit run app.py
   ```

6. **Access the web interface**:
   Open your browser and navigate to `http://localhost:8501`

---

## Docker Deployment

The project includes two Dockerfiles for containerized deployment:

- **Dockerfile.train** - Training pipeline container
- **Dockerfile.infer** - Inference service container

Docker Compose can be used to orchestrate multiple services for production environments.

---

## Configuration Management

Configuration parameters are stored in `config.json`, including:
- Model metadata
- Hyperparameters
- Feature specifications

This approach ensures version control, reproducibility, and easy parameter management.

---

## Project Rationale

This project demonstrates professional machine learning practices:

- End-to-end ML system design with clear separation of concerns
- Production-grade API and UI integration
- Clean, maintainable code organization
- Real-world deployment considerations
- MLOps fundamentals without unnecessary complexity

---

## Author

**Shreyash Singhai**

---

## License

[Specify your license here]
