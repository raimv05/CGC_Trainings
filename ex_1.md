//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

📅 DAY 26
JWT Authentication + Axios + Protected APIs
Duration

3 Hours

Learning Outcomes

Students will learn

JWT (JSON Web Token)
Authentication vs Authorization
Token-based Authentication
Axios
Axios Instance
Authorization Headers
Protected APIs
Private Routes
Refreshing Authentication State
Project Goal

Replace the temporary login system with a real authentication system using JWT.

Final Deliverable
Login

↓

JWT Token

↓

Axios

↓

Protected Backend APIs

↓

Dashboard
First 90 Minutes
JWT Authentication
Part 1
Start with Question

Yesterday

User Login

↓

Context API

Question

Can anyone open Postman

and call

GET /courses

Yes.

Need

Authentication
Authentication vs Authorization

Draw

Authentication

↓

Who are you?

Authorization

↓

What can you access?
Install JWT
npm install jsonwebtoken
Generate Token
const jwt = require("jsonwebtoken");

const token = jwt.sign(

{ id: user._id },

process.env.JWT_SECRET,

{ expiresIn: "1d" }

);

Explain

Token contains

User ID

Expiry

Signature
Login API

After password verification

Return

{

"token":"eyJhbGciOiJIUzI1Ni..."

}
Verify Token Middleware

Create

middleware

authMiddleware.js
const jwt = require("jsonwebtoken");

function protect(req,res,next){

const token=req.headers.authorization;

...

}

Explain

Request

↓

Token

↓

Verification

↓

Next()
Protect Routes
router.get(

"/courses",

protect,

getCourses

);

Students see

Protected APIs.

Second 90 Minutes
Axios + Frontend Authentication
Install
npm install axios
Why Axios?

Compare

fetch()

vs

axios.get()

Explain advantages:

Cleaner syntax
Automatic JSON parsing
Interceptors
Base URL configuration
Axios Instance
import axios from "axios";

const api = axios.create({

baseURL:"http://localhost:5000/api"

});
Login Request
const response=

await api.post(

"/login",

loginData

);
Store Token
localStorage.setItem(

"token",

response.data.token

);
Attach Token
api.defaults.headers.common[
"Authorization"
]=

`Bearer ${token}`;
Access Protected API
await api.get("/courses");
Logout
localStorage.removeItem("token");
Mini Challenge

Implement

Student Login

Admin Login

Logout

Protected Dashboard
Assignment

Complete Authentication Module

✔ JWT

✔ Axios

✔ Login

✔ Logout

✔ Protected APIs

✔ Private Dashboard
Project Status
React

↓

Axios

↓

JWT

↓

Protected APIs

↓

MongoDB
📅 DAY 27
Complete MERN LMS Dashboard

Duration

3 Hours

Learning Outcomes

Students will learn

Dashboard Design
Admin Panel
Student Module
Course Module
Enrollment Module
Role-Based Access
API Integration
Project Refactoring
Project Goal

Finish the complete SkillHub LMS.

Final Deliverable
Admin Dashboard

↓

Student Module

↓

Course Module

↓

Enrollment Module

↓

Analytics
First 90 Minutes
Student Management
Build Student Dashboard

Features

View Students

Search Students

Update Student

Delete Student
Course Dashboard

Features

Add Course

Edit Course

Delete Course

Search Course
Enrollment Module

Students

↓

Enroll

↓

Course

↓

Database

Dashboard Cards
Total Students

Total Courses

Total Enrollments

Active Trainers
Charts (Optional)

Introduce

Chart.js
Recharts

Display

Course Enrollment Chart

Student Growth

Course Distribution
Second 90 Minutes
Project Refactoring
Backend Folder Structure
backend

config/

controllers/

middleware/

models/

routes/

utils/

app.js

server.js
Frontend Folder Structure
src

components/

pages/

context/

services/

hooks/

utils/

assets/

App.jsx
Error Handling

Create

Error Component
Loading Component
Spinner
Toast Notifications

Replace

alert()

with

Bootstrap Toast or React Toastify.

Mini Challenge

Students build

Profile Page

Settings

Change Password
Assignment

Complete LMS

✔ CRUD

✔ JWT

✔ Dashboard

✔ Analytics

✔ Search

✔ Error Handling
End Result
Professional MERN LMS
📅 DAY 28
Deployment & Production

Duration

3 Hours

Learning Outcomes

Students learn

Environment Variables
Build Process
Deployment
GitHub
Vercel
Render
MongoDB Atlas
Production Best Practices
Project Goal

Deploy SkillHub LMS online.

Final Deliverable
Live MERN LMS

Frontend

↓

Vercel

Backend

↓

Render

Database

↓

MongoDB Atlas
First 90 Minutes
Production Preparation
Environment Variables

Frontend

.env

VITE_API_URL=

Backend

.env

PORT

MONGO_URI

JWT_SECRET

Explain

Never hardcode secrets.

Build React
npm run build

Explain

src

↓

dist
GitHub Push
git add .

git commit -m "Final MERN LMS"

git push
Deploy Backend

Render

Create Web Service
Connect GitHub repository
Configure build/start commands
Add environment variables
Deploy Frontend

Vercel

Import GitHub repository
Set VITE_API_URL
Deploy
Second 90 Minutes
Testing & Final Presentation
End-to-End Testing

Test:

Login

Register

CRUD

Search

Enrollment

Logout

Protected Routes
Bug Fixing Session

Students identify and fix:

API errors
Validation issues
Broken routes
Deployment configuration
Project Documentation

Create

README.md

Include:

Project Overview
Features
Tech Stack
Folder Structure
Installation
Environment Variables
API Endpoints
Screenshots
Live Demo
Future Enhancements
Resume & Portfolio

Teach students how to present the project.

Resume Example:

SkillHub LMS

• Developed a full-stack Learning Management System using MERN Stack.

• Implemented JWT Authentication, Role-Based Access, CRUD Operations, REST APIs, MongoDB Atlas, and React Context API.

• Deployed frontend on Vercel and backend on Render with secure environment configuration.
Mini Challenge

Students present their LMS in 5-minute demo sessions covering:

Project overview
Architecture
Features
Authentication flow
CRUD operations
Deployment
Final Assignment

Polish the application by adding at least three advanced features, such as:

Email notifications for course enrollment
Student profile image upload
Pagination and sorting
Dark mode
Course completion progress
Wishlist/Favorites
Password reset
Admin analytics charts

Deploy the updated project and share:

GitHub repository
Live frontend URL
Live backend API URL
README documentation
🎓 Final Course Outcome
HTML5
    │
CSS3
    │
Bootstrap
    │
JavaScript (ES6+)
    │
Git & GitHub
    │
Node.js
    │
Express.js
    │
REST APIs
    │
MongoDB Atlas
    │
Mongoose
    │
React
    │
React Router
    │
Context API
    │
Axios
    │
JWT Authentication
    │
Full CRUD
    │
Deployment
    │
Production MERN Application
🎯 What Students Achieved