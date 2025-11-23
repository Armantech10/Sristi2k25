# Sristi2k25 
# Adaptive EdTech Personalized Learning Platform

A comprehensive, production-ready adaptive learning platform that personalizes educational content based on student knowledge state, learning patterns, and accessibility needs.

## 🏗️ Architecture

This is a monorepo containing:

- **Frontend**: Next.js 14 (App Router) with TypeScript, TailwindCSS, Shadcn UI
- **Backend**: FastAPI with PostgreSQL, Redis, Auth0 authentication
- **ML Service**: FastAPI microservice with PyTorch models for knowledge tracing and recommendations
- **Infrastructure**: Dockerized deployment with NGINX reverse proxy

## 📁 Project Structure

```
edtech-platform/
├── frontend/          # Next.js application
├── backend/           # FastAPI core API
├── ml_service/        # ML microservices
├── infrastructure/    # Docker, docker-compose, NGINX
└── shared/            # Shared schemas and utilities
```

## 🚀 Quick Start

### Prerequisites

- Docker & Docker Compose
- Node.js 18+ (for local frontend development)
- Python 3.11+ (for local backend development)
- PostgreSQL 14+ (if running locally)
- Redis 7+ (if running locally)

### Local Development

1. **Clone and setup environment variables:**

```bash
cp .env.sample .env
# Edit .env with your Auth0 credentials, database URLs, etc.
```

2. **Start all services with Docker Compose:**

```bash
docker-compose up -d
```

3. **Run database migrations:**

```bash
docker-compose exec backend alembic upgrade head
```

4. **Access the application:**

- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- ML Service: http://localhost:8001
- API Docs: http://localhost:8000/docs

### Development Mode (without Docker)

#### Frontend

```bash
cd frontend
npm install
npm run dev
```

#### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload
```

#### ML Service

```bash
cd ml_service
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8001
```

## 🔐 Authentication

This platform uses Auth0 for authentication. Configure your Auth0 credentials in `.env`:

- `AUTH0_DOMAIN`
- `AUTH0_AUDIENCE`
- `AUTH0_CLIENT_ID`
- `AUTH0_CLIENT_SECRET`

## 📊 Features

### Student Portal
- Personalized lesson recommendations
- Interactive exercises
- Progress visualization
- Accessibility controls (font size, high contrast, dyslexia-friendly)

### Teacher Portal
- Class dashboard with mastery heatmaps
- Early warning system for struggling students
- Content authoring
- Manual recommendation overrides

### Adaptive Learning Engine
- Knowledge tracing (LSTM/Transformer)
- Hybrid recommendation system (Collaborative Filtering + Contextual Bandit)
- IRT-based difficulty estimation
- Real-time student model updates

## 🧪 Testing

```bash
# Backend tests
cd backend
pytest

# Frontend tests
cd frontend
npm test
```

## 📦 Deployment

### Production Build

```bash
docker-compose -f docker-compose.prod.yml build
docker-compose -f docker-compose.prod.yml up -d
```

### CI/CD

GitHub Actions workflows are configured in `.github/workflows/`. They handle:
- Linting and type checking
- Unit tests
- Docker image building
- Deployment to staging/production

## 🔧 Configuration

See `.env.sample` for all environment variables. Key settings:

- Database: PostgreSQL connection string
- Redis: For caching and session storage
- S3: For content storage
- Cloudflare: CDN configuration
- Auth0: Authentication settings

## 📚 API Documentation

- Backend API: http://localhost:8000/docs (Swagger UI)
- ML Service API: http://localhost:8001/docs

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Run tests and linting
4. Submit a pull request

## 📄 License

MIT License

## 🆘 Support

For issues and questions, please open a GitHub issue.


