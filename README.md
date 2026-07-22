# 💳 CreditZ - Smart Ledger & Credit Tracker

**CreditZ** is a modern, high-performance Flutter mobile application designed for effortless personal and business credit management, customer ledgers, and transaction tracking.

---

## ✨ Features

- 👥 **Customer Management**: Add, view, edit, and delete customers with associated transaction history.
- 📒 **Interactive Ledger**: Record **Paid** and **Received** entries with running balances, full transaction edit, and deletion options.
- 👤 **Customer Profile Screen**: Dedicated customer profile view with avatar, net balance cards, paid/received totals, and transaction count.
- 📄 **PDF Statement Export**: Generate, print, and share professional PDF customer account statements.
- 📲 **WhatsApp Payment Reminders**: Send formatted WhatsApp payment reminder messages in one click.
- 🎨 **Complete Dark Mode Support**: ThemeMode system default, Light mode, and Dark mode persisted via `SharedPreferences`.
- 📊 **Dashboard Analytics**: Visual summary cards and interactive pie charts (`fl_chart`) calculating *"You Will Give"* vs *"You Will Get"*.
- 🧮 **In-App Calculator**: Integrated responsive numeric calculator for calculating transaction amounts.
- 💾 **Backup & Restore**: Local device storage backup/restore and Google Drive cloud backup options.
- 🚀 **Animated Splash Screen**: Smooth logo opening animation with elastic scale and fade transitions.

---

## 🛠️ Technology Stack & Dependencies

| Layer / Feature | Technology Used |
| :--- | :--- |
| **Framework** | Flutter (Dart SDK ^3.7.0) |
| **Database** | SQLite (`sqflite`) |
| **State & Theme** | `ChangeNotifier` / `ListenableBuilder`, `SharedPreferences` |
| **PDF & Printing** | `pdf`, `printing`, `path_provider` |
| **Charts** | `fl_chart` |
| **Utilities** | `uuid`, `url_launcher`, `googleapis`, `google_sign_in` |

---

## 📂 Project Structure

```text
lib/
├── core/
│   └── theme_controller.dart        # Manages Light/Dark theme modes & SharedPreferences
├── data/
│   ├── local/
│   │   └── database_service.dart    # SQLite initialization and schema configuration
│   ├── models/
│   │   ├── customer.dart            # Customer data model
│   │   ├── profile_model.dart       # User profile data model
│   │   └── transaction_model.dart   # Transaction entry model
│   ├── repositories/
│   │   ├── customer_repository.dart # Customer CRUD & backup operations
│   │   ├── profile_repository.dart  # Profile storage handler
│   │   └── transaction_repository.dart # Transaction queries & balance calculations
│   └── services/
│       ├── backup_service.dart      # Device & Google Drive backup/restore engine
│       └── pdf_service.dart         # PDF statement generator & layout renderer
├── presentation/
│   ├── screens/
│   │   ├── about_screen.dart        # About app screen
│   │   ├── add_customer_screen.dart # Customer entry form
│   │   ├── add_transaction_screen.dart # Transaction creation & editing form
│   │   ├── contact_screen.dart      # Contact support screen
│   │   ├── customer_profile_screen.dart # Detailed customer profile screen
│   │   ├── dashboard_screen.dart    # Financial overview & statistics
│   │   ├── home_screen.dart         # Customer list, filters, and dashboard
│   │   ├── ledger_screen.dart       # Customer ledger, transactions, and PDF export
│   │   ├── more_screen.dart         # Settings, backup, theme, and profile hub
│   │   ├── profile_screen.dart      # User profile edit & image picker
│   │   └── splash_screen.dart       # Animated opening splash screen
│   └── widgets/
│       └── calculator_widget.dart   # Built-in math calculator widget
├── main.dart                        # Application entry point & ThemeData setup
└── whatsapp_service.dart            # WhatsApp messaging utility
```

---

## 🔒 Data Security & Backup Specifications

CreditZ enforces a **Privacy-First** architecture, keeping all financial ledgers, customer profiles, and transaction records securely on-device.

### 1. Database Storage (SQLite)
The application utilizes an offline SQLite database for persistent transactional data:
- **Database Name**: `creditz.db`
- **Standard Location**:
  - **Android**: `/data/data/<package_name>/databases/creditz.db`
  - **iOS**: `~/Library/LocalDatabase/creditz.db`

### 2. Local Backup File
When executing a local backup, the SQLite schemas are compiled into a unified, encrypted-ready JSON layout:
- **Backup File Name**: `creditz_backup.json`
- **Application Documents Directory Paths**:
  - **Android**: `/data/user/0/<package_name>/app_flutter/creditz_backup.json`
  - **iOS**: `/var/mobile/Containers/Data/Application/<App-UUID>/Documents/creditz_backup.json`

### 3. Cloud Synchronization (Google Drive)
Cloud backups are authenticated through secure **OAuth 2.0 client authentication** using `GoogleSignIn`:
- **Auth Scope**: `https://www.googleapis.com/auth/drive.file` (limits app access to files created by this app only).
- **Target File**: `creditz_backup.json` uploaded directly to the user's secure Cloud drive container.

---

## 🚀 Getting Started

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) (v3.7.0 or higher)
- Android Studio / VS Code with Flutter extensions
- Android device or emulator (API Level 21+)

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/CreditZ.git
   cd CreditZ
   ```

2. **Install dependencies:**
   ```bash
   flutter pub get
   ```

3. **Run the application:**
   ```bash
   flutter run
   ```

4. **Build APK Release Bundle:**
   ```bash
   flutter build apk --release
   ```

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
