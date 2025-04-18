Routing in Node.js means handling different URLs (routes) and sending the appropriate response based on the request. You can do this using the built-in http module or a framework like Express.js (which is way easier for complex apps).

const http = require('http');

const server = http.createServer((req, res) => {
  const url = req.url;

  if (url === '/') {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.end('<h1>Home Page</h1>');
  } else if (url === '/about') {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.end('<h1>About Page</h1>');
  } else if (url === '/api') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Hello from API' }));
  } else {
    res.writeHead(404, { 'Content-Type': 'text/html' });
    res.end('<h1>404 Not Found</h1>');
  }
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});


RESPONSE HEADERS 

const http = require('http');

const server = http.createServer((req, res) => {
  // Set headers
  res.writeHead(200, {
    'Content-Type': 'text/html',
    'X-Powered-By': 'Node.js',
  });

  res.end('<h1>Hello with headers!</h1>');
});

server.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});



QUERY PARAMS 

const http = require('http');
const url = require('url');
const querystring = require('querystring');

const server = http.createServer((req, res) => {
  const parsedUrl = url.parse(req.url);
  const queryParams = querystring.parse(parsedUrl.query);

  console.log(queryParams); // example: { name: 'Aninda', age: '25' }

  res.writeHead(200, { 'Content-Type': 'application/json' });
  res.end(JSON.stringify({ message: 'Query Received', data: queryParams }));
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});


