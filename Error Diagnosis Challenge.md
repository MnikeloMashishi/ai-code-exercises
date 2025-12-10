# Error Diagnosis Challenge
## Selected Scenario

## Global Variable Being Overwritten

I chose this JavaScript global variable error because it’s a subtle bug that often confuses developers. It highlights how variable scope can unexpectedly break code.

# Error Analysis
## Error message
TypeError: Cannot read properties of undefined (reading 'map')

## What it means:
This happens when you try to use map() on something that isn’t an array. Essentially, the code is trying to treat a single object (or undefined) like a collection.

# root cause
Inside the addTask function, the code looks like this:
let tasks = { id: Date.now(), name: taskName, completed: false };

## Why it breaks:
- let tasks declares a new local variable called tasks inside the function.
- This local variable hides the global tasks array, replacing it with a single object.
- Later, when displayTasks() runs tasks.map(), it fails because an object isn’t iterable.

# Solution

Remove let so you modify the global array instead of creating a new variable:
function addTask(taskName) {
  tasks.push({ id: Date.now(), name: taskName, completed: false });
  console.log("Task added:", taskName);
  displayTasks();
}

## Learning points
- Declaring a variable with let or var inside a function creates a new local variable, even if one with the same name exists globally.
- Be cautious with global variables — accidentally overwriting them can cause runtime errors.
- Use array methods like push() to add items instead of replacing the array.
- Choose variable names carefully to avoid shadowing globals.

# Applying Debug Prompts

Using Prompt 1 (Error Message Translation), I might ask:

"I’m getting a TypeError in my JavaScript task manager when I add a new task. It says 'Cannot read properties of undefined.' Can you explain why this happens, which line causes it, and what I should check in my variable declarations?"

AI can immediately pinpoint the variable hiding issue and explain it clearly in context, which is faster than sifting through documentation.