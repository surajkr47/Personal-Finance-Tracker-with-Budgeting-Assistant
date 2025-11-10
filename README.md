# 💸 Personal Finance Tracker with Budgeting Assistant

A comprehensive, cross-platform mobile application built with Flutter and Firebase. This app is designed to help users manage their personal finances by providing secure authentication, real-time transaction tracking, and interactive budget management to promote financial literacy.

This project was developed as a Mini Project for the Mobile Application Development Lab (24CAP-702).

## ✨ Features

* **Secure Authentication:** Full user registration (with name, email, phone, gender, etc.) and login system using **Firebase Authentication**.
* **Real-time Dashboard:** A home screen that instantly updates to show your total balance, total income, and total expenses.
* **Full Transaction Management (CRUD):** Easily **C**reate, **R**ead, **U**pdate, and **D**elete income or expense transactions.
* **Monthly Budgeting:** Set a custom monthly expense budget and see your remaining funds in real-time on the dashboard.
* **Interactive Analysis:** A visual breakdown of your spending habits with an interactive **pie chart** on the "Analysis" tab, built with `fl_chart`.
* **User Profile:** A dedicated profile page showing your account details and a gender-based online avatar.
* **Yearly Reports:** A report page to view your complete financial summary for any financial year (April 1 - March 31).

---

## 🛠️ Tech Stack

* **Frontend:** Flutter
* **Backend:** Firebase
* **Database:** Cloud Firestore (for all user and transaction data)
* **Authentication:** Firebase Authentication (Email/Password)
* **State Management:** `StreamBuilder` for real-time data from Firestore.
* **Key Packages:**
    * `firebase_core`
    * `firebase_auth`
    * `cloud_firestore`
    * `google_fonts` (for UI styling)
    * `intl` (for date formatting)
    * `fl_chart` (for the analysis pie chart)

---

## 🚀 Getting Started

This project is fully configured to run with a new Firebase project.

1.  **Clone the repository:**
    ```sh
    git clone [https://github.com/YourUsername/Personal-Finance-Tracker-with-Budgeting-Assistant.git](https://github.com/YourUsername/Personal-Finance-Tracker-with-Budgeting-Assistant.git)
    cd Personal-Finance-Tracker-with-Budgeting-Assistant
    ```

2.  **Create your own Firebase Project:**
    * Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
    * Enable **Authentication** (Email/Password).
    * Enable **Cloud Firestore** (start in **test mode**).

3.  **Set Secure Firestore Rules:**
    * In your Firebase project, go to **Cloud Firestore > Rules**.
    * Replace the default rules with these secure rules:
    ```javascript
    rules_version = '2';
    service cloud.firestore {
      match /databases/{database}/documents {
      
        // Allows a user to create their own document
        match /users/{userId} {
          allow create: if request.auth.uid != null;
          allow read, update, delete: if request.auth.uid == userId;
        }
        
        // Allows a user to read/write their own transactions
        match /users/{userId}/transactions/{transactionId} {
          allow read, write, create, delete: if request.auth.uid == userId;
        }
      }
    }
    ```
    * Click **Publish**.

4.  **Connect your app:**
    * Run `flutterfire configure` in your project terminal and select the Firebase project you just created. This will generate your `lib/firebase_options.dart` file.

5.  **Run the app:**
    ```sh
    flutter pub get
    flutter run
    ```
    * **IMPORTANT:** You must **register a new user** to create the user document in the database.

---

## 📸 Screenshots

*(You can add your own screenshots here by taking pictures of the app and dragging them into this README file on GitHub)*

| Login/Register | Home Dashboard | Analysis Page |
| :---: |:---:| :---:|
| 

[Image of Login Screen]
 |  |  |
| **Profile Page** | **Add Transaction** | **Yearly Report** |
|  |  |  |

---

## 👨‍💻 Author

* **Suraj Kumar**
* **UID:** 24MCA20013
* **Chandigarh University, MCA**
