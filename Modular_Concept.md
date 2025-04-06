🧩 What is a Module?
A module in Node.js is a separate file or piece of code that can be reused in other parts of your application.

📦 Think of it like:
Lego blocks – small, reusable, and each has a specific function. You can combine them to build something big and complex.

🧠 Why Use Modules?
🔁 Reusability – Write once, use many times.

🧹 Clean Code – Keeps codebase organized.

🔒 Encapsulation – Each module has its own scope.

🧪 Testability – Easier to test smaller pieces of code.

🔹 Types of Modules in Node.js
1. Built-in Modules
Provided by Node.js out of the box.
Examples: fs, http, path, os, events

js
Copy
Edit
const fs = require('fs');
fs.readFile('file.txt', (err, data) => {
  console.log(data.toString());
});
2. User-defined Modules
Your own custom code organized into files.

math.js

js
Copy
Edit
function add(a, b) {
  return a + b;
}
module.exports = add;
main.js

js
Copy
Edit
const add = require('./math');
console.log(add(5, 3)); // 8
3. Third-party Modules
Installed via npm (Node Package Manager).

bash
Copy
Edit
npm install express
js
Copy
Edit
const express = require('express');
const app = express();
🧰 How Modules Work Internally
Each module in Node.js is wrapped like this:

js
Copy
Edit
(function(exports, require, module, __filename, __dirname) {
  // your module code here
});
So each module has its own:

exports – To export functions/variables

require – To import other modules

__filename – File path of the module

__dirname – Directory path

🛠️ Exporting in Modules
✅ Export a single function or object
js
Copy
Edit
module.exports = function greet(name) {
  return `Hello, ${name}`;
}
✅ Export multiple values
js
Copy
Edit
exports.add = (a, b) => a + b;
exports.sub = (a, b) => a - b;
🧾 Summary
Node.js modules help split code into small, manageable files.

Three types: built-in, custom/user-defined, and npm/third-party.

Use require() to import and module.exports or exports to export.

Encourages clean architecture and code reuse.