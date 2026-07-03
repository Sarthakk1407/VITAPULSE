# VitaPulse

**Cardiovascular Disease Risk Prediction Platform**

A comprehensive full-stack web application for predicting cardiovascular disease risk using machine learning. VitaPulse provides hospital staff with intelligent risk assessment, patient management, and clinical decision support features.

---

##  Features

- **AI-Powered Risk Prediction**: ML model predicts cardiovascular disease risk from patient health metrics
- **Patient Management**: Complete patient records with health data, ECG analysis, and trend tracking
- **Clinical Dashboard**: Real-time insights with visualizations for BP, BMI, and health trends
- **Doctor Notes**: Secure documentation and patient notes with timestamp tracking
- **PDF Reports**: Generate professional medical reports for patient records
- **Hospital Authentication**: Secure role-based access (Hospital Staff, Doctors, Admin)
- **Visit Timeline**: Track patient visits, outcomes, and clinical history
- **Audit Trail**: Complete audit logs for compliance and accountability
- **Admin Dashboard**: Management interface for requests, approvals, and system statistics
- **Report Delivery**: Email integration for sending patient reports securely

---

##  Tech Stack

### Backend
- **Framework**: Flask (Python 3.11)
- **ML**: scikit-learn, pandas, numpy
- **Database**: Google Cloud Firestore
- **Authentication**: Firebase Admin SDK
- **Server**: Gunicorn
- **API Communication**: REST, CORS enabled
- **PDF Generation**: ReportLab
- **Email**: Integrated SMTP support

### Frontend
- **Framework**: React 19 with Vite
- **Authentication**: Firebase Auth
- **Charts**: Recharts
- **Routing**: React Router v7
- **Styling**: CSS (custom + component-specific)
- **Module Bundler**: Vite with HMR

### Infrastructure
- **Cloud Database**: Google Cloud Firestore
- **Cloud Storage**: Google Cloud Storage
- **Authentication**: Firebase Authentication
- **Deployment**: Procfile-ready (Heroku compatible)

---

##  Project Structure

```
VitaPulse/
├── backend/                          # Flask backend application
│   ├── app.py                        # Main Flask application
│   ├── config.py                     # Configuration settings
│   ├── requirements.txt              # Python dependencies
│   ├── firebase.py                   # Firebase initialization
│   │
│   ├── ml/                           # Machine Learning module
│   │   ├── predictor.py              # Risk prediction engine
│   │   ├── preprocess.py             # Data preprocessing
│   │   └── train_model.py            # Model training script
│   │
│   ├── models/                       # Trained ML models
│   │   ├── model.pkl                 # Trained classifier
│   │   └── scaler.pkl                # Feature scaler
│   │
│   ├── routes/                       # API endpoints
│   │   ├── auth.py                   # Authentication routes
│   │   ├── patients.py               # Patient management
│   │   ├── predict.py                # Risk prediction API
│   │   ├── report.py                 # Report generation
│   │   ├── doctor_notes.py           # Doctor notes API
│   │   ├── timeline.py               # Visit timeline
│   │   ├── dashboard.py              # Dashboard data
│   │   ├── hospital_request.py       # Hospital requests
│   │   ├── admin_approve.py          # Admin approval routes
│   │   ├── admin_reject.py           # Admin rejection routes
│   │   ├── admin_audit.py            # Audit log routes
│   │   ├── admin_stats.py            # Statistics routes
│   │   └── send_report.py            # Report delivery
│   │
│   ├── utils/                        # Utility functions
│   │   ├── auth.py                   # Auth helpers
│   │   ├── validators.py             # Data validation
│   │   ├── email_sender.py           # Email service
│   │   ├── pdf_generator.py          # PDF generation
│   │   ├── health_score.py           # Health scoring logic
│   │   ├── ecg_validator.py          # ECG validation
│   │   ├── risk_mapper.py            # Risk classification
│   │   ├── confidence.py             # Confidence scoring
│   │   └── explain.py                # Model explanation
│   │
│   ├── scripts/                      # Utility scripts
│   │   ├── create_admin_user.py
│   │   ├── export_records_to_csv.py
│   │   ├── set_admin_claim.py
│   │   └── export_retraining_csv.py
│   │
│   ├── Procfile/                     # Deployment config
│   └── readme.md                     # Backend README
│
├── frontend/                         # React + Vite frontend
│   ├── package.json                  # Node dependencies
│   ├── vite.config.js                # Vite configuration
│   ├── eslint.config.js              # ESLint configuration
│   ├── index.html                    # HTML entry point
│   │
│   ├── src/
│   │   ├── main.jsx                  # React entry point
│   │   ├── App.jsx                   # Root component
│   │   ├── firebase.js               # Firebase config
│   │   │
│   │   ├── api/                      # API integration
│   │   │   ├── authApi.js            # Auth API calls
│   │   │   ├── dashboard.js          # Dashboard data
│   │   │   ├── patient.js            # Patient APIs
│   │   │   ├── predict.js            # Prediction API
│   │   │   ├── reportApi.js          # Report APIs
│   │   │   ├── timelineApi.js        # Timeline APIs
│   │   │   ├── DoctorNote.js         # Doctor notes APIs
│   │   │   ├── patientDetails.js     # Patient details
│   │   │   └── recordApi.js          # Records APIs
│   │   │
│   │   ├── components/               # Reusable React components
│   │   │   ├── BMITrend.jsx
│   │   │   ├── BPTrend.jsx
│   │   │   ├── DoctorNote.jsx
│   │   │   └── ... (other components)
│   │   │
│   │   ├── pages/                    # Page components
│   │   ├── services/                 # Business logic services
│   │   ├── styles/                   # Global styles
│   │   └── utils/                    # Utility functions
│   │
│   └── public/                       # Static assets
│
├── frontend_v2/                      # Static HTML frontend (alternative)
│   ├── *.html                        # HTML pages
│   ├── css/                          # Stylesheets
│   └── js/                           # JavaScript files
│
├── .gitignore                        # Git ignore rules
├── README.md                         # This file
└── cardio_records_export.csv         # Sample data

```

---

##  Getting Started

### Prerequisites

- **Python 3.11+** (for backend)
- **Node.js 18+** (for frontend)
- **Firebase Project** with Firestore database
- **Git**

### Backend Setup

1. **Navigate to backend directory**:
   ```bash
   cd backend
   ```

2. **Create virtual environment**:
   ```bash
   python -m venv venv
   # On Windows
   venv\Scripts\activate
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Firebase**:
   - Download `serviceAccountKey.json` from Firebase Console
   - Place it in `backend/` directory (or set `FIREBASE_KEY_PATH` environment variable)

5. **Set up environment variables** (create `.env` file):
   ```env
   FLASK_ENV=development
   DEBUG=True
   FIREBASE_KEY_PATH=./serviceAccountKey.json
   ```

6. **Run the backend**:
   ```bash
   python app.py
   ```
   The backend will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory**:
   ```bash
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Firebase** (`src/firebase.js`):
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_AUTH_DOMAIN",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_STORAGE_BUCKET",
     messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

4. **Run development server**:
   ```bash
   npm run dev
   ```
   The frontend will run on `http://localhost:5173`

5. **Build for production**:
   ```bash
   npm run build
   npm run preview
   ```

---

##  API Endpoints

### Authentication
- `POST /auth/register` - Register new hospital staff
- `POST /auth/login` - Login user
- `POST /auth/logout` - Logout user
- `GET /auth/verify` - Verify authentication token

### Predictions
- `POST /predict` - Predict cardiovascular risk
  ```json
  {
    "age": 45,
    "gender": 2,
    "height": 170,
    "weight": 72,
    "ap_hi": 130,
    "ap_lo": 85,
    "cholesterol": 2,
    "gluc": 1,
    "smoke": 0,
    "alco": 0,
    "active": 1
  }
  ```

### Patients
- `GET /patients` - List all patients
- `GET /patients/{id}` - Get patient details
- `POST /patients` - Create new patient
- `PUT /patients/{id}` - Update patient
- `DELETE /patients/{id}` - Delete patient

### Doctor Notes
- `GET /doctor-notes/{patientId}` - Get notes for patient
- `POST /doctor-notes` - Add doctor note
- `PUT /doctor-notes/{noteId}` - Update note
- `DELETE /doctor-notes/{noteId}` - Delete note

### Reports
- `POST /report/generate` - Generate PDF report
- `GET /report/{reportId}` - Retrieve report
- `POST /report/send-email` - Send report via email

### Timeline
- `GET /timeline/{patientId}` - Get patient visit timeline
- `POST /timeline/event` - Add timeline event
- `GET /dashboard` - Get dashboard summary data

### Admin Routes
- `GET /admin/requests` - List approval requests
- `POST /admin/approve/{requestId}` - Approve request
- `POST /admin/reject/{requestId}` - Reject request
- `GET /admin/audit` - Get audit logs
- `GET /admin/stats` - Get system statistics

---

##  Machine Learning

### Model Training

The ML module includes:
- **Predictor** (`ml/predictor.py`) - Makes predictions using trained model
- **Preprocessor** (`ml/preprocess.py`) - Handles feature scaling and normalization
- **Trainer** (`ml/train_model.py`) - Trains the risk prediction model

### Features Used

The model predicts cardiovascular disease risk based on:
- Age, Gender
- Physical measurements (Height, Weight, BMI)
- Blood pressure (Systolic, Diastolic)
- Cholesterol levels
- Glucose levels
- Lifestyle factors (Smoking, Alcohol use, Physical activity)

### Model Files
- `backend/models/model.pkl` - Trained classifier
- `backend/models/scaler.pkl` - Feature scaler for normalization

---

##  Security & Authentication

- **Firebase Auth**: Hospital staff authentication with email/password
- **JWT Tokens**: API request authentication
- **Role-Based Access Control**: Admin, Doctor, Staff roles
- **Audit Logging**: All critical operations logged with timestamps
- **CORS Security**: Configured CORS for authorized domains
- **Environment Variables**: Sensitive keys stored in `.env` (gitignored)

---

##  Development Workflow

### Running Tests
```bash
# Backend
cd backend
pytest

# Frontend
cd frontend
npm test
```

### Linting
```bash
# Backend
flake8 backend/

# Frontend
npm run lint
```

### Code Formatting
```bash
# Backend
black backend/
```

---

##  Deployment

### Heroku Deployment

The project includes a `Procfile` for Heroku deployment:

```bash
# 1. Create Heroku app
heroku create vitapulse

# 2. Set environment variables
heroku config:set DEBUG=False
heroku config:set FLASK_ENV=production

# 3. Deploy
git push heroku main
```

### Docker Deployment (Optional)

Create a `Dockerfile`:
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY backend/requirements.txt .
RUN pip install -r requirements.txt
COPY backend/ .
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:create_app()"]
```

---

##  Database Schema

### Patients Collection
```json
{
  "id": "string",
  "firstName": "string",
  "lastName": "string",
  "age": "number",
  "gender": "number",
  "height": "number",
  "weight": "number",
  "email": "string",
  "phone": "string",
  "createdAt": "timestamp",
  "updatedAt": "timestamp",
  "hospitalId": "string"
}
```

### Predictions Collection
```json
{
  "patientId": "string",
  "riskScore": "number",
  "riskLevel": "string",
  "confidence": "number",
  "predictedAt": "timestamp",
  "hospitalId": "string"
}
```

### DoctorNotes Collection
```json
{
  "patientId": "string",
  "doctorId": "string",
  "notes": "string",
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

---

##  Contributing

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit changes**:
   ```bash
   git commit -m 'Add amazing feature'
   ```
4. **Push to branch**:
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Code Standards
- Follow PEP 8 for Python
- Follow ESLint rules for JavaScript
- Add comments for complex logic
- Update README for new features
- Write unit tests for new code

---

##  Scripts

### Backend Scripts
```bash
# Create admin user
python scripts/create_admin_user.py

# Export patient records to CSV
python scripts/export_records_to_csv.py

# Set admin claims for user
python scripts/set_admin_claim.py

# Export data for model retraining
python scripts/export_retraining_csv.py
```

---

##  Troubleshooting

### Backend Issues

**ModuleNotFoundError**:
```bash
# Ensure virtual environment is activated
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
```

**Firebase Connection Error**:
- Check `serviceAccountKey.json` is in correct location
- Verify Firebase project credentials in config

### Frontend Issues

**Module not found**:
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

**Port already in use**:
```bash
# Kill process on port 5173
lsof -ti:5173 | xargs kill -9  # macOS/Linux
```

---

##  License

This project is licensed under the **MIT License** - see the LICENSE file for details.

---

##  Team & Contact

**VitaPulse Development Team**

For issues, questions, or suggestions:
-  Email: support@vitapulse.dev
-  Issues: [GitHub Issues](https://github.com/yourorg/vitapulse/issues)
-  Discussions: [GitHub Discussions](https://github.com/yourorg/vitapulse/discussions)

---

##  Acknowledgments

- Built with Flask, React, and Firebase
- ML powered by scikit-learn
- Data visualization with Recharts
- Medical expertise from healthcare professionals

---

**Last Updated**: January 2026

 If you find this project helpful, please consider giving it a star on GitHub!
