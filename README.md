# Python App for Backstage Internal Developer Portal

This is a simple Python Flask application designed to be used within the Backstage Internal Developer Portal (IDP) project. It provides basic API endpoints for information and health checks, demonstrating integration with Backstage's service catalog and deployment workflows.

## Features

- **Info Endpoint**: Returns current time, hostname, and a motivational message
- **Health Check Endpoint**: Provides application health status
- **Containerized**: Includes Dockerfile for easy containerization
- **Kubernetes Ready**: Comes with Helm charts and Kubernetes manifests for deployment
- **Backstage Integration**: Registered as a component in the Backstage catalog
- **Documentation**: Uses MkDocs for technical documentation

## Prerequisites

- Python 3.10+
- Docker (for containerized deployment)
- Kubernetes cluster (for production deployment)
- Helm (for chart-based deployment)

## Local Development

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd python-app
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the application:
   ```bash
   python src/app.py
   ```

5. Access the API:
   - Info: http://localhost:5000/api/v1/info
   - Health: http://localhost:5000/api/v1/healthz

## API Endpoints

### GET /api/v1/info
Returns system information including:
- Current time
- Hostname
- Message
- Deployment platform

**Response Example:**
```json
{
  "time": "02:30:45PM on January 02, 2026",
  "hostname": "localhost",
  "message": "You are doing great, little human! <3",
  "deployed_on": "kubernetes"
}
```

### GET /api/v1/healthz
Returns the health status of the application.

**Response Example:**
```json
{
  "status": "up"
}
```

## Docker Deployment

Build and run with Docker:
```bash
docker build -t python-app .
docker run -p 5000:5000 python-app
```

## Kubernetes Deployment

### Using Helm
```bash
helm install python-app ./charts/python-app
```

### Using kubectl
```bash
kubectl apply -f k8s/
```

## Backstage Integration

This application is registered in the Backstage catalog via `catalog-info.yaml`. It includes:
- Component metadata
- GitHub repository annotation
- TechDocs reference for documentation

## Documentation

Technical documentation is available via MkDocs:
```bash
mkdocs serve
```

## Project Structure

```
.
├── src/
│   └── app.py              # Main Flask application
├── charts/
│   └── python-app/         # Helm chart for deployment
├── k8s/                    # Kubernetes manifests
├── docs/                   # MkDocs documentation
├── Dockerfile              # Container build instructions
├── requirements.txt        # Python dependencies
├── catalog-info.yaml       # Backstage catalog registration
└── mkdocs.yaml             # MkDocs configuration
```
