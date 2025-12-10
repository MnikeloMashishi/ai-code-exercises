Part 1: Understanding a Specific Feature

When I began exploring the code I focused on how tasks are created and how their statuses are updated. I did nott try to understand everything at once. Instead I looked at key files like models.js, cli.js and storage.js. Reading the README and scanning file names helped me get a basic picture before diving deeper.

To understand task creation, I searched the code for keywords like create, add, and status in both cli.js and models.js. With the help of AI, I traced how everything connects when the create command runs. I learned that the CLI command makes a new Task, sets its status and other fields, and then saves it through Storage. All data ends up written into a file, and each change updates that file.

Part 2: Deepen Understanding Through Guided Questions

I wanted to understand how priority works in the system. At first glance, it looked simple priorities like low, medium, high and urgent are assigned when a task is created and stored as fields. But I was not sure if priority affected sorting, overdue rules or anything else.

The AI asked helpful questions such as:
- Does priority influence how tasks are displayed or sorted?
- Does priority trigger any special logic in the code?
- What happens if a high-priority task becomes overdue?

After checking the code again, I realized that priority doesn’t change behavior, it is just stored for now. These guided questions helped me notice where I was making assumptions without evidence.

Part 3: Mapping the Data Flow

To understand what happens when a task is marked complete, I traced the whole flow:
- The user runs a CLI command
- The input is handled in cli.js
- The Task object is updated in models.js
- The updated tasks are saved by storage.js

I even drew a simple diagram:
CLI -> cli.js -> models.js -> storage.js -> file system

The AI helped me break this down further by asking questions like 'Who updates the status?' It also made me think about possible issues, such as what happens if saving fails or if the status change is invalid.

Part 4: Reflection and Presentation

After going through all this I feel like I understand the structure of the app much better. I can clearly see how task creation starts at the CLI, flows through the Task model, and ends with file storage. I also understand that priority is currently just a field, but it could be expanded into something more useful later. Completing a task simply means updating the status and saving the change.

I really like the design choice of separating the model logic from the storage logic. The hardest part at first was figuring out where everything lived, but using keyword searches and guided AI questions made it much easier to navigate the project without feeling overwhelmed.

If I had to present this to a team, I’d share how I approached the code step by step, starting with file names and the README, then searching for key terms, and using AI to ask deeper questions whenever something didn’t make sense. The prompts helped me avoid assumptions and stay confident that I wasn’t missing important details.