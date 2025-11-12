# Doveable AI Website Builder

## Overview
A full-stack AI-powered website builder that uses multiple LLM providers (Google Gemini, Groq, OpenAI, Emergent LLM) to generate complete, multi-page, interactive web applications from natural language prompts.

## Project Architecture

### Frontend
- **Framework**: React 19.2.0 with TypeScript
- **Build Tool**: Vite 6.2.0
- **Styling**: Tailwind CSS (via CDN)
- **Port**: 5000 (configured for Replit)

### Backend (Optional - NEW!)
- **Framework**: FastAPI (Python)
- **LLM Providers**: Google Gemini, Groq, OpenAI, Emergent LLM
- **Database**: MongoDB (optional, for project persistence)
- **Port**: 8000 (default)
- **API Documentation**: Available at `/docs` when backend is running

### Storage
- **Frontend**: LocalStorage for user data and configurations
- **Backend**: MongoDB (optional) for persistent project storage

## Key Features
- **Multi-LLM Support**: Choose from Gemini, Groq, OpenAI, or Emergent LLM
- **Full-Stack Architecture**: React frontend + FastAPI backend
- **AI-Powered Generation**: Create complete websites from prompts
- **Project Management**: Save, edit, and manage multiple projects
- **File Explorer & Code Editor**: Browse and edit generated files
- **Live Preview**: Real-time preview of generated websites
- **Admin Panel**: Manage API keys and configurations
- **Vercel-Ready**: Optimized for deployment on Vercel

## Environment Variables

### Frontend (.env.local)
- `GEMINI_API_KEY`: Required for AI functionality (Gemini API key from Google)
- `VITE_API_URL`: Optional - Backend API URL (leave empty for frontend-only mode)

### Backend (backend/.env)
- `GEMINI_API_KEY`: Google Gemini API key
- `GROQ_API_KEY`: Groq API key (optional)
- `EMERGENT_LLM_KEY`: Emergent LLM API key (optional)
- `OPENAI_API_KEY`: OpenAI API key (optional)
- `MONGO_URL`: MongoDB connection string (optional)
- `DB_NAME`: Database name (optional, default: doveable_ai)
- `CORS_ORIGINS`: Allowed CORS origins (default: *)

## Running Locally

### Frontend Only (Current Setup):
```bash
npm install
npm run dev
```
Visit http://localhost:5000

### Full Stack (Frontend + Backend):
**Terminal 1 - Backend:**
```bash
cd backend
pip install -r requirements.txt
python main.py
```

**Terminal 2 - Frontend:**
```bash
npm run dev
```

## Recent Changes (2025-11-12)

### Frontend Setup
- Configured Vite to use port 5000 (required for Replit)
- Added HMR configuration for Replit's proxy environment
- Set up workflow for automatic server restart
- Installed all frontend dependencies (React, Vite, TypeScript, Axios)

### Backend Addition (NEW!)
- Created FastAPI backend with Python
- Implemented LLM service supporting multiple providers:
  - Google Gemini
  - Groq AI
  - OpenAI
  - Emergent LLM
- Added MongoDB integration for project storage
- Created API endpoints for:
  - LLM text generation (`/api/llm/generate`)
  - Provider listing (`/api/llm/providers`)
  - Health checks (`/api/llm/health`)
  - Project CRUD operations (`/api/projects/*`)
- Added backend API service for frontend integration

### Deployment
- Created `vercel.json` for Vercel deployment
- Configured for both frontend and backend deployment
- Added comprehensive deployment documentation (DEPLOYMENT.md)
- Updated README with deployment instructions

### Documentation
- Created comprehensive README.md
- Added DEPLOYMENT.md for deployment guide
- Updated .gitignore for Python and environment files
- Added .env.example files for both frontend and backend

## File Structure

```
doveable-ai-website-builder/
├── components/              # React UI components
│   ├── HomePage.tsx
│   ├── WebsiteBuilder.tsx
│   ├── AdminPanel.tsx
│   └── ...
├── services/               # Frontend services
│   ├── geminiService.ts
│   ├── backendApiService.ts  # NEW! Backend API client
│   ├── githubService.ts
│   └── ...
├── backend/                # NEW! Python backend
│   ├── main.py            # FastAPI application
│   ├── database.py        # MongoDB connection
│   ├── requirements.txt   # Python dependencies
│   ├── services/
│   │   └── llm_service.py # Multi-provider LLM service
│   ├── routes/
│   │   ├── llm_routes.py  # LLM API endpoints
│   │   └── project_routes.py # Project management
│   └── models/
│       └── schemas.py     # Pydantic models
├── App.tsx                # Main React component
├── index.tsx              # React entry point
├── vite.config.ts         # Vite configuration
├── vercel.json            # NEW! Vercel deployment config
├── package.json           # Node dependencies
├── README.md              # Project documentation
├── DEPLOYMENT.md          # NEW! Deployment guide
└── replit.md             # This file
```

## API Endpoints (Backend)

### LLM Endpoints
- `POST /api/llm/generate` - Generate text using LLM
  - Request: `{ "prompt": "...", "provider": "auto|groq|gemini|openai" }`
  - Response: `{ "success": true, "response": "...", "provider": "...", "model": "..." }`
- `GET /api/llm/providers` - Get list of available LLM providers
- `GET /api/llm/health` - Check LLM service health status

### Project Endpoints
- `GET /api/projects/` - List all projects
- `POST /api/projects/` - Create new project
- `GET /api/projects/{id}` - Get project by ID
- `DELETE /api/projects/{id}` - Delete project

## Deployment Options

### Option 1: Replit (Frontend Only)
Currently running on Replit with frontend-only mode. The app uses the Gemini API directly from the browser.

### Option 2: Vercel (Full Stack)
Deploy both frontend and backend to Vercel:
```bash
vercel --prod
```
See DEPLOYMENT.md for detailed instructions.

### Option 3: Split Deployment
- Frontend: Deploy to Vercel/Netlify/Replit
- Backend: Deploy to Heroku/Railway/Render
- Set `VITE_API_URL` to point to your backend

## User Preferences
None specified yet.
