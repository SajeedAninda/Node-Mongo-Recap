🧠 Different Types of Parsers in Express.js
In Express, parsers are used to handle and extract data from incoming HTTP request bodies.
This makes it easier to work with req.body.

1️⃣ express.json()
Parses JSON data from the request body.

Used when you send data as Content-Type: application/json.

app.use(express.json());


2️⃣ express.urlencoded()
Parses data from HTML form submissions.

Used for application/x-www-form-urlencoded content-type (default from HTML <form>).

app.use(express.urlencoded({ extended: true }));



3️⃣ express.raw()
Parses raw binary data.

Used when you want the request body as a Buffer without any parsing.

app.use(express.raw());
✅ Use case:
File uploads or handling non-standard binary formats.

4️⃣ express.text()
Parses incoming requests with text/plain content type.

Converts plain text to req.body as a string.

app.use(express.text());