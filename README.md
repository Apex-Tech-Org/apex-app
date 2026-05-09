# ApexApp | University Resource Management System

A scalable Flutter application built with **Layered Clean Architecture**. The system provides a scalable infrastructure for academic content delivery, integrating **Firebase Auth**, **Supabase PostgreSQL**, and **SQLite** for offline-first capabilities.

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

| Tool                 | Purpose                                                 |
| :------------------- | :------------------------------------------------------ |
| **Flutter**          | Cross-platform UI framework                             |
| **Supabase**         | Primary PostgreSQL Backend & Real-time DB               |
| **Firebase Auth**    | Identity Provider (Google & Email Auth)                 |
| **SQLite (sqflite)** | Local persistence & caching layer                       |
| **Get_it**           | Dependency Injection (Service Locator)                  |
| **Dartz**            | Functional Programming (Either type for error handling) |

## 📊 Database Schema Design (Supabase)

The relational schema is optimized for high-speed querying of hierarchical academic data:

- `users`: Core profile metadata (Linked to Firebase UID).
- `news`: Campus announcements, news feeds, and updates.
- `levels`: Academic tiers (e.g., Year 1, Year 2, etc.).
- `terms`: Semesters nested under levels (1:N relationship).
- `materials`: Content metadata (PDFs, Images) linked to specific terms.
- `courses`: Learning modules including instructor details and thumbnails.
- `course_enrollments`: Junction table for tracking student subscriptions and progress.

## 🌿 Git Workflow

To maintain code quality and ensure a scalable collaborative development process, the project follows the branching strategy below:

| Branch      | Purpose                                                         |
| :---------- | :-------------------------------------------------------------- |
| `main`      | Stable production-ready branch                                  |
| `dev`       | Active development and integration branch                       |
| `feature/*` | Dedicated branches for new features, enhancements, or bug fixes |

## 📁 Project Structure

```text
lib/
├── core/          # Dependency Injection, Themes, Errors, and Constants
├── features/      # Feature-based modules (Auth, Materials, Courses, etc.)
└── main.dart      # Application entry point
```

### Workflow Overview

1. Developers create feature branches from `dev`.
2. Completed features are merged back into `dev`.
3. After testing and stabilization, `dev` is merged into `main` for production releases.

## 🚀 Getting Started

### ⚙️ Environment & Project Setup

#### Environment Configuration

The project uses `flutter_dotenv` for secure environment variable management.

Create a `.env` file in the project root directory and populate it using the structure provided in `env.example`.

```env
SUPABASE_URL=your_project_url
SUPABASE_ANON_KEY=your_anon_key
```

#### Firebase Configuration

Firebase configuration files are excluded from version control for security reasons.

| Platform | File Location                                         |
| :------- | :---------------------------------------------------- |
| Android  | Place `google-services.json` inside `android/app/`    |
| iOS      | Place `GoogleService-Info.plist` inside `ios/Runner/` |

#### Install Dependencies

Fetch all required packages defined in `pubspec.yaml`:

```bash
flutter pub get
```

#### Run the Project

Ensure an emulator or physical device is connected, then execute:

```bash
flutter run
```

### Prerequisites

- Flutter SDK `^3.x.x`
- Supabase Project URL & Anon Key
- Firebase `google-services.json` / `GoogleService-Info.plist`

### Setup Environment Variables

Create a `.env` file in the project root directory and add the required environment variables using the structure provided in `env.example`.

### Developed and Maintained by APEX Team 🛠️
