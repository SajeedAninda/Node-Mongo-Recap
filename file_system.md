The File System (fs) module in Node.js allows you to work with the file system—like reading, writing, updating, deleting, and renaming files and directories. It’s built-in, so no installation is needed.

const fs = require('fs');


You can use it in two ways:

Synchronous (blocking)

Asynchronous (non-blocking, preferred)

📄 Reading Files
Asynchronous
js
Copy
Edit
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
Synchronous
js
Copy
Edit
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data);
📝 Writing Files
Asynchronous
js
Copy
Edit
fs.writeFile('newfile.txt', 'Hello Node!', (err) => {
  if (err) throw err;
  console.log('File created!');
});
Synchronous
js
Copy
Edit
fs.writeFileSync('newfile.txt', 'Hello Node!');
🧩 Appending to a File
js
Copy
Edit
fs.appendFile('newfile.txt', '\nAppended text', (err) => {
  if (err) throw err;
  console.log('Updated!');
});
❌ Deleting a File
js
Copy
Edit
fs.unlink('newfile.txt', (err) => {
  if (err) throw err;
  console.log('File deleted!');
});
📁 Working with Directories
Create a Folder
js
Copy
Edit
fs.mkdir('newFolder', (err) => {
  if (err) throw err;
  console.log('Folder created!');
});
Read a Directory
js
Copy
Edit
fs.readdir('.', (err, files) => {
  if (err) throw err;
  console.log(files); // Array of file/folder names
});
Delete a Folder
js
Copy
Edit
fs.rmdir('newFolder', (err) => {
  if (err) throw err;
  console.log('Folder removed!');
});
🛠 Useful Options
Always provide 'utf8' when dealing with text files.

Use fs.promises or fs-extra for Promise-based file handling.