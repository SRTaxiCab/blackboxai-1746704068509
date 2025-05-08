# Project Looking Glass - Backend

Project Looking Glass is an advanced predictive intelligence platform that aggregates and analyzes global digital data to simulate and visualize future outcomes in political, social, economic, technological, and environmental domains.

## Features

- Data ingestion from multiple sources (News APIs, Social Media, Research Databases)
- Natural Language Processing & Analysis
- Temporal & Scenario Modeling Engine
- RESTful API with FastAPI
- Authentication & Authorization
- PostgreSQL Database
- Docker Containerization

## Prerequisites

- Docker and Docker Compose
- Python 3.11+
- PostgreSQL
- OpenAI API Key

## Environment Setup

1. Clone the repository
2. Create a `.env` file in the backend directory:

```bash
# Copy example environment file
cp .env.example .env

# Edit the .env file with your configurations
# Especially update the OPENAI_API_KEY
```

## Running with Docker

1. Build and start the containers:

```bash
docker-compose up --build
```

This will start:
- FastAPI backend on http://localhost:8000
- PostgreSQL database on port 5432

2. Access the API documentation:
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## API Endpoints

### Authentication
- POST `/api/v1/login/access-token` - Get JWT access token
- POST `/api/v1/test-token` - Test access token

### Users
- GET `/api/v1/users/` - List users (admin only)
- POST `/api/v1/users/` - Create user (admin only)
- GET `/api/v1/users/me` - Get current user
- PUT `/api/v1/users/me` - Update current user

### Predictions
- GET `/api/v1/predictions/` - List predictions
- POST `/api/v1/predictions/` - Create prediction
- GET `/api/v1/predictions/{id}` - Get prediction by ID
- PUT `/api/v1/predictions/{id}` - Update prediction
- DELETE `/api/v1/predictions/{id}` - Delete prediction
- POST `/api/v1/predictions/{id}/events` - Add event to prediction

## Development

### Running Locally

1. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the development server:
```bash
uvicorn app.main:app --reload
```

### Running Tests

```bash
pytest
```

## Project Structure

```
backend/
├── app/
│   ├── api/
│   │   └── v1/
│   │       ├── endpoints/
│   │       │   ├── auth.py
│   │       │   ├── users.py
│   │       │   └── predictions.py
│   │       └── api.py
│   ├── core/
│   │   └── security.py
│   ├── models/
│   │   ├── user.py
│   │   └── prediction.py
│   ├── schemas/
│   │   ├── user.py
│   │   └── prediction.py
│   ├── config.py
│   ├── database.py
│   └── main.py
├── docker/
├── tests/
├── .env.example
├── docker-compose.yml
├── Dockerfile
├── requirements.txt
└── README.md
```

## Security Notes

- In production, update the `SECRET_KEY` in the environment variables
- Configure proper CORS settings in `main.py`
- Use strong passwords for database
- Keep API keys and sensitive data secure
- Regular security audits and updates

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is proprietary and confidential.
