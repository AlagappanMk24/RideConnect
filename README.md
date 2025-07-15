🚗 Ride Connect
Ride Connect is a full-stack carpooling web application built with ASP.NET Core 9.0 for the backend and Angular 17+ for the frontend, meticulously designed following Clean Architecture principles. It connects drivers and passengers for safe, efficient, and eco-friendly shared rides, aiming to reduce traffic congestion and transportation costs through seamless ride booking and management.

🎯 Project Goal
To reduce traffic congestion and transportation costs by building a smart carpooling platform that enables seamless ride booking and management, supported by real-time mapping and seat-based booking features.

✨ Key Features
Ride Connect offers a comprehensive set of features for both drivers and passengers, as well as administrators:

Core Functionality

User Authentication & Authorization: Secure registration, login (JWT), password reset, email confirmation, and role-based access for Passengers, Drivers, and Admins.

Trip Management: Drivers can create and manage new carpooling trips; Passengers can search, book, and manage available trips with detailed views.

Delivery System: Integrated feature for creating and managing package delivery requests alongside passenger trips.

User Profiles: Comprehensive profile management, including personal information updates and document uploads (e.g., driver's license, national ID).

Driver Verification: Streamlined process for drivers to register and get documents verified by administrators.

Real-time Notifications: Automated email notifications and in-app updates for critical events (e.g., booking confirmations, status changes).

Rating & Feedback: Users can rate trips and provide reviews for drivers/passengers.

Admin Dashboard: Centralized panel for user management, document verification approvals, and system oversight.

Advanced Features
Real-time Location Tracking: Utilizes GPS coordinates for precise trip source and destination tracking.

Gender Preferences: Optional gender-based matching for personalized trip preferences.

Document Upload: Secure file storage for user documents via Cloudinary integration.

User Experience (Frontend Specific)

Responsive Design: Seamlessly adapts to desktop, tablet, and mobile devices for optimal viewing.

Modern UI: Built with Angular Material components, ensuring a clean and contemporary interface.

Intuitive Navigation: User-friendly navigation structure for effortless interaction.

Form Validation: Comprehensive client-side validation with real-time feedback.

Loading States: Smooth loading indicators and transitions for a better user experience.

Error Handling: User-friendly error messages and success feedback notifications.

🏗️ Architecture

This project strictly adheres to Clean Architecture principles, ensuring a clear separation of concerns, testability, and maintainability.

Backend Structure (CarPooling.Backend/)

The backend is organized into the following layers:

CarPooling.API/: Presentation Layer - Handles HTTP requests, authentication, and orchestrates calls to the application layer.

CarPooling.Application/: Application Layer - Defines use cases and orchestrates business logic. Contains DTOs and interfaces for infrastructure concerns.

CarPooling.Domain/: Domain Layer - The core of the business logic, containing entities, value objects, domain services, and domain events. Independent of other layers.

CarPooling.Infrastructure/: Infrastructure Layer - Provides concrete implementations for data access (e.g., Entity Framework Core), external services (Cloudinary, SMTP), and other technical concerns.

Frontend Structure (CarPooling.Frontend/)

The Angular frontend follows a modular and component-driven architecture:

src/
├── app/
│   ├── components/           # Feature components (e.g., account, admin, auth, trip, user)
│   ├── core/                 # Core services, guards, interceptors, models
│   ├── features/             # Feature modules (if using lazy loading)
│   └── shared/               # Shared utilities and components (navbar, footer)
├── assets/                   # Static assets (images, icons)
├── environments/             # Environment configurations (dev, prod)
└── styles/                   # Global styles

🚀 Technology Stack

Backend

Framework: ASP.NET Core 9.0

Database: SQL Server with Entity Framework Core

Authentication: ASP.NET Core Identity + JWT

File Storage: Cloudinary

Email Service: SMTP (Gmail)

Documentation: Swagger/OpenAPI

Frontend

Framework: Angular 17+

Language: TypeScript

UI Library: Angular Material

State Management: Angular Services + RxJS

HTTP Client: Angular HttpClient

Routing: Angular Router

Build Tool: Angular CLI

Package Manager: npm

📋 Prerequisites

Before running this application, ensure you have the following installed:

Node.js: v18 or later

npm: v8 or later (or yarn)

Angular CLI: Install globally via npm install -g @angular/cli

.NET 9.0 SDK: or later

SQL Server: (LocalDB, Express, or full version)

Visual Studio 2022 or VS Code with C# extension

Git

🛠️ Installation & Setup

Clone the Repository

git clone <repository-url>

cd RideConnect # Or your actual root repo folder name

Backend Setup

Navigate to the backend directory:

cd CarPooling.Backend

Database Setup:

Update your connection string in CarPooling.API/appsettings.json to point to your SQL Server instance:

"ConnectionStrings": {
    "DefaultConnection": "Server=.;Database=CarPoolingDb;Trusted_Connection=True;TrustServerCertificate=True;"
}

Run migrations to create the database schema. Open your terminal in the CarPooling.Backend directory and run:

dotnet ef database update --project CarPooling.API

(Note: If you're using Package Manager Console in Visual Studio, it's Update-Database)

External Services Configuration:

Cloudinary: Update your Cloudinary settings in CarPooling.API/appsettings.json:

"CloudinarySettings": {
    "CloudName": "your-cloud-name",
    "ApiKey": "your-api-key",
    "ApiSecret": "your-api-secret"
}

Email (SMTP): Configure SMTP settings in CarPooling.API/appsettings.json for email functionality:

"Email": {
    "Username": "your-email@gmail.com",
    "Password": "your-app-password", # Use an app password for Gmail
    "Host": "smtp.gmail.com",
    "Port": 587,
    "EnableSsl": true,
    "DisplayName": "Car Pooling App"
}

Build and Run Backend:

Navigate to the CarPooling.API project folder:

cd CarPooling.API

dotnet restore # Restore NuGet packages
dotnet build   # Build the project
dotnet run     # Run the application (API will typically run on https://localhost:7082 or similar)

Frontend Setup

Open a new terminal and navigate to the frontend directory:

cd CarPooling.Frontend

Install Dependencies:

npm install

Configure Backend API URL:

Ensure your Angular environment configuration (src/environments/environment.ts or environment.development.ts) points to your running backend API. For example:

export const environment = {
  production: false,
  apiUrl: 'https://localhost:7082/api/' // Adjust to your backend API URL
};

Run Frontend:

ng serve --open

This will compile the Angular application and open it in your default web browser (typically at http://localhost:4200/).
