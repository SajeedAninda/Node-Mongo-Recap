In Node.js, the EventEmitter is a class in the events module that allows you to create, listen to, and emit custom events. It's part of the core API and is used extensively in Node.js for handling asynchronous events.

✅ Common Methods
Method	Description
on(event, listener)	Adds a listener
emit(event, [...args])	Emits the event
once(event, listener)	Listens only once
off(event, listener) / removeListener()	Removes a listener
removeAllListeners([event])	Removes all listeners

🔍 Real-World Use Case
EventEmitters are used behind the scenes in many core Node.js modules like:

http.Server (emits request, connection, etc.)

fs.ReadStream (emits data, end, etc.)

