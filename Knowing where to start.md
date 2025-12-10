Part 1: Understanding Project Structure

At first glance, this looks like a Node.js task manager. The codebase isn’t big. I can see cli.js, app.js, models.js, and storage.js right away. There is a README fole as well.

I started questioning, how does this save tasks? Is there a database somewhere? After a quick look at storage.js, it looks like everything is saved to a local JSON file.

The main components are:
- The CLI (for interacting with tasks)
- Models (to describe what a task is)
- Storage (where tasks are saved or loaded)
- Main application logic (how everything connects)
 
Part 2: Finding feature implementation

If I were to add an 'Export Tasks to CSV' feature, I would start by searching the project for anything related to saving or exporting. After checking for keywords like export, save, file, and transform, it became clear that most of the task loading and saving happens in storage.js.

So it makes sense that the CSV export logic should live there. I’d create a function that takes the task data and turns it into CSV format. I’d also update cli.js so users can run this as a command

Part 3: Understanding 

The main thing the app deals with is a Task. Each task has a title, description, status (like todo, in progress, review, done), a priority level, a due date, and optional tags. The rules for how tasks move and behave seem to be handled in the model files and core logic.

Question I still have:
- Are there limits on what tags users can add?
- Can you change a task’s priority after it’s created?
- And how exactly does the app check if a task is overdue?

Part 4: Practical Application

For the rule that says any task overdue by more than 7 days should be marked as “abandoned,” unless it’s high or urgent priority, here’s what I would do:
- Add logic—probably in models.js or storage.js, that automatically checks for overdue tasks when the app loads or when tasks are displayed.
- Mark anything overdue by more than a week as abandoned, except high or urgent tasks.
- I’d also get input from the team on when this check should run: automatically on startup, or only when tasks are listed or updated.

Reflection

Breaking the problem into smaller parts made everything easier. At first I felt a bit overwhelmed, but searching by keywords and looking at the main files instead of reading everything line by line helped a lot. I still want to understand how task updates and validations work in detail, but now I know where to look and what to ask.

Next time, I’ll start by reading the README, checking the file structure, and then searching for keywords related to the feature I’m trying to understand. It’s definitely faster than trying to read the entire codebase.