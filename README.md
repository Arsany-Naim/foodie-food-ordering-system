<div align="center">

# 🍔 FoodieApp API

**A modern, social food-discovery platform built with ASP.NET Core 8.**

Discover restaurants. Share reviews. Follow fellow foodies.

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![C#](https://img.shields.io/badge/C%23-12.0-239120?style=flat&logo=csharp&logoColor=white)](https://learn.microsoft.com/en-us/dotnet/csharp/)
[![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-Web_API-5C2D91?style=flat&logo=.net&logoColor=white)](https://learn.microsoft.com/en-us/aspnet/core/)
[![Swagger](https://img.shields.io/badge/API-Swagger-85EA2D?style=flat&logo=swagger&logoColor=black)](https://swagger.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-in_active_development-orange)](#-roadmap)

</div>

---

## 📖 Overview

**FoodieApp** is a RESTful Web API that powers a social food-exploration experience. Users can browse restaurants and dishes, submit ratings and reviews, follow other foodies, and discover new places to eat based on community recommendations.

The project is built as a learning-driven, portfolio-grade implementation of a real-world backend system — emphasizing clean architecture, RESTful design principles, and modern .NET practices.

> ⚠️ **Project Status:** This project is **in active development**. The API foundation (ASP.NET Core 8 + Swagger) is in place; domain features are being implemented incrementally. See the [Roadmap](#-roadmap) for what's shipped and what's coming next.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
- [API Endpoints](#-api-endpoints)
- [Project Structure](#-project-structure)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## ⭐ Key Features

🔐 **Authentication & Authorization** — Secure user registration, login, and role-based access via JWT.
🍽️ **Restaurant Discovery** — Browse, search, and filter restaurants by cuisine, location, and rating.
⭐ **Reviews & Ratings** — Submit detailed reviews with star ratings and image uploads.
👥 **Social Layer** — Follow other users and discover food through your network.
🔎 **Search & Filtering** — Fast, flexible querying across restaurants, dishes, and reviews.
📑 **Self-Documenting API** — Interactive Swagger / OpenAPI documentation out of the box.
📱 **Frontend-Agnostic** — Pure REST API, ready to power web (Angular/React) or mobile clients.

---

## 🛠 Tech Stack

| Layer            | Technology                                    |
| ---------------- | --------------------------------------------- |
| **Runtime**      | .NET 8                                        |
| **Language**     | C# 12                                         |
| **Framework**    | ASP.NET Core Web API                          |
| **Data Access**  | Entity Framework Core *(planned)*             |
| **Database**     | SQL Server *(planned)*                        |
| **Auth**         | ASP.NET Core Identity + JWT Bearer *(planned)* |
| **Docs**         | Swagger / OpenAPI (Swashbuckle)               |
| **Testing**      | xUnit *(planned)*                             |
| **Source**       | Git + GitHub                                  |

---

## 🏗 Architecture

The API is being designed around a **layered architecture** to keep concerns cleanly separated and the codebase easy to evolve:

```
┌──────────────────────────────────────────────┐
│  Controllers (HTTP / REST endpoints)         │
├──────────────────────────────────────────────┤
│  Services (business logic, validation)       │
├──────────────────────────────────────────────┤
│  Repositories (EF Core data access)          │
├──────────────────────────────────────────────┤
│  Domain Models & DTOs                        │
└──────────────────────────────────────────────┘
                      │
                      ▼
               SQL Server Database
```

**Design principles guiding the build:**

- ✅ RESTful resource design with predictable HTTP verbs and status codes
- ✅ Dependency injection throughout
- ✅ DTOs to decouple wire models from domain entities
- ✅ Async/await end-to-end for I/O-bound operations
- ✅ Clear separation between controllers, services, and data access

---

## 🚀 Getting Started

### Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads) (LocalDB or full instance)
- [Git](https://git-scm.com/)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Arsany-Naim/FoodieApp.git
cd FoodieApp/Foodie_Web_API

# 2. Restore dependencies
dotnet restore

# 3. Configure your connection string in appsettings.json
#    "ConnectionStrings": {
#      "DefaultConnection": "Server=.;Database=FoodieApp;Trusted_Connection=True;TrustServerCertificate=True;"
#    }

# 4. Run the application
dotnet run
```

### Exploring the API

Once running, open Swagger UI in your browser:

```
https://localhost:{port}/swagger
```

You'll get an interactive playground where you can explore and test every endpoint.

---

## 📡 API Endpoints

> Endpoints are being added incrementally. Below is the target surface for v1.

| Method   | Endpoint                       | Description                       | Auth |
| -------- | ------------------------------ | --------------------------------- | ---- |
| `POST`   | `/api/auth/register`           | Register a new user               | ❌    |
| `POST`   | `/api/auth/login`              | Log in and receive a JWT          | ❌    |
| `GET`    | `/api/restaurants`             | List/search restaurants           | ❌    |
| `GET`    | `/api/restaurants/{id}`        | Get restaurant details            | ❌    |
| `POST`   | `/api/restaurants`             | Create a restaurant               | ✅    |
| `GET`    | `/api/restaurants/{id}/reviews`| List reviews for a restaurant     | ❌    |
| `POST`   | `/api/reviews`                 | Submit a review                   | ✅    |
| `DELETE` | `/api/reviews/{id}`            | Delete your review                | ✅    |
| `GET`    | `/api/users/{id}`              | Get user profile                  | ❌    |
| `POST`   | `/api/users/{id}/follow`       | Follow a user                     | ✅    |

---

## 📁 Project Structure

```
FoodieApp/
├── Foodie_Web_API/
│   ├── Controllers/          # API endpoints
│   ├── Models/               # Domain entities (planned)
│   ├── DTOs/                 # Request/response models (planned)
│   ├── Services/             # Business logic (planned)
│   ├── Data/                 # EF Core DbContext & migrations (planned)
│   ├── Properties/
│   ├── Program.cs            # Application entry point & DI wiring
│   ├── appsettings.json
│   └── Foodie_Web_API.csproj
└── README.md
```

---

## 🗺 Roadmap

**✅ Shipped**
- [x] .NET 8 Web API project scaffold
- [x] Swagger / OpenAPI integration
- [x] HTTPS + Authorization pipeline

**🚧 In Progress**
- [ ] Domain models: `User`, `Restaurant`, `Dish`, `Review`
- [ ] EF Core + SQL Server integration with migrations
- [ ] Repository & service layers

**📋 Planned**
- [ ] JWT authentication & ASP.NET Core Identity
- [ ] Restaurant, Review, and User endpoints
- [ ] Image upload (reviews & profiles)
- [ ] Search, filtering, and pagination
- [ ] Following / social graph
- [ ] xUnit test coverage
- [ ] CI/CD pipeline (GitHub Actions)
- [ ] Docker support

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📜 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.

---

## 📬 Contact

**Arsany Naim**

[![GitHub](https://img.shields.io/badge/GitHub-Arsany--Naim-181717?style=flat&logo=github)](https://github.com/Arsany-Naim)
[![Repository](https://img.shields.io/badge/Repo-FoodieApp-2ea44f?style=flat&logo=github)](https://github.com/Arsany-Naim/FoodieApp)

---

<div align="center">

⭐ **If you find this project interesting, consider giving it a star!** ⭐

</div>
