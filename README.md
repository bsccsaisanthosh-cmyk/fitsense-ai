🏋️ FitSense AI 🤖
Personalized Fitness Recommendations Powered by AI

FitSense AI is an AI-powered fitness tracking and recommendation system developed as part of the Naan Mudhalvan Project.

The application combines Node.js, Express.js, MongoDB, JWT Authentication, bcrypt, and Google Gemini AI to provide secure workout management, personalized workout recommendations, and AI-powered fitness insights.

📌 Project Overview

Fitness applications can help users record their workouts, but simply storing workout data does not always provide personalized guidance.

FitSense AI combines workout tracking with Generative AI to help users understand their fitness activity and receive personalized recommendations based on their goals and experience.

The system provides a secure REST API that allows users to:

Create and manage their accounts
Authenticate securely using JWT
Record workout activities
View and search workout history
Update and delete workouts
Get AI-powered workout recommendations
Get AI-generated fitness insights
🎯 Problem Statement

Many fitness tracking systems primarily focus on recording workout information.

Users may still need personalized guidance to understand their workout patterns and decide what type of activities may be suitable for their fitness goals and experience.

FitSense AI addresses this problem by combining fitness tracking with Generative AI.

💡 Proposed Solution

FitSense AI provides a centralized backend API that connects:

User → REST API → Authentication & Validation → Workout Management → MongoDB → Google Gemini AI → Personalized Fitness Response

The system securely stores workout data and uses AI to generate personalized recommendations and fitness insights.

✨ Key Features
🔐 User Authentication
User registration
Secure password hashing using bcrypt
User login
JWT-based authentication
Protected API routes
User profile retrieval
🏃 Workout Management

Users can:

Add workouts
View all workouts
View a specific workout
Update workout details
Delete workouts
Search workouts

Each workout contains:

Workout name
Category
Duration
Calories burned
Workout date
🔍 Workout Search

Users can search workouts using workout-related information.

Example:

GET /api/workouts/search?q=running

🧠 AI Workout Recommendation

FitSense AI integrates Google Gemini AI to generate personalized workout recommendations.

The recommendation system uses:

Age
Fitness goal
Experience level
Example Request
{
  "age": 22,
  "fitnessGoal": "Weight Loss",
  "experience": "Beginner"
}

The system generates a personalized workout recommendation based on the provided fitness information.

📊 AI Fitness Insights

The application can analyze workout statistics and generate AI-powered fitness insights.

The AI receives information such as:

Total workouts
Average workout duration
Total calories burned
Example Request
{
  "totalWorkouts": 18,
  "averageDuration": 45,
  "totalCaloriesBurned": 6200
}

The AI generates:

Performance observations
Suggestions
Motivation
Fitness summary
🏗️ System Architecture
                    ┌──────────────────────┐
                    │        User          │
                    │  Postman / Frontend  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Express.js       │
                    │       REST API       │
                    └──────────┬───────────┘
                               │
                    ┌──────────▼───────────┐
                    │   JWT Middleware     │
                    │    Authentication    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Controllers      │
                    └──────────┬───────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
                ▼                             ▼
       ┌─────────────────┐          ┌─────────────────┐
       │     MongoDB     │          │   Gemini AI     │
       │                 │          │                 │
       │ Users           │          │ Recommendations │
       │ Workouts        │          │ Insights        │
       └─────────────────┘          └─────────────────┘
🧠 AI Workflow
User Fitness Information
          │
          ▼
    REST API Request
          │
          ▼
   JWT Authentication
          │
          ▼
    AI Controller
          │
          ▼
    Gemini Service
          │
          ▼
    Google Gemini AI
          │
          ▼
 Personalized Response
          │
          ▼
        User
🛠️ Technology Stack
Technology	Purpose
Node.js	Backend runtime
Express.js	REST API framework
MongoDB	Database
Mongoose	MongoDB ODM
Google Gemini AI	Generative AI
JWT	Authentication
bcryptjs	Password hashing
Morgan	HTTP request logging
Postman	API testing
Git & GitHub	Version control
📁 Project Structure
fitsense-ai/
│
├── src/
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── workoutController.js
│   │   └── aiController.js
│   │
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   │
│   ├── models/
│   │   ├── User.js
│   │   └── Workout.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── workoutRoutes.js
│   │   ├── aiRoutes.js
│   │   └── index.js
│   │
│   ├── services/
│   │   └── geminiService.js
│   │
│   ├── app.js
│   └── server.js
│
├── postman/
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── README.md
└── FitTrack.postman_collection.json
🚀 Getting Started
1. Prerequisites

Make sure the following are installed:

Node.js
npm
MongoDB
Git
Postman
Google Gemini API Key
2. Clone the Repository
git clone https://github.com/bsccsaisanthosh-cmyk/fitsense-ai.git
cd fitsense-ai
3. Install Dependencies
npm install
4. Configure Environment Variables

Create a .env file in the project root.

Use .env.example as a reference.

PORT=5000
MONGO_URI=mongodb://localhost:27017/fittrack
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-3.6-flash
⚠️ Security

Never upload the .env file to GitHub.

The .env file is excluded using .gitignore.

▶️ Running the Application

Start the server using:

npm start

The server runs on:

http://localhost:5000

🩺 API Health Check

Open:

http://localhost:5000

Expected response:

{
  "success": true,
  "message": "AI FitTrack API is running successfully",
  "version": "1.0.0"
}
🔌 API Documentation

Base URL:

http://localhost:5000/api

🔐 Authentication APIs
Method	Endpoint	Authentication
POST	/auth/register	Not Required
POST	/auth/login	Not Required
GET	/auth/profile	JWT Required
Register User

POST /api/auth/register

Example request:

{
  "name": "John Doe",
  "email": "john@gmail.com",
  "password": "123456"
}
Login User

POST /api/auth/login

Example request:

{
  "email": "john@gmail.com",
  "password": "123456"
}
User Profile

GET /api/auth/profile

Authentication:

Authorization: Bearer <JWT_TOKEN>

🏃 Workout APIs

All workout APIs require JWT authentication.

Method	Endpoint	Purpose
POST	/workouts	Create workout
GET	/workouts	Get all workouts
GET	/workouts/:id	Get workout by ID
PUT	/workouts/:id	Update workout
DELETE	/workouts/:id	Delete workout
GET	/workouts/search?q=	Search workouts
Create Workout

POST /api/workouts

Example request:

{
  "workoutName": "Morning Running",
  "category": "Running",
  "duration": 35,
  "caloriesBurned": 400,
  "workoutDate": "2026-06-26T18:00:00.000Z"
}
🤖 AI APIs
AI Workout Recommendation

POST /api/ai/workout-recommendation

Example request:

{
  "age": 22,
  "fitnessGoal": "Weight Loss",
  "experience": "Beginner"
}

Purpose:
Generates a personalized workout recommendation using Google Gemini AI.

AI Fitness Insights

POST /api/ai/fitness-insights

Example request:

{
  "totalWorkouts": 18,
  "averageDuration": 45,
  "totalCaloriesBurned": 6200
}

Purpose:
Analyzes workout statistics and generates AI-powered fitness insights.

🔒 Security

FitSense AI implements:

JWT authentication
bcrypt password hashing
Protected API routes
User-specific workout access
Environment variables for secrets
Centralized error handling
Input validation
.env protection using .gitignore
🧪 Postman API Testing

The project includes a Postman collection:

FitTrack.postman_collection.json

The collection contains:

Authentication APIs
Workout APIs
Workout search
AI workout recommendation
AI fitness insights

The JWT token can be used for authenticated requests.

✅ Tested Features
 User Registration
 User Login
 JWT Authentication
 User Profile
 Create Workout
 Get All Workouts
 Get Workout by ID
 Update Workout
 Delete Workout
 Workout Search
 AI Workout Recommendation
 AI Fitness Insights
 MongoDB Connection
 Google Gemini AI Integration
 GitHub Repository
📸 Project Screenshots

Screenshots can be added to demonstrate the working project.

Recommended screenshots:

User Registration
User Login
User Profile
Create Workout
Get Workouts
Search Workout
AI Workout Recommendation
AI Fitness Insights
🎓 Naan Mudhalvan Project
Project Information

Project Name: FitSense AI

Project Title: Personalized Fitness Recommendations Powered by AI

Program: Naan Mudhalvan

Domain: Artificial Intelligence / Backend Development

Institution: University of Madras

Course: BSc Computer Science with Artificial Intelligence

🎯 Project Objectives

The main objectives of FitSense AI are:

Develop a secure REST API for fitness tracking.
Implement user authentication using JWT.
Store workout information using MongoDB.
Implement CRUD operations for workout management.
Provide workout search functionality.
Integrate Google Gemini AI.
Generate personalized workout recommendations.
Generate AI-powered fitness insights.
Apply MVC architecture.
Test REST APIs using Postman.
📚 Learning Outcomes

Through this project, the team gained practical experience in:

REST API development
Node.js
Express.js
MongoDB
Mongoose
JWT authentication
Password hashing
MVC architecture
Generative AI
Google Gemini API
API testing
Git
GitHub
Environment configuration
👥 Project Team

This project was developed as a team project under the Naan Mudhalvan program.

Name	Role
Santhosh C	👑 Team Leader
Tharun M.P	Team Member
Rajiv P	Team Member
Logesh I	Team Member
👑 Team Leader
Santhosh C

Course: BSc Computer Science with Artificial Intelligence

University: University of Madras

Role: Team Leader

GitHub:
https://github.com/bsccsaisanthosh-cmyk

🔮 Future Enhancements

Future versions of FitSense AI can include:

Fitness dashboard
Workout progress charts
Weekly and monthly reports
Exercise library
Workout reminders
Personalized nutrition recommendations
Mobile application
AI-based progress prediction
Admin dashboard
Cloud deployment
Real-time fitness tracking
📄 Project Purpose

This project was developed for educational purposes as part of the Naan Mudhalvan program.

The project demonstrates the practical implementation of:

Backend Development + Database Management + Authentication + Generative AI

⭐ FitSense AI

Track your workouts. Understand your progress. Get AI-powered recommendations.

Built with ❤️ by the FitSense AI Team
