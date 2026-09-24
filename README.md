# 🏋️ FitSense AI 🤖

## Personalized Fitness Recommendations Powered by AI

FitSense AI is an AI-powered fitness management and recommendation system developed as a Naan Mudhalvan project. It provides REST APIs for user authentication, workout tracking, workout management, and personalized fitness recommendations using Google Gemini AI.

---

## 📌 Project Overview

Many people track their workouts but do not receive personalized guidance based on their fitness goals, experience level, and workout history.

FitSense AI addresses this problem by combining workout management with Artificial Intelligence.

The system allows users to:

- Create and manage their fitness account
- Securely log in using JWT authentication
- Record and manage workout activities
- Search workouts
- Receive AI-generated personalized workout recommendations
- Analyze workout statistics using AI
- Get fitness insights, suggestions, and motivation

---

## ❗ Problem Statement

Traditional workout tracking applications mainly store workout information such as:

- Workout name
- Workout category
- Duration
- Calories burned
- Workout date

However, simply storing workout data does not provide personalized guidance.

Users need a system that can understand their fitness goals, experience level, and workout statistics and provide meaningful recommendations.

---

## 💡 Proposed Solution

FitSense AI provides an AI-powered REST API that combines secure workout management with Google Gemini AI.

### System Flow

User  
↓  
REST API  
↓  
Authentication & Validation  
↓  
Workout Management  
↓  
MongoDB Database  
↓  
Google Gemini AI  
↓  
Personalized Fitness Response

The system uses JWT authentication to protect user-specific workout data and Google Gemini AI to generate personalized recommendations and fitness insights.

---

## 🏗️ System Architecture

~~~~text
                    ┌──────────────────┐
                    │      Client      │
                    │  Postman / App   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   Express.js     │
                    │    REST API      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     Routes       │
                    │ Auth / Workout   │
                    │       / AI       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Authentication   │
                    │   & Validation   │
                    └────────┬─────────┘
                             │
                 ┌───────────┴───────────┐
                 ▼                       ▼
        ┌──────────────────┐    ┌──────────────────┐
        │   Controllers    │    │   AI Services    │
        │                  │    │  Google Gemini   │
        └────────┬─────────┘    └────────┬─────────┘
                 │                       │
                 ▼                       │
        ┌──────────────────┐              │
        │    MongoDB       │              │
        │   + Mongoose     │              │
        └──────────────────┘              │
                                          ▼
                              Personalized AI Response
~~~~

---

## 🤖 AI Workflow

FitSense AI uses Google Gemini to generate fitness-related responses.

### AI Workout Recommendation

The recommendation system accepts:

- Age
- Fitness goal
- Experience level

Example input:

~~~~json
{
  "age": 22,
  "fitnessGoal": "Weight Loss",
  "experience": "Beginner"
}
~~~~

The AI generates personalized workout guidance based on the provided information.

The recommendation can include:

- Personalized workout plan
- Weekly suggestions
- Experience-level recommendations
- Motivation
- Safety considerations

### AI Fitness Insights

The fitness insights API accepts workout statistics such as:

- Total workouts
- Average workout duration
- Total calories burned

Example input:

~~~~json
{
  "totalWorkouts": 10,
  "averageDuration": 35,
  "totalCaloriesBurned": 4000
}
~~~~

The AI analyzes these statistics and provides:

- Performance analysis
- Fitness suggestions
- Motivation
- Overall workout summary

---

## 🛠️ Technology Stack

### Backend

- Node.js
- Express.js
- JavaScript

### Database

- MongoDB
- Mongoose

### Authentication & Security

- JSON Web Tokens (JWT)
- bcrypt.js
- Environment variables

### Artificial Intelligence

- Google Gemini AI

### API Testing

- Postman

### Development Tools

- Visual Studio Code
- npm
- Git
- GitHub

---

## 📂 Project Structure

~~~~text
Code Files/
│
├── src/
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   ├── aiController.js
│   │   ├── authController.js
│   │   └── workoutController.js
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
│   │   ├── aiRoutes.js
│   │   ├── authRoutes.js
│   │   ├── index.js
│   │   └── workoutRoutes.js
│   │
│   ├── services/
│   │   └── geminiService.js
│   │
│   ├── app.js
│   └── server.js
│
├── .env
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── README.md
└── FitTrack.postman_collection.json
~~~~

---

## ⚙️ Prerequisites

Before running the project, install:

- Node.js 16 or later
- npm 8 or later
- MongoDB
- Visual Studio Code
- Postman
- Git

---

## 🚀 Installation and Setup

### 1. Clone the Repository

~~~~bash
git clone https://github.com/bsccsaisanthosh-cmyk/fitsense-ai.git
~~~~

### 2. Navigate to the Project

~~~~bash
cd fitsense-ai
~~~~

### 3. Install Dependencies

~~~~bash
npm install
~~~~

### 4. Start MongoDB

Make sure MongoDB is running locally.

The default database used by the application is:

~~~~text
mongodb://localhost:27017/fittrack
~~~~

### 5. Configure Environment Variables

Create a `.env` file in the project root.

~~~~env
PORT=5000
MONGO_URI=mongodb://localhost:27017/fittrack
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-3.6-flash
~~~~

Do not commit the `.env` file to GitHub.

### 6. Start the Server

~~~~bash
npm start
~~~~

The server will run on:

~~~~text
http://localhost:5000
~~~~

---

## ❤️ API Health Check

After starting the server, open:

~~~~text
http://localhost:5000
~~~~

Expected response:

~~~~json
{
  "success": true,
  "message": "AI FitTrack API is running successfully",
  "version": "1.0.0"
}
~~~~

---

# 📡 API Documentation

Base URL:

~~~~text
http://localhost:5000/api
~~~~

---

## 🔐 Authentication APIs

### Register User

~~~~text
POST /auth/register
~~~~

Example request:

~~~~json
{
  "name": "Santhosh",
  "email": "user@example.com",
  "password": "your_password"
}
~~~~

### Login User

~~~~text
POST /auth/login
~~~~

Example request:

~~~~json
{
  "email": "user@example.com",
  "password": "your_password"
}
~~~~

The login response provides a JWT token that is used to access protected APIs.

### Get Profile

~~~~text
GET /auth/profile
~~~~

Requires:

~~~~text
Authorization: Bearer <JWT_TOKEN>
~~~~

---

## 🏋️ Workout APIs

All workout operations are protected using JWT authentication.

### Create Workout

~~~~text
POST /workouts
~~~~

Example:

~~~~json
{
  "workoutName": "Morning Running",
  "category": "Running",
  "duration": 35,
  "caloriesBurned": 400,
  "workoutDate": "2026-06-26"
}
~~~~

### Get All Workouts

~~~~text
GET /workouts
~~~~

Returns the authenticated user's workouts.

### Get Workout by ID

~~~~text
GET /workouts/:id
~~~~

### Update Workout

~~~~text
PUT /workouts/:id
~~~~

Example:

~~~~json
{
  "workoutName": "Morning Running",
  "category": "Running",
  "duration": 35,
  "caloriesBurned": 400,
  "workoutDate": "2026-06-26"
}
~~~~

### Delete Workout

~~~~text
DELETE /workouts/:id
~~~~

### Search Workouts

~~~~text
GET /workouts/search?q=running
~~~~

The search API can be used to find workouts based on their name or related information.

---

## 🤖 AI APIs

### AI Workout Recommendation

~~~~text
POST /ai/workout-recommendation
~~~~

Example request:

~~~~json
{
  "age": 22,
  "fitnessGoal": "Weight Loss",
  "experience": "Beginner"
}
~~~~

The API sends the information to Google Gemini AI and returns a personalized fitness recommendation.

### AI Fitness Insights

~~~~text
POST /ai/fitness-insights
~~~~

Example request:

~~~~json
{
  "totalWorkouts": 10,
  "averageDuration": 35,
  "totalCaloriesBurned": 4000
}
~~~~

The API analyzes the workout statistics and generates AI-based fitness insights.

---

## 🔒 Security

FitSense AI implements several security practices:

- JWT-based authentication
- Password hashing using bcrypt.js
- Protected workout APIs
- Environment variables for sensitive configuration
- User-specific workout access
- Request validation
- Centralized error handling
- Secure API key management

Sensitive information such as database credentials, JWT secrets, and Gemini API keys should never be committed to GitHub.

---

## 🧪 Testing

The APIs were tested using Postman.

The Postman collection contains requests for:

- User registration
- User login
- Profile retrieval
- Workout creation
- Workout retrieval
- Workout retrieval by ID
- Workout update
- Workout search
- Workout deletion
- AI workout recommendation
- AI fitness insights

### Tested Project Flow

~~~~text
Register
   ↓
Login
   ↓
Get Profile
   ↓
Create Workout
   ↓
Get Workouts
   ↓
Get Workout by ID
   ↓
Update Workout
   ↓
Search Workout
   ↓
AI Workout Recommendation
   ↓
AI Fitness Insights
   ↓
Delete Workout
~~~~

---

## ✅ Tested Features

- [x] User Registration
- [x] User Login
- [x] JWT Authentication
- [x] User Profile
- [x] Create Workout
- [x] Get Workouts
- [x] Get Workout by ID
- [x] Update Workout
- [x] Search Workout
- [x] Delete Workout
- [x] AI Workout Recommendation
- [x] AI Fitness Insights
- [x] MongoDB Integration
- [x] Google Gemini AI Integration
- [x] Postman API Testing

---

## 🎓 Naan Mudhalvan Project

FitSense AI was developed as part of the Naan Mudhalvan academic project.

The project focuses on applying modern software development and Artificial Intelligence concepts to a practical fitness-related problem.

### Project Objectives

- Develop a RESTful backend application
- Implement secure user authentication
- Store and manage workout information
- Integrate Artificial Intelligence into a real-world application
- Generate personalized fitness recommendations
- Analyze workout statistics using AI
- Practice API development and testing
- Work with MongoDB and Mongoose
- Understand MVC-based backend architecture

---

## 📚 Learning Outcomes

Through this project, the team gained practical experience in:

- Node.js backend development
- Express.js REST API development
- MongoDB database management
- Mongoose ODM
- JWT authentication
- Password hashing
- Middleware implementation
- MVC architecture
- API validation
- Error handling
- Google Gemini AI integration
- Prompt-based AI interaction
- Postman API testing
- Git and GitHub version control

---

## 👥 Project Team

### Team Leader

**Santhosh C**

### Team Members

**Tharun M.P**

**Rajiv P**

**Logesh I**

---

## 🔮 Future Enhancements

Future versions of FitSense AI can include:

- Mobile application
- Web-based fitness dashboard
- Fitness progress charts
- AI-powered diet recommendations
- Workout reminders
- Exercise video guidance
- Wearable device integration
- Advanced workout analytics
- Personalized long-term fitness plans
- Cloud deployment
- More advanced AI fitness insights

---

## 🌟 Project Purpose

FitSense AI demonstrates how Artificial Intelligence can be integrated with a secure REST API and database to create a practical personalized fitness system.

The project combines:

**Backend Development + Database Management + Authentication + Artificial Intelligence**

to provide users with personalized and data-driven fitness assistance.

---

## 📌 Repository

GitHub Repository:

https://github.com/bsccsaisanthosh-cmyk/fitsense-ai

---

## 📄 License

This project is developed for academic and educational purposes as part of the Naan Mudhalvan project.

---

# 🏋️ FitSense AI

### Personalized Fitness Recommendations Powered by AI

**Developed by the FitSense AI Team**
