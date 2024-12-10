# Express MongoDB

## Overview

This project showcases the successful implementation of an Express application integrated with MongoDB using Mongoose. The assignment focused on understanding the core concepts of MongoDB, setting up a cloud database on MongoDB Atlas, and creating a seamless connection to an Express server. Despite encountering challenges with GitHub and the local project, I was able to quickly regroup and resolve these issues, thus completing the assignment. Below are the details of my process, challenges, and accomplishments.

---

## Assignment Objectives

- Understand MongoDB and its key features.
- Set up a MongoDB Atlas account.
- Connect to MongoDB from an Express application using Mongoose.

---

## **Part 1: Introduction to MongoDB**

- **Key Features Learned :**
  - MongoDB is a NoSQL database storing data in flexible, JSON-like documents.
  - It is document-oriented, schema-less, and scalable.

---

## **Part 2: Setting Up MongoDB Atlas**

1. **Created MongoDB Atlas Account:**

   - Signed up for a free MongoDB Atlas account.
   - Created a cluster using the free tier.

2. **Database User Creation:**

   - Added a new database user with a secure username and password in **Database Access**.

3. **Whitelisted IP Address:**

   - Configured **Network Access** to whitelist my current IP address for secure connections.

4. **Connection String:**
   - Generated the connection string via **Clusters > Connect > Connect Your Application (Driver)**.
   - Stored the connection string securely in an `.env` file.

---

## **Part 3: Connecting to MongoDB from an Express Application**

1. **Project Initialization:**

   - Created a repository with a README.md and .gitignore set to Node.
   - Ran the following commands:
     ```bash
     git clone <repository_url>
     cd express-mongodb
     npm init -y
     npm install express mongoose
     code .
     ```
   - Ran the following commands in VS Code terminal:
     ```bash
     npm install mongodb
     npm install dotenv
     npm install --save-dev nodemon
     ```
   - In `package.json` added scripts for `nodemon`.
     ```json
     "scripts": {
         "start": "node index.js",
         "dev": "nodemon index.js"
       }
     ```

2. **Application Development:**

   - Created `index.js` to set up the Express server and MongoDB connection.
   - Created a `.env` file to store the MongoDB connection string securely.
   - Used `dotenv` to load environment variables.
   - Connected to MongoDB using `mongoose`.

   **Key Files:**

   - **index.js**

     ```javascript
     const express = require("express");
     const mongoose = require("mongoose");
     const app = express();
     const port = 3000;

     require("dotenv").config();
     const mongoUrl = process.env.MONGO_URL;

     // Middleware to parse JSON bodies
     app.use(express.json());

     // Connect to MongoDB
     mongoose
       .connect(mongoUrl, {
         useNewUrlParser: true,
         useUnifiedTopology: true,
       })
       .then(() => {
         console.log("Connected to MongoDB");
       })
       .catch((error) => {
         console.error("Error connecting to MongoDB:", error);
       });

     app.get("/", (req, res) => {
       res.send("Hello, World!");
     });

     app.listen(port, () => {
       console.log(`Server is running at http://localhost:${port}`);
     });
     ```

   - **package.json**
     ```json
     {
       "name": "express-mongodb",
       "version": "1.0.0",
       "scripts": {
         "start": "node index.js",
         "dev": "nodemon index.js"
       },
       "dependencies": {
         "dotenv": "^16.4.7",
         "express": "^4.21.2",
         "mongoose": "^8.8.4"
       },
       "devDependencies": {
         "nodemon": "^3.1.7"
       }
     }
     ```

3. **Testing the Connection:**
   - Started the server using `npm run dev`.
   - Verified successful MongoDB connection with the console log `Connected to MongoDB`.
   - Accessed `http://localhost:3000/` in the browser to see the "Hello, World!" response.

---

## Challenges Faced

### **GitHub and Local Project Issues**

- **Problem:**
  I encountered challenges syncing my local project with GitHub, which required a restart of the project setup.
- **Solution:**
  Took a step back to assess the issue, reinitialized the project, and carefully added the `.env` file to `.gitignore` to prevent sensitive data from being pushed.

---

## Accomplishments

- Successfully connected to MongoDB Atlas and implemented a functional Express application with Mongoose.
- Followed best practices for securing sensitive information using environment variables.
- Resolved technical issues effectively, demonstrating adaptability and problem-solving skills.

---

## How to Run the Project

1. Clone the repository.
   ```bash
    git clone <repository_url>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file and add the MongoDB connection string:
   ```
   MONGO_URL=your-mongodb-connection-string
   ```
4. Start the server:
   ```bash
   npm run dev
   ```
5. Access `http://localhost:3000/` in your browser.
