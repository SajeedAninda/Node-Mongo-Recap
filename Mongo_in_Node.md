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
