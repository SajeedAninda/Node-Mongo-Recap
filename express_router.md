🚀 Routing in Express.js
Routing defines how your server responds to client requests for specific URLs (endpoints) and HTTP methods.

In short:
"When a client hits a certain URL with a specific HTTP method — what should happen?"

app — your Express application instance.

METHOD — HTTP method (get, post, put, delete, etc.).

PATH — the URL path.

HANDLER — function that runs when the route matches.

const express = require('express');
const app = express();

// GET Route
app.get('/', (req, res) => {
    res.send('Welcome to Home Page');
});

// POST Route
app.post('/submit', (req, res) => {
    res.send('Form submitted');
});

// PUT Route
app.put('/update', (req, res) => {
    res.send('Data Updated');
});

// DELETE Route
app.delete('/delete', (req, res) => {
    res.send('Data Deleted');
});

app.listen(3000, () => console.log('Server running on port 3000'));


🌍 Route Parameters
You can define dynamic segments in routes using :.

app.get('/user/:id', (req, res) => {
    res.send(`User ID is ${req.params.id}`);
});



💡 Query Parameters
Handled through req.query:

app.get('/search', (req, res) => {
    const keyword = req.query.keyword;
    res.send(`Search keyword: ${keyword}`);
});

