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

## 🏗️ 2. Architecture | المعمارية
We use **Simplified Clean Architecture**. Do not mix logic with UI:
نحن نستخدم **المعمارية النظيفة المبسطة**. لا تخلط المنطق بواجهات المستخدم:

* **Data:** Models and Data Sources (Supabase/SQLite).
* **Domain:** Entities and Repository Interfaces.
* **Presentation:** UI Widgets and **Cubit** for state management.

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