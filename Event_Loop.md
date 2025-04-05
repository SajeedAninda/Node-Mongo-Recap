🔄 What is the Event Loop?
The event loop is the mechanism that allows JavaScript (especially in Node.js and browsers) to handle asynchronous operations (like timers, API calls, file reading) without blocking the main thread — even though JavaScript is single-threaded.

It continuously watches and manages multiple queues, executing callbacks when they’re ready.

📌 Key Components Involved
Call Stack – Where your code is executed.

Heap – Memory storage for variables and objects.

Web APIs / Node APIs – Browser or Node-provided async functions (like setTimeout, fs.readFile, fetch, etc.)

Callback / Task Queue – Stores callbacks of completed tasks waiting to be executed.

Event Loop – The heart that connects all pieces.

Microtask Queue – A higher-priority queue for Promises, queueMicrotask, process.nextTick.

🔁 Step-by-Step Flow
1. Code Execution Starts
JavaScript runs top-down on the Call Stack.

It encounters functions like setTimeout, fetch, etc.

2. Asynchronous APIs Offload Work
Those async functions are offloaded to browser or Node APIs (not run in JS).

Example: setTimeout(cb, 1000) is sent to the timer API.

3. When Task Completes
After the timer/network/file operation completes, the callback is sent to the Callback Queue (aka Task Queue or Macrotask Queue).

4. Microtasks Check
Before picking callbacks from the Callback Queue, the Event Loop checks the Microtask Queue and clears it completely first.

5. Call Stack Execution
When the Call Stack is empty, the Event Loop moves tasks from the Callback Queue to the Call Stack (one at a time) and executes them.

🎯 Microtasks vs Macrotasks
Type	Example	Queue
Microtasks	Promises, process.nextTick, queueMicrotask	Microtask Queue
Macrotasks	setTimeout, setInterval, I/O callbacks	Callback Queue
Order of Execution:
Microtasks are always executed before the next macrotask.

🧪 Example
js
Copy
Edit
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
🔍 Output:
sql
Copy
Edit
Start
End
Promise
Timeout
💬 Why?
setTimeout is a macrotask — placed in the Callback Queue.

Promise is a microtask — placed in the Microtask Queue.

Microtasks are processed first, after current code finishes.

🧠 Node.js Event Loop Phases
Node.js event loop has 6 phases, and each handles different types of callbacks:

Timers Phase

Executes setTimeout and setInterval.

Pending Callbacks

Executes I/O callbacks deferred to next loop.

Idle / Prepare (internal)

Used internally by Node.

Poll Phase

Retrieves new I/O events (like reading from files).

Check Phase

Executes setImmediate() callbacks.

Close Callbacks

Executes close events like socket.on('close').

Note: After each phase, the Event Loop processes all microtasks before moving to the next phase.

🎨 Visualization
scss
Copy
Edit
while (true) {
  // 1. Execute all microtasks (Promises, nextTick)
  processMicrotaskQueue();

  // 2. Check each phase
  timersPhase();           // setTimeout/setInterval
  pendingCallbacksPhase();
  pollPhase();             // I/O
  checkPhase();            // setImmediate
  closeCallbacksPhase();
}
⚠️ Common Misunderstandings
Misunderstanding	Truth
JavaScript is multi-threaded	It's single-threaded (though Node uses background threads for I/O)
setTimeout(fn, 0) runs immediately	No, it's placed in the task queue, after current code & microtasks
Promises and setTimeout are handled the same	No, Promises are microtasks, setTimeout is a macrotask
🧾 Summary
Event Loop = Watches the call stack & task queues, and coordinates async behavior.

Microtasks are always processed before macrotasks.

Node.js has additional event loop phases.

Helps JavaScript remain non-blocking and asynchronous despite being single-threaded.