🚀 Express.js — Why It’s Used
Express.js is a lightweight and flexible Node.js web application framework
used for building APIs and web servers easily and efficiently.

💡 Benefits of Express.js
✅ 1️⃣ Minimal & Fast

It’s a small framework but super powerful.

Makes handling HTTP requests, routing, and middleware easy.

✅ 2️⃣ Routing Made Simple

You can handle different URL paths with clean, readable code.

javascript
Copy
Edit
app.get('/', (req, res) => res.send('Hello World'));
✅ 3️⃣ Middleware Support

You can write reusable functions to handle requests (logging, validation, authentication) before they hit your route logic.

✅ 4️⃣ Simplified Request & Response

Express makes handling req and res objects intuitive and less verbose compared to raw Node.js.

✅ 5️⃣ Easy Integration

Works smoothly with databases like MongoDB, MySQL, PostgreSQL, Firebase, etc.

✅ 6️⃣ Template Engines Support

Easily integrates with EJS, Pug, Handlebars for server-side HTML rendering.

✅ 7️⃣ Scalable

Supports both small projects and large-scale enterprise APIs.

✅ 8️⃣ Strong Community & Ecosystem

Massive NPM package support.

Helpful and mature documentation.

✅ 9️⃣ Error Handling

Built-in error-handling pattern using middleware for consistent and centralized management.

✅ 🔟 RESTful API Friendly

Perfect for creating REST APIs that serve mobile apps, websites, or other services.

💡 Summary
Without Express —
You manually handle routing, status codes, headers, parsing, and responses.

With Express —
You write clean, short, professional server-side logic using simple methods like:

javascript
Copy
Edit
app.get()
app.post()
app.put()
app.delete()



POSTING DATA WITH EXPRESS 

const express = require('express');
const { MongoClient } = require('mongodb');

const app = express();
app.use(express.json());  // parse JSON bodies

const uri = "mongodb://127.0.0.1:27017";
const client = new MongoClient(uri);

async function main() {
  try {
    await client.connect();
    console.log("MongoDB Connected!");

    const db = client.db('testdb');
    const usersCollection = db.collection('users');

    // POST: Create new user
    app.post('/users', async (req, res) => {
      try {
        const newUser = req.body;
        const result = await usersCollection.insertOne(newUser);
        res.status(201).json({
          message: "User added successfully!",
          insertedId: result.insertedId
        });
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });

    // GET: Fetch all users
    app.get('/users', async (req, res) => {
      try {
        const users = await usersCollection.find().toArray();
        res.status(200).json(users);
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });

    app.listen(3000, () => {
      console.log('Server running at http://localhost:3000');
    });

  } catch (err) {
    console.error('Failed to connect to MongoDB', err);
  }
}

main();
