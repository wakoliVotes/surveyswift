# SurveySwift
- SurveySwift is a fast, user-friendly app designed to create and manage surveys easily. It streamlines gathering feedback, providing real-time insights, and helping you make data-driven decisions quickly and efficiently. It is ideal for businesses, researchers, and anyone needing swift, accurate survey results.

### **SurveySwift App Documentation**
#### **Overview**
**SurveySwift** is a mobile application built using Jetpack Compose, designed for fast and efficient survey creation, distribution, and response collection. It supports both offline and online functionalities, allowing users to create, manage, and analyze surveys in real-time.
### **Project Setup**

- **Architecture**: The app follows the **MVVM architecture** (Model-View-ViewModel), ensuring separation of concerns and easier maintenance.
- **Modules**: The project is modularized into core components:
    - **UI Module**: For managing all UI interactions via Jetpack Compose.
    - **Data Module**: Handles database operations (Room) and network requests.
    - **Network Module**: Integrates with Retrofit/OkHttp for backend services.
    - **Feature Modules**: Separate features for survey creation, response collection, and analytics.

- **Dependencies**:
    - Jetpack Compose for UI.
    - Room Database for offline storage.
    - Retrofit/OkHttp for REST API integration.
    - Hilt for dependency injection.
    - Firebase for authentication and real-time data sync (optional).
    - Jetpack Navigation for seamless navigation between screens.
### **Project Layout (Directory Structure)**

```txt

SurveySwift/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/surveyswift/
│   │   │   │   ├── di/                // Dependency Injection (Hilt)
│   │   │   │   ├── ui/                // UI-related components (Jetpack Compose)
│   │   │   │   │   ├── components/    // Reusable Compose components
│   │   │   │   │   ├── screens/       // Composable screens (e.g., SurveyListScreen, SurveyDetailScreen)
│   │   │   │   │   └── theme/         // Theme definitions (colors, typography, shapes)
│   │   │   │   ├── data/              // Data layer
│   │   │   │   │   ├── model/         // Data models (Survey, Question, etc.)
│   │   │   │   │   ├── repository/    // Repositories for data management
│   │   │   │   │   └── source/        // Local and remote data sources (Room, Retrofit)
│   │   │   │   ├── domain/            // Domain layer (business logic)
│   │   │   │   │   ├── usecase/       // Use cases for handling business logic
│   │   │   │   │   └── entity/        // Domain entities and mappers
│   │   │   │   ├── viewmodel/         // ViewModel classes for handling UI state
│   │   │   │   └── utils/             // Utility classes and extensions
│   │   │   ├── res/
│   │   │   │   ├── drawable/          // Images, icons, etc.
│   │   │   │   ├── values/            // Resource values (colors.xml, strings.xml, etc.)
│   │   │   ├── AndroidManifest.xml    // App-level manifest file
├── buildSrc/                           // Dependencies and build scripts
│   ├── src/
│   │   ├── main/kotlin/com/example/surveyswift/
│   │   │   └── Build.kt                // Dependency versions, plugins
├── core/                               // Core features shared across modules
│   ├── src/
│   │   ├── main/kotlin/com/example/surveyswift/
│   │   │   ├── network/                // Network configuration (Retrofit, OkHttp)
│   │   │   ├── database/               // Local database configuration (Room)
│   │   │   ├── preferences/            // Shared Preferences or DataStore
│   │   │   ├── utils/                  // General utilities
├── feature/                            // Feature-specific modules (modularized architecture)
│   ├── surveycreation/
│   │   ├── src/
│   │   │   ├── main/kotlin/com/example/surveyswift/surveycreation/
│   │   │   └── ...                     // Code for survey creation feature (separate from app module)
│   ├── surveyresponse/
│   │   ├── src/
│   │   │   ├── main/kotlin/com/example/surveyswift/surveyresponse/
│   │   │   └── ...                     // Code for survey response collection and management
├── analytics/                          // Analytics features (e.g., Firebase, custom analytics)
│   ├── src/
│   │   ├── main/kotlin/com/example/surveyswift/analytics/
├── build.gradle                        // Root build.gradle file
└── settings.gradle                     // Settings for project-level configuration

```

### **Core Features**

#### **User Authentication**
The app integrates optional **user authentication** using Firebase Authentication to enable secure login. Users can sign in via email or social media accounts. Once authenticated, they can save survey drafts, track responses, and access detailed analytics.

#### **Survey Creation**
**SurveySwift** allows users to create surveys with a flexible interface:
- **Question Types**: Supports multiple question types including multiple-choice, text input, checkboxes, dropdowns, and rating scales.
- **Conditional Logic**: Allows users to set up logic where specific questions are shown based on previous answers.
- **Predefined Templates**: Users can choose from various templates for specific survey types (e.g., customer satisfaction, event feedback).

#### **Real-Time Results**
The app features a **real-time dashboard** that updates as survey responses are collected. Users can view responses in various formats, such as:
- Bar charts, pie charts, and progress bars.
- Survey completion rate and average time to complete.
- Options to **export** data in CSV or PDF formats for further analysis.

#### **Offline Mode**
Surveys can be created, edited, and completed while offline. All data is stored locally using Room, and it syncs with the server once the device regains connectivity.

#### **Survey Sharing**
Users can share surveys via:
- **QR codes**: Automatically generated for easy sharing.
- **Shareable links**: Accessible through the app, allowing survey participants to fill out surveys through a mobile browser or the app.
- **Embed Surveys**: Provides an embed code to place surveys on websites.

#### **Customizability**
Surveys are highly customizable. Users can:
- Choose **themes** (colors, fonts) that align with their brand or preference.
- Customize **anonymity settings**, requiring participants to remain anonymous or allowing identified responses.
### **Security & Privacy**
SurveySwift employs the following security features:
- **Encryption**: Data is encrypted both in transit and at rest to ensure user privacy.
- **Role-Based Access**: Admin users have access to manage surveys and view results, while respondents only have access to fill out surveys.
### **User Interface (UI)**

#### **Form Builder**
The UI is built using Jetpack Compose components. The form builder allows for the drag-and-drop creation of survey elements:
- **LazyColumn** and **LazyRow** are used to manage lists of questions efficiently.
- Each question type (text, multiple-choice, rating) is represented as a separate **Composable**.

#### **Survey List Screen**
Users are greeted by a list of active surveys on the home screen. This screen uses card-based composables to display survey details such as:
- Survey title.
- Number of questions.
- Status (Active/Closed).
- Response count.

#### **Survey Preview**
Surveys can be previewed by the creator before being published. This screen presents a swipe-based interface where users can see how their surveys will look to respondents.

#### **Real-Time Dashboard**
The **dashboard** utilizes Compose animations to display results in real-time, providing an engaging experience. It features:
- Dynamic charts (e.g., bar, pie).
- **Progress bars** for response completion tracking.
### **Advanced Features**

#### **Multilingual Support**
The app supports **multilingual surveys**, allowing creators to design surveys in different languages. Users can toggle between languages during survey creation.

#### **Push Notifications**
**Push notifications** are integrated for sending reminders to participants about survey deadlines or notifying creators when surveys receive a high number of responses.

#### **Admin Dashboard**
An admin dashboard is available to manage all surveys, track analytics, and monitor user participation. This section features:
- Detailed performance metrics.
- **Role management** to control access for different types of users.
### **Theming and Accessibility**
The app is built with **dynamic theming**, allowing users to switch between light and dark mode. Accessibility features such as larger text sizes and screen reader support ensure inclusivity for all users.
### **Testing and Maintenance**

- **Unit Testing**: Unit tests are written for all ViewModels using **JUnit**.
- **UI Testing**: Compose UI testing is used to ensure that all UI components behave as expected.
- **Crash Reporting**: **Firebase Crashlytics** is integrated for real-time crash reporting and troubleshooting.
### **Analytics**

SurveySwift includes an analytics module to track:
- **Completion rates**.
- **Time spent** on each survey.
- Geographic distribution of responses.

These insights are presented through an intuitive **Compose-based dashboard** that updates dynamically as responses come in.
### **Closing**
SurveySwift combines the power of Jetpack Compose with modern architecture to deliver a seamless and efficient survey experience. Its focus on real-time feedback, offline functionality, and rich customizability makes it an ideal tool for users seeking fast, reliable survey solutions.
