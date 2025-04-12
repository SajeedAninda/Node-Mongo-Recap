🥇 Method 1: Using mongodb Native Driver
Step 1: Install the package
bash
Copy
Edit
npm install mongodb
Step 2: Connect to MongoDB
js
Copy
Edit
const { MongoClient } = require('mongodb');

// Replace this with your MongoDB connection string
const uri = 'mongodb://127.0.0.1:27017';
const client = new MongoClient(uri);

async function run() {
  try {
    await client.connect();
    console.log('MongoDB connected!');

    const database = client.db('testdb');
    const collection = database.collection('users');

    // Insert a document
    const result = await collection.insertOne({ name: 'Aninda', age: 25 });
    console.log('Inserted:', result.insertedId);

  } finally {
    await client.close();
  }
}

run().catch(console.dir);


CREATE AND GET OPERATIONS 

const http = require('http');
const { MongoClient } = require('mongodb');

// MongoDB setup
const uri = "mongodb://127.0.0.1:27017";
const client = new MongoClient(uri);
let usersCollection;

async function connectDB() {
  await client.connect();
  const db = client.db('testdb');
  usersCollection = db.collection('users');
  console.log("MongoDB connected");
}

connectDB();

// Node.js server
const server = http.createServer(async (req, res) => {
  if (req.url === '/users' && req.method === 'POST') {
    let body = '';
    req.on('data', chunk => body += chunk);
    
    req.on('end', async () => {
      try {
        const user = JSON.parse(body);
        const result = await usersCollection.insertOne(user);
        res.writeHead(201, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({ message: 'User created', id: result.insertedId }));
      } catch (err) {
        res.writeHead(500, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({ error: err.message }));
      }
    });
  }

  else if (req.url === '/users' && req.method === 'GET') {
    try {
      const users = await usersCollection.find().toArray();
      res.writeHead(200, { 'Content-Type': 'application/json' });
      res.end(JSON.stringify(users));
    } catch (err) {
      res.writeHead(500, { 'Content-Type': 'application/json' });
      res.end(JSON.stringify({ error: err.message }));
    }
  }

  else {
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('Route not found');
  }
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});

