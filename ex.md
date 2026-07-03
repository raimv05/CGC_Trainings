DAY 14
Express.js Fundamentals
Duration

3 Hours

Learning Outcomes

Students will understand

Express.js
Server
Routing
Middleware
Request
Response
JSON
HTTP Status Codes
Project Goal

Create the first backend server for SkillHub LMS.

Final Deliverable
SkillHub Backend

GET /courses

POST /courses

Middleware

Express Server Running
First 90 Minutes
Express.js Basics
Part 1
Why Express?

Start with Question

Yesterday we wrote

Node.js

Can Node create APIs easily?

Yes

But

Too much code.

Need

Express
Install
npm install express
Create Server
const express=require("express");

const app=express();

const PORT=5000;
Listen
app.listen(PORT,()=>{

console.log(`Server Running on Port ${PORT}`);

});

Run

node app.js

Browser

localhost:5000

Nothing happens.

Need Route.

First Route
app.get("/",(req,res)=>{

res.send("Welcome to SkillHub Backend");

});

Refresh.

Students see response.

Explain
Request

↓

Server

↓

Response
Request Object
(req,res)

Explain

req

↓

Incoming Request

res

↓

Outgoing Response
Part 2
Routing

Create

app.get("/courses",(req,res)=>{

res.send("Course API");

});

Create

app.get("/students",(req,res)=>{

res.send("Student API");

});

Create

app.get("/about",(req,res)=>{

res.send("SkillHub LMS");

});

Open browser.

/courses

/students

/about
Route Parameters
app.get("/student/:id",(req,res)=>{

res.send(req.params.id);

});

Visit

localhost:5000/student/101

Output

101
Second 90 Minutes
Middleware + Course API
What is Middleware?

Analogy

Airport Security

Passenger

↓

Security Check

↓

Flight

Express

Request

↓

Middleware

↓

Route
Built-in Middleware
app.use(express.json());

Explain

Without this

POST Body

Cannot be read.

Logger Middleware
app.use((req,res,next)=>{

console.log(req.method);

console.log(req.url);

next();

});

Explain

next()

↓

Continue
Course API

Create

let courses=[];

GET

app.get("/courses",(req,res)=>{

res.json(courses);

});

POST

app.post("/courses",(req,res)=>{

courses.push(req.body);

res.json({

message:"Course Added"

});

});

Example

Postman

{
"name":"MERN",

"duration":"12 Weeks"
}
HTTP Status Codes

Explain

res.status(201)
200

201

400

404

500
Mini Challenge

Students build

GET /trainers

GET /dashboard

POST /students
Assignment

Create

Course API

Student API

Trainer API

using Express.

End Result
Express Server

↓

Routing

↓

Middleware

↓

GET

↓

POST
DAY 15
REST APIs
Duration

3 Hours

Learning Outcomes

Students learn

REST
CRUD APIs
GET
POST
PUT
DELETE
Postman
Request Body
URL Params
Project Goal

Complete Course CRUD APIs.

First 90 Minutes
REST Concepts

Draw

Frontend

↓

GET

POST

PUT

DELETE

↓

Backend

Explain

Method	Meaning
GET	Read
POST	Create
PUT	Update
DELETE	Delete
GET
app.get("/courses",(req,res)=>{

res.json(courses);

});
POST
app.post("/courses",(req,res)=>{

courses.push(req.body);

res.status(201).json({

message:"Course Created"

});

});
Postman Demo

Send

POST

localhost:5000/courses
Second 90 Minutes
PUT
app.put("/courses/:id",(req,res)=>{

const id=req.params.id;

courses[id]=req.body;

res.json({

message:"Updated"

});

});
DELETE
app.delete("/courses/:id",(req,res)=>{

courses.splice(req.params.id,1);

res.json({

message:"Deleted"

});

});
Test Every API

Students test

GET

POST

PUT

DELETE

using Postman.

Assignment

Complete

Student CRUD API

Trainer CRUD API
End Result
Complete Course CRUD

↓

Postman Tested
DAY 16
MongoDB Atlas
Duration

3 Hours

Learning Outcomes

Students learn

MongoDB
Collections
Documents
CRUD
Atlas
Compass
MongoDB Driver
Project Goal

Replace in-memory arrays with MongoDB.

First 90 Minutes
Introduction

Current

let courses=[];

Problem

Server Restart

↓

Everything Lost.

Need

Database
MongoDB Concepts

Explain

Database

↓

Collection

↓

Document

Example

SkillHub

↓

courses

↓

{

name:"React"

}
Atlas

Create Account.

Create Cluster.

Whitelist IP.

Create Database User.

Copy Connection String.

Second 90 Minutes
Install Driver
npm install mongodb
Connect
const {MongoClient}=require("mongodb");
Connection
const client=new MongoClient(uri);

await client.connect();
Insert
db.collection("courses")

.insertOne({

name:"React"

});
Find
find()
Update
updateOne()
Delete
deleteOne()
Assignment

Create

students

courses

trainers

Collections.

End Result
Express

↓

MongoDB Atlas

↓

Persistent Database
DAY 17
Mongoose ODM
Duration

3 Hours

Learning Outcomes

Students learn

Mongoose
ODM
Schemas
Models
Validation
CRUD using Mongoose
Project Goal

Build a production-ready backend for SkillHub LMS.

First 90 Minutes
Install
npm install mongoose
Connect
mongoose.connect(MONGO_URI);
Course Schema
const courseSchema=new mongoose.Schema({

name:String,

duration:String,

fees:Number

});
Model
const Course=mongoose.model(

"Course",

courseSchema

);
Student Schema
const studentSchema=new mongoose.Schema({

name:String,

email:String,

course:String

});
Enrollment Schema
const enrollmentSchema=new mongoose.Schema({

studentId:String,

courseId:String,

enrolledAt:Date

});
Second 90 Minutes
CRUD with Mongoose
Create
await Course.create(req.body);
Read
await Course.find();
Update
await Course.findByIdAndUpdate(id,req.body);
Delete
await Course.findByIdAndDelete(id);
Folder Structure
backend

controllers/

models/

routes/

config/

middleware/

app.js

Explain why we separate concerns.

Mini Challenge

Students create:

Trainer schema
Batch schema
Validation for required fields
Assignment

Refactor the LMS backend so that:

All routes use Mongoose models.
Course, Student, and Enrollment data are stored in MongoDB Atlas.
Add validation (required fields, email format where applicable).
Test all CRUD endpoints with Postman.