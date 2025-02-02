# Svelte + FastAPI Application Template

This is a minimal, production-ready template for building web applications with Svelte and FastAPI.

## Project Structure

```
./
├── backend/           # FastAPI backend
│   ├── main.py       # Main application entry
│   ├── utils/        # Utility functions
│   ├── routers/      # API routes
│   └── models/       # Data models
└── frontend/         # Svelte frontend
    ├── src/          # Source code
    ├── public/       # Static files
    └── vite.config.js # Vite configuration
```

## Getting Started

### Backend Setup

1. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: .\venv\Scripts\activate
   ```

2. Install dependencies:
   ```bash
   cd backend
   pip install -r requirements.txt
   ```

3. Run the backend:
   ```bash
   uvicorn main:app --reload
   ```

### Frontend Setup

1. Install dependencies:
   ```bash
   cd frontend
   npm install
   ```

2. Run the development server:
   ```bash
   npm run dev
   ```

## Features

- Modern Svelte + Vite frontend setup
- FastAPI backend with CORS configuration
- Basic authentication system
- Structured project layout
- Development tools configuration

## Development

- Frontend runs on `http://localhost:5173` by default
- Backend API runs on `http://localhost:8000`
- API documentation available at `http://localhost:8000/docs`