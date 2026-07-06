🚀 DAY 22
React Forms & Event Handling
Duration

3 Hours

Learning Outcomes

Students will learn

Controlled Components
Event Handling
onChange
onSubmit
Controlled Forms
React Validation
useState with Objects
Dynamic Form Handling
Project Goal

Build the Student Registration Module inside React.

Replace

HTML Registration Form

with

React Registration Form
Final Deliverable
SkillHub LMS

React Registration Form

↓

Input Handling

↓

Validation

↓

Display Student Details
First 90 Minutes
Controlled Components
Part 1
Why React Forms?

Ask

Earlier

HTML Form

↓

DOM

↓

getElementById()

Now

React

↓

State

Draw

Input

↓

State

↓

UI
Create Form
function Register(){

return(

<form>

<input

type="text"

placeholder="Student Name"

/>

</form>

);

}
Problem

How do we access

Input Value?

useState
const [name,setName]=useState("");

Input

<input

value={name}

onChange={(e)=>setName(e.target.value)}

/>

Explain

value

↓

Current State

onChange

↓

Updates State

Display

<h2>

Welcome {name}

</h2>

Students love seeing live updates.

Part 2

Multiple Inputs

Instead of

name

email

course

Three states

Teach

Object State

const [student,setStudent]=useState({

name:"",

email:"",

course:""

});

Change

onChange={(e)=>{

setStudent({

...student,

name:e.target.value

});

}}

Explain

Spread Operator.

Generic Input Handler
const handleChange=(e)=>{

setStudent({

...student,

[e.target.name]:e.target.value

});

}

Students realize

One function

Handles

Entire Form.

Second 90 Minutes
Validation + Student Preview
Form Submit
<form

onSubmit={handleSubmit}

>

Prevent Refresh

const handleSubmit=(e)=>{

e.preventDefault();

}

Validation

if(student.name===""){

alert("Enter Name");

return;

}

Validate Email

Password

Course

Display Student Card

After Submit

Show

Bootstrap Card

Rahul

MERN Stack

rahul@gmail.com

using

student.name

student.email
Reset Form
setStudent({

name:"",

email:"",

course:""

});
Mini Challenge

Students add

Phone

City

College

Semester
Assignment

Create

Trainer Registration

Name

Technology

Experience

Photo URL

Preview Card
End Result
React Registration Form

↓

Controlled Components

↓

Validation

↓

Student Preview
🚀 DAY 23
useEffect + Fetch API Integration

Duration

3 Hours

Learning Outcomes

Students learn

useEffect
API Calls
Fetch API
Loading State
Error Handling
Dynamic Data
CRUD Integration
Project Goal

Connect

React

↓

Express

↓

MongoDB

Finally

React becomes

Full Stack.

Final Deliverable
React

↓

GET Courses

↓

Display Cards

↓

POST Course

↓

Delete Course
First 90 Minutes
useEffect
Start with Question

Current

Courses

Hardcoded

Need

Database

What is useEffect?

Explain

Component Loads

↓

Call API

↓

Display Data

Import

import{

useEffect,

useState

}from"react";

Create State

const [courses,setCourses]=useState([]);

useEffect

useEffect(()=>{

console.log("Component Loaded");

},[]);

Explain

[]

↓

Run Once
Fetch API
async function getCourses(){

const response=

await fetch(

"http://localhost:5000/courses"

);

const data=

await response.json();

setCourses(data);

}

Call

useEffect(()=>{

getCourses();

},[]);

Students see

Database

↓

React

Loading State
const[loading,setLoading]

=useState(true);

Before API

setLoading(true);

After

setLoading(false);

Display

Loading...
Second 90 Minutes
Complete CRUD Integration
Display Cards
courses.map(course=>(

<CourseCard

key={course._id}

...

/>

))
Add Course

Current

Local State

Replace

API

await fetch(

"/courses",

{

method:"POST",

headers:{

"Content-Type":"application/json"

},

body:JSON.stringify(course)

}

);

Refresh

getCourses();
Delete
await fetch(

`/courses/${id}`,

{

method:"DELETE"

}

);

Refresh

Again

Error Handling
try{

}

catch(error){

console.log(error);

}
Empty State

If

No Courses

Display

No Courses Found
Dashboard

Display

Total Courses

↓

courses.length
Mini Challenge

Students implement

Search

↓

filter()

↓

React State
Assignment

Complete

React Course Dashboard

Features

✔ Fetch Courses

✔ Add Course

✔ Delete Course

✔ Loading

✔ Error Handling

✔ Search

✔ Course Count
Project Progress
React LMS

↓

Components

↓

Props

↓

State

↓

Forms

↓

Validation

↓

useEffect

↓

Fetch API

↓

MongoDB

↓

Full Stack CRUD

DAY 24
React Router & Multi-Page Application
Duration

3 Hours

Learning Outcomes

Students will learn

React Router
BrowserRouter
Routes
Route
Link
NavLink
useNavigate
URL Parameters
404 Page
Project Goal

Convert SkillHub LMS from a Single Component into a Multi-Page Application.

Final Deliverable
SkillHub LMS

Home

Courses

Students

Dashboard

About

Login

404 Page
First 90 Minutes
React Router Fundamentals
Part 1
Start with a Question

Ask

Currently

Everything is inside

App.jsx

What happens if our project has

50 pages?

Impossible to maintain.

Need

Routing
Install
npm install react-router-dom
Wrap Application

main.jsx

import { BrowserRouter } from "react-router-dom";

ReactDOM.createRoot(document.getElementById("root")).render(

<BrowserRouter>

<App/>

</BrowserRouter>

);

Explain

BrowserRouter controls navigation.

Create Pages Folder
src

pages

Home.jsx

Courses.jsx

Students.jsx

Dashboard.jsx

About.jsx

Login.jsx

Explain

Professional Folder Structure

Create Home
function Home(){

return(

<h1>

Home Page

</h1>

);

}

export default Home;
Configure Routes
import{

Routes,

Route

}from"react-router-dom";
<Routes>

<Route path="/" element={<Home/>}/>

<Route path="/courses" element={<Courses/>}/>

<Route path="/students" element={<Students/>}/>

<Route path="/dashboard" element={<Dashboard/>}/>

</Routes>

Run

Visit

/courses

/dashboard

Students immediately understand routing.

Second 90 Minutes
Navigation & Dynamic Routing
Link

Current

<a href="">

Wrong in React.

Use

<Link to="/courses">

Courses

</Link>

Explain

No Page Reload.

Navbar

Create reusable Navbar

<Link to="/">Home</Link>

<Link to="/courses">Courses</Link>

<Link to="/students">Students</Link>

<Link to="/dashboard">Dashboard</Link>
NavLink

Instead of

<Link>

Teach

<NavLink
to="/courses"
className={({isActive})=>

isActive?

"active"

:""

}
>

Courses

</NavLink>

Students see active navigation.

useNavigate()

Problem

After Login

Need

Dashboard.

const navigate=useNavigate();

After Login

navigate("/dashboard");
Dynamic Route
<Route

path="/course/:id"

element={<CourseDetails/>}

/>

Visit

/course/101

Inside

import{

useParams

}
const{id}=useParams();

Output

101
404 Page
<Route

path="*"

element={<NotFound/>}

/>
Mini Challenge

Students build

Student Profile Page

/student/:id
Assignment

Create

Home

Courses

Students

Dashboard

About

Login

404

Responsive Navbar

using React Router.

End Result
Multi Page React LMS

↓

React Router

↓

Professional Navigation
DAY 25
Context API & Authentication State Management

Duration

3 Hours

Learning Outcomes

Students learn

Context API
createContext
Provider
useContext
Global State
Login State
Logout
Protected Routes
Project Goal

Implement Authentication State using Context API.

Final Deliverable
Login

↓

Context

↓

Dashboard

↓

Logout

↓

Protected Routes
First 90 Minutes
Context API
Start with Question

Current

Navbar

Needs

User Name

Dashboard

Needs

User Name

Profile

Needs

User Name

Passing Props

App

↓

Navbar

↓

Dashboard

↓

Profile

↓

Settings

Problem

Prop Drilling
Solution

Context API

Draw

Context

↓

Every Component

↓

Access Data
Create Context
context

AuthContext.jsx
import{

createContext

}from"react";

export const AuthContext=

createContext();
Provider
<AuthContext.Provider

value={{user}}

>

<App/>

</AuthContext.Provider>

Explain

Every Component

Can Access

User.

useContext
const{

user

}=useContext(AuthContext);

Display

<h2>

Welcome

{user}

</h2>

Students now understand

Global State.

Second 90 Minutes
Authentication Flow
Login

Current

Local State

Replace

Context

Create

const[

user,

setUser

]=useState(null);

Login

setUser({

name:"Rahul"

});

Navbar

Welcome

Rahul

Automatically

Updates.

Students love this.

Logout
setUser(null);

Navigate

navigate("/login");
Protected Route

Create

function ProtectedRoute(){

}

Logic

if(!user){

return<Navigate

to="/login"

/>

}

Wrap

Dashboard

<ProtectedRoute>

<Dashboard/>

</ProtectedRoute>
Session Persistence

Store

localStorage

When

Login

Restore

Using

useEffect()

Students remain logged in after refresh.

Dashboard

Display

Logged In User

Total Courses

Total Students

Logout Button
Mini Challenge

Students add

Profile

Settings

Notifications

using Context.

Assignment

Complete Authentication Module

✔ Login

✔ Logout

✔ Context API

✔ Protected Dashboard

✔ Session Restore

✔ User Greeting

✔ Protected Routes
Final Project Progress
SkillHub LMS

Frontend
     │
React Router
     │
Context API
     │
Authentication
     │
Protected Routes
     │
Dashboard




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
🎯 What Students Achieve