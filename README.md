# Logistria - Supply Chain Orchestration Platform

An intelligent, agent-based supply chain orchestration platform that automates inventory management, production planning, procurement, logistics, and warehouse operations through autonomous agents and ML-powered optimization.

## 📋 Project Overview

Logistria is a comprehensive supply chain management system that leverages autonomous agents and machine learning to optimize operations across multiple domains:

- **Inventory Management**: Real-time stock tracking with capacity management
- **Production Planning**: Autonomous production scheduling and order fulfillment
- **Procurement**: Intelligent supplier selection and purchase order management
- **Logistics**: Route optimization, vehicle allocation, and delivery verification
- **Warehouse Operations**: Capacity tracking and inventory distribution

The system uses Google Generative AI for intelligent decision-making and features REST APIs for seamless integration with frontend applications.

## 🎯 Key Features

- **Autonomous Agents**: Specialized agents for inventory, warehouse, supplier, and orchestration
- **ML-Powered Optimization**: Route optimization, vehicle allocation, and demand forecasting
- **Warehouse Capacity Management**: Real-time tracking of warehouse utilization and constraints
- **Supplier Intelligence**: Multi-stage delivery tracking and supplier performance metrics
- **Logistics Optimization**: Weather-aware routing and ML-based service optimization
- **REST API**: Complete API for all supply chain operations
- **Mobile Frontend**: React Native/Expo frontend for mobile access

## 🏗️ Project Structure

```
Logistria/
├── app.py                          # Flask application factory
├── agents/                         # Autonomous agents
│   ├── central_orchestrator.py     # Main orchestration agent
│   ├── inventory.py                # Inventory agent
│   ├── supplier_agent.py           # Supplier management agent
│   ├── warehouse_agent.py          # Warehouse operations agent
│   ├── orchestrator_agent.py       # Orchestration logic
│   └── logistics/                  # Logistics-specific modules
│       ├── autonomous_orchestrator_agent.py
│       ├── route_optimizer.py      # Route optimization engine
│       ├── vehicle_allocator.py    # Vehicle allocation
│       ├── distance_engine.py      # Distance calculations
│       ├── weather_service.py      # Weather data integration
│       ├── ml_fetch_service.py     # ML-based service
│       └── delivery_verifier.py    # Delivery verification
├── services/                       # Business logic services
│   ├── inventory_service.py
│   ├── procurement_service.py
│   ├── production_service.py
│   ├── warehouse_service.py
│   └── reorder_service.py
├── routes/                         # REST API endpoints
│   ├── inventory_routes.py
│   ├── production_routes.py
│   ├── procurement_routes.py
│   ├── logistics_routes.py
│   ├── warehouse_routes.py
│   └── orchestrator_routes.py
├── execution/                      # Event execution and logging
│   ├── event_router.py
│   ├── logistics_logger.py
│   ├── orchestration_logger.py
│   └── production_execution_agent.py
├── adapter/                        # External service adapters
│   └── supplier_adapter.py
├── data_base/                      # Data storage (CSV-based)
│   ├── inventory.csv
│   ├── logistics_orders.csv
│   ├── logistics_shipments.csv
│   ├── logistics_vehicles.csv
│   ├── purchase_orders.csv
│   ├── supplier_master.csv
│   ├── warehouse.csv
│   └── [20+ other data files]
├── logistria-frontend/             # React Native/Expo frontend
│   ├── app/
│   ├── components/
│   └── tsconfig.json
└── templates/                      # HTML templates for web UI
    ├── inventory.html
    ├── logistics.html
    ├── production.html
    └── warehouse.html
```

## 🛠️ Tech Stack

### Backend
- **Framework**: Flask 3.1+
- **Language**: Python 3.12+
- **AI/ML**:
  - Google Generative AI (google-generativeai 0.8+)
  - scikit-learn 1.4+ (Machine Learning)
- **Data Processing**: Pandas 2.0+, NumPy 2.0+
- **HTTP**: Requests 2.31+
- **CORS**: flask-cors 4.0+

### Frontend
- **Framework**: React Native with Expo
- **Language**: TypeScript
- **Build**: Node.js, pnpm
- **UI**: Tailwind CSS

### Database
- **Storage**: CSV-based data files
- **Data Format**: Structured CSV with headers

## 📦 Installation

### Prerequisites
- Python 3.12+
- Node.js 18+ (for frontend)
- pip or conda for Python package management
- Google Generative AI API key

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Logistria
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -e .
   # For development:
   pip install -e ".[dev]"
   ```

4. **Set environment variables**
   ```bash
   export GOOGLE_API_KEY=your_api_key_here
   # On Windows:
   set GOOGLE_API_KEY=your_api_key_here
   ```

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd logistria-frontend
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Configure Firebase** (if applicable)
   - Update `firebaseConfig.ts` with your Firebase credentials

## 🚀 Running the Application

### Backend

```bash
python app.py
```

The Flask server will start on `http://localhost:5000` with CORS enabled for mobile devices.

### Frontend (Expo)

```bash
cd logistria-frontend
pnpm start
```

Then select your preferred platform:
- Web: Press `w`
- iOS: Press `i`
- Android: Press `a`

Or open in Expo Go app by scanning the QR code.

## 📡 API Endpoints

### Inventory Management
- `GET /inventory` - Get all inventory items
- `GET /inventory/warehouse-status` - Get warehouse utilization
- `POST /inventory` - Add/update inventory items

### Procurement
- `GET /procurement/suppliers` - Get supplier recommendations
- `POST /procurement/orders` - Create purchase orders
- `POST /procurement/receive-po` - Receive purchase order
- `GET /procurement/po-status` - Get PO status

### Production
- `GET /production/orders` - Get production orders
- `POST /production/execute` - Execute production

### Logistics
- `POST /logistics/orders` - Create delivery order
- `GET /logistics/shipments` - Get shipment status
- `POST /logistics/verify-delivery` - Verify delivery completion

### Warehouse
- `GET /warehouse/inventory` - Get warehouse inventory
- `POST /warehouse/transfer` - Transfer stock between warehouses

### Orchestration
- `POST /orchestrator/evaluate` - Trigger orchestration evaluation

## 🤖 Autonomous Agents

### Central Orchestrator Agent
Coordinates all supply chain operations, makes high-level decisions based on ML models and agent feedback.

### Inventory Agent
- Monitors stock levels
- Triggers reorder points
- Manages warehouse capacity constraints
- Tracks inventory across warehouses

### Supplier Agent
- Evaluates supplier performance
- Provides supplier recommendations
- Tracks delivery stages and fulfillment times
- Manages supplier relationships

### Warehouse Agent
- Monitors warehouse capacity
- Optimizes stock distribution
- Enforces capacity constraints
- Manages warehouse operations

### Logistics Orchestrator
- Optimizes delivery routes
- Allocates vehicles to orders
- Implements weather-aware routing
- Verifies delivery completion

## 📊 Data Storage

The system uses CSV files for data persistence stored in the `data_base/` directory:

- **inventory.csv** - Stock levels and warehouse locations
- **warehouse.csv** - Warehouse capacities and utilization
- **logistics_orders.csv** - Customer delivery orders
- **logistics_shipments.csv** - Shipment tracking information
- **purchase_orders.csv** - Supplier purchase orders
- **supplier_master.csv** - Supplier information
- **supplier_product.csv** - Product-supplier relationships
- **logistics_vehicles.csv** - Fleet information
- **logistics_customers.csv** - Customer information

## 🧪 Testing

### Unit Tests
```bash
pytest tests/
```

### Integration Tests
```bash
pytest tests/ -v
```

### API Testing
Use the HTML templates in `templates/` for manual API testing or use tools like Postman/curl.

## 📝 Development Notes

### Architecture Principles
- **Separation of Concerns**: Agents handle decisions, services handle execution
- **Agent-Oriented**: Autonomous agents make decisions with AI reasoning
- **ML-Powered**: Machine learning models optimize routing, allocation, and forecasting
- **Modular Design**: Each component can be independently developed and tested
- **API-First**: All operations available through clean REST API

### Adding New Features

1. **Create a new agent** (if needed): Add to `agents/`
2. **Create business logic**: Add to `services/`
3. **Create API routes**: Add to `routes/`
4. **Update data storage**: Modify CSV schemas in `data_base/`
5. **Add tests**: Create corresponding test files

### Important Concepts

#### Warehouse Capacity Management
- Each warehouse has `max_capacity` and `current_occupied` tracking
- Orders are rejected if they would exceed capacity
- Capacity is checked before accepting deliveries

#### Multi-Stage Supplier Delivery
- Suppliers provide delivery stages: "Order Placed → Confirmed → In Transit → Out for Delivery → Delivered"
- Each supplier has `avg_fulfillment_days` for planning
- Delivery verification confirms final stage completion

#### ML-Powered Optimization
- Route optimization uses ML models for distance/time prediction
- Vehicle allocation optimized for cost and delivery time
- Demand forecasting for inventory planning

## 🔄 Integration with Frontend

The React Native frontend communicates with the Flask backend via REST API:

1. User actions trigger API calls to backend
2. Backend processes through agents and services
3. Data persisted to CSV files
4. Results returned to frontend for display
5. Mobile app renders responsive UI with Tailwind CSS

## 📈 Performance & Scaling

- CSV-based storage suitable for small to medium datasets
- Consider database migration (PostgreSQL/MongoDB) for enterprise scale
- ML models can be containerized for horizontal scaling
- API can be deployed behind load balancer

## 🐛 Troubleshooting

### CORS Issues
- Already configured in `app.py` - should work with mobile clients

### Missing API Key
- Set `GOOGLE_API_KEY` environment variable
- Required for generative AI agent reasoning

### Warehouse Capacity Errors
- Check `warehouse.csv` for max_capacity configuration
- Verify inventory CSV has correct warehouse assignments

### Route Optimization Issues
- Check distance engine data availability
- Verify vehicle data in `logistics_vehicles.csv`

## 📄 License

[Specify your license here]

## 👥 Contributors

[List contributors here]

## 📞 Support

For support or issues, please create an issue in the repository or contact the development team.

---

**Last Updated**: February 2026
