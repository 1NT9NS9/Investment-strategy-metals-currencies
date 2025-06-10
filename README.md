# Russian Investment Platform - Architecture Overview

## 🎯 Executive Summary

The Russian Investment Platform is an AI-powered investment system designed to construct and manage portfolios of metals and currencies with yields exceeding Sberbank's deposit rates. The platform leverages state-of-the-art machine learning models, microservices architecture, and modern web technologies.

## 🏗️ System Architecture

russian-investment-platform/
├── services/
│   ├── api-gateway/         # API Gateway with authentication
│   ├── prediction/          # ML prediction service
│   ├── genai/              # Content generation service
│   ├── data-ingestion/     # Market data collection
│   ├── portfolio-management/
│   └── user/
├── frontend/               # Next.js application
├── infrastructure/
│   ├── docker/            # Docker configurations
│   └── kubernetes/        # K8s deployments
├── shared/                # Shared models and utilities
├── docs/                  # Documentation
├── docker-compose.yml     # Local development setup
├── requirements.txt       # Python dependencies
└── README.md             # Project overview

Diagram showing how predictions work in the system:

![image](https://github.com/user-attachments/assets/dc82f09c-3e82-4ff4-940d-4614eeed48e4)


### Core Components

1. **AI Prediction Engine**
   - **Time Series Transformer**: Primary prediction model using self-attention mechanisms
   - **N-BEATS**: Interpretable forecasting with trend/seasonality decomposition
   - **Ensemble Predictor**: Combines both models with adaptive weighting

2. **Microservices**
   - **API Gateway**: Single entry point, authentication, rate limiting
   - **Prediction Service**: ML model training and inference
   - **GenAI Service**: Market commentary and risk analysis generation
   - **Portfolio Management**: Optimization and rebalancing
   - **User Service**: Authentication and user management
   - **Data Ingestion**: Real-time market data collection

3. **Data Infrastructure**
   - **ClickHouse**: Time-series data storage
   - **PostgreSQL**: Relational data (users, portfolios)
   - **Redis**: Caching and session management
   - **RabbitMQ**: Event-driven communication

4. **Frontend**
   - **Next.js**: In development

## 📊 Data Flow

1. **Market Data Collection**
   ```
   Moscow Exchange API → Data Ingestion → ClickHouse
   Central Bank API → Data Ingestion → ClickHouse
   ```

2. **Prediction Pipeline**
   ```
   Historical Data → Transformer Model → Ensemble → Predictions
                  → N-BEATS Model → 
   ```

3. **Content Generation**
   ```
   Predictions → GenAI Service → Market Commentary
                              → Risk Summaries
                              → Scenario Analysis
   ```

## 🔧 Technical Stack

### Backend
- **Language**: Python 3.11
- **Framework**: FastAPI
- **ML Libraries**: PyTorch, Transformers, Darts
- **Database Clients**: clickhouse-driver, psycopg2, redis-py

### Infrastructure
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Cloud**: Google Cloud Platform
- **Monitoring**: Prometheus + Grafana

## 🚀 Key Features

### 1. AI-Powered Predictions
- Daily automated model training
- 7-day price forecasts
- Confidence intervals and quality metrics
- Interpretable components (trend, seasonality)

### 2. Generative AI Integration
- Automated market commentary in Russian/English
- Personalized risk summaries
- "What-if" scenario simulations
- Interactive chat for market insights

### 3. Portfolio Optimization
- Risk-adjusted portfolio construction
- Automated rebalancing
- Performance tracking vs benchmarks
- Multi-asset allocation (metals + currencies)

### 4. Real-time Market Data
- Live prices from Moscow Exchange
- Central Bank currency rates
- Historical data analysis
- Technical indicators

## 🔐 Security & Reliability

### Security Measures
- JWT-based authentication
- Rate limiting per endpoint
- Input validation and sanitization
- Encrypted data storage
- Role-based access control

### Reliability Features
- Horizontal scaling with Kubernetes
- Database replication
- Circuit breakers for external APIs
- Graceful degradation
- Comprehensive logging and monitoring

## 📈 Performance Specifications

### Model Performance
- Transformer MAPE: < 3%
- N-BEATS MAPE: < 4%
- Prediction latency: < 500ms
- Training time: < 2 hours daily

### System Performance
- API Gateway throughput: 10,000 req/min
- Database query time: < 100ms (p99)
- Cache hit rate: > 80%
- Uptime target: 99.9%

## 📊 Monitoring & Observability

### Metrics Collection
- Prometheus for metrics aggregation
- Grafana dashboards for visualization
- Custom metrics for ML model performance

### Logging
- Structured JSON logging
- Centralized log aggregation
- Log-based alerting

### Tracing
- Distributed tracing with OpenTelemetry
- Request flow visualization
- Performance bottleneck identification

## 🔄 Continuous Improvement

### Model Updates
- Daily retraining with latest data
- A/B testing for model improvements
- Performance tracking and reporting

### Feature Roadmap
- Investment Strategies Website
- Subscription system
- Financial management
- Mobile application
- Advanced portfolio strategies
- More asset classes (stocks, сryptocurrency)
- Social trading features


