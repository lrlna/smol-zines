# Scavenging heaps: Garbage collection in V8
This guide is unlike others I've done so far, and has a bit of a narrative to go
along with the sketches. I thought the entire concept of garbage collection and how
it gets dealt with in javascript, or more specifically in engines that run
javascript, deserves a bit more of an explanation. I would also like to mention
that this guide is meant to be beginner friendly, and does not cover every aspect
of memory management within V8, and the rest of V8 internals. I've added a bunch
of [resources](#sources), if you want to delve into it more. This guide also
focuses on ✨ javascript ✨.Ok, so let's get started.

## What's v8?
V8, the javascript runtime engine, not to be confused with your fav tomato juice 🍹,
compiles and executes your beautifully written javascript. V8 comes with a generational,
stop-the-world garbage collector, which I am going to try to explain below. It
comes hand in hand together with Chrome. SpiderMonkey would be the Mozilla's
equivalent, and Chakra, Microsoft's. Basically when running javascript, you need
an engine to handle it for ya and V8 is one of your options. 

## What is garbage collection?
The essential point of garbage collection is the ability to manage memory usage
by a specific program. Languages such as C are generally able to hook into program's
memory management and allocate and free object within the context of the program.
ECMAScript, on the other hand, lacks that particular interface to access memory
management (yes, that means no API). Which basically means all *memory management*
rights™ in a program get passed over to V8. 

Since we don't have access to infinte amount of memory, garbage collector's job
is to go through objects that are allocated in memory and determine whether they
are *dead* or *alive*. Those that are alive get to stay in memory, those that are
dead get removed, and memory gets allocated back to the heap. 

*What's a heap though?* A heap is an unstructured region, where the objects get
allocated memory. This kind of allocation is *dynamic*, since the size /
lifetime / quantity of objects is unknown, so it needs to be allocated and
deallocated at runtime.

So if we look at the concurrency model, heap works directly with the call stack, 
as the objects showing up in the stack require memory allocation. It would look
something like this:

![concurrency model](./img/garbage-collection/stack-heap-queue.png)

## Dead or alive?
The basic check for when an object is dead or alive, is whether or not the
client, or the program that executes the code, can reach it. The most reachable
object you can think of, is probably an object defined in root scope. In vanilla
dot js(vanilla.js) on the client, this would look something like this:

```js
document.addEventListener("DOMContentLoaded", function () {
  var alive = "whoa i am alive" // object in root scope && reachable
})
```
Some C++ bindings (or web APIs on the client) are also part of the root, so you
can access things like `setInterval` directly.

Reachability could also be thought of as whether or not another object or root
can get a hold of it, if it can, the memory required by that object gets kept.

## 🆒 sources.js
- [memory management](http://www.memorymanagement.org/); i like reading through
the [glossary](http://www.memorymanagement.org/glossary/) section, cause you
discover a bunch of neat stuff.
