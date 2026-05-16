# ApexApp | University Resource Management System

A scalable Flutter application built with a modular **Feature-First Architecture**. The system provides a robust infrastructure for academic content delivery and e-learning, integrating **Firebase Auth**, **Supabase PostgreSQL**, and **SQLite** for offline-first local caching capabilities.

---

## 🏗️ System Architecture

The project implements a **Modular Feature-First Architecture** combined with a centralized **Core Layer**. This design ensures a strict separation of concerns, high maintainability, and a smooth workflow for team collaboration, keeping the business logic completely isolated from the UI presentation layer.

### Architectural Structure:

1. **Core Layer (`lib/core/`)**: The backbone of the application containing centralized, shared configurations and infrastructure:
   - `constants`: Global application configurations, styles, themes, and asset paths.
   - `database`: Local caching configuration and database management implemented via **SQLite**.
   - `network`: Remote data operations, API clients, and **Supabase** / **Firebase** authentication services.
   - `services`: App-wide utilities, dependency injection containers, and global services.
   - `widgets`: Reusable, atomic UI components engineered to enforce the **DRY (Don't Repeat Yourself)** principle across all features.

2. **Features Layer (`lib/features/`)**: A modular layer where each directory represents an independent functional module of the platform (e.g., `auth`, `courses`, `home`, `materials`, `profile`). Each feature encapsulates its own responsibilities:
   - **Data Handling**: Manages Data Transfer Objects (DTOs), JSON serialization (Models), and local/remote data sources.
   - **Business Logic**: Processes functional operations and coordinates communication between data repositories and the UI.
   - **UI Representation**: Standard Flutter widgets dedicated exclusively to presenting states visually to the user.

3. **State Management Layer**:
   - Explicitly managed via **Cubit (via the `flutter_bloc` ecosystem)**.
   - Implements a unidirectional data flow where business logic resides strictly inside Cubits, rendering UI widgets entirely stateless and presentation-driven.

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

- `roles`: Defines user privileges (e.g., Student, Admin, Instructor).
- `users`: Core profile metadata including academic associations (Major, Level) and wallet balance (Linked to Firebase UID).
- `majors`: Academic specializations (e.g., IT, Computer Science, Cyber Security).
- `academic_levels`: Academic tiers (e.g., Level 1, Level 2, etc.).
- `terms`: Semesters nested under academic levels (1:N relationship).
- `tracks`: Specialized learning paths nested under specific majors and levels.
- `materials` & `material_files`: Academic subjects and their associated downloadable content, linked to specific terms, majors, and tracks.
- `courses` & `course_lessons`: Video-based learning modules including instructor details, pricing, and ordered lessons.
- `enrollments` & `lesson_progress`: Tables for tracking student course subscriptions, lesson completion status, and overall progress.
- `wallet_transactions`: Logs of all financial operations (e.g., deposits, course purchases, refunds).
- `news`: Platform announcements, news feeds, and updates.

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

- Flutter SDK `^3.35.3`
- Supabase Project URL & Anon Key
- Firebase `google-services.json` / `GoogleService-Info.plist`

### Developed and Maintained by APEX Team 🛠️
