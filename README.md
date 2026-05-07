# AppexApp | University Resource Management System

A high-performance Flutter application built with **Layered Clean Architecture**. The system provides a scalable infrastructure for academic content delivery, integrating **Firebase Auth**, **Supabase PostgreSQL**, and **SQLite** for offline-first capabilities.

---

## 🏗 System Architecture

The project implements a **Simplified Clean Architecture** to ensure separation of concerns, testability, and maintainability.

### Layers:
1. **Domain Layer**: Contains functional `Entities` and `Repository Interfaces`. This layer is independent of any external libraries.
2. **Data Layer**: Responsible for data retrieval and persistence.
   - `Models`: JSON serialization and Data Transfer Objects (DTOs).
   - `Data Sources`: Implementation of **Supabase** (Remote) and **SQLite** (Local).
   - `Repositories`: Implementation of domain interfaces with logic to handle data caching (Local vs Remote).
3. **Presentation Layer**: 
   - Managed via **State Management** (Bloc/Cubit).
   - Atomic Design pattern for UI components.

## 🛠 Tech Stack & Dependencies

| Tool | Purpose |
| :--- | :--- |
| **Flutter** | Cross-platform UI framework |
| **Supabase** | Primary PostgreSQL Backend & Real-time DB |
| **Firebase Auth** | Identity Provider (Google & Email Auth) |
| **SQLite (sqflite)** | Local persistence & caching layer |
| **Get_it** | Dependency Injection (Service Locator) |
| **Dartz** | Functional Programming (Either type for error handling) |

## 📊 Database Schema Design (Supabase)

The relational schema is optimized for fast querying of hierarchical data:
- `users`: UUID (Auth linked), profile metadata.
- `levels`: Academic tiers (e.g., Level 1, Level 2).
- `terms`: Nested under levels (1:N relationship).
- `materials`: Content metadata linked to terms.
- `courses`: Independent module for enrolled learning content.

## 🚀 Getting Started

### Prerequisites
- Flutter SDK `^3.x.x`
- Supabase Project URL & Anon Key
- Firebase `google-services.json` / `GoogleService-Info.plist`

### Installation
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/AppexApp.git](https://github.com/your-username/AppexApp.git)
