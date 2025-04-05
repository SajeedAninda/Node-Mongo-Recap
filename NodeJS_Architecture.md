🏗️ Node.js Architecture Overview
Node.js follows an event-driven, non-blocking I/O model, built on Google’s V8 engine and powered by libuv under the hood.

🔑 Key Characteristics:
Single-threaded (for JS execution)

Non-blocking & asynchronous

Event-driven

Uses a Thread Pool for handling heavy I/O tasks

🧠 Event-Driven Architecture in Node.js
In traditional web servers (like Apache), each client request creates a new thread. But in Node.js:

There’s a single main thread

Incoming requests/events are handled using callbacks or events

No new threads are created per request (unless needed for I/O)

🧲 How it works:
A client sends a request.

Node registers the request as an event.

Instead of blocking the thread, it assigns the task to the event loop.

When the task (like file read or DB fetch) finishes, it emits an event, and the callback is executed.

🔁 What is the Event Loop?
The event loop is the core of Node.js's non-blocking architecture.
It constantly listens for new tasks, executes them, and responds when asynchronous operations are completed.

💡 Key Point:
Node.js may be single-threaded, but the event loop allows it to handle many connections at once.