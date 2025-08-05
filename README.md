# ICMarkets Web API
This project is part of an assessment for ICMarkets to demonstrate the ability to design a scalable, testable, and dockerized .NET Web API using Clean Architecture principles.
It fetches blockchain data for ETH, BTC, LTC, and DASH from BlockCypher APIs and stores it in a database along with a timestamp.
## Features

- 🔄 Fetches live blockchain data from BlockCypher API
- 🧾 Stores historical data with timestamps
- ✅ Clean Architecture (API, Application, Domain, Infrastructure)
- 🔍 Swagger UI for API testing
- 🐳 Docker support
- 🧪 Unit & integration test setup

## 🧰 Technologies Used

- .NET 6 + Web API
- Entity Framework Core (SQLite)
- Swagger (Swashbuckle)
- AutoMapper
- Serilog (for logging)
- Docker

## 🗂️ Project Structure

ICMarketsSolution/
├── ICMarkets.Api/ --> API controllers, middlewares, Swagger setup
├── ICMarkets.Application/ --> DTOs, interfaces, logic
├── ICMarkets.Domain/ --> Entities
├── ICMarkets.Infrastructure/--> Repositories, DbContext, external API calls
├── ICMarkets.Tests/ --> Unit/integration tests
├── ICMarketsSolution.sln
└── README.md

## 🧪 API Endpoints

| Method | Route                          | Description                          |
|--------|--------------------------------|--------------------------------------|
| POST   | `/api/Blockchain/fetch        | Fetches & stores data from BlockCypher |
| GET    | `/api/Blockchain/history     | Returns all stored blockchain entries |

---

## 🔄 Example API Response

### ✅ POST `/api/Blockchain/fetch`

```json
{
  "message": "Blockchain data fetched and stored successfully."
}
✅ GET /api/Blockchain/history
json

[
  {
    "id": 1,
    "name": "BTC",
    "createdAt": "2025-08-05T14:20:45",
    "rawJson": "{...}"
  },
  ...
]
🖥️ How to Run
🔹 Option 1: Using .NET CLI

cd ICMarkets.Api
dotnet run
Open in browser:


https://localhost:5001/swagger
🔹 Option 2: Using Docker

docker build -t icmarkets-api -f ICMarkets.Api/Dockerfile .
docker run -d -p 8080:80 --name icmarkets-container icmarkets-api
Open in browser:

http://localhost:8080/swagger
💾 Database
SQLite is used by default 
Data is stored in a file like icmarkets.db
Each blockchain record includes:
Coin type (BTC, ETH, etc.)
Raw API JSON
CreatedAt timestamp

🧪 Testing
Run tests:
cd ICMarkets.Tests
dotnet test
Includes:

✅ Unit tests for services/handlers

🔁 Integration tests for DB and API endpoints

📦 BlockCypher API Sources
ETH
BTC
LTC
DASH
