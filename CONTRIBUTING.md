# 🛠️ Contribution Guide | دليل المساهمة

Welcome to the **APEX** technical team. To maintain high-quality code and a scalable architecture, all contributors must follow these standards.

أهلاً بك في فريق **أبكس** التقني. للحفاظ على جودة الكود ومعمارية قابلة للتوسع، يجب على جميع المساهمين الالتزام بهذه المعايير.

---

## 📏 1. Naming Conventions | قواعد التسمية
We follow the official Dart style guide:
نحن نتبع دليل تنسيق Dart الرسمي:

* **Folders & Files:** Use `snake_case` (e.g., `custom_button.dart`).
    * **المجلدات والملفات:** استخدم `snake_case`.
* **Classes:** Use `PascalCase` (e.g., `MaterialsRepository`).
    * **الكلاسات:** استخدم `PascalCase`.
* **Variables & Functions:** Use `camelCase` (e.g., `fetchData()`).
    * **المتغيرات والدوال:** استخدم `camelCase`.

## 🏗️ 2. Architecture & Folder Structure | المعمارية وهيكلة المجلدات

We use a modular **Feature-First Architecture** grouped by functional modules, combined with a centralized **Core Layer** for shared logic. This ensures a strict separation of concerns and keeps code clean and maintainable:

تعتمد المعمارية على تقسيم المشروع بناءً على الميزات (**Feature-First**) مع وجود طبقة مركزية مشتركة (**Core**)، لضمان فصل المنطق عن الواجهات وسهولة صيانة الكود:

### 📁 1. Core Layer (`lib/core/`)
Contains all shared components, utilities, and configurations used across multiple features:
يحتوي على المكونات والخدمات المشتركة التي تخدم أكثر من ميزة داخل التطبيق:
* **constants:** App-wide constants (styles, themes, asset paths, API keys).
* **database:** Local storage configuration and database management (e.g., SQLite).
* **network:** Remote API clients, Supabase / Firebase authentication, and network configurations.
* **services:** Global application services (e.g., dependency injection, shared preferences, notifications).
* **widgets:** Reusable UI components (buttons, text fields, custom loaders) shared across different screens to maintain the **DRY (Don't Repeat Yourself)** principle.

### 📁 2. Features Layer (`lib/features/`)
Each directory inside represents a standalone functional module containing its own UI, logical components, and data handling:
تنقسم كل ميزة إلى مجلد مستقل يحتوي على الواجهات والمنطق وإدارة الحالة والبيانات الخاصة بها:
* **auth:** Handles user registration, login, and onboarding sessions.
* **courses:** Manages instructional modules, lessons, and video streaming.
* **home:** The main landing dashboard showcasing personalized student feeds.
* **materials:** Manages downloadable academic materials, PDF files, and subjects.
* **profile:** Handles user settings, personal metadata, and wallet balance/transactions.

### 💡 State Management & Logic Separation
* **State Management:** We strictly use **Cubit (via `flutter_bloc`)** for managing UI states. 
* **Separation of Concerns:** Business logic and data manipulation must reside entirely within the Cubit and repository files inside each feature. **UI widgets must remain stateless representation layers only**, triggered exclusively by state updates.

## ♻️ 3. DRY Principle | مبدأ عدم التكرار
**Don't Repeat Yourself.** Before creating a new widget, check `lib/core/widgets/`.
**لا تكرر نفسك.** قبل إنشاء أي "ودجت" جديد، تحقق من مجلد العناصر المشتركة.
* If a common widget (Button, TextField, Card) exists, **you must use it**.
* إذا كان هناك عنصر مشترك جاهز، **يجب عليك استخدامه**.

## 🚀 4. Git & Commits | التعامل مع جيت
* Write clear commit messages (e.g., `feat: add login cubit` or `fix: repair local db sync`).
* اكتب رسائل واضحة عند الرفع (مثل: إضافة نظام تسجيل الدخول).
* Always `pull` the latest changes before starting your work.
* قم دائماً بسحب آخر التحديثات قبل البدء بعملك لتجنب التضارب.