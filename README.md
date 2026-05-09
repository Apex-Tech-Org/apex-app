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
│
├── core/                             # Shared app-wide utilities and infrastructure
│   │
│   ├── constants/                   # Global constant values used across the app
│   │   ├── app_colors.dart          # Application color palette
│   │   ├── app_strings.dart         # Static text and labels
│   │   └── app_sizes.dart           # Dimensions, paddings, radii, spacing
│   │
│   ├── database/                    # Local database configuration and helpers
│   │   ├── sqlite_service.dart      # SQLite initialization and database access
│   │   └── database_tables.dart     # Database table names and schemas
│   │
│   ├── network/                     # Remote API and internet-related configuration
│   │   ├── supabase_client.dart     # Supabase client initialization
│   │   ├── network_info.dart        # Internet connection checker
│   │   └── api_endpoints.dart       # API routes and endpoints
│   │
│   ├── services/                    # Shared services used globally
│   │   ├── auth_service.dart        # Authentication helper methods
│   │   ├── storage_service.dart     # File upload/download handling
│   │   └── notification_service.dart # Push notification management
│   │
│   ├── utils/                       # Helper functions and utility classes
│   │   ├── validators.dart          # Form validation helpers
│   │   ├── formatters.dart          # Text/date/number formatters
│   │   └── extensions.dart          # Dart extension methods
│   │
│   └── widgets/                     # Reusable shared UI components
│       ├── custom_button.dart       # Shared custom button widget
│       ├── custom_textfield.dart    # Shared text input widget
│       └── loading_indicator.dart   # Shared loading spinner widget
│
├── features/                        # Application features/modules
│   │
│   ├── auth/                        # Authentication feature
│   │   │
│   │   ├── cubit/                   # State management for authentication
│   │   │   ├── auth_cubit.dart      # Authentication business logic
│   │   │   └── auth_state.dart      # Authentication states
│   │   │
│   │   ├── data/                    # Data sources and API/database operations
│   │   │   ├── auth_remote_data_source.dart # Firebase/Supabase auth requests
│   │   │   └── auth_local_data_source.dart  # Local auth caching
│   │   │
│   │   ├── models/                  # Authentication-related data models
│   │   │   └── user_model.dart      # User data model
│   │   │
│   │   ├── repositories/            # Repository layer connecting cubit and data
│   │   │   └── auth_repository.dart # Authentication repository implementation
│   │   │
│   │   ├── pages/                   # Authentication screens/pages
│   │   │   ├── login_page.dart      # Login screen
│   │   │   └── register_page.dart   # Registration screen
│   │   │
│   │   └── widgets/                 # Auth-specific reusable widgets
│   │       ├── auth_textfield.dart  # Authentication text field widget
│   │       └── social_login_button.dart # Google/Facebook login button
│   │
│   ├── home/                        # Home/dashboard feature
│   │
│   ├── materials/                   # Academic materials feature
│   │
│   ├── courses/                     # Courses management feature
│   │
│   └── profile/                     # User profile feature
│
├── firebase_options.dart            # Generated Firebase configuration file
│
└── main.dart                        # Application entry point
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

### Developed and Maintained by APEX Team 🛠️
